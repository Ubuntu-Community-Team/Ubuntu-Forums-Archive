---
title: "Please help get my notebook booting"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by sjhupp on 2010-05-16
Hi all, hoping someone could help please.
I have a compar F500 series laptop, and I wiped Vista and put Lucid 10.04 64bit on it.  After getting wireless driver going, everything seemed fine.
But then I tried to make a bootable usb stick for clonezilla, and I must have done something incorrectly, as next boot I get a blank screen and no disk activity. Could grub be screwed?
Interestingly I can't get anything on the screen now, no display at all. Sounds like it will read a CD/DVD but nothing will boot, can't get to bios.
I've got the hdd hooked up to another 10.04 server box, but not sure hoe to go about repairing grub, to see if that's the issue.
Any ideas?
I obviously don't want to screw my server box up either :confused:
Thanks.

---

### Post by garvinrick4 on 2010-05-16
Can you boot off of the installation CD in try only mode. If you can post what you get
using.

```
sudo fdisk -l
```

That is a small L.

Hopefully it will show something. Clonezilla is a very dangerous if you do not know how to use it. Been there done that.

---

### Post by sjhupp on 2010-05-16
Can't get it to boot off any media - no screen display, no BIOS, nothing.
Hooked up to my server box it does show:

simon@ubuntu:~$ sudo fdisk -l
[sudo] password for simon:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1e40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       30402   243947521    5  Extended
/dev/sda5              32       30402   243947520   8e  Linux LVM

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f230

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9328    74920960   83  Linux
/dev/sdb2            9328        9730     3227648+   5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

The 80gb is the laptop drive in question.

Have used clonezilla quite a bit, and think it's great, but I wanted to use a usb stick rather than CD image. It was creating the usb stick via the commands here I may have stuffed up:
[http://www.clonezilla.org/clonezilla-live/liveusb.php](http://www.clonezilla.org/clonezilla-live/liveusb.php) :(

---

### Post by NUboon2Age on 2010-05-16
I have a pretty good idea of (at least part) of what is going on, because I have a similar problem.  

Check out [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/356095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/356095)

Due to a bug the MBR of your notebook's internal HD was overwritten when you installed to the USB and now its expecting that pen drive to be plugged in.  I had the same thing happen.

Now **have you tried booting WITH the USB plugged in**?  When I do that its happy (although it comes up with the new Grub2 menu instead of the one that previously came up so of course I'm not entirely off the hook.  I have to learn how to restore the old Grub or at least reset it so there is no dependency on the external USB drive.

Please, please anyone who gives a hoot about this serious bug, please go the that bug page and indicate that the bug effects you (and possibly subscribe to it as well).  We need this to be fixed ASAP for future releases.  Also if anyone can give advice as to how to proceed with appropriate ways to raise the bug's profile, please post it.

---

### Post by sjhupp on 2010-05-16
Thought I did, but will try again.
...
nope, no go. power light comes on, does the cd/dvd check, then silence. no hdd activity at all, then a few seconds later seems to reboot.
Laptop might be fubar :mad:

---

### Post by NUboon2Age on 2010-05-16
> **sjhupp said:**
> Thought I did, but will try again.
...
nope, no go. power light comes on, does the cd/dvd check, then silence. no hdd activity at all, then a few seconds later seems to reboot.
Laptop might be fubar :mad:

[B]I assume this is in reply to my question if you'd booting w/ the USB plugged in (and I'm assuming the configuration of HDs and other bootable devices is the exact same as when you did the USB install).
[/B]
Well at least it might be more involved than simply the bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/356095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/356095), Grub overwriting MBR, like maybe the new Grub installation has the display and other settings incorrectly set.

BTW **I forgot to ask something very important: How did you do the clonezilla install?**  ie. Did you boot off Live clonezilla disk in a CD drive and then tell it to install or use a program like Unetbootin or Startup Disk Creator or ....?

---

### Post by sjhupp on 2010-05-16
> **NUboon2Age said:**
> [B]I assume this is in reply to my question if you'd booting w/ the USB plugged in (and I'm assuming the configuration of HDs and other bootable devices is the exact same as when you did the USB install).
[/B]
Well at least it might be more involved than simply the bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/356095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/356095), Grub overwriting MBR, like maybe the new Grub installation has the display and other settings incorrectly set.

BTW **I forgot to ask something very important: How did you do the clonezilla install?**  ie. Did you boot off Live clonezilla disk in a CD drive and then tell it to install or use a program like Unetbootin or Startup Disk Creator or ....?

Sorry, was in response to your suggestion.  Did try botting with usb plugged in, as when I thought I had the problem, but still no good.
Originally I booted into 10.04 desktop as usual, then tried to create a clonezilla usb stick to boot off. That's when I made the changes, meking it bootable and following the usb instructions on the clonezilla site. I had thought this buggered up my MBR (maybe I overwrote the wrong disk), but now I can't boot off a CD/DVD, even if I remove the hard drive, and the screen won't show anything at all, not even the bios.

---

