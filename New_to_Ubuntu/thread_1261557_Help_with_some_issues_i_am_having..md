---
title: "Help with some issues i am having."
date: 2009-09-08
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-09-08
OK. Last week I think it was, I posted about a scareware/malware virus that kept popping up on my Windows XP Home Edition on my Acer Aspire AOA150 ZG5. Well after many thwarted attempts to get rid of this virus, it persists on staying alive ( used drweblive.iso, bitdefender, clamav, avg, anti malware, and ccleaner ) . My last attempt is going to be formatting my entire drive, because right now my windows wont even start( I am not sure why and i dont really wanna know why ). NOW, the question: if I use a USB drive with Easy Peasy to hopefully take all my important files off of my partitioned hard drive. Will formatting my hard drive completely wipe EVERYTHING out? and does anyone know where i can find a version of TINYVISTA for my lil' Acer? If not i have a version of Windows XP Wolf Edition on stand by. OH how do i go about formatting my hard drive safely and effictively? If non of the Windows I try to put on work I will probly put on Ubuntu and make this machine run just that. But I'd prefer a dual boot. Thank You for any help.

---

### Post by nhasian on 2009-09-09
well if you are going to dual boot you can just boot off the windows CD first.  when the partition part of the install comes up, delete the entire partition.  this will erase everything from the drive including the virus.  Then create a partition but make sure to leave enough space for ubuntu.  finish install windows, and then boot off your ubuntu liveCD and start the installation.  make sure to use the empty drive space for the new / root, /home, and swap partitions.  since your doing a fresh install now would be a good time to give Karmic a try with its EXT4 and grub2 :)

---

### Post by Bartender on 2009-09-09
If your PC is all goofed up, you can do this on any Windows PC with a broadband connection.  Download the latest stable version of GParted LiveCD (link under my sig).  It's an .iso, so you have to burn the image, not just copy the data.  When done, you have a bootable disc that can be used to delete partitions, create partitions, move them, etc.  It's a wonderful tool.

Manipulating empty spaces is one thing.  If you're trying to move existing data, things get a little trickier.  I've used GParted to move data with success a few times, but I screwed up Vista when I tried to shrink it.  Herman says you can avoid that by ticking the "Round up Cylinders" box when moving the data.  I haven't tried that.

General consensus on this forum *seems* to be that shrinking a Vista partition is more reliably done via the Vista partitioner.

---

### Post by howefield on 2009-09-09
Are you asking about how to prepare your system in order to install copies of pirated windows operating systems ? Probably the wrong forum to ask....

Of the three questions you ask,..

1. Formatting the drive will wipe it clean, you'll have an empty drive.
2. No one here can tell you how to obtain pirated programs.
3. The installers for windows/ubuntu should be able to format your drive.

---

### Post by LewRockwell on 2009-09-09
> **Bartender said:**
> If your PC is all goofed up, you can do this on any Windows PC with a broadband connection.  Download the latest stable version of GParted LiveCD (link under my sig).  It's an .iso, so you have to burn the image, not just copy the data.  When done, you have a bootable disc that can be used to delete partitions, create partitions, move them, etc.  It's a wonderful tool.

Manipulating empty spaces is one thing.  If you're trying to move existing data, things get a little trickier.  I've used GParted to move data with success a few times, but I screwed up Vista when I tried to shrink it.  Herman says you can avoid that by ticking the "Round up Cylinders" box when moving the data.  I haven't tried that.

General consensus on this forum *seems* to be that shrinking a Vista partition is more reliably done via the Vista partitioner.

we thought he said to UNtick the box?

.

---

### Post by LewRockwell on 2009-09-09
> **howefield said:**
> Are you asking about how to prepare your system in order to install copies of pirated windows operating systems ? Probably the wrong forum to ask....

Of the three questions you ask,..

1. Formatting the drive will wipe it clean, you'll have an empty drive.
2. No one here can tell you how to obtain pirated programs.
3. The installers for windows/ubuntu should be able to format your drive.

formatting does NOT wipe a drive or media, all the data is STILL there...just not as "easy" to get to...

[http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)

[http://en.wikipedia.org/wiki/Data_recovery](http://en.wikipedia.org/wiki/Data_recovery)

[http://en.wikipedia.org/wiki/Testdisk](http://en.wikipedia.org/wiki/Testdisk)

[http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)

[http://en.wikipedia.org/wiki/DBAN](http://en.wikipedia.org/wiki/DBAN)

[http://en.wikipedia.org/wiki/Data_erasure](http://en.wikipedia.org/wiki/Data_erasure)

{{sigh}}

as always, your mileage may vary

.

---

### Post by howefield on 2009-09-09
> **LewRockwell said:**
> formating does NOT wipe a drive or media, all the data is STILL there...just not as "easy" to get to....

Oh dear, technically you are correct, for the intent of the OPs question, formatting will do what he wants.

{{sigh}}

---

### Post by LewRockwell on 2009-09-09
> **howefield said:**
> Oh dear, technically you are correct, for the intent of the OPs question, formatting will do what he wants.formatting will do what he wants

> **cirabisi2009 said:**
> ...
Will formatting my hard drive completely wipe EVERYTHING out?
...

nope

.

---

### Post by NCLI on 2009-09-09
> **cirabisi2009 said:**
> OK. Last week I think it was, I posted about a scareware/malware virus that kept popping up on my Windows XP Home Edition on my Acer Aspire AOA150 ZG5. Well after many thwarted attempts to get rid of this virus, it persists on staying alive ( used drweblive.iso, bitdefender, clamav, avg, anti malware, and ccleaner ) . My last attempt is going to be formatting my entire drive, because right now my windows wont even start( I am not sure why and i dont really wanna know why ). NOW, the question: if I use a USB drive with Easy Peasy to hopefully take all my important files off of my partitioned hard drive. Will formatting my hard drive completely wipe EVERYTHING out? and does anyone know where i can find a version of TINYVISTA for my lil' Acer? If not i have a version of Windows XP Wolf Edition on stand by. OH how do i go about formatting my hard drive safely and effictively? If non of the Windows I try to put on work I will probly put on Ubuntu and make this machine run just that. But I'd prefer a dual boot. Thank You for any help.
You're better off with [Tiny7]("http://tinyurl.com/lfeydn").

NOTE: I'm not linking to pirated software, it's just a Google search.

---

### Post by bapoumba on 2009-09-09
TO the OP: please keep discussions regarding pirated versions of Windows elsewhere, thanks.

---

