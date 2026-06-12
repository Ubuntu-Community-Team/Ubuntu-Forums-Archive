---
title: "FAST help with the 10.04 zoom feature"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by thejakeman on 2010-05-07
When you press and hold the super/boss/windows/<mod4> key and click and drag with the middle mouse button it does some zoom thing. HOW in the world does one get out of this zoom feature back to a normal un-zoomed desktop? Please help!

---

### Post by YuiDaoren on 2010-05-07
> **thejakeman said:**
> When you press and hold the super/boss/windows/<mod4> key and click and drag with the middle mouse button it does some zoom thing. HOW in the world does one get out of this zoom feature back to a normal un-zoomed desktop? Please help!
SuparKey+Mousewheel_Down

(Actually a Compiz thing)

---

### Post by thejakeman on 2010-05-07
> **YuiDaoren said:**
> SuparKey+Mousewheel_Down

(Actually a Compiz thing)

Didn't work, but I'll just reboot every time it happens. Rebooting is so fast these days it doesn't really bother me.

---

### Post by manoriax on 2010-05-07
Try this:
```
sudo apt-get install compizconfig-settings-manager
```
Navigate to:
System -> Preferences -> CompizConfig Settings Manager
There, select "Enhanced Desktop Zoom" and check the key bindings.

---

### Post by YuiDaoren on 2010-05-07
> **thejakeman said:**
> Didn't work, but I'll just reboot every time it happens. Rebooting is so fast these days it doesn't really bother me.

You could also install "Advanced Desktop Effects Settings (ccsm)" and use it to turn off the magnifier (or otherwise adjust it.)

___EDIT_____
What [manoriax]("http://ubuntuforums.org/member.php?u=626193") said. :)

---

### Post by johntramp on 2010-08-26
Use the same mod4+middle drag from one corner of the screen to the opposite corner to zoom out again.

---

