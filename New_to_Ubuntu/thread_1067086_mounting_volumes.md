---
title: "mounting volumes"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by liferocket on 2009-02-11
Ugg. i'm such a noob.
system has 2 hdds.. one with Ubuntu 8.10, other with WinXP Home.
Windows HDD has multiple NTFS partitions.
using Ubuntu to access music files on more than one of those partitions.
each boot, the first time I try open each partition, it tells me it can't mount 'cuz it doesn't have a mount file. the second time i click on it, it opens fine.

so, i poked around online, and found a suggestion about a mount script (something about "-t smbfs"). so, i put that into the little mount instructions box, and everything went to hell in a handbasket! now, it can't mount the volumes at all, so i can't get in there to take that script out!

i assume there's a way to fix this from the command line? please be patient, i know only 3 or 4 linux commands...

---

### Post by NT4usB on 2009-02-11
I don't know the answer straight up so here's a couple things to look at.
```
cat /etc/fstab
``` Is yout '-t smbfs' in there?

```
ls -al /dev/sd*
``` (or hd* if you're using PATA drives)
Do you see sda... and sdb...? 

You can mount the Windows drive using some commands and poke around or add it to fstab and it will mount when you boot Ubuntu.

Is the music on separate partitions from the Windows OS?

---

### Post by ebattleon on 2009-02-11
Use NTFS 3g which allow you to mount, read and write to NTSF(windows partitions). 

Their web page [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

