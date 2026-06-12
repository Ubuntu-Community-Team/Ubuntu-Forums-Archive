---
title: "Fprot"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Treelvr on 2009-01-04
First I have looked everywhere for the .deb install for f prot. I do not think it exist. The best I can find is:

fp-Linux-i686-ws.tar.gz
44120-fprot_gui-0.6.kmdr.tar.gz
visual_f-prot_v2.1.tar.gz

Everytime I use this forum and search on f prot it always gives a link that is an 404.

Can someone either tell me how to install these or where to find the .deb files or am I just SOL. I have clam installed but it will only scan ubuntu install. I want to scan windows. I only use windows for frontpage but I want it clean.

I'm using using ubuntu 8.10 amd64

---

### Post by albinootje on 2009-01-04
There was a f-prot installer in the past.
[http://packages.ubuntu.com/search?keywords=f-prot](http://packages.ubuntu.com/search?keywords=f-prot)

See also :
[https://bugs.launchpad.net/ubuntu/+source/f-prot-installer/+bug/81996](https://bugs.launchpad.net/ubuntu/+source/f-prot-installer/+bug/81996)

---

### Post by Treelvr on 2009-01-04
Thanks for the info. But I'm using 8.10 and Amd64 and their isn't an installer.

---

### Post by albinootje on 2009-01-04
> **Treelvr said:**
> Thanks for the info. But I'm using 8.10 and Amd64 and their isn't an installer.

If you really want an alternative to Clamav (Clamav should be able to scan your Windows-partition), then there's also AVG for Linux I've read, and there must be more to download.

GL!

---

### Post by thane1 on 2009-01-04
[https://launchpad.net/ubuntu/intrepid/amd64/amavisd-new](https://launchpad.net/ubuntu/intrepid/amd64/amavisd-new)
     Hope the above link is of use.  Cheers

---

### Post by thane1 on 2009-01-04
I think this version of fprot might work for you.
[http://www.f-prot.com/download/home_user/download_fplinux.html](http://www.f-prot.com/download/home_user/download_fplinux.html)

---

### Post by Treelvr on 2009-01-04
I have fp-Linux-i686-ws.tar.gz  I don't know what to do with it. I've opened it with the archive manager. But when I've tried to run the install-f-prot.pl file it does nothing. I have no clue with how to get anything but a .deb file to work. Sorry noob. Tars and Gzs mystify me.

---

### Post by albinootje on 2009-01-04
> **Treelvr said:**
> I have fp-Linux-i686-ws.tar.gz  I don't know what to do with it. I've opened it with the archive manager. But when I've tried to run the install-f-prot.pl file it does nothing. I have no clue with how to get anything but a .deb file to work. Sorry noob. Tars and Gzs mystify me.

That fp-Linux-i686-ws.tar.gz has a README file in it, but..

See here :
[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)
--> [http://www.avg.com/filedir/inst/avg75fld-r51-a1243.i386.deb](http://www.avg.com/filedir/inst/avg75fld-r51-a1243.i386.deb)

Found it via this webpage, which has instructions (skip the alien part which converts the rpm into a deb) :

[http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html](http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html)

---

### Post by albinootje on 2009-01-04
> **thane1 said:**
> [https://launchpad.net/ubuntu/intrepid/amd64/amavisd-new](https://launchpad.net/ubuntu/intrepid/amd64/amavisd-new)
     Hope the above link is of use.  Cheers

Amavisd-new is software meant for mailservers to call one or more anti-virus software to do the scanning of emails.
It does not come with its own anti-virus software iirc.

---

### Post by Treelvr on 2009-01-05
Ok I figured out how to install fprot. Then I installed xfprot (get the newest because you can't get Gtk+ 2.4). Now the whole time I fought with this was because I wanted to scan all my drives (including win). But just like clam it will only let me see the ubuntu install. It won't even let me see the 2nd umbuntu drive. I have over 3 TB of HD and scanning the on win isn't an option because of the time. 14 hrs later win can't even scan its own 500 gig HD. And you can't do anything while its scanning cause its so slow.

Heres the question??

How can I use either clam or fprot to scan my whole computer??

---

### Post by albinootje on 2009-01-05
> **Treelvr said:**
>  But just like clam it will only let me see the ubuntu install.

Sounds like a permission problem.
Please post the output of the following :
```

sudo fdisk -l
mount
cat /etc/fstab

```

---

### Post by Treelvr on 2009-01-05
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x582f582f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb351b351

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84f47887

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   83  Linux

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cbc8a83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001    7  HPFS/NTFS
treelvr@treelvr-desktop:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/treelvr/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=treelvr)
/dev/sdd1 on /media/New Volume_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
treelvr@treelvr-desktop:~$ cat /etc/fstab

---

### Post by albinootje on 2009-01-05
> **Treelvr said:**
> 
treelvr@treelvr-desktop:~$ mount
/host/ubuntu/disks/root.disk on / type ext3
/dev/sdd1 on /media/New Volume_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /host type fuseblk 
/dev/sdc1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)

Can you run 
```

gksu clamtk 

```
And then choose "/media/New Volume" and/or "/media/disk-1" to scan ?

---

### Post by albinootje on 2009-01-05
In clamtk, select directory, then at the left choose "File System", then Media etc.

---

### Post by Treelvr on 2009-01-05
Works like a charm.

Thanks.

Tim

Isn't there a solved button around here??

---

