---
title: "Problem with HDMI"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Anouthen on 2010-12-27
I'm using a ATI HD 5570, along with a Acer G245H hooked up through HDMI. Grub loads, and works up to the point when your past the purple ubuntu loading screen. Then my monitor goes black.

I'm very new to ubuntu/linux and have no clue what do to from here in order to get this to work properly D:

Please help me!

---

### Post by Anouthen on 2010-12-27
Bump! Please I need some help D:

---

### Post by papibe on 2010-12-27
After a few secs you get the black screen press Alt-Ctrl-F1 so can get into text mode. Log into your account and look into the X Windows log:
```
$ more /var/log/Xorg.0.log
```
It's a long log so search for errors (/error the first time and then n for next). Another way would be filter it:
```
$ grep -i error /var/log/Xorg.0.log
```
Post what you find here.

Regards.

---

