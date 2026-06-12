---
title: "Backing up to/from disk images"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by nathan28 on 2010-09-13
So I have an XP machine that takes 12 minutes to boot + login, and easily at least 5 to come out of "hiberation". I'm installing ubuntu 10.04 on it. Problem is it's got all my institutional/corporate licensed software, which I need from time to time (OpenOffice gets no respect). So I want to back it up to an image on an external disk just in case.

I'm going to use knoppix to dd it, per this:

[html]http://www.linuxweblog.com/dd-image[/html]

To backup and restore, it says:
> # dd if=/dev/hda conv=sync,noerror bs=64K | gzip -c  > /mnt/sda1/hda.img.gz

> # gunzip -c /mnt/sda1/hda.img.gz | dd of=/dev/hda conv=sync,noerror bs=64K

Seems legit. Are there any issues with those flags like bs=64K?

That, and that page says to "blank" all the unused disk space for maximum compress--how do I do zero out all the empty space?

---

### Post by howefield on 2010-09-14
Open a terminal and type 

```
man dd
```

for an explanation on each of the options.

And to give you an alternative, Clonezilla from a Live CD (or USB) 

clonezilla.org

---

### Post by nathan28 on 2010-09-14
> **howefield said:**
> Open a terminal and type 

```
man dd
```

for an explanation on each of the options.

And to give you an alternative, Clonezilla from a Live CD (or USB) 

clonezilla.org

Thanks, clonezilla was a quicker download than a knoppix torrent.

My question is how to zero out the unused space (presumably from a live CD boot) on the XP drive so it will compress down--I've defragged it, and am trying not to have a 120GB image gobbling up my external disk's space.

---

### Post by asmoore82 on 2010-09-14
[SIZE="3"]BIG +1 for CloneZilla.[/SIZE]

It is a complete enterprise ready imaging solution.
No need to worry about the free/unused space - it takes sparse images.

---

### Post by howefield on 2010-09-15
> **nathan28 said:**
> I've defragged it, and am trying not to have a 120GB image gobbling up my external disk's space.

If your only reason for zeroing out the space is to get a smaller image, then you don't need to worry, as said above, clonezilla will only image the used space.

Eg, to give you an example, my 500 gig disk has 2 Ubuntu installs on it, total used disk space for both is about 8 gig, the Clonezilla image is 2.7 gig.

Unless you do a sector by sector image, you'll be fine.

---

### Post by nathan28 on 2010-09-15
Thanks for the help!

---

