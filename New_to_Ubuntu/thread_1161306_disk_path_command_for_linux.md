---
title: "disk path command for linux"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Enter t'Ibex on 2009-05-16
OK I have spent the better part of the morning trying to figure out how to get the terminal (booted from the LIVE CD 8.10) to point to the /dev/sda1 instead of the CDROM. I have gone through about 10 online tutorials and I cant take it anymore.

I have created a small partition on the HDD and want to put the live CD installer on it. (long story if your bored look for my other threads)

I must be missing something basic.  In msdos you just go "D:"  "C:" and it switches to whichever mounted drive....

Please please help me, very very frustrated....
Thanks

i see this right now
ubuntu@ubuntu:/$

---

### Post by logos34 on 2009-05-16
Try this:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

(-->'Live CD')

then add this to your existing menu.lst:

> title           installer
root            (hd0,0) [[COLOR="Red"]-->points to sda1, if that's where the .iso files are[/COLOR]]
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd          /casper/initrd.gz

---

### Post by s.fox on 2009-05-16
Hi,

Do you mean you want to change the directory?  If so take a look at [this]("http://http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-cd.html") guide.

Hope it helps,

Ash R

P.S.  I am aware that its a redhat guide,  but it will still work the same in Ubuntu.

---

### Post by mikewhatever on 2009-05-16
I think you need to simply go **cd /media/sda1**. I am assuming that the partition is mounted in /media and the mount point is sda1.

---

### Post by Enter t'Ibex on 2009-05-16
Ok you talked me into it. i will try it again.

---

### Post by Enter t'Ibex on 2009-05-16
ubuntu@ubuntu:/ cd /dev/sda1
bash: cd: dev/sda1:  Not a directory


right now ls give the contents of the CDROM

---

### Post by s.fox on 2009-05-16
Try using:
```

cd ../

``` to navigate backwards a directory.

Forward can be achieved by

```

cd someFolder

```

-Ash R

P.S.  Edited due to misreading of previous post

---

### Post by Enter t'Ibex on 2009-05-16
sure I can go further than that
ubuntu@ubuntu:/$ mount|grep ^'/dev'
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

ubuntu@ubuntu:/$ ls -p
bin/    dev/   initrd.img  mnt/   rofs/  srv/     tmp/  vmlinuz
boot/   etc/   lib/        opt/   root/  sys/     usr/
cdrom/  home/  media/      proc/  sbin/  target/  var/

---

### Post by mikewhatever on 2009-05-16
Do you know where the partition is mounted? What's the output of **ls /media**?

---

### Post by Enter t'Ibex on 2009-05-16
ubuntu@ubuntu:/$ ls /media
disk

---

### Post by mikewhatever on 2009-05-16
Try **cd /media/disk**.

Edit: An even better approach is to run **df -h** and see what is mounted and where.

---

### Post by logos34 on 2009-05-16
the live cd automounts partitions in /media/**disk**, /media/**disk-1,** /media/**disk-2**, etc.

so 

cd /media/disk

and you will be in / of sda1

---

### Post by Enter t'Ibex on 2009-05-17
I had a bunch of issues yesterday needed to reboot several times and then I ran out of personal time.  so sorry for the delay.

the df -h is awesome.  Thanks so much for all your help.  I was able to get unetbootin to load a bootable over to the drive (which was sda1 actually since the I had to put the actuall bootable drive as the secondary in bios sdb1)

I'm going to switch my issue back to the installation/laptop since now I have other errors that make NO sense to me.

Cheers

---

