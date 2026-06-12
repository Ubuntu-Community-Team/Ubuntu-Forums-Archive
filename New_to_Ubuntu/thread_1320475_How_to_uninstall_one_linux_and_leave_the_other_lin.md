---
title: "How to uninstall one linux and leave the other linux (and GRUB) alone"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by AlHounos on 2009-11-09
Sorry for the basic question but every search I do talks about uninstalling linux and  restoring the windows boot loader - all i want to do is remove my karmic 64 bit partition and give it back to my karmic 32 bit partition.  

I tried to delete the 64 bit partition, but of course it confounded grub which halted the system at boot with "no such partition". 

So how can I remove the 64 bit partition without making GRUB unusable?

---

### Post by kansasnoob on 2009-11-09
We need to know what version of grub is in the OS you are keeping. Are you right now able to boot the 32 bit OS you're keeping?

If so you can run the command:

```
grub-install -v
```

I should clarify: I mean run that command while booted into the OS you're keeping if possible. If not we can do it from the live CD, but it's harder to do.

---

### Post by AlHounos on 2009-11-09
GRUB 1.97~beta4


i actually just reinstalled the 64 bit 9.10 to make GRUB happy, so yes, i am in the 32bit 9.10 right now.

---

### Post by kansasnoob on 2009-11-09
Well, that's grub2 and since you are booted into the OS you're keeping just run the following commands, first just to find out how the drive (or drives) are recognized by Ubuntu:

```
sudo fdisk -l
```

(BTW that's a lower case L.) The pertinent part is in bold in this example:

> lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance:

Disk **/dev/sda**: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63056305

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2104 16900348+ 7 HPFS/NTFS
/dev/sda2 2883 9729 54998527+ 5 Extended
/dev/sda3 2105 2882 6249285 83 Linux
/dev/sda5 4214 5012 6417967+ 83 Linux
/dev/sda6 5013 7434 19454683+ 83 Linux
/dev/sda7 7435 8199 6144831 83 Linux
/dev/sda8 8200 9576 11060721 83 Linux
/dev/sda9 9577 9729 1228941 82 Linux swap / Solaris
/dev/sda10 2883 4213 10691194+ 83 Linux

Partition table entries are not in disk order 

If you have more than one drive we'll have to figure out which one is your 32 bit.

If it's "/dev/sda" as illustrated above then just run:

```
sudo grub-install /dev/sda
```

If that returns any errors run:

```
sudo grub-install --recheck /dev/sda
```

And then:

```
sudo update-grub
```

Then reboot. If all was successful you'll be booting with the 32 bit grub which should be obvious because it'll be the default boot unless you've modified files.

Then after removing the 64 bit run "update-grub" again and the 64 bit should be dropped from menu.

---

### Post by AlHounos on 2009-11-09
excellent, that was just what I needed.  thanks!

---

