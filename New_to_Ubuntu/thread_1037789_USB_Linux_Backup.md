---
title: "USB Linux Backup"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by mike27ob on 2009-01-12
Hi,

I've built a persistent USB version of Linux from 8.10 "Create a USB Startup Disk" and have updated OOo and added a few applications. I would like to be able to make an image file of the USB drive but having searched the web can't find out how to do it. The traditional apps I've found only look at hard drives and not removable media. Does anyone have any thoughts on this?

Thanks

Mike

---

### Post by jgoguen on 2009-01-28
Do you mean that you want to make an exact, bit-for-bit copy of the entire USB drive?  That can be handled with the "dd" command.  First, you need to open a Terminal (Applications -> Accessories -> Terminal) and find the mount point for the USB drive.  You can look at the output of this command: ```
mount
```
That will display all mounted file systems, including your USB drive.  Likely, it's an entry near the end of the list.  For example, the line I get when I mount my USB drive starts out like this:
> /dev/sdb1 on /media/Kingston type vfat (rw,...
The "/dev/sdb1" part is the device name.  It may or may not be the same for you, but for this post I will assume you have the same device name.  If you aren't sure, post the output of this command and we'll tell you what to use:
```
mount | grep '/media'
```
So, now that you have your device name, unmount it.  Do this any way you feel comfortable, but leave the drive plugged into the computer.  Now, this command will make an exact, bit-for-bit copy of your USB drive:
```
dd if=/dev/sdb1 of=${HOME}/usbkey.img bs=1k
```
The options used here are:

[list]
[*]if - The input file or device
[*]of - The output file or device
[*]bs - The block size to use
[/list]

Depending on how big the USB drive is, this could sit there and appear to do nothing for a long time.  I have a 16GB USB key, and based on quick tests dd can move data at about 15MB/s, meaning it would take almost 20 minutes to make a full copy.  When it's done, you will see something similar to the following (probably different numbers):
> 1024+0 records in
1024+0 records out
67108864 bytes (67 MB) copied, 4.31613 s, 15.5 MB/s
That's it, you've got a file named usbkey.img in your home directory that is an exact copy of your entire USB drive!

Now, if you want to restore this image to your USB key later, use this command:
```
sudo dd if=${HOME}/usbkey.img of=/dev/sdb1 bs=1k
```
Make sure to verify that your USB drive is still mounted there!  If something has changed, you might end up with a nasty surprise!

---

