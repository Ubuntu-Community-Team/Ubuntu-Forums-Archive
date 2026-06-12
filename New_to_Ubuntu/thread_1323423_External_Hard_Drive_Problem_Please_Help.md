---
title: "External Hard Drive Problem Please Help"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by amarumayo on 2009-11-11
Hi all,

I have a WD 500GB external hard drive that will not mount.  When I plug it in it spins but fails to mount.  It shows up in Gnome as a USB drive but when I click on it it says "Unable to mount location, cannot mount file"

I ran testdisk to try and get into the drive and i get a comment that says "Partition sector doesn't have the endmark 0xAA55"  

Does anyone know what this means?  Is my drive ruined?

Thanks

---

### Post by earthpigg on 2009-11-11
> **amarumayo said:**
> 
Does anyone know what this means?  Is my drive ruined?


dunno. here are four tools i would look into, though, if i where you:

[badblocks]("http://en.wikipedia.org/wiki/Badblocks") - in repos
[fsck]("http://en.wikipedia.org/wiki/Fsck") - already installed. what filesystem is on the hard drive?
[testdisk]("http://www.cgsecurity.org/wiki/TestDisk") - in repos
[smartmontools]("https://help.ubuntu.com/community/Smartmontools") - in repos

the first thing i'd do is check system -> administration -> partition editor and see what gparted can tell me. if it isn't installed, the package name is 'gparted'.

after that, in order: id make use of fsck first, then smartmontools, then badblocks, and testdisk as the last resort.

let us know what filesystem the external hard drive is (FAT32, ext3, etc), and we can get you started with fsck.

---

### Post by amarumayo on 2009-11-11
Partition editor says that /dev/sdc is unallocated.

How would I find out what filesystem I have (FAT32, ext3, etc) so that I can get started with fsck?

Thanks for the reply

---

### Post by earthpigg on 2009-11-11
> **amarumayo said:**
> Partition editor says that /dev/sdc is unallocated.

How would I find out what filesystem I have (FAT32, ext3, etc) so that I can get started with fsck?

Thanks for the reply

well... ideally, you would already have known. that way you can tell fsck what to attempt to repair. 

if you didn't change it, odds are it is fat32.

if data recovery is the priority and you have 500gb free somewhere, use photorec (comes with testdisk) to attempt to recover data first.

```
sudo photorec
```

after you give it time to recover all the files on the drive (you will lose file names and folder structure, but the data itself will probably mostly be ok... sorting through it will be a pain, though.), move on to fsck to attempt to repair the partition table.

```
sudo fsck.msdos -a /dev/sd_
```

replace _ with whatever letter it shows in gparted.

---

