---
title: "spellchecker not set for English language"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by biomedtech on 2009-11-13
Using Firefox web browser, I prefer to have the spell checker giving me feedback, but every word I type is marked as incorrectly spelled. I couldn't figure out why until I mistakenly typed a word in Spanish, and it was the only one not under-lined as a mistake. 

I am still running off of the UNR Live CD, and I did select English as the default for running the Live CD. I also selected English as the default language in the Ubuntu system settings. I also ran Update Manager to ensure I was up-to-date as of an hour ago, but typing in this forum still has a malfunctioning spell checker. 

Is there a way to reset Firefox's spell checker to English language?   The only option I saw was to disable it completely. Thank you

---

### Post by Jon Monreal on 2009-11-15
In a Firefox tab, type about:config. Click the button to get into the configuration settings.

At the top, you will see a box with "Filter:" before it. Type "spell". Go down to the entry "spellchecker.dictionary" and right-click it, selecting modify. Replace the value with "en-GB".

---

