---
title: "Formatting Removable drive"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by jeggerleg on 2009-01-31
Hi

I have just been through a thread regarding formatting usb drives as ext3 - something I have done. The result needless to say is a useless drive which will not allow me to write anything to it. 
I have tried to follow the advice given in that thread to no avail and need help for the hard of understanding. Can anyone point me in the right direction?

---

### Post by diablo75 on 2009-01-31
Download a gParted Live CD, boot off of it, and use that format your drive.  Should work like a charm.

Here's a direct download of the latest version:

[http://downloads.sourceforge.net/gparted/gparted-live-0.4.1-2.iso?modtime=1230460364&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-live-0.4.1-2.iso?modtime=1230460364&big_mirror=0)

---

### Post by taurus on 2009-01-31
If the drive is an ext3, you just need to change the mount point of it from root to your login name if you want to write to it without being root.

Assuming it is mounted to /media/sdb1 and your login name is jegger, you would do something like this from a terminal.

Applications -> Accessories -> Terminal
```
sudo chown -R jegger:jegger /media/sdb1
ls -la /media
```

---

### Post by richg on 2009-01-31
May not be any help, but I have never formatted any hard drives the five years I have been using Linux. I must be the only one who does this.

I also have multiple plug in (in the PC box) hard drives for the OS, IDE type. One drive, one OS.

I have an external hard drive for backing up personal files and used it straight out of the box. Use to back up W98SE files and Linux files to different directories with no issues. Now, only Linux files. Still use files created some years ago under Windows.

I guess if you want to install a OS on the external drive you will have to do the proper format thingy.

Rich

---

### Post by jeggerleg on 2009-01-31
The only reason I wanted to format to anything other than fat 32 is that I couldn't transfer files bigger than 4 or 5gb - can't remember which.
Had I had the foresight to format the drive originally to NTFS the problem wouldn't have arisen.
Had I done that I could have used the drive under Windows/DOS and Linux without any difficulty. Formatting using the supposedly superior Linux file system means I can't read it at all. 
And if I haven't got it wrong even when I do finally manage to read and write to it I can only do it on this machine. Not much good as a backup when this hard disc goes tits up.
Using the inferior NTFS system I can read it on any machine.

---

### Post by sirebral on 2009-01-31
look into fdisk

---

