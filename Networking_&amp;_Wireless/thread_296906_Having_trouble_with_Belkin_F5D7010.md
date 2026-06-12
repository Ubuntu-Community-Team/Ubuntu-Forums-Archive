---
title: "Having trouble with Belkin F5D7010"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by Heyholetsgogrant on 2006-11-10
:(  Im having trouble getting my Belkin F5D7010 Ver.5100 (notebook wireless card) to work.  I searched the forum and found instructions [http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813), but for some reason it will not let me copy the driver to the 'sudo mkdir /windows-drivers'  The created windows file is located in the file system.  When ever, I try to copy the driver to that file keeps saying "You do not have permissions to write to this folder."  Does anyone know how I can get this belkin card to work?  I'm not very good at this, because I just started using Ubuntu a few days ago (I'm currently using the newest verison of Ubuntu 6.10?).  One last question is, can anyone provide me a link to either bestbuy or compusa.com, so if this card does not work, I can just buy a card for a laptop that works out of the box?


Thanks!

-Grant

---

### Post by FrodoB on 2006-11-10
He is saying to create the directory:

$ sudo mkdir /windows-drivers

Then copy your drivers into /windows-drivers, so that would be:

$ sudo cp driver_name /windows-drivers

where driver_name is the name of whatever file you want to copy into the directory.

---

### Post by joyflop on 2007-02-04
FrodoB,

I tried your instruction, and got an error message:

pam@ubuntu-laptop:~$ sudo cp Rt2500.INF /windows-drivers
Password:
cp: cannot stat `Rt2500.INF': No such file or directory

I am using the same post that Heyholetsgogrant referenced ([http://www.ubuntuforums.org/showthread.php?t=272813)](http://www.ubuntuforums.org/showthread.php?t=272813)).

Sorry it's such a beginner's question, I am still learning :)

Pam

---

