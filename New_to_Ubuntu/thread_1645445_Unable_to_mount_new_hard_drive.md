---
title: "Unable to mount new hard drive"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by nivek4x4 on 2010-12-14
First and foremost I am completely new to Ubuntu,

The computer [#1] I am using has 10.04 on it and recognizes the new Seagate 500MB 16MB Internal 7200RPM hard drive I purchased and plugged into the motherboard as floppy0 but is unable to mount.

I want to load Ubuntu 10.10 64bit on it so I can transfer the hard drive to another computer [#2] I am building. I have downloaded 10.10 and utilized Make Startup Disk Utility and have the file on a USB stick. 

How can I mount the drive and load 10.10 64 bit on to the new hard drive? Please be specific as possible, because if it can be goofed up I will find the way.

Very respectfully,
Humble Newbie

---

### Post by ender4 on 2010-12-14
How are you trying to mount the hard drive?  If you are using the mount command on the terminal, then you need to be the root user, and the target directory would need already exist.  So you would do something like ```
sudo mkdir /media/hardDrive
sudo mount /dev/floppy0 /media/hardDrive
```

This assumes that the device /dev/floppy0 points to your hard drive, and you want to mount it on /media/hardDrive.  If this doesn't work, please post the output of the mount command.

---

### Post by albert s on 2010-12-14
would it not be easier to simply put the new HDD in the new computer and have it boot off the USB stick you have Ubuntu on.?
this way the install is set up for all your new hardware too.

---

