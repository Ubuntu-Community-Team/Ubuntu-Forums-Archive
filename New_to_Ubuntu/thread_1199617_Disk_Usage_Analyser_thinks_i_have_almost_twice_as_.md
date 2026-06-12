---
title: "Disk Usage Analyser thinks i have almost twice as much hd space as i do (i think)"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Max Williams on 2009-06-29
I have an 80GB hard disk (i think) but when i run the disk usage analyser it says 

total capacity - 142 gb 
used - 115 gb
available - 26 gb

But, my / folder has 60GB of data - so where's the other 55G of used up space?  Is the disk usage analyzer getting confused?  I tried a couple of command line tools and got these results:

"fdisk -l" gives me this -

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

"df -h" gives me this:

/dev/sda1              72G   56G   13G  83% /
varrun                502M  148K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   52K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon       72G   56G   13G  83% /home/max/.gvfs
tmpfs                 502M   40M  463M   8% /lib/modules/2.6.24-24-generic/volatile

Any ideas anyone?  I'm now starting to wonder if i DO have a 142gb drive - which would be nice.  It's a dell inspiron 1300 laptop which according to the net has an 80gb drive though.  

confused...
thanks!
max

---

### Post by Roadbloc on 2009-06-29
it did that to me. i want too bothered about it though. it cheered me up.

---

### Post by mcduck on 2009-06-29
The .gvfs file confuses disk usage analyzer, causing it report disk size & usage twice higher than what you really have.

```
gvfs-fuse-daemon 72G 56G 13G 83% /home/max/.gvfs
```
.gvfs is actually a virtual file system, with 0 size and 0 disk use.

I remember there being some way to make Disk Usage Analyzer to ignore .gvfs, but I can't remember it right now. I'll have to check if I can find it.

edit: Are you running 9.04 or some older Ubuntu release? Becasue I'm using 9.04 and the version of Baobab seems to treat .gvfs correctly and doesn't have the "double disk size, double disk use"-bug.. Which is probably why I can't find the fix any more either. :D Anyway, check Edit/Preferences, and if the .gvfs shows in the file systems list disable it.

---

### Post by Max Williams on 2009-06-29
> **mcduck said:**
> The .gvfs file confuses disk usage analyzer, causing it report disk size & usage twice higher than what you really have.

```
gvfs-fuse-daemon 72G 56G 13G 83% /home/max/.gvfs
```
.gvfs is actually a virtual file system, with 0 size and 0 disk use.

I remember there being some way to make Disk Usage Analyzer to ignore .gvfs, but I can't remember it right now. I'll have to check if I can find it.
Aha, thanks.   What's the function of gvfs, if it has 0 size?  I'm guessing it's a necessary part of linux.

cheers
max

---

### Post by mcduck on 2009-06-29
> **Max Williams said:**
> Aha, thanks.   What's the function of gvfs, if it has 0 size?  I'm guessing it's a necessary part of linux.

cheers
max

It's a kind of abstraction layer Gnome uses for mounting network drives, virtual file systems and such and to access files on them.

[http://en.wikipedia.org/wiki/GVFS]("http://en.wikipedia.org/wiki/GVFS")

---

### Post by Max Williams on 2009-06-29
> **mcduck said:**
> It's a kind of abstraction layer Gnome uses for mounting network drives, virtual file systems and such and to access files on them.

[http://en.wikipedia.org/wiki/GVFS]("http://en.wikipedia.org/wiki/GVFS")

ah, thanks for the info!
max

---

### Post by searchesend on 2009-10-15
I'm quite new to this but I just edited the the Disc Usage Analyser Preferences so they were only looking at the Ubuntu partition and ignoring GVFS. That's given me the usage I was expecting.

---

