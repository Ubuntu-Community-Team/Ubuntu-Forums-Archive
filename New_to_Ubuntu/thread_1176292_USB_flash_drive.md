---
title: "USB flash drive"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by uppidada on 2009-06-02
I've a 2GB usb flash drive.
The problem with this is its displayed in \home directory:
When i try to open it,it displays "Unable to mount media.There is probably no media in the drive"

Please help me with this...

---

### Post by bennachie on 2009-06-02
What data do you expect to find on the USB stick, and how was the data put there? I have never experienced any difficulty in mounting USB data sticks formatted as FAT16, FAT32, ext2 or ext3 (I haven't tried the other normal options). 

On the other hand, bootable disks prepared by making a direct copy of an IMG file or a hybrid ISO file may well not mount normally, since there is not much that the system can sensibly do with them. However, you should be able to clear and reformat them with a partition editor (gparted or the like) if you really want to do so.

---

### Post by Volt9000 on 2009-06-02
After inserting the USB stick, type the following command and paste for us the output:

```

sudo fdisk -l

```

---

### Post by uppidada on 2009-06-02
Sorry for the delayed reply..



upesh@upesh-desktop:~$ sudo fdisk -l
[sudo] password for upesh:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x172f172e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   c  W95 FAT32 (LBA)
/dev/hda2            1531        8315    54500512+   f  W95 Ext'd (LBA)
/dev/hda3            8316        9733    11390085   83  Linux
/dev/hda5            1531        2254     5815498+   b  W95 FAT32
/dev/hda6            2255        3529    10241406    b  W95 FAT32
/dev/hda7            3530        4422     7172991    b  W95 FAT32
/dev/hda8            4423        6971    20474811    b  W95 FAT32
/dev/hda9            6972        8246    10241406    b  W95 FAT32
/dev/hda10           8247        8315      554211   82  Linux swap / Solaris
upesh@upesh-desktop:~$

---

### Post by uppidada on 2009-06-02
Screen Shot of my computer is as follows:  [IMG]http://i378.photobucket.com/albums/oo230/uppidada/Screenshot-1.png[/IMG]

---

### Post by uppidada on 2009-06-03
Someone help me with this..please.!!:confused:

---

### Post by spcwingo on 2009-06-03
Is it a DOS startup disk?  If so, I have the same problem and can only add/remove/edit/etc files from a Win system without formatting the disk.

---

### Post by uppidada on 2009-06-03
Nopes.. It is a 4GB USB flash drive.

---

### Post by Volt9000 on 2009-06-03
Ok based on your output it looks like your system isn't even recognizing the USB device.
What happens if you try another USB stick? Does that work?

---

### Post by uppidada on 2009-06-03
Yes.Other USB's work.
Has it gone wrong with USB stick..?? or is there any debugging that i can do..

---

### Post by SOULRiDER on 2009-06-03
> **uppidada said:**
> Sorry for the delayed reply..



upesh@upesh-desktop:~$ sudo fdisk -l
[sudo] password for upesh:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x172f172e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   c  W95 FAT32 (LBA)
/dev/hda2            1531        8315    54500512+   f  W95 Ext'd (LBA)
/dev/hda3            8316        9733    11390085   83  Linux
/dev/hda5            1531        2254     5815498+   b  W95 FAT32
/dev/hda6            2255        3529    10241406    b  W95 FAT32
/dev/hda7            3530        4422     7172991    b  W95 FAT32
/dev/hda8            4423        6971    20474811    b  W95 FAT32
/dev/hda9            6972        8246    10241406    b  W95 FAT32
/dev/hda10           8247        8315      554211   82  Linux swap / Solaris
upesh@upesh-desktop:~$

You typed that command AFTER inserting the USB drive, right?

---

### Post by QIII on 2009-06-03
Can you access the media on a Windoze machine?

---

### Post by ptsubin on 2009-06-03
Plug the device again, and issue this command, tail -f /var/log/messages or dmesg and see th output.

---

### Post by Zebra Lord on 2009-06-03
I literally was just having this problem a few minutes ago.  I used the USB Start Up Disk Creator application to copy the Ubuntu 8.10 .iso image onto my flash drive so I could boot from it.  The process worked fine and I was even able to boot from my flash drive. However, when I booted into Jaunty on my HD and tried to view the files on my flash drive, I got the same error message as you.  To fix it I just took out my flash drive and plugged it back in and it worked.

You probably already tried that but thats what worked for me.

By the way I have a 2 GB flash drive as well.

---

### Post by uppidada on 2009-06-03
Well in windows this is how it appears:

[IMG]http://i714.photobucket.com/albums/ww149/upeshdada/untitled.png[/IMG]





All the commands are donw with USB stick connected as well..!!










upesh@upesh-desktop:~$ sudo tail -f /var/log/messages
[sudo] password for upesh:
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.754398] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.755648] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.756776] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.758024] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.759274] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.760524] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.761774] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.763024] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.764274] end_request: I/O error, dev sda, sector 0
Jun  4 08:27:34 upesh-desktop kernel: [ 1471.765398] end_request: I/O error, dev sda, sector 0

---

### Post by Volt9000 on 2009-06-03
Looks like the USB stick is fubar'd.

So that output you pasted of sudo fdisk -l, is that AFTER you inserted the USB stick as SOULRiDER asked? I just want to make sure, but based on your log there it looks like the USB stick is dead.

---

### Post by QIII on 2009-06-04
FUBAR.

Loved that term while I was in the Army.

Ah, the memories.

Yes.  I agree.

He's sucking hind teat, I'm afraid . . .

---

### Post by spcwingo on 2009-06-04
> **uppidada said:**
> Nopes.. It is a 4GB USB flash drive.

I realize that it's flash drive, but that flash drive could be a DOS, Linux, etc startup disk...if you made it that way.

---

### Post by spcwingo on 2009-06-04
> **QIII said:**
> FUBAR.

Loved that term while I was in the Army.

What about remf, pogue, and dat?  :)

---

### Post by QIII on 2009-06-04
We dug holes for DATs to hide their tracked coffins in.

---

### Post by triffle on 2009-07-06
Hey Everyone...I have been seening this all over the forums and I was having this same problem. Mine started when I created a "usb startup disk" so after alot of forum searching a googling... i finally found a fix that worked for me.... Here is the link... [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) please see after installing for the fix.

I guess what happens is that while booting from a usb flash drive you trick ubuntu into thinking that it is the CD Rom. You have to go into and edit your /etc/fstab from terminal

sudo gedit /etc/fstab

you will see a line towards the bottom of the page 

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

just put a comment in front of the line like this

#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

save and close

try and put your thumbstick back in and for me anyways tahh dahhh... Word!!!

Much Thanks to the ubuntu community...

---

### Post by kansasnoob on 2009-07-06
First try installing pmount:

```
sudo apt-get install pmount && sudo apt-get -f install
```

If the drive is formatted in NTFS then also install ntfsprogs:

```
sudo apt-get install ntfsprogs
```

You may have to restart to get-r-done!

---

