---
title: "Can't get some hotkeys and touchpad  to work on jaunty"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by king EZi on 2009-05-31
I recently bought a new laptop (Lenovo g430) after getting my older one (benq s41) stolen...i had to get some ubuntu so i got jaunty, everything seems to work okay except for the touchpad being disabled on every startup and my "network" hotkeys dont work at all...if i want to enable/disable WiFi or bluetooth i have to reboot to windowz XP and do it there...and for the touchpad, i have to tap the enable/disable key twice to get it working...im not sure if it's jaunty coz i tried with 8.04 and its the same problem...please help.

---

### Post by SunnyRabbiera on 2009-05-31
Hmm, well the hotkeys thing might not be solvable, most hotkeys dont really work for Ubuntu but its not really our fault.
As for the touchpad, do you at least have a mouse?
I typically use mice myself, I never liked touchpads.

---

### Post by Mark Phelps on 2009-06-01
Not sure from your post what worked and what didn't in 8.04, but as to hotkeys, I found on one machine that they stopped working altogether on an upgrade to 9.04.  Not able to get a solution to that.

If the touchpad worked in 8.04 and doesn't not, it's most probably because 9.04 quite using the xorg.conf file for touchpad support.  If you have an old copy of your xorg.conf file, or if the touchpad lines are commented out in your current file, you can either paste the lines into the new file from the old, or remove the comments from the lines in the new, and once you restart X, the touchpad should work again.

As to the other problems, if they didn't work in 8.04, unless there was a specific bug written against them, they most likely will remain in 9.04.  Suggest you check the networking subforum for fixes to the wireless problem -- it's a common one and there are several posts there that address that.

---

### Post by king EZi on 2009-06-02
I tried 8.04 but touchpad problem is still the same...and i also tried some other distros but i still have to tap it twice to get it moving, anyways thats the least of my worries. My main concern is to be able to enable and disable WiFi and bluetooth...

---

