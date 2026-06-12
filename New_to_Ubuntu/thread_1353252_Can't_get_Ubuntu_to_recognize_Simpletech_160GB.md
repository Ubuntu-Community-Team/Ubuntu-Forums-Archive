---
title: "Can't get Ubuntu to recognize Simpletech 160GB"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by grpphoto on 2009-12-12
I bought a SimpleTech 160GB remote drive some time back. I was able to get it to mount one time on a Windows 2000 system. Since then, I have not been able to use it. I have tried W-2000, XP, and now Ubuntu. Ubuntu seems to have more tools than Windows, so I am hoping for eventual success here.

I tried buying a remote power supply for the drive, and today I bought a 2.0 USB hub so that I can plug the drive into both a 2.0 port and a 1.1 port at the same time. The light on the drive indicates activity, and there is the normal slight vibration and noise, which proves that the drive is spinning. I have tested the 1.1 port with a flash drive and the 2.0 hub with a mouse, and both are working.

I found an old thread here that recommended the sudo command, so I ran that. It seems to indicate that Ubuntu doesn't even "know" that the drive is plugged in. Here are the results:

george@new-hostGeorges:~$ sudo fdisk -l
[sudo] password for george: 

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66976697

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9779    78549786   83  Linux
/dev/sda2            9780        9964     1486012+   5  Extended
/dev/sda5            9780        9964     1485981   82  Linux swap / Solaris
george@new-hostGeorges:~$ 

Any help would be appreciated.

George

---

### Post by NCLI on 2009-12-13
It sounds like the drive is broken, but to make sure, try posting a new thread in either [Hardware and Laptops]("http://ubuntuforums.org/forumdisplay.php?f=332") or [General Help]("http://ubuntuforums.org/forumdisplay.php?f=336"). This doesn't sound like something for the Absolute Beginners forum.

Though before you do that, I'd try installing the application gparted from the Software Centre and see whether it shows up there.

---

### Post by happyhamster on 2009-12-13
Perhaps checking the computer's BIOS settings might do the trick: search for an option to enable a 1.1 USB controller, or enable "Legacy USB storage detect" or such (the exact name depends on your BIOS). Be careful when fiddling with options though, because you could wreck the system (to the point you'll have to manually clear the CMOS to get things working again).

Good luck.

---

### Post by sandyd on 2009-12-13
[B]What's the output of
```

lsusb

```
[/B]

---

