---
title: "Grub looking for uninstalled usb hard drive"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by kdub on 2011-06-19
Long story short-I installed 10.10 onto a usb hard drive in order to place hard drive into my spare lap top (no cd/dvd,wont boot from usb) I used my hp tc1100 with an usb external cased drive to load Ubuntu. When I try to boot the tc now it looks for the exterenal drive-gives a drive not found error if the external drive is not plugged in.The tc is running ubuntu 10.10. How do I fix grub to boot from it's internal drive?
thanx
kdub

---

### Post by jtarin on 2011-06-19
Simple fix might be to just boot with the drive plugged in then when it gets to the desktop unplug it......make sure it doesn't show as in a terminal the command ```
df
```then ```
sudo update-grub
```watch the print out and it should not detect it (the drive)reboot.

---

### Post by kdub on 2011-06-19
Jatarin,
thanx for the suggestion but upon reboot I still get amessage that says that the usb drive is not found (it's not plugged in), next line is grub rescue and a blinking curser. It wasn't listed when I followed your suggestion (thought sure that would get it-)
thanx
ken

---

### Post by jtarin on 2011-06-19
Issue the command ```
sudo grub-update
``` see if it lists the USB drive still in the terminal window.....After you unplug it.
If it will still not boot without the USB plugged in try the command "sudo grub-install /dev/sdx" (Where /sdx is the partition you want to install Grub to..should be /sda, /sdb something like that) The usage is basically very simple. You only need to specify one argument to the program, namely, where to install the boot loader. The argument has to be either a device file (like &#8216;/dev/sda&#8217;). For example, under Linux the following will install GRUB into the MBR of the first disk:```
sudo grub-install /dev/sda
```
Watch the printout after the command runs to see if Grub did or did not detect your drive in question.

---

### Post by kdub on 2011-06-19
No,
following your directions it wasn't listed.
thanx
ken

---

### Post by jtarin on 2011-06-19
> **kdub said:**
> No,
following your directions it wasn't listed.
thanx
kenNow reboot and see if things are OK

---

### Post by kdub on 2011-06-20
Jtarin please ignore my previous post.I followed your directions and got:

sudo grub-install /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
p.s. the tc1100 hard drive is broken into 3 partions (a 60 gig , a 52 gigand the os)

---

### Post by jtarin on 2011-06-20
If you are using Grub as bootmanager for all OS's on the disk...then it should be placed in MBR of /dev/sda. If you are using another bootloader in that location and using it to chainload Grub then place Grub at the "/" of the partition you have a Linux OS.

---

### Post by kdub on 2011-06-20
J,
Ionly have the one Ubuntu 10.10 installed on my drive-the 52 and 60 gig parts are free space
kdub

---

### Post by jtarin on 2011-06-20
Then amend your command:
sudo grub-install /dev/sda

---

### Post by kdub on 2011-06-20
J,
It worked!! Thankyou,thankyou
Hope I can help someone else some time
again thankyou,
Ken

---

### Post by jtarin on 2011-06-20
Excellent!! As you learn your way around the system I am sure you will be able to help someone else in the near future. Mark this thread as solved and you will help your first one when they have the same problem.

---

