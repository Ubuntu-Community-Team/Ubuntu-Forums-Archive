---
title: "Can't install Ubuntu minimal on Acer Aspire One"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by aut-omatic on 2011-04-22
I want to install Ubuntu minimal on my Netbook. For some reason though, whenever I boot from the USB stick, it just gives me "SYSLINUX 4.03 2010-10-22 EDD Copyright (C) 1994-2013 H. Peter Anvin et al"

It seems to me that the installation just isn't starting. Any suggestions on how I could make it work?

---

### Post by cmcanulty on 2011-04-22
install unetbootin from software center burn the image to a thumb drive and install make sure you set it to boot from usb drive by hitting whateer key your machine says as it boots. Works great on my aspire one. I tried the netbk version and hated it now just have regular Ubuntu 10.10 on it. I made a separate home partition during install so my docs are safe if I screw up the OS. Keep the usb image for disaster recovery

---

### Post by clausrei on 2011-04-22
Hi ,

I had the same problem last year with a Toshiba Notebook and I never get it to work. The problem was, so I have been told by a computer repair shop, is that the boot-able USB sticks are fairly new technology, which makes it possible to boot from USB-Memory at some Computers but not from others. Try to install from a external CD- Rom drive. 

How reliable this information was, I don't know? On the end I sold the Toshiba and bought myself a laptop and installed Ubuntu from CD-Rom.  Much happier now !

Claus

---

### Post by clausrei on 2011-10-23
Hi,


I finally couldn't  re-size the partition from my old Karmik Koala Ubuntu CD for what ever reason. But I have downloaded the GParted live CD and with this tool I managed to  shrink the NTFS partition. 

Now, I have a new problem: I can move the smaller NTFS, which is visually located left, into the empty space, I can grow the NTFS again and I can format the empty space with any File System I like ( have formatted it to ext3 for now) 

Ubuntu recognize the new partition but I can't merge the two ext3 partitions on this hard disc drive. I guess it will be important, when I am upgrading. 

Any idea ?!

Claus 

PS: Another option would be to just install the newest Ubuntu on top. But I am not so happy, because I loose all the software I am using, which would have to be re-installed. But maybe this will be the only option, if I can't find a solution to merge the two ext3 partitions.

Who ever has the same problem and read this post, I recommend to read the Info file on the GParted Live CD after booting from the burned CD.  There have been some cases where people could not log-on to their Windows XP anymore, because Windows could not find the new right size of the NTFS partition and you have to delete a Registry Key 
(HKEY_Local_Machine\system\MountedDevices. ) However I didn't have any problems and everything worked fine.

---

