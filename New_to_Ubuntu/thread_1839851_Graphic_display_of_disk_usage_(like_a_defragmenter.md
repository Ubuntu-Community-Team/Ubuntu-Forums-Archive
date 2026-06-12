---
title: "Graphic display of disk usage? (like a defragmenter)"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by flemur13013 on 2011-09-06
Howdy - 

Is there any linux software that'll show a graphical display of disk usage for ext3/4 filesystems?

Like this:  [http://gallery.techarena.in/data/519/UltimateDefrag_Pics.jpg](http://gallery.techarena.in/data/519/UltimateDefrag_Pics.jpg)
(Display from UltimateDefrag, or from similar windows defrag tools - the fact that the UD display is round rather than rectangular isn't important)

Plus points would include highlighting a given file by name and returning file name(s) from a click on the display.

Thanks!

---

### Post by aeiah on 2011-09-06
yea its called disk usage analyzer (or baobab). its probably in your admin menu if you're on gnome or perhaps unity

---

### Post by flemur13013 on 2011-09-06
No, NOT like baobab, which only shows file sizes.  

A defragmenter type of display shows where files are located on the disk, and also shows where the fragmented parts, if any, are located.

---

### Post by haqking on 2011-09-06
> **flemur13013 said:**
> No, NOT like baobab, which only shows file sizes.  

A defragmenter type of display shows where files are located on the disk, and also shows where the fragmented parts, if any, are located.

Ext4 doesnt really suffer from fragmentation as much as other Filesystems.

If you want to know where files are on disk

sudo apt-get install tree

then:

tree > filename.txt

Which will show a tree list of files and put it in the file for you to see.

you can also use system monitor to see filesystems and space etc.

---

### Post by Wim Sturkenboom on 2011-09-06
tree does not show where it's physically on the disk ;) And I think that that is what flemur13013 is looking for.

---

### Post by beew on 2011-09-06
In Linux you don't need to defragment as ext4 hardly fragments

---

### Post by haqking on 2011-09-06
> **Wim Sturkenboom said:**
> tree does not show where it's physically on the disk ;) And I think that that is what flemur13013 is looking for.


ha see your point, i guess he means the sector location.

fair one ;-)

---

### Post by Wim Sturkenboom on 2011-09-07
> **beew said:**
> In Linux you don't need to defragment as ext4 hardly fragments

He/she does not ask for a defrag tool. Read post 1 and 3 !

---

### Post by flemur13013 on 2011-09-07
> **haqking said:**
> ha see your point, i guess he means the sector location.

Yes, but not necessarily literal sectors - just the disk storage divided up into a grid.  Grid elements could be sectors or just some other amount of storage (10M/graphical block, whatever).

It's mostly just curiosity*, and I could swear I had some program** at some point  that showed file (physical) locations on ext4 partitions because I remember thinking that the ext4 positioning made a lot more sense than how files ended up with NTFS (= auto-magically fragmented immediately with parts all over the place for no apparent reason).  

*"filefrag" shows 3 to 10 fragments for each of my fairly large AVI files on an ext4 partition: they're all fragmented, but why? I think the partition is big enough and sparse enough so that no fragmentation should ever occur. Are the parts next to each other, or what?  That's the curiosity part.

**It may have been a windows program, or perhaps something on a Bart-PE CD, that I was running under dual-boot so it had access to linux partitions.  

And thanks_, haqking, _for "tree" - that'll come in handy !

---

