---
title: "Aligning filesystems to an SSD’s erase block size"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by nhasian on 2010-04-25
I just purchased two Corsair P128 SSD for use with my Laptop and Desktop with Ubuntu Lucid Lynx 10.04.  I understand for the drive to be set up properly I need three things:

Partition Offset ÷ NAND Page Size Aligned
Partition Offset ÷ NAND Erase Block Size Aligned
Partition Offset ÷ File Allocation Unit Size Aligned

What i don't understand is how to go about getting this done in linux.  I plan on making a 10 gig partition for root and the remaining space /home.  I can make a swap partition on my secondary HDD.  I'm comfortable with using gparted but to my knowledge it does not allow for this level of detail when creating partitions.  So i think i'm stuck with fdisk.  I also have an unopened Windows7 sitting in my desk drawer.  I wonder if I could just cheat and tell the windows7 installer to create two partitions for me then change them to ext4 in gparted...

---

### Post by srs5694 on 2010-04-25
Do you have any references to the alignment requirements for SSD devices? I'd like to read up on the topic. Thanks.

As to practicalities: With GNU Parted it's possible, but a bit awkward, to align precisely -- you've got to use the "unit s" command to enter partition start and end points in sectors and compute the alignment manually. Some versions will override your entries under at least some circumstances even then. Get the very latest version for best flexibility. GParted permits sector-precise alignment if you uncheck the "align to cylinder" box, but the values you enter are relative to the end of the previous partition, so you've got to be careful to size each partition correctly. You can check absolute alignment via the Partition->Information dialog box.

IMHO, fdisk (or gdisk for GPT disks) is better for this task, but you still need a recent version for best flexibility. You can type 'u' in fdisk to change the units to sectors rather than cylinders, and that adds a lot of flexibility. Typing 'c' toggles the DOS compatibility mode (the default is on). In DOS compatibility mode, fdisk tries to align partitions to cylinders; with the mode off, it tries to align to 1MiB boundaries. GPT fdisk (gdisk) is different; it uses sectors (or KiB, MiB, or GiB when so specified) for all input units. You can set alignment by using the 'l' option on the experts' menu. The default alignment varies with the program's version. With the latest version, it's 1MiB alignment on new disks, or the program tries to determine the alignment used by existing partitions on pre-partitioned disks.

---

### Post by nhasian on 2010-04-25
So far, here are the two most important URLs I've bookmarked:

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226)

and

[http://randomtechoutburst.blogspot.com/2010/03/4k-alignment-for-disks-important.html](http://randomtechoutburst.blogspot.com/2010/03/4k-alignment-for-disks-important.html)

one more:

[http://forum.corsair.com/forums/showthread.php?t=83608](http://forum.corsair.com/forums/showthread.php?t=83608)

i'd still like step by step instructions on how to do it properly.

---

### Post by nhasian on 2010-04-30
bump

(its been 5 days so hopefully now that lucid is released more people can benefit from this issue)

---

### Post by srs5694 on 2010-05-01
An article I wrote on drives with 4096-byte sectors is [now up on IBM developerWorks.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) Although the issues aren't identical, they're similar, at least in terms of how to create optimized partitions. The biggest practical difference is that the SSD block sizes are bigger -- they're more like the RAID arrays mentioned in the sidebar. The performance measures in the article should *not* be taken as representative of SSD performance issues, so ignore those if you've got an SSD drive. The section entitled "Aligning Partitions" is relevant, though.

---

### Post by libssd on 2010-06-17
Attached is an early draft of a how-to I'm working on. My goal isn't to explain the theory (see: [http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux](http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux)), but rather to document a series of steps that will be straightforward enough for anybody to follow.

---

### Post by nhasian on 2010-06-18
thanks its looking good!  i'm hoping that Mavrick will make it easier for people using SSDs...

---

### Post by cmcginty on 2011-06-24
What? :confused::confused:

Don't run shred on an SSD. Any data you write will have to be erase later and tank the performance.

Second, I also don't think you want to put a swap on an SSD. Memory is pretty cheap these days. I don't run swap on any of my systems.

---

