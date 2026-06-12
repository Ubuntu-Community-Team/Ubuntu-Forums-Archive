---
title: "Verifying DMI pool data."
date: 2011-06-19
forum: New to Ubuntu
---

### Post by wavemaker on 2011-06-19
Gooday all. I am still in the process of getting this off the ground. I am here in absolute beginner talk as I feel I should have been able to sort this by now. I have downloaded latest Ubuntu ISO,stuck it on my machine, did updates etc and am now having fun getting to know it.
As reported earlier I have put it onto a spare machine that was working well with the previous hard drive with windoze on it. I have been able to get it to go through the full install process with updates and proprietary drivers all happening through the installation. Little sign comes up and says. Installation complete, Restart machine now? yes ticked. Goes down for reboot, ejects disc on the way, press enter, machine winds down, goes to restart. I get the following output on the monitor
:Verifying DMI pool data, update success.Boot failure, insert system disc and retry:
HD is a Seagate Barracuda 7200.7, 80gb.unsure of other details other than it's in a pretty old viewmaster  box. 1 stick of ram, prolly 512.Help/comments appreciated

---

### Post by fooman on 2011-06-19
make sure that there are no other bootable devices such as floppy or another cd/dvd inserted, or a flash drive/external usb hard drive plugged in when you try to boot.

also might want to check the boot order in the bios?

---

### Post by wavemaker on 2011-06-19
Thanks fooman. I will have a look at that tonight.

---

### Post by HereInOz on 2011-06-19
If you have replaced the hard drive from the time when you had Windows on the machine, make sure that you have set the jumpers on the hard drive, which is bound to be an IDE drive, given the age of the machine, to set the disk as the master.  

If it is set as a slave drive, then it is possible that Ubuntu will install on it but the system won't then boot from it.  I can't remember the jumper settings for Seagate drives, but it should be on there somewhere.

Also, make sure that the drive is visible in the BIOS, and that the boot order has the hard drive first.

---

