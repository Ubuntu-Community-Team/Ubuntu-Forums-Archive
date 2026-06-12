---
title: "Ubuntu minimal on USB - cannot mount ext4 file"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Alxl on 2011-02-05
I have installed Ubuntu mini 10.04 on a 2GB USB and Ubuntu mini 10.10 on another 2 GB USB and both work very well.        Unfortunately 2GB is not enough    (I am down to some 50 MB free space)..
 

 So I tried but never succeeded to install Ubuntu Lucid mini on a 8GB stick . Used Gparted to format to fat16 and then to fat32  and even tried ext4 on a portion of the stick.
 

 Installation goes well up to partitioning  of the stick when I get the error : 'attempt to mount a file ext4 on SCDI5 (0,0,0) partitin #1 (sdb) at   /  failed '    (my wording).
 

 What am I doing wrong?

---

### Post by fabricator4 on 2011-02-05
I usually use ext2 for a USB drive, since it's non-journalling.  No reason why ext4 wouldn't work though.  Are you sure that the USB drive in question is sdb1?  Make sure you select sdb1 (or whatever) to mount as root '/' - and I think this may be your problem.

You should also make a swap space since there's room on an 8 GB drive to do so, and install grub on sdb1

Chris.

---

### Post by Alxl on 2011-02-05
Hi Chris,
this is not a matter of mistaken the drive.  I gave the installer the option to use the entire drive (the USB).\

As said,
  'I have installed Ubuntu mini 10.04 on a 2GB USB and Ubuntu mini 10.10 on  another 2 GB USB and both work very well.  ' ,

using the same method i.e. allowing the installer to do what it wants with the entire drive.  Each of the 2GB installations has a small swap installed that way.

For some reason it does not work on a 8 gig stick. 

Hope that somebody can figure this out somehow.

Thanks

---

### Post by fabricator4 on 2011-02-05
OK, try another USB port.  The USB drive may be dropping out or be otherwise unreliable.  I had a similar thing when trying to boot an older machine to perform some data recovery.  I kept trying all the ports, and combinations of ports (I also had a powered external HDD that was to be the target for the recovery operation) and eventually got it to boot off the USB drive and stay up.  Annoying.

This problem is normally caused by a voltage drop on the USB port causing the device to be not recognised.  Sometimes they'll connect and drop out after a few seconds or even minutes.

Chris.

---

### Post by Alxl on 2011-02-06
I tried several ports (even pulled out the printer cord from the back and tried that one too).
 

 Initially  the  stick it is formated in fat16 or fat32.


  After I am informed that the 'mount of file ext4 on the partition at /  has failed' ,  and after I abort the installation , at first I cannot mount the USB (has errors), but Disk Utility lets me unmount it .           And at that time I can see that it is formated to ext4  -  so the installer has seen it and formatted it to ext4 but then the installer cannot mount it to start the installation.


So the problem appears to be that the installer cannot mount the partition after it was formatted to ext4 by the same installer.

---

### Post by fabricator4 on 2011-02-06
Odd.  Try a different approach.  Use Gparted (or disk utility) to format it to ext2.  Partition it with a 1 GB swap file if you wish.

Now rund the live CD and start the install.  When it asks for the install options use the third one: specifiy partitions manually.  Do NOT tick the box to allow it to format the drive.  Put grub on the USB (sdb1 or whatever).  Make sure you select mount as root ("/") for the ext2 partition.  Check that the swap file is correct if necessary.  Go ahead with the install.

I've definitely done this on both an 8 GB SD card and an 8 GB USB, with 10.10, but I did make the partions with Gparted first.

Chris.

---

### Post by Alxl on 2011-03-04
As a follow-up
both the USB stick and the card were very old and apparently faulty.

I got a new 4GB sdhc card   (C is 4) and installation went flawlessly .\

 And it is also working as expected .

thank you all

---

