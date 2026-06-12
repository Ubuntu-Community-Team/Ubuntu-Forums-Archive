---
title: "USB ports"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by triaxlethomas on 2011-07-20
Help! I have been running Ubuntu 10.04 on my old Dell 8000 for several months. Recently the computer has stopped recognizing the USB ports! Was this due to an update?

---

### Post by Grenage on 2011-07-20
While unlikely, it's not impossible; do all ports fail, both front and back?

What are the results of *lsusb* both before and after inserting a device?  Do devices get power when connected?

---

### Post by skatinjj on 2011-07-20
Can you plug in a USb device then run this from the terminal:

```
lsusb
```

and display the output here?

---

### Post by skatinjj on 2011-07-20
> **Grenage said:**
> While unlikely, it's not impossible; do all ports fail, both front and back?

What are the results of *lsusb* both before and after inserting a device?  Do devices get power when connected?

Beat me to it XD

+1

---

### Post by triaxlethomas on 2011-07-20
I don't know how to do that!... Is that code?

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> Beat me to it XD

+1
Where do I type that command?
yes, there is power to the usb's

---

### Post by skatinjj on 2011-07-20
Press alt-F2, then type gnome-terminal in the run box.

When it pops up, type the command.

---

### Post by skatinjj on 2011-07-20
> **triaxlethomas said:**
> Where do I type that command?
yes, there is power to the usb's

Well at least you know the USB ports have not failed completely so there may be some hope.

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> Press alt-F2, then type gnome-terminal in the run box.

When it pops up, type the command.
tom@tom-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04b8:0818 Seiko Epson Corp. Stylus CX3700/CX3800/DX3800
Bus 001 Device 004: ID 048d:1336 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 002: ID 050d:0414 Belkin Components 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-desktop:~$

---

### Post by skatinjj on 2011-07-20
> **triaxlethomas said:**
> tom@tom-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04b8:0818 Seiko Epson Corp. Stylus CX3700/CX3800/DX3800
Bus 001 Device 004: ID 048d:1336 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 002: ID 050d:0414 Belkin Components 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-desktop:~$

Just to verify, the mouse plugged in has its laser on, but does not actually work correct?

Also, have you tested all the usb ports to see if any of them work?

---

### Post by wep940 on 2011-07-20
BTW - please don't open more than 1 thread on the same topic.  If you don't get replies as quickly as you'd like you will really just have to wait a while.  Having 2 threads open on the same topic can result in confusion due to some people posting in 1 thread and other people posting in the other thread.

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> Just to verify, the mouse plugged in has its laser on, but does not actually work correct?

Also, have you tested all the usb ports to see if any of them work?
no, the mouse works fine. I have this device that I bought at Staples to plug USB's into (rather than the computer directly). But it's stopped functioning. When I remove this device, and plug something (such as an ipod) into the computer directly, it makes no difference. There is power, but no function.

---

### Post by triaxlethomas on 2011-07-20
> **wep940 said:**
> BTW - please don't open more than 1 thread on the same topic.  If you don't get replies as quickly as you'd like you will really just have to wait a while.  Having 2 threads open on the same topic can result in confusion due to some people posting in 1 thread and other people posting in the other thread.
understood

---

### Post by Grenage on 2011-07-20
> **triaxlethomas said:**
> no, the mouse works fine. I have this device that I bought at Staples to plug USB's into (rather than the computer directly). But it's stopped functioning. When I remove this device, and plug something (such as an ipod) into the computer directly, it makes no difference. There is power, but no function.

There is a chance that the ports are semi-knackered; I've seen non-powered USB hubs wreck the USB host.

---

### Post by skatinjj on 2011-07-20
Ok so you bought a non-functioning USB hub, got it.

What I would do is, remove the USB hub, reboot the PC, and test the USB port(s) again.

Also, does the one usb port fail (where the usb hub is plugged into) or do all the ports fail?  

One more question, are there front and back usb ports? If so, which is the hub plugged into?

---

### Post by triaxlethomas on 2011-07-20
> **Grenage said:**
> There is a chance that the ports are semi-knackered; I've seen non-powered USB hubs wreck the USB host.

Yikes!...Maybe that's what's happening here?

---

### Post by Grenage on 2011-07-20
It's a possibility, but only that; if you boot from a live CD, do the ports work then?  If not, it's more likely to be a hardware issue.  I suspect that any powered, or low-power devices will work, but anything more might fail.

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> Ok so you bought a non-functioning USB hub, got it.

What I would do is, remove the USB hub, reboot the PC, and test the USB port(s) again.

