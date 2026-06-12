---
title: "not allowed to make a link to anything in a fat32 filesystem.Help.."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by cirrusminora on 2009-02-08
One of my filesystems is fat32 and when I try to make a link for any item I'm told : Error "Operation not permitted" while creating a link to "/media/sda1/stuff

I use 7.10 gutsy and my other two NTFS systems work just fine.

I'd be grateful for any work-arounds for this.Thanks.

---

### Post by hyper_ch on 2009-02-08
I tend to think fat32 can't handle sym links.

---

### Post by ugm6hr on 2009-02-08
> **hyper_ch said:**
> I tend to think fat32 can't handle sym links.

You should be able to link to /media/sda1/ but probably not /media/sda1/stuff (which is presumably within a fat partition).

---

### Post by cirrusminora on 2009-02-08
Yes.You just can't link to folders "within" sda1. So,is there nothing that can be done about it,short of modifying it altogether? 

Thanks guys.

---

### Post by ugm6hr on 2009-02-08
> **cirrusminora said:**
> So,is there nothing that can be done about it,short of modifying it altogether? 

Don't think so. Sorry.  fat partitions don't support symlinks.

---

### Post by jimv on 2009-02-08
Could migrate to EXT3 on that partition.  Then in Windows, just install the EXT2 driver from [http://www.fs-driver.org](http://www.fs-driver.org).

Or you could go to NTFS (just noticed that you said that worked fine).

---

### Post by hyper_ch on 2009-02-08
as ugm6hr says:

you cannot create symlinks on fat32

however you can create symlinks on a ext3 that points to a file on fat32

---

### Post by brianfactors on 2009-07-09
Ok, this is very important to understand: There are two types of links in Ubuntu. It's a different concept from the "shortcut" in Windoze. So two types:

1) Hard Links: Hard links link to the actual file (identified by an inode number). So Hard links link to a physical place on the hard drive.

2) Soft Links: A link that points to a file location in the file hierarchy. In other words, it's based upon the file organization in the location bar.

The best way to put this is real terms is to say that a hardlink is like telling you to go to 20 degrees North 40 degrees west latitude. A symolic link is like telling someone to go to 200 Main St. If you send someone into a city, coordinates are useless, just like hard links don't work when you're "sending" the computer to another drive.

I don't know which one of these ubuntu creates graphically, but I know that if you use the command prompt, symbolic links work great for linking to another system.

First, mount the file (so It's in a place like /media/drive/). Then use the terminal to navigate to the file you wish to link FROM. Then type:
```

ln -s <the file you want to link to>

```
For example:
```

ln -s /media/drive/files

```
A link named "files" will be in the directory you are in.

If you want help on what exactly I mean when I say "navigate using the terminal," check this out: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Really this is a lot easier than it sounds. Just take a little getting used to.

---

