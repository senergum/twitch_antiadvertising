# twitch_antiadvertising
Script in TamperMonkey


## Отключение "Помогите каналу ***, отключив блокировщик рекламы Стримеры зарабатывают деньги, когда зрители смотрят рекламу или покупают Twitch Turbo, чтобы обойтись без рекламы"
### установить расширение tampermonkey https://chromewebstore.google.com/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo?hl=ru
### Добавить новый скрипт 
```
// ==UserScript==
// @name         Twitch Auto Click Overlay Button (Observer)
// @namespace    http://tampermonkey.net/
// @version      2.0
// @description  Автоклик при появлении оверлея на Twitch
// @author       You
// @match        https://www.twitch.tv/*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    // Селекторы
    const triggerSelector = 'div.player-overlay-background.player-overlay-background--darkness-3';
    const buttonSelector = 'button[aria-label="Вернуться к трансляции"]';

    function tryClick() {
        const trigger = document.querySelector(triggerSelector);
        const button = document.querySelector(buttonSelector);

        if (trigger && button) {
            console.log("клик");
            button.click();
            return true;
        }
        return false;
    }

    tryClick();

    const observer = new MutationObserver(() => {
        tryClick();
    });

    observer.observe(document.body, {
        childList: true,
        subtree: true
    });
})();

```
