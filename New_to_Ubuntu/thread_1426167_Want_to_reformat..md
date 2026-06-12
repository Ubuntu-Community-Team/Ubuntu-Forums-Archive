---
title: "Want to reformat."
date: 2010-03-09
forum: New to Ubuntu
---

### Post by at2smithjason on 2010-03-09
I want to reformat my computer, but when I try to boot from the CD that I have installed it just runs up to ubuntu instead.  I would like to go back to windows (sorry), because there are a few games that I want to get back into playing again.  Is there anything that I can get with the software center that I can use to completely wipe out my HDD so that I can load windows again.

---

### Post by fivex on 2010-03-09
Try burning a netbook remix cd to see if you can boot off that.
Then using gparted(should open by just typing in gparted into the terminal), delete all the partitions.

---

### Post by Phillomath on 2010-03-09
Sounds like a bios setting.  When you boot the computer, a screen should flash up telling you to press one of the F1-12 keys to "Enter Setup" or possibly "Enter Boot Menu".  If you hit the correct key when prompted you should be able to set the computer to try booting from your CD first and your HDD second.

After you've done that and inserted your windows cd watch for a prompt "Hit any key to boot from CD" or something similar. That should get you into the windows installer.

There is a command which will wipe the entire drive while the system is running but I don't recommend using it unless you get the PC to boot from a CD first. Otherwise you'll be stuck with a blank system and no way to install a new one.

---

### Post by at2smithjason on 2010-03-09
But here is the thing, I want to go to windows.  I want to totally reformat this HDD.

---

### Post by Phillomath on 2010-03-09
Also you are aware that you can install Ubuntu and Windows side by side right?  That way  you can play all your games on windows and still use the awesomeness that is Ubuntu for everything else.

---

### Post by fivex on 2010-03-09
> **at2smithjason said:**
> But here is the thing, I want to go to windows.  I want to totally reformat this HDD.

It's possible to do that using the windows cd by deleting all partitions. I have no idea if it will deleted an extended type partition, so it's best to check to see if you have one in gparted or somesuch.

---

### Post by Phillomath on 2010-03-09
Both the windows and Ubuntu installation disks allow you to reformat the disk before installing.

---

