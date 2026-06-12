---
title: "how to delete old usb drive - media file"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by fredfelter on 2009-08-08
I was attempting to format/partition a usb drive with Ubuntu but somehow the contents of the drive ended up as a Place called "8.0 GB Media". Now when I open Ubuntu it shows up even though the usb drive is not plugged in, so somehow it got copied to my HD. When I try to send it to Trash that is not an option and when I click on it it opens as "disk - File Browser" with the included files. I cannot delete the individual files either as there is no option to send them to Trash. This "disk" shows up on my desktop if I "mount" it even though it is not connected to the computer and in either case I cannot seem to delete it. 
There must be a way to get rid of this non existent item but how?
Thanks.

---

### Post by nandemonai on 2009-08-08
Can you please post the output from:

```
sudo fdisk -l
```

and

```
df -h
```

---

### Post by fredfelter on 2009-08-08
Thanks for the reply nandemonai. I'm fascinated but completely baffled (being a novice Linux user) about how you are approaching this but here are the results of the 2 code commands. If you figure this out I would love to know how you got there:

fred@fred-laptop:~$ sudo fdisk -l
[sudo] password for fred: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x669b0829

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4848    36650848+   c  W95 FAT32 (LBA)
/dev/sda2            4849        5168     2419200   1c  Hidden W95 FAT32 (LBA)

Disk /dev/sdb: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6cedf53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         608     4883728+  83  Linux
/dev/sdb2             609         730      979965   82  Linux swap / Solaris
/dev/sdb3             731        1459     5855692+   5  Extended
/dev/sdb4   *        1460        2432     7815622+  83  Linux
/dev/sdb5             731        1459     5855661   83  Linux
fred@fred-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             4.7G  2.9G  1.6G  65% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M   92K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  164K  249M   1% /dev
tmpfs                 249M  176K  249M   1% /dev/shm
lrm                   249M  2.2M  247M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb5             5.5G  629M  4.7G  12% /home
fred@fred-laptop:~$

---

### Post by nandemonai on 2009-08-08
I wanted the output from fdisk and df to see what was mounted on the system. That all looks fine. I was curious if perhaps you had another partition floating around the same size as the USB drive and you were confusing that partition with the external one or something along those lines. Always helps to check these things ;)

With that out of the way. Let's try the output from:

```
lsusb
```

That should list all usb devices connected to the system.

A couple things..

Has the machine been restarted since the drive was last plugged in? Also, did you eject it before removing it? You can do that by hitting the little eject arrow next to it's name in places.

Although I've never seen it happen, I'd assume if you pulled the drive out without ejecting it first via software it 'could' freak out and not auto remove it from the places list properly.

Those are just guesses at the moment. I'd be interested to see what lsusb shows.

---

### Post by fredfelter on 2009-08-09
Thanks again nandemonai.

Here are the results (with no usb connected):
fred@fred-laptop:~$ lsusb
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 050d:0218 Belkin Components 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fred@fred-laptop:~$

With usb connected and mounted:
fred@fred-laptop:~$ lsusb
Bus 001 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 050d:0218 Belkin Components 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fred@fred-laptop:~$  

The only thing I have been doing prior to removing the usb device is to make sure it is not mounted. I have not been aware of the need to do more. In my Ubuntu unmounted there is no DT icon and in Places a red marker; mounted there is a DT icon with red marker and in Places a red check + padlock. With usb plugged in, mounted or unmounted there are now 2 Medias, an 8.0 and an 8.1. The 8.1 goes away upon removal of usb drive.
Yes, the computer has been restarted several times without the drive in and the Place > 8.0 GB Media does not go away.
If this is of interest when I click on Places > 8.0... > requests pass for priviledges > Authenticate > "disk - File Browser" > opens a folder with the Puppy linux files that I had put on the usb to run as a frugal install on another computer.

Would the padlock and need to authenticate suggest I need to do something at a higher file level to remove it?

---

### Post by nandemonai on 2009-08-11
That's quite bizare. As far as I know, any devices that are not currently picked up by the system (which is this case there is none shown by df / dh) should not be shown in places. Sounds like udev and or hotplug has made a mistake and kept it there after it was removed.

I'm afraid I'm not too sure where to take it from here.

Apologies.

---

### Post by mystmaiden on 2009-08-12
I had a couple of backup files that were supposed to be on my external land in the wrong place, but I couldn't delete them. I logged in as root and deleted through nautilus using shift+delete.  Might that work for you?

myst

---

### Post by fredfelter on 2009-08-12
Thanks for the idea myst. I think what you are suggesting is that I log-in as root > "Nautilus" from terminal but when I open up any likely (to me) folders (like dev>disk, media or mnt) I can't find that illusive "8.0 GB Media". When I go to Search for files it is one of the folder options in which to start a search thereby eliminating the possibility of drilling down on where it resides in order to delete it.

---

### Post by fredfelter on 2009-08-12
Problem Solved as redundant "8.0 GB Media" entry went away on its own. Thanks everyone for the advice.

---

### Post by mystmaiden on 2009-08-12
glad you got it fixed! The only other suggestion I had was to be sure and reveal hidden folders once you got into nautilus.

mystmaiden

:)

---

