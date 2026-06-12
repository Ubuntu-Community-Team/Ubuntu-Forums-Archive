---
title: "ubuntu 11.04 booting problem"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by deepakpathak on 2011-06-12
I have installed ubuntu 11.04 in sony vaio laptop along with windows7 using bootable usb externally(not wubi), I m facing following problems:
1. While booting ubuntu , in few seconds laptop gets suspended and screen gets off while power remains on and then it is to be restarted. If mouse pad is browsed continuously during boot it gets loaded. I have adjusted power settings , but still the problem persists...help me out.
2. Grub 2 is not getting updated , i have changed settings in startup manager regarding default OS but its not getting changed,& yeah font settings are getting updated.

---

### Post by westie457 on 2011-06-12
> **deepakpathak said:**
> I have installed ubuntu 11.04 in sony vaio laptop along with windows7 using bootable usb externally(not wubi), I m facing following problems:
1. While booting ubuntu , in few seconds laptop gets suspended and screen gets off while power remains on and then it is to be restarted. If mouse pad is browsed continuously during boot it gets loaded. I have adjusted power settings , but still the problem persists...help me out.
2. Grub 2 is not getting updated , i have changed settings in startup manager regarding default OS but its not getting changed,& yeah font settings are getting updated.


Hello, Try this first

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Read it through at least twice to understand what you will be doing and do not try to rush things. It will work quick enough taking it 1 step at a time.

It worked for me when I had a similar problem.

If this does not work for you come back here and we will look at other options.

---

### Post by Mark Phelps on 2011-06-12
Does your laptop have the ability to boot from CD/DVD? 

IF not, be VERY CAREFUL messing around with reinstalling GRUB.  WHY? Because if you accidentally install GRUB to the Win7 boot partition, that is likely to corrupt it and render Win7 unbootable after that.

If you do have the ability to boot from CD/DVD, then before you do anything else, use the Win7 backup feature to create and burn a Win7 Repair CD.  That will give you the ability to repair the Win7 boot loader -- should it become corrupted during your GRUB reinstall.

---

