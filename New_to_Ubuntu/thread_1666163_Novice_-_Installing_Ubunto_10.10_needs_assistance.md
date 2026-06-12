---
title: "Novice - Installing Ubunto 10.10 needs assistance"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by nmc70 on 2011-01-13
Hello.
 
Please can someone offer me some assistance?
 
I am a complete novice looking to install Ubunto version 10.10 from a CD on an old machine I have with the aim of learning all about Linux. 
 
I have amended the boot sequence to boot from CD first, but on doing so the machine gets to the boot screen and them aborts linux install, leaving only "boot" as the last entry on the screen with a flashing underscore/ line.
 
I have a feeling that my keyboard is not being recognised at this point, but don't know how to get round this to start the installation?
 
In addition to the above, the disk I am installing it on is partitioned for which I would like to either install on the larger partition or even better wipe the whole thing leaving no partitions and only Ubunto on the drive. If you can, please can you offer some guidance on this also?
 
Much appreciated
nmc

---

### Post by NightwishFan on 2011-01-13
Firstly, make sure the disk is burned properly. When you insert the CD and reboot, you should see a purple screen with a white logo at the bottom briefly. While that is up press any key to get a menu. Choose "Check CD For Errors". If you do not get to this screen, then refer to the instructions here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This may not be the problem though and you might need certain boot parameters to boot. If the disk checks out OK, reboot again and go back to that menu. Highlight "try ubuntu" and press F6. Highlight the option that says "nomodeset" and press enter to enable it. Press ESC, and then ENTER again to try to boot. Do you get to a desktop?

---

### Post by Legeril on 2011-01-13
I would advise an Ubuntu 10.04 installation, 10.10 may be the newest release but 10.04 is the most stable and the most likely to support your hardware, just saying :)

---

### Post by hansolo4949 on 2011-01-13
I agree, you should try 10.04. You might have gotten a bad .ISO file, which would make installing linux with that iso a no-go:( You should also try re-burning the CD and re-downloading the .ISO to see if it just got corrupted or not.

hansolo4949

---

