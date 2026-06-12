---
title: "Making USB"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Zahne on 2009-05-01
Hi,

So I'm trying to format my USB flas drive with MAC OSX and followed these steps:

# Download the desired .img file
# Open a Terminal (under Utilities)
#

Run diskutil list to get the current list of devices
# Insert your flash media
#

Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
#

Run diskutil unmountDisk /dev/diskN
#

Execute sudo dd if=/path/to/downloaded.img of=/dev/diskN bs=1m
#

Run diskutil eject /dev/diskN and remove your flash media when the command completes 

but when I get to step seven the one where you "execute," the response is always "Unknown file or destination" I input the correct name for the removable media because the ejection was successful but what do i put in for the destination? where do i write that in the code and where should the file be? Also, i wrote the correct .img file name.

---

### Post by Zahne on 2009-05-01
BUMP

This got thrown back to the 2nd page in 20 minutes. I'm sure the answer is right under my nose, a little nudge in the right direction would be much appreciated!:-)

---

### Post by blueridgedog on 2009-05-01
Can you post the actual command you are using and the output and also post the output of 

```
sudo fdisk -l
```

It is likely that you have a typo in the image name or the disk name.

---

### Post by hatalar205 on 2009-05-01
Try easy way. unetbootin (windows version)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by gandaran on 2009-05-01
> So I'm trying to format my USB flas drive with MAC OSX and followed these steps:
MAC OSX?
use ubuntu, install gnome format or gparted!

---

