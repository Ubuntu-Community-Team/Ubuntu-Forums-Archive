---
title: "Resizing a partition?"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Mugabuga on 2010-04-26
If I dual boot XP and Ubuntu, can I resize the partitions later to make more room for the Ubuntu part?

---

### Post by Bucky Ball on 2010-04-26
Yes, you can. Use the partition editor (System->Admin) BUT, the partition you are wanting to resize needs to be unmounted. Therefore, boot from the install disk and 'try Ubuntu' and do it from there. This way, none of your partitions will be mounted because you are not running from the hard drive install.

Before you try this, make sure you backup anything important.

---

### Post by nhasian on 2010-04-26
yes you can resize both the windows XP NTFS partition as well as the linux EXT3/4 partition using the parition editor (gparted) from the ubuntu LiveCD.  make sure to backup your data first!

---

### Post by tonymartini on 2010-04-27
hi guys does that mean that by resizing the ubu part it will erase the data already there on the hard disk?? is it the backup just a precaution?
regards 
TM :P

---

### Post by Mugabuga on 2010-04-27
> **tonymartini said:**
> hi guys does that mean that by resizing the ubu part it will erase the data already there on the hard disk?? is it the backup just a precaution?
regards 
TM :P

I'm pretty sure its just a precaution, whenever you deal with hard drives you want to backup.

---

### Post by egalvan on 2010-04-27
> **Bucky Ball said:**
> Use the partition editor,
  the partition you are wanting to resize needs to be unmounted
, boot from the install disk and 'try Ubuntu' and do it from there. 
**This way, none of your partitions will be mounted because you are not running from the hard drive install.**

Actually, most LiveCD's will search for a valid swap partition...
The Ubuntu LiveCD does this, so if you have a swap partition, you must un-mount it (via 'swap-off').

> Before you try this, [COLOR="Red"]make sure you backup anything important[/COLOR].

Absolutely +1

gparted is very stable, but it's always a good idea to back up.
Gremlins can sneak in.

---

### Post by aeiah on 2010-04-27
> **tonymartini said:**
> hi guys does that mean that by resizing the ubu part it will erase the data already there on the hard disk?? is it the backup just a precaution?
regards 
TM :P

it wont erase anything. it'll only allow you to reduce a partition within its free space. bear in mind though that in truth data may be spread out everywhere.. its probably a good idea to defrag the windows partition if you are shrinking it before doing anything, so the actual resize process goes quicker. it may still need to shift data blocks around of course, and this can mean that resizing partitions can take several hours.

---

### Post by Mugabuga on 2010-04-27
> **egalvan said:**
> Actually, most LiveCD's will search for a valid swap partition...
The Ubuntu LiveCD does this, so if you have a swap partition, you must un-mount it (via 'swap-off').


Whats a swap partition?

---

### Post by Bucky Ball on 2010-04-27
Just one more thing: if you are resizing the Windows partition, make sure you defragment it first or you can run into some real issues and that may screw the Windows install.

Just in case ...

---

### Post by warfacegod on 2010-04-27
> **Mugabuga said:**
> Whats a swap partition?

Its the Linux version of a Windows Paging file. Both are at their basic idea, Hard Drive as RAM

---

### Post by nhasian on 2010-04-27
i'm not 'this guy' :-P
i mean backup as a precaution.  people make mistakes.  my friend inserted a 2GB thumbdrive into his computer, and went to format it.  he accidentally formatted his 2TB external drive instead!  OOOPS!  plus it was already 75% full.  he lost 1.5TB of data.

> **tonymartini said:**
> hi guys does that mean that by resizing the ubu part it will erase the data already there on the hard disk?? is it the backup just a precaution?
regards 
TM :P

---

### Post by mrpinchy on 2010-04-27
> **nhasian said:**
> i'm not 'this guy' :-P
i mean backup as a precaution.  people make mistakes.  my friend inserted a 2GB thumbdrive into his computer, and went to format it.  he accidentally formatted his 2TB external drive instead!  OOOPS!  plus it was already 75% full.  he lost 1.5TB of data.

Wow!!  It's gonna take a long time to re-find and download all that porn...








Sorry, couldn't help it.

---

### Post by gadolinio on 2010-04-27
> **mrpinchy said:**
> wow!!  It's gonna take a long time to re-find and download all that porn...


hahahahahahahah!!!



What's that about having to unmount the swap partition when working with a liveCD? Doesn't the liveCD refrain from touching the HD?
I have resized partitions more than once, and never had that in mind. And things went out well.

---

### Post by warfacegod on 2010-04-28
While you are resizing partitions, you may want to consider doing away with your swap partition and reclaiming that space. If you don't do any video encoding and you don't Suspend/Hibernate, and you have a decent amount of RAM say 1 GB or more, you'll probably never really need swap at all.

I have 2 GB RAM and I've been running without swap for over a year. With 9.04 and 9.10 as well as around a dozen other Linux distros on another partition, I've never had any issues and my system is faster because of it.

---

### Post by srs5694 on 2010-04-28
> **warfacegod said:**
> While you are resizing partitions, you may want to consider doing away with your swap partition and reclaiming that space. If you don't do any video encoding and you don't Suspend/Hibernate, and you have a decent amount of RAM say 1 GB or more, you'll probably never really need swap at all.

I disagree with this recommendation, for a couple of reaons. First, swap space exists, in part, so that the system has a fallback in case extra memory is needed. You might run for a year without needing it, but then if you have a temporary need for extra memory, having swap space will help immensely.

Second, Linux will often use swap space to improve performance even if the demand for memory by programs doesn't exceed the available RAM. To understand this, remember that Linux caches disk accesses. In fact, once a Linux system has been running for a while, chances are most of its available memory will be used in this way. Consider the following memory use, which is from my MythTV system running Ubuntu:

```

 free -m
             total       used       free     shared    buffers     cached
Mem:          1940       1900         40          0         11       1448
-/+ buffers/cache:        439       1501
Swap:         3472        151       3320

```

The "-/+ buffers/cache" line shows the memory demand by programs: Only 439MB of 1940MB available memory is in use. The "Mem" line, OTOH, shows the total memory use (including buffers and cache): 1900MB of 1940MB is in use. In other words, 1501MB (77% of available memory) is being used by buffers and caches. Furthermore, 151MB of swap space is in use. The reason is that memory allocated by programs, but not much used, has been moved to swap so that the system can use more memory for buffers and caches to improve disk performance.

Of course, in this specific case, 151MB out of 1940MB isn't a huge amount (it's 7.8% of memory), so the performance improvement won't be dramatic; but it could be important for some people or in some situations, and the amount of memory swapped out in this way could be bigger on some systems, depending on usage patterns. Furthermore, on modern hard disks, a typical swap partition of 2-10GB is trivial, so the disk resources freed up by not creating a swap partition are pretty minor. Overall, for most people, it's far better to create a swap partition than to not do so.

---

### Post by warfacegod on 2010-04-28
I've never had my swap use more than 52 MB. I decided having a 4 GB swap taking up space simply didn't justify such a trivial amount of use.

With no swap, I've let my laptop run for well over two weeks. Full Compiz graphics w/ transparencies, Swiftfox, Gmone M-Player, Pidgin, Update Manager, Synaptic, 3 Terminals, Open Office, GCompris, Brasero, plus many others, w/ ktorrent downloading 8 torrents the entire time.

Zero problems.

---

