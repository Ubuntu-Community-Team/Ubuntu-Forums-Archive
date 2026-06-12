---
title: "mount external hard drive"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by murox on 2010-11-08
Running 10.04. went to move some files from another computer via a freecom toughdrive . Ubuntu will not "mount" the drive and denies access. Does the same thing with the freecom CD as well. Any help  or suggestions please.

---

### Post by Grenage on 2010-11-08
Assuming that the Toughdrive is an HD with a USB connection, what happens when you plug it in?

A) It doesn't do anything.
B) It tries to auto-mount, and errors.
C) Other?

---

### Post by toekneewood on 2010-11-08
Have a go at the following:
Remove the drive, open a terminal and type
```

tail -f /var/log/messages

```
Now plug in your device
This should give you a start point on what to look for.  If you upload the contents of the console so that we can see the message log
Some other commands that might help you would be:
```

lsusb
sudo fdisk -l
mount

```

---

### Post by rn.kalyan on 2010-11-08
I too have the same problem. When i try connecting a Seagate FreeAgent Go external hard drive to my IBM thinkpad T40, the hard drive light is on but i dont see the hard drive been mounted to my desktop. Also i have a ubuntu installed to a desktop pc. The same hard drive when connected to my desktop installed with the same version of Ubuntu the hard drive works absolutely fine. Please guide me in finding a solution to mounting my external HDD to my laptop. I run Ubuntu 10.10 with all updates installed.

---

### Post by murox on 2010-11-08
> **Grenage said:**
> Assuming that the Toughdrive is an HD with a USB connection, what happens when you plug it in?

A) It doesn't do anything.
B) It tries to auto-mount, and errors.
C) Other?

toughdrive is a HD with usb connection. When plugged in it tries to auto mount and ubuntu gives error message that it cant mount the HD.

---

### Post by moink on 2010-11-08
I seem to be having the same problem. My external usb HD randomly mounts on boot.  I just keep reseting the computer until it sees the drive. Unplugging it does not work either.  I tried messing with the fstab and mtab file but I really have no clue.

Here is what I noticed so far.

when the external drive gets mounted to sda1 it doesn't work. When it gets mounted to sdb1 it does.  It seems like it gets mounted to / and my internal drive with ubuntu on it gets mounted to / also.  If I keep resetting the computer eventually it gets the internal drive mounted /dev/sda1  /  and the external one gets mounted to /dev/sdb1 /media/data_drive.  

right now it is messed up
mtab:
/dev/sdb1 / ext4 rw,errors=remount-ro,commit=0 0 0

fstab:
/dev/sda1                                   /                                ext4   errors=remount-ro      

when I try to mount using the mount button in the disk utility it says:

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

---

### Post by murox on 2010-11-08
> **toekneewood said:**
> Have a go at the following:
Remove the drive, open a terminal and type
```

tail -f /var/log/messages

```
Now plug in your device
This should give you a start point on what to look for.  If you upload the contents of the console so that we can see the message log
Some other commands that might help you would be:
```

lsusb
sudo fdisk -l
mount

```
**Here is the output**;

murray@murray-desktop:~$ tail -f /var/log/messages
Nov  8 17:15:05 murray-desktop kernel: [ 2248.096022] usb 1-7: new high speed USB device using ehci_hcd and address 9
Nov  8 17:15:05 murray-desktop kernel: [ 2248.231361] usb 1-7: configuration #1 chosen from 1 choice
Nov  8 17:15:05 murray-desktop kernel: [ 2248.233003] scsi5 : SCSI emulation for USB Mass Storage devices
Nov  8 17:15:16 murray-desktop kernel: [ 2259.098592] scsi 5:0:0:0: Direct-Access     SAMSUNG  HM121HI          0-08 PQ: 0 ANSI: 2 CCS
Nov  8 17:15:16 murray-desktop kernel: [ 2259.100138] sd 5:0:0:0: Attached scsi generic sg7 type 0
Nov  8 17:15:16 murray-desktop kernel: [ 2259.103832] sd 5:0:0:0: [sdf] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Nov  8 17:15:16 murray-desktop kernel: [ 2259.105332] sd 5:0:0:0: [sdf] Write Protect is off
Nov  8 17:15:16 murray-desktop kernel: [ 2259.107173]  sdf: sdf1
Nov  8 17:15:16 murray-desktop kernel: [ 2259.780943] sd 5:0:0:0: [sdf] Attached SCSI disk
Nov  8 17:22:13 murray-desktop kernel: [ 2676.094338] usb 1-7: USB disconnect, address 9
Nov  8 19:16:57 murray-desktop kernel: [ 9560.352065] usb 1-7: new high speed USB device using ehci_hcd and address 10
Nov  8 19:16:57 murray-desktop kernel: [ 9560.487170] usb 1-7: configuration #1 chosen from 1 choice
Nov  8 19:16:57 murray-desktop kernel: [ 9560.489096] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  8 19:17:08 murray-desktop kernel: [ 9571.354890] scsi 6:0:0:0: Direct-Access     SAMSUNG  HM121HI          0-08 PQ: 0 ANSI: 2 CCS
Nov  8 19:17:08 murray-desktop kernel: [ 9571.356283] sd 6:0:0:0: Attached scsi generic sg7 type 0
Nov  8 19:17:08 murray-desktop kernel: [ 9571.359774] sd 6:0:0:0: [sdf] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Nov  8 19:17:08 murray-desktop kernel: [ 9571.365208] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 19:17:09 murray-desktop kernel: [ 9571.368078]  sdf: sdf1
Nov  8 19:17:09 murray-desktop kernel: [ 9572.006627] sd 6:0:0:0: [sdf] Attached SCSI disk

---

### Post by Grenage on 2010-11-09
Does the drive mount ok on any other system or OS?
What filesystem is the drive using, FAT32?
If you try to manually mount the drive, does it?

---

### Post by murox on 2010-11-09
> **murox said:**
> Running 10.04. went to move some files from another computer via a freecom toughdrive . Ubuntu will not "mount" the drive and denies access. Does the same thing with the freecom CD as well. Any help  or suggestions please.
:)  well I am scratching my chin and wondering whats going on. This afternoon I fired up ubuntu and just thought I would try transferring some files from the freecom tough drive again. Well it worked!! Flawlessly!!!
The only change was that the computer had been turned off overnight and I had left the toughdrive CD in by mistake. At startup everything just clicked in and performed well. So for no obvious reason this one is Solved.

---

### Post by murox on 2010-11-10
> **Grenage said:**
> Does the drive mount ok on any other system or OS?
What filesystem is the drive using, FAT32?
If you try to manually mount the drive, does it?
Thanks for your help Grenage. As per my last post all seems ok now.
for your info:- the drive mounts on other ubuntu comp. and windoze  comp.- FAT 32 -yes  - manual mount did not work . Simply got access denied message along with cant mount.

---

### Post by Grenage on 2010-11-10
Odd! Still, at least it's working now. :)

---

