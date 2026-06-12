---
title: "How to find the device name for a digital camera?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by creperum on 2009-04-24
Okay..

I am trying to mount my digital camera so I can look at its internal memory as if it were an external drive (to try and recover a deleted picture).  

I know how to do something like "sudo mount /dev/sda1 /media/disk," but my question is: How do I know what to use for "/dev/sda1"?  I mean, how do I know the device name?  

The camera does not auto-mount when I connect it (which it did in some previous versions).  I am running Ubuntu 8.04, if that matters.

lsusb gives this:
```
Bus 001 Device 004: ID 040a:05b5 Kodak Co. 
Bus 001 Device 002: ID 0461:4d07 Primax Electronics, Ltd 
Bus 001 Device 001: ID 0000:0000  
```

with the camera plugged in, while dmesg gives
```
[  128.052000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  128.288000] usb 1-2: configuration #1 chosen from 1 choice
[  253.420000] usb 1-2: USB disconnect, address 3
```

How do I get the device name from that output so I can mount it?  Or, is there some other command I should be using?

Thanks so much!

---

### Post by duanedesign on 2009-04-24
In Terminal run

```
sudo fdisk -l
```

this should give you some additional info

You also might try messing around with the camera settings. Some people have had luck with setting their camera to "mass storage device" or similar.

EDIT: Additionally you might try gthumb to import photos. If you cant get it to work (I have read Kodak cameras and Linux dont get along) you can always but a card reader.

Good Luck!

---

### Post by creperum on 2009-04-24
Thanks for the reply! 

I forgot to mention that I already tried that.  fdisk -l only sees my internal hard drive.  

I don't know why; gphoto2 is able to find the camera, but even after running gphoto2, the camera still doesn't show up in fdisk -l or mount.

Any ideas??

---

### Post by tom56 on 2009-04-24
Usually on the camera there will be an option to switch between MTP and USB Mass Storage. Right now it is set to the former, and you want it set to the latter.

---

### Post by duanedesign on 2009-04-24
here are a few links that I hope solve your problem or at least get you going in the right direction.

[https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting)

this one is long but towards the last half has some workaround ideas, links to bugs and threads, ect.
[http://ubuntuforums.org/showthread.php?t=965167](http://ubuntuforums.org/showthread.php?t=965167)

I dont know if you get this error message or not. Regardless there is a lot of discussion regarding your problem
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682)

Good Luck

---

### Post by creperum on 2009-04-25
Thanks for the links....

I have managed to shift the problem to a different one, but I'm going to start a new thread because it's a different sort of issue.  Thanks for your help!

---

