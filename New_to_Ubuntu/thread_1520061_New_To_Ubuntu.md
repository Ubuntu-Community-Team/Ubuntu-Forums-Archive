---
title: "New To Ubuntu"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Zunair on 2010-06-29
Hi every one.
This is Zunair and am mighty glad to join the community of Ubuntu.
Well i recently installed ubuntu 10.04 and every thing is great except for the fact that.
To begin with im using inspiron 1525. After upgrading my OS i noticed fuzzy power management issue when i got into BIOS the battery was fully charged i plugged in the supply booted and after coming to main screen that is after login. when i take out my power supply and switch back in immediately the meter on top panel shows it would take 5 hours to charge the battery.
I can't understand how to fix this bug. I would be obliged if some one can help me out in this matter even though it's no big deal but the perfection of Ubuntu is not here.
apart from that. i would also like to say that switching from windows 7 to Ubuntu was a great idea with tons of stuff to keep me busy thanks every one for making this possible.
cheers.
and if some one can help me for that thanks in advance

---

### Post by Zunair on 2010-06-30
i accidently deleted battery icon on top panel would some one be kind enough to tell how to restore the panel

---

### Post by modularModel on 2010-06-30
Hey Zunair, welcome to Ubuntu, hope you will enjoy using as well as learning more about it.

About the problem you're experiencing I dont have much in the way of a fix since I dont use a laptop with Ubuntu on it myself.
But I could tell you how to restore that applet, right click on the top panel and press "Add to panel", there among other cool applets should be the one you are looking for :p

---

### Post by Jakiejake on 2010-06-30
It should be part of the Indicator Applet or Notification Applet
Right Click on the panel (that bar where the battery symbol is/was) and click add to panel then add either the Indicator or Notification Applet one of them should work

---

### Post by mörgæs on 2010-06-30
The battery indicator showing strange values is a known bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258)

---

### Post by Zunair on 2010-07-01
> **modularModel said:**
> Hey Zunair, welcome to Ubuntu, hope you will enjoy using as well as learning more about it.

About the problem you're experiencing I dont have much in the way of a fix since I dont use a laptop with Ubuntu on it myself.
But I could tell you how to restore that applet, right click on the top panel and press "Add to panel", there among other cool applets should be the one you are looking for :p

> **Jakiejake said:**
> It should be part of the Indicator Applet or Notification Applet
Right Click on the panel (that bar where the battery symbol is/was) and click add to panel then add either the Indicator or Notification Applet one of them should work

thanks a lot for your kind words and am really enjoying ubuntu thanks to the community making it happen
as far as the bug is concerned thanks for telling me i'll be reading this page after this reply

---

### Post by lkjoel on 2010-07-01
Yes, Welcome to Ubuntu!
If the power meter still does not work, there are many alternatives.
Try downloading LinuxEssentials in my signature.
Extract it (there should be an Archive Manager somewhere)
Then open a Terminal (Applications->Accessories->Terminal) window and type this in (Hold the text, and type CTRL+C, then on the Terminal type CTRL+SHIFT+V)
```
cd "path/to/your/extracted/folder"
chmod +x FASTGNOME.sh
chmod +x FASTKDE.sh
chmod +x FASTXFCE.sh
./FASTKDE.sh
```You might wonder what chmod means.
It changes properties of files.
chmod +x makes a file executable.
./ executes a file.
cd changes directories. (**C**hange **D**irectories)

---

