---
title: "How do I format my USB?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by kevinwmiller on 2009-12-09
If I use USB Disc Creator to format my USB, will that make it a Linux Format?

Say, if I wanted to format to create a PC-BSD install USB, could I use the Linux Disc Creator or should I look elsewhere to format my USB?

I formatted it using Disc Creator, and when I used UNetBootin, to create a USB install for PC-BSD, it didnt work.  When I rebooted, it booted into a thing that gave me info for Debian's syslinux.  Why would that be on PC-BSD?  So, what should I use to format my USB?

---

### Post by SuperSonic4 on 2009-12-09
GParted or another Partition manager ought to work

---

### Post by Marlonsm on 2009-12-09
In the Software Center (or Add/remove) you can find gparted, use it to format the PenDrive. Just make sure to select the right device to format, because your HD will also be on the list. Look at the device's size to know which one you're about to format.

---

### Post by laidback on 2009-12-09
I've used gparted, worked fine for me.

---

### Post by kevinwmiller on 2009-12-09
I used disk utility and formatted my drive to FAT 32, and I selected FreeBSD instead of W95 FAT 32.

It failed again, any ideas?

Why would PCBSD have some Debian Syslinux thing on it?  If they don't, then maybe it is something to do with the Linux I am using now?

I can't figure out how to use Gparted and select my USB..

---

### Post by nothingspecial on 2009-12-09
Type```
 sudo fdisk -l
``` and try to figure out from the output which your usb stick is. It will be something like /dev/sdb1

To be on the safe side, if your not sure, unplug any other usb drives before you do anything else.

---

### Post by wilee-nilee on 2009-12-09
> **kevinwmiller said:**
> I used disk utility and formatted my drive to FAT 32, and I selected FreeBSD instead of W95 FAT 32.

It failed again, any ideas?

Why would PCBSD have some Debian Syslinux thing on it?  If they don't, then maybe it is something to do with the Linux I am using now?

I can't figure out how to use Gparted and select my USB..

There is a dropdown in the top right corner to get to the right device.

---

### Post by kevinwmiller on 2009-12-09
Yeah, I see that.  Earlier when I clicked on the drop down menu, it wouldn't.  It is there now, but I don't need it.  Disk Utility formats is easier and better for me.  

What I am wondering, is why Syslinux Debian blah blah is on the Bootup for PC-BSD, that is failing.  

I hate a problem I can't solve. lol.  I have to solve it, even if I have to run out and buy some DVD RW and try that out.

---

### Post by wilee-nilee on 2009-12-09
> **kevinwmiller said:**
> Yeah, I see that.  Earlier when I clicked on the drop down menu, it wouldn't.  It is there now, but I don't need it.  Disk Utility formats is easier and better for me.  

What I am wondering, is why Syslinux Debian blah blah is on the Bootup for PC-BSD, that is failing.  

I hate a problem I can't solve. lol.  I have to solve it, even if I have to run out and buy some DVD RW and try that out.

If Disc Utility is working for you then why are you having this problem?

---

### Post by kevinwmiller on 2009-12-09
I couldn't see how Gparted could format it any different.  I don't know, I honestly don't know what the problem is.  :(

---

### Post by wilee-nilee on 2009-12-09
I am not familiar with BSD or Debian in general. I think probably the USB was not cleaned completely with the Disc utility probably. One of the advantages of gparted though is that you can delete the partition in there then create a new one. I have a SanDisk Cruzer that works best when I use gparted do to a built in portion that is MS orientated.

It may be to that what ever USB loader your using may not be BSD friendly so it isn't getting loaded with the OS. Have you tried the pendrive loader?
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I suspect that there are BSD forums you might check, and see if there are answers there.

I have also just put a ISO on a thumb and set it as a boot partition in gparted and had that work with puppy linux

---

### Post by Marlonsm on 2009-12-09
To use Gparted:

-Get it in the Software Centre and open.

-Select the right device, usually it'll be /dev/sdb, but make sure looking at the size, in my example it is a 2Gb pendrive, so 1.86Gb is normal.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139234&stc=1&d=1260402139[/IMG]

-Right click and unmount

-Right click again and select the file system, usually fat32 is the best, because Windows can also use it.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139235&stc=1&d=1260402139[/IMG]

-Click Apply and it's done.


It should format no matter what happened to the device (unless it's broken, of course).

---

### Post by ramjet_1953 on 2009-12-09
An easier way:

1. Plug in your pen drive

2. When the drive's icon appears on your desktop, right click on it.

3. Choose the format option in the drop down menu.

4. It will give you a selection of formatting options.


Regards,
Roger :D

---

