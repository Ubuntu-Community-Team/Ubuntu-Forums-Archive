---
title: "Flash Drive Missing Space"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Raynman37 on 2008-12-29
Hey everyone,

I have an 8gb Sandisk flash drive, and a couple weeks ago I tried to make it into a bootable Ubuntu flash drive.  I got frustrated with it not working so I stopped and I just picked it back up today to work on.  I remember trying it multiple times, both from the live CD and from the directions here: 

[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

I tried both ways and it never booted on any of the computers I tried, hence the frustration.  Now I think though that I am even worse off than before.  When I plug the flash drive in, it only shows that there is around 3.8gb left on it.  Where did the the other 4.2gb go?  I went into gparted and it only shows one large 3.8gb partition.  Here are the results from fdisk -l:

```
Disk /dev/sdb: 3759 MB, 3759734272 bytes
255 heads, 63 sectors/track, 457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000095cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         457     3670821    b  W95 FAT32

```

I tried reformatting the flash drive to see if anything happened, but alas nothing did.  Did I irreversibly damage my flash drive or am I just missing something?

PS-I wasn't sure what kind of diagnostic things to run, so if there is more information you want, just let me know.

---

### Post by shearn89 on 2008-12-29
I found something called unetbootin, which runs on windows (i think) and lets you create a bootable drive from an iso or such.

Can't remember the link, but GIYF (google is your friend).

---

### Post by Raynman37 on 2008-12-29
Yeah, I've seen a lot of programs that do similar things, but at this point, I'm not worried about making the flash drive bootable anymore.  I just want to know if I can ever recover that missing space.

---

### Post by shearn89 on 2008-12-30
I'd plug it in and try running gparted - it should give you a graphical representation of whats on the drive. You should be able to merge 2 partitions if they're there. If not, i'm not sure whats going on...

---

### Post by Raynman37 on 2008-12-30
Yeah, gparted was the first thing I tried.  It just showed one 3.8gb partition and nothing else.

---

### Post by Raynman37 on 2009-01-01
Bumpify.  Hoping someone knows what happened to the flash drive so I know whether to scrap it, fix it, or just cry.

---

### Post by Raynman37 on 2009-03-02
I let this go for a while, but I was hoping maybe I can get some new opinions if I bump this again.

---

### Post by shearn89 on 2009-03-02
forgot i was subscribed to this. bumpity bump just to get an answer (its a weird problem i've never come across).

---

### Post by egalvan on 2009-03-02
> **Raynman37 said:**
> I let this go for a while, but I was hoping maybe I can get some new opinions if I bump this again.

1)
If you have nothing you need on the drive,
then try gparted to erase all partions.

2)
See if Sandisk website has software to wipe the drive.

3)
I use dban (Darik's Boot'n'Nuke) to wipe drives.

if nothing works, you may have a wonky drive.
It may be under warranty.

---

### Post by Raynman37 on 2009-03-02
So far nothing has worked.

1.) I tried Gparted again, deleted the partition, but it says that all that is present then is an unformatted 3.5 GB storage device. (See attachment)

2.) I downloaded a SanDisk utility and ran it, but no luck

3.) Dban seems like it may be a viable alternative, but I haven't found any good documentation on how to use it to only wipe a flash drive, and not my whole HDD.  Do you know a good place with documentation, or do you know how to use it?

My big question is: Is it possible to corrupt only a part of flash memory so that it is permanantly unusable?

---

