---
title: "Keyboard shortcut to toggle power scheme settings?"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by pforkp on 2010-12-03
Hi, I've been running Ubuntu 10.10 for a month now after switching from Windows, so I have only basic experience with Linux.

What I want to do is have a keyboard shortcut or a script that changes the power management setting that puts the display to sleep when inactive. It's for gaming and watching movies online - it's really annoying to have to move my mouse every so often, and I don't want to manually adjust power settings every time I want to watch or play something.

Is it possible to create a shortcut that toggles this setting between two values (put the display to sleep in 15 minutes, and never put the display to sleep)?

---

### Post by pforkp on 2010-12-03
Solved my own problem - I'll post the solution here if anyone else is looking for this.

Went to System>Preferences>Keyboard Shortcuts
Added 2 new ones with these commands: 

1) PM 15mins - command: gconftool-2 --type int --set /apps/gnome-power-manager/timeout/sleep_display_ac 900

2) PM Off - command: gconftool-2 --type int --set /apps/gnome-power-manager/timeout/sleep_display_ac 0

Bound these to some keys, and poof! I can change the power management settings by using shortcuts!

---

