---
title: "External Hard Disk Problem."
date: 2009-05-02
forum: New to Ubuntu
---

### Post by sapple on 2009-05-02
Hello,

I have an external harddisk which I can connect to the computer with USB. However when I plug it in, my computer (running Xubuntu 8.04) doesn't recognize it. Nothing happens.

I try plugging in a flash disk, it is ok, it is recognized properly. I also try this external harddisk on different computers (both running XP or Ubuntu), and it works fine there also. It only doesnt work on my computer.

What should I do ?

Note: I type fdisk -l and here is the output:

Disk /dev/sda: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13651364

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2421 19446651 83 Linux
/dev/sda2 2422 2490 554242+ 5 Extended
/dev/sda5 2422 2490 554211 82 Linux swap / Solaris


So it doesnt recognize it. (my external HD is 100GB and has 3 partitions)

---

### Post by sapple on 2009-05-02
up

---

### Post by Sir Jasper on 2009-05-02
Hi sapple,

Please tell us how each of the three partitions is formatted.

I had the same problem which was easily fixed. If you do not 
get an answer within the next 18 hours, I will try to remember
how and then let you know.

My regards

PS I read it is polite to wait 24 hours before bumping a post.

Addendum:

Type "xubuntu" into the search engine above and you will see there a more recent thread to help you.

---

### Post by sapple on 2009-05-03
Ok, the thing is it works perfectly fine on another laptop which is running Ubuntu 8.04.  But it doesnt work in this old Desktop running Xubuntu 8.04.

So when I right click on the partition and go to the properties tab, It says: file system: ntfs (3.1).

I hope this helps.

Edit: the cable is connected to the computer with a USB, and to the hard disk with a fire wire

---

### Post by sapple on 2009-05-03
I need help please...

---

### Post by cariboo on 2009-05-03
Can you paste the results of:

```
dmesg | tail -n15
```

when you plug the drive in, this may help diagnose the problem. 

I had a usb drive disappear after a crash, I just let is sit for a couple of hours then pulled the usb cable and plugged it back in again, it has been working ever since.

---

### Post by DJonsson2008 on 2009-05-04
if the drive is ntfs 

ntfs-config

gui may give you some leverage.

---

### Post by sapple on 2009-05-08
the response to   dmesg | tail -n15    is:

[  472.907876] usb 1-2: device not accepting address 2, error -110
[  473.019825] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[  483.420318] usb 1-2: device not accepting address 2, error -110
[  483.420632] usb 1-2: USB disconnect, address 2
[  483.420955] scsi 2:0:0:0: Device offlined - not ready after error recovery
[  483.532252] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  498.637571] usb 1-2: device descriptor read/64, error -110
[  513.842503] usb 1-2: device descriptor read/64, error -110
[  514.058318] usb 1-2: new full speed USB device using uhci_hcd and address 4
[  529.159443] usb 1-2: device descriptor read/64, error -110
[  544.364540] usb 1-2: device descriptor read/64, error -110
[  544.580357] usb 1-2: new full speed USB device using uhci_hcd and address 5
[  554.980876] usb 1-2: device not accepting address 5, error -110
[  555.092787] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  565.493289] usb 1-2: device not accepting address 6, error -110

---

### Post by sapple on 2009-05-08
> **DJonsson2008 said:**
> if the drive is ntfs 

ntfs-config

gui may give you some leverage.

when i do that a window pops up, I click OK and nothing happens..

---

### Post by Marvin666 on 2009-05-08
NTFS-config works well. I keep all my files on an ntfs partion, so I can access them under windows too, and I've never had any troubles with it so far.
Do both check boxes apear when the drive is plugged in, and you start ntfs-config?

---

### Post by sapple on 2009-05-08
what? my problem is i cant access to my external hard disk

---

### Post by Sir Jasper on 2009-05-08
Try: Accessories>Thunar File Manager>Media 
then, if that doesn't work with the external
drive plugged in, what options are available?

---

### Post by sapple on 2009-05-08
there is no media folder in thunar

---

### Post by Sir Jasper on 2009-05-08
I'm using Xubuntu 8.10 and my Thunar has a Media folder.
Perhaps your lack of a Media folder will help someone else
to help you.

---

### Post by sapple on 2009-05-08
my vesion is 8.04

---

### Post by Sir Jasper on 2009-05-08
I read yours is 8.04 which is why I said mine is 8.10; but it may not matter.

---

