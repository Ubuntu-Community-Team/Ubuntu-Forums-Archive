---
title: "stuck in purple screen in ubuntu 10.04 LTS for 30s after login &amp; plymouth error"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by prams on 2010-05-04
i had a recent problem in ubuntu 9.10 ,in which i cant shut it down completely , i used the tricks in this forum but none worked ,i decided to upgrade to 10.04 downloaded the upgrade via synaptic package manager & installed it ,when i restarted the pc the screen showed me something like 

plymouth main process(255  killed by KILL signal ,even the ubuntu logo isnt coming as in 9.10

i then logged in & a purple screen came & stuck there for 30s ,no hard disk activity was observed during that time , then finally the actual desktop came 
although i could shut it down properly
the whole process took around 1 minute , can anybody tell how i could start faster ,why this i s happening & how to solve it

---

### Post by Troublegum on 2010-05-04
Does your computer have a floppy drive installed? I've read some reports from people *without* floppy drive, that they had to wait very long between gdm and the desktop. When they deactivated their floppy controller in BIOS, it worked ok. 

See [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515)

Hope that works for you.

---

### Post by prams on 2010-05-04
> **Troublegum said:**
> Does your computer have a floppy drive installed? I've read some reports from people *without* floppy drive, that they had to wait very long between gdm and the desktop. When they deactivated their floppy controller in BIOS, it worked ok. 

See [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515)

Hope that works for you.
i cant see any option to disable floppy drive in bios ,
i am using a PHOENIX AWARD BIOS ,
can anyone tell me how to do it

---

### Post by prams on 2010-05-05
I entered the following code in the terminal , after which ubuntu booted faster but it istill stucks for 30s after login & i get a new error " unknown user id(0)" before GDM comes . i then changed the plymouth theme to solaris but the theme still didnt show durin boot. finally when i shut down pc  the theme finally appeared. i guess its not a problem of my graphic card


Code:
 	gksu gedit /etc/initramfs-tools/conf.d/splash 
 and add this option FRAMEBUFFER=y, save the file.
Then
 	Code:
 	sudo update-initramfs -u

---

### Post by hellomoto on 2010-05-05
Please see for further details, a bug for this has been filed on launchpad

[http://ubuntuforums.org/showthread.php?t=1468152](http://ubuntuforums.org/showthread.php?t=1468152)

---

### Post by prams on 2010-05-05
i have intel graphic card in my pc & intel p4 processor

---

### Post by prams on 2010-05-05
> **hellomoto said:**
> Please see for further details, a bug for this has been filed on launchpad

[http://ubuntuforums.org/showthread.php?t=1468152](http://ubuntuforums.org/showthread.php?t=1468152)

this bug is reported for nvidia graphic card not intel graphic card

---

### Post by gerardojerry on 2010-05-05
Wow if you disable the floppy disk in bios LTS starts really fast, from login screen to desktop, try this and you will see the difference:p :guitar:

---

### Post by prams on 2010-05-05
> **gerardojerry said:**
> Wow if you disable the floppy disk in bios LTS starts really fast, from login screen to desktop, try this and you will see the difference:p :guitar:
how do i do it in phoenix award bios

---

### Post by Troublegum on 2010-05-05
Hey prams, 

should be in "Standard CMOS Features" -> "Floppy". Select "None" or "Not installed" or "Disabled". See Picture.

If that alone does not help, you could try to uncomment the floppy drive in /etc/fstab. To do that, hit ALT+F2 on your keyboard and type
```
gksudo gedit /etc/fstab
```
Then look for a line that begins with 
```
/dev/fd0
```
Uncomment that line by inserting a # at the beginning:
```
#/dev/fd0
```
Then reboot.

---

### Post by prams on 2010-05-06
> **Troublegum said:**
> Hey prams, 

should be in "Standard CMOS Features" -> "Floppy". Select "None" or "Not installed" or "Disabled". See Picture.

If that alone does not help, you could try to uncomment the floppy drive in /etc/fstab. To do that, hit ALT+F2 on your keyboard and type
```
gksudo gedit /etc/fstab
```Then look for a line that begins with 
```
/dev/fd0
```Uncomment that line by inserting a # at the beginning:
```
#/dev/fd0
```Then reboot.

a million thanks to u man , thanks for pasting the thumbnail, the solution just
  worked:lolflag:  can anyone tell me how get the plymouth theme workin ????

---

