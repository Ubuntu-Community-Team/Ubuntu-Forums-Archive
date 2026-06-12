---
title: "can't detect usb harddrive after 10.04"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by zhanglini on 2011-09-07
Up till 10.04, I never have problems with my SimpleTech 250 Gb external hard drive (detect/auto mount etc), but once I started using 10.10/11.04, I can't detect it any more.
It does not show up when I plug it in, nor would commands such as fdsik, dmesg yield anything.
Is it possible the newer versions got rid of the driver?  How do I fix this problem?

---

### Post by corncob on 2011-09-07
Try MountManager.  It needs to be installed from the Software Center.

---

### Post by anewguy on 2011-09-08
If you have no luck with that, try the following and post back the results.  Be sure the drive is attached.

lsusb

sudo lsusb

It's a long shot, but perhaps some udev rule caught this somehow.  We can at least tell from the above if your userid can see it, or if not, if root can see it.  This would indicate something happened to permissions.

Dave ;)

---

### Post by zhanglini on 2011-09-08
Thank you guys, I had other problems with 11.04 and decided to go back to 10.04 LTS.  I will keep this thread in mind when I upgrade to 13.04 LTS in the future.

---

### Post by anewguy on 2011-09-08
No problem - as we all say - use whatever works best for you!  Of course, as you know, when a LTS release is outdated, then the support goes away to. However, since 10.04 is is still valid it doesn't matter.  I think there are several of us who tried 11.04 but ended up going back to 10.xx for whatever our personal reasons were.  Some had some sort of problem, some, like me, are just getting too dang old and had a hard time getting used to some of the changes (I have an open request on launchpad for the window buttons) ;)  I know I could just use Ubuntu Classic and end up with Gnome, but I really do want to get to and use Unity, as it does seem like a neat idea as everything seems graphical rather than menued, but that will take some getting used to for me ;)

Best of luck, and sorry we couldn't get your problem fixed for now.  I'm just glad you're sticking with linux!

Dave ;)

---

### Post by zhanglini on 2011-09-09
For whoever may find this useful!
It seems that I have found the source of the problem --- sort of.  I noticed that  I had made two changes before the usb hard drive started giving me problems: 1.  Ubuntu version; 2.  The HD was plugged in different power outlets.  It is not turned off anything, but somehow it is affected --- strange!
So I plugged into the original one --- all is working now.

---

### Post by corncob on 2011-09-09
> **zhanglini said:**
> For whoever may find this useful!
It seems that I have found the source of the problem --- sort of.  I noticed that  I had made two changes before the usb hard drive started giving me problems: 1.  Ubuntu version; 2.  The HD was plugged in different power outlets.  It is not turned off anything, but somehow it is affected --- strange!
So I plugged into the original one --- all is working now.

Is it powered through the USB cable or do you plug it into the wall?

---

### Post by zhanglini on 2011-09-10
> **corncob said:**
> Is it powered through the USB cable or do you plug it into the wall?

Into the wall.
Versions above 10.04 still won't work no matter the power outlet, maybe they got rid of the driver.

---

### Post by corncob on 2011-09-10
I'd worry about the power outlet.  Do other things work in it?  It doesn't get hot, does it?  Just because the outlet has a ground receptacle doesn't mean its connected.  You need some kind of equipment to check that out though, even if its just a test light.

---

### Post by zhanglini on 2011-09-11
> **corncob said:**
> I'd worry about the power outlet.  Do other things work in it?  It doesn't get hot, does it?  Just because the outlet has a ground receptacle doesn't mean its connected.  You need some kind of equipment to check that out though, even if its just a test light.

the outlet is fine, in the sense that when the harddrive is plugged in, the drive can be turned on (and stays on).  The problem is when under 10.04, the drive will sometimes shows up, sometimes disappears --- while the drive is physically on all along!

---

### Post by anewguy on 2011-09-11
Please post the outputs I requested before:

lsusb

sudo lsusb

mount


Dave ;)

---

### Post by zhanglini on 2011-09-11
> **anewguy said:**
> 
sudo lsusb
mount 

The following is the results I got, I am trying to detect/mount "Simpletech".  Thanks

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**Bus 002 Device 003: ID 4971:cb07 SimpleTech **


/cow on / type overlayfs (rw,commit=0,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

---

### Post by anewguy on 2011-09-11
If you do

lsusb

without the sudo, does the disk still show in the output?

Thanks!
dave ;)

---

### Post by zhanglini on 2011-09-12
> **anewguy said:**
> If you do

lsusb

without the sudo, does the disk still show in the output?

Thanks!
dave ;)

Well they yield practically the same things:
**ubuntu@ubuntu:~$ sudo lsusb**

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive

Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

Bus 002 Device 003: ID 4971:cb07 SimpleTech 

Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

[B]ubuntu@ubuntu:~$ lsusb
[/B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive

Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

Bus 002 Device 003: ID 4971:cb07 SimpleTech 

Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

---

### Post by anewguy on 2011-09-15
Just wanted to let you know I haven't forgotten you, just that I'm still searching to see if I can find something to help you.

Dave ;)

---

### Post by zhanglini on 2011-10-04
> **anewguy said:**
> Just wanted to let you know I haven't forgotten you, just that I'm still searching to see if I can find something to help you.

Dave ;)

Thanks, I was out of the country myself and just got back!

---

