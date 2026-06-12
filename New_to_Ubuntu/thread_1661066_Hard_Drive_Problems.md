---
title: "Hard Drive Problems"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by Simjeey on 2011-01-06
Hi everyone.
I am in a bit of a sticky situation.  For some reason all pc places in jhb dont know anything about linex or how to work in it.  Go figure...
 
I bought a new external hard drive, its a 1.5Terribite Toshiba.  
My pc is not picking up the hard drive and i have no idea how to get it to work. 
HELP!

---

### Post by seawolf167 on 2011-01-06
With any new hard disk, you need to initialize and format the drive before it works. 

The easiest way (IMO) to do this in Ubuntu is to use gparted (System -> Administration -> GParted).

Note: if its not installed, open a terminal and type

```
sudo apt-get install gparted
```

Select your new disk, then format it (if you are ever going to plug it into a Windows computer you will want to format it in NTFS format vs. ext3 or ext4).

If for some reason NTFS is greyed out, open a terminal again and get ntfsprogs

```
sudo apt-get install ntfsprogs
```

Then re-format the drive in NTFS

Here is the [Ubuntu documentation link]("https://help.ubuntu.com/community/InstallingANewHardDrive")

---

### Post by Simjeey on 2011-01-07
Thanx, i'm gonna try it.
Hopefully i dont break it...

---