Also, does the one usb port fail (where the usb hub is plugged into) or does the whole hub fail?  

One more question, are there front and back usb ports? If so, which is the hub plugged into?
  The USB hub is not new, I've had it for months. The whole hub seems to fail, although there is still power. The hub is plugged into the rear port on the computer.

---

### Post by skatinjj on 2011-07-20
I'd go with the idea of booting the livecd and testing the usb ports.

I would initially though not have that hub plugged in.

---

### Post by triaxlethomas on 2011-07-20
I don't have a livecd. Is that a bootable cd?

---

### Post by skatinjj on 2011-07-20
Yes its a bootable cd.

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> Yes its a bootable cd.
I'm sorry, the USB hub is apparently working (I plugged a flash drive into it). It's the Ipod and the SD card that the computer refuses to recognize. Now I'm more confused than before!

---

### Post by skatinjj on 2011-07-20
Try the IPOD and SD card one at a time connecting them to the computer directly (no hub).

Do they work?

Ps
Post the output of lsusb for each device.

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> Try the IPOD and SD card one at a time connecting them to the computer directly (no hub).

Do they work?

Ps
Post the output of lsusb for each device.
they do not

---

### Post by skatinjj on 2011-07-20
Does lsusb list them?

Also, do they work in other computers?

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> Does lsusb list them?

Also, do they work in other computers?
the ipod did not work in another computer

---

### Post by triaxlethomas on 2011-07-20
> **triaxlethomas said:**
> the ipod did not work in another computer
lsusb did not list them

---

### Post by skatinjj on 2011-07-20
I'm rummaging through my notes trying to find a command......

Is the other computer running windows or linux?

---

### Post by triaxlethomas on 2011-07-20
> **skatinjj said:**
> I'm rummaging through my notes trying to find a command......

Is the other computer running windows or linux?
It was an apple

---

### Post by triaxlethomas on 2011-07-20
> **triaxlethomas said:**
> It was an apple
Also, the printer is plugged into that hub, and is working normally. And I can move .mp3 files to and from the memory stick, just not the ipod or SD card.
?????

---

### Post by triaxlethomas on 2011-07-20
> **triaxlethomas said:**
> Also, the printer is plugged into that hub, and is working normally. And I can move .mp3 files to and from the memory stick, just not the ipod or SD card.
?????
The computer refers to these items as "generic storage devices" but I can't do a thing with them

---

### Post by skatinjj on 2011-07-20
Plug them in and run:

```
sudo fdisk -l
```

Please note 'l' is a lower case L "ell"
And no spaces between '-' and 'l'

Post the output here please.

---

### Post by skatinjj on 2011-07-20
My time is short right now, after running the above command they should appear something like sdb,sdc, and so on.

This will mount sdb to the media directory:

```
sudo mount /dev/sdb /media
```

It should come up as a device on the desktop if not CD to /media and that should open the device so you can save to it.

---

### Post by triaxlethomas on 2011-07-20
ok thank you!

---

### Post by skatinjj on 2011-07-20
Now that's not a permanent solution.  The mount point will be gone after a reboot or logging out.

If you want it to automount I would make a directory in /mnt for each device then edit fstab accordingly.

If you don't know how to configure fstab, use google first and if you still have questions we are here.

---

### Post by triaxlethomas on 2011-07-20
tom@tom-desktop:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a08e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19178   154042368   83  Linux
/dev/sda2           19178       19458     2245633    5  Extended
/dev/sda5           19178       19458     2245632   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c791

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3650    29318593+  83  Linux

Disk /dev/sde: 521 MB, 521796608 bytes
17 heads, 59 sectors/track, 1016 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   ?     1914209     2457017   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(1914208, 5, 40)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(2457016, 16, 59)
Partition 1 does not end on cylinder boundary.
/dev/sde2   ?     1326206     1863570   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(1326205, 9, 57)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(1863569, 13, 16)
Partition 2 does not end on cylinder boundary.
/dev/sde3   ?      537378     1931558   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(537377, 4, 25)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(1931557, 10, 42)
Partition 3 does not end on cylinder boundary.
/dev/sde4   *     1390457     1390478       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(1390456, 5, 1)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(1390477, 9, 38)
Partition 4 does not end on cylinder boundary.

---

### Post by triaxlethomas on 2011-07-20
tom@tom-desktop:~$ sudo mount /dev/sdb /media
mount: /dev/sdb already mounted or /media busy
tom@tom-desktop:~$

---

### Post by skatinjj on 2011-07-20
I need to dee all your mount points.  Run this:

```
mount
```

Post the output here please.

---

