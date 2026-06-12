---
title: "blank taskbar after login"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Sbarton on 2010-09-14
Hi all! This is what I am getting at login, after typing name and password I get the Desktop with 1 blank taskbar at the bottom of sceen, no icons / applets. clicking / right clicking taskbar/screen does nothing. I have tried Ctrl+Alt+F1 which takes me to a black screen no with no curser also Ctrl+Alt+F2 which does nothing. I cannot proceed further with no Terminal.I installed the Cosmos wallpaper pack from System/Preferences/Appearance 2 days ago but have rebooted a number of times successfully. Any help to progress this is appreciated.
regards & thanks.
sbarton

---

### Post by ubudog on 2010-09-14
If you can, can you try removing the cosmos background and see what happens?

---

### Post by drpjkurian on 2010-09-14
Hi
I do not think that it is related to the cosmos wall paper. Ir may be due to crashing of display manager programme. Why cant you google it in that way

---

### Post by drpjkurian on 2010-09-14
Hi boot into terminal and then try the
```
dpkg-reconfigure gdm
```

Hope it will help you

---

### Post by Sbarton on 2010-09-14
Thanks to you all who responded with help!
It was solved eventually by selecting (at login) to start a gnome session 'xterm' and then typing the necessary code:```
rm -rf -/.gconf/apps/panel
``` and then rebooting. Afterlogin I had to add the icons I had before to the taskbar.Everything is now fine.
Once again thanks for your responses and time
regards
sbarton

---

### Post by ubudog on 2010-09-14
Cool.

---

