---
title: "Can't load Ubuntu 10.10"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by grahambrookbanks on 2011-01-13
I'm very new to Ubuntu and not very tech savvy.

My PC is a Dell Dimension 3100
System:  DV05
BIOS Version A03  (10/08/05)
Processor Pentium 4 CPU 2.8 Ghz

I installed a new hard drive and installed Ubuntu 10.10 from CD downloaded from the internet.

I managed to sort out a problem with wireless internet connection and all seemed to be well.

However, when I tried to shut down, the screen just froze with a box on the desktop saying 'Shut Down'.

I left it until I was sure nothing further was going to happen, then I forced a shutdown by holding the power button in.

When I started up again, I was presented with 4 No. options:

Ubuntu with Linux 2.6.35 - generic
Ubuntu with Linux 2.6.35 - generic (recovery mode)
memory Test (memtest 86+)
memory Test (memtest 86+, serial console 11520)

Recovery mode seemed the best bet, so I selected that and got screenfuls of text, ending up with:

Begin:Running/scripts/init-bottom.....mount:mounting/dev on/root/dev failed
:No such directory
done
mount:mounting/sys on/root/sys failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found.  Try passing init=bootarg
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) [  2.032017]usb 3-2:new low speed USB device using uhci_hcd and address 2

I think I've transcribed that correctly.
None of the keyboard keys seemed to do anything, so I forced another shut down and held down F12 during boot up, and booted from the ISO disk.

The install started, but then I got a black screen with the following message:
(process:274):GLib-WARNING  **:get pwuid_r():failed due to inknown user id (0)

I'm at complete loss as to what to do next. Please help?:confused:

---

### Post by cariboo on 2011-01-13
Because you used the power button to shut down, you need to run fsck on your Ubuntu partition.

Boot from the Live CD, and once at the desktop, open an Applications->Accessories->Terminal, at the prompt type:

```
sudo fdisk -l
```

the above command will show a listing of your partitions, it should look something like this:

```
sudo fdisk -l
[sudo] password for cariboo: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005653a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10199    81817600    7  HPFS/NTFS
/dev/sda3           10199       19458    74368001    5  Extended
/dev/sda5           10199       11415     9764864   83  Linux
/dev/sda6           11415       19458    64602112   83  Linux

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0e5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9764864   83  Linux
/dev/sdb2            1216        1459     1952768   82  Linux swap / Solaris
/dev/sdb3            1459       20024   149116928   83  Linux

```

I have two hardrives in my system, but as you can see n the first drive /dev/sda5 is my Ubuntu partition. To run fsck on it I would type the following command:

```
sudo fsck -y /dev/sda5
```

When I run the command, I get the following result:

```
sudo fsck -y /dev/sda5
[sudo] password for cariboo: 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda5: clean, 216046/610800 files, 1362038/2441216 blocks
```

Once the command has finished, you can reboot.

---

### Post by grahambrookbanks on 2011-01-14
Thanks for your help, Cariboo, I really appreciate it.

Is the Live CD you mentioned the same thing as the install disk?

Anyway, I booted from the install CD and selected 'Try Ubuntu'

At the desk top I followed your instructions.  

Linus is on /dev/sda1 so I entered:

sudo fsck -y /dev/sda1

I got the message:

fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$

What should I do now?

---

### Post by grahambrookbanks on 2011-01-17
I think Cariboo has given up on me.  Can anybody else help this novice to re-load Ubuntu?

---

