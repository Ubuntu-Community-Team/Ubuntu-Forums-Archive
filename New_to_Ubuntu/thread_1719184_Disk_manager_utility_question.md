---
title: "Disk manager utility question"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2011-04-01
Having grub problems, currently running on live CD.  Question re  disk manager utility:

When looking at the graphic for the entire drive, the 3 blocks representing the partitions for Maverick and its swap as well as 60Gb of unallocated space are all underneath one long block (think think shortish legos next to each other with one long lego on top from edge to edge).

My problems started when I was deleting my edubuntu partition and combining it with unallocated space, whence I lost grub and now can't get into anything.  

I'm no rocket surgeon, but does this block on block bit mean that grub is still there but is not seeing the Maverick partition because I somehow screwed up the partition change?

I am willing to wipe the whole drive and start over, done with windows anyway, but there is at least ONE file in the Maverick system that I MUST have.  Preferably all my docs and music, but if I can at least get my gradebook out of there I'll recreate the rest.

I'm no rocket surgeon :-) but I'm thinking that nothing changed this morning except the partitioning and this "top block" may be the problem.  I'm reluctant to delete it though as I have no idea if it will take the smaller blocks underneath it with when I delete.

harrumph! Richard

---

### Post by Rubi1200 on 2011-04-01
On the LiveCD, go to Applications > Accessories > Terminal and post the output of the following command:

sudo parted -l
(lowercase L not 1)

You can copy/paste from the terminal and then paste the results in a new post here. Once pasted, highlight the text and click on # from the toolbar to wrap with code tags.

Thanks.

---

### Post by grahammechanical on 2011-04-01
Do you see written in the large block that looks like one large lego brick on top of three other lego (copyright) bricks the words Extended and then the size in GB?

What you are seeing is information that those three partitions are inside an extended partition. This is correct. My system looks the same. Why?

Do not take my word for it. Someone will surly correct me. I think that some files systems can only handle primary four partitions. To get around this the idea of the Extended partition was developed so that we can have four primary partitions, including the Extended partition and then additional partitions inside the Extended partition.

So, this Extended partition is not the cause of the problem. My guess is that Grub has been deleted somehow.

Regards.

P.S. If you delete the Extended partition you will indeed delete the three other partitions. No doubt about it.

---

### Post by srs5694 on 2011-04-01
> **grahammechanical said:**
> Do not take my word for it. Someone will surly correct me. I think that some files systems can only handle primary four partitions. To get around this the idea of the Extended partition was developed so that we can have four primary partitions, including the Extended partition and then additional partitions inside the Extended partition.

I'll try not to be too surly. ;-) The primary vs. logical thing has nothing to do with filesystems; it has to do with the fact that the Master Boot Record (MBR) partitioning system was initially designed to support a maximum of four partitions -- what we now call "primary" partitions. To support more than four partitions per disk, extended and logical partitions were added to the scheme. An extended partition is just a particular type of primary partition that holds other (logical) partitions. Thus, a disk can have either four primary partitions or three primary partitions, one extended partition, and an arbitrary number of logical partitions. Any of the primary or logical partitions may contain any filesystem. There are, however, OS-specific limitations, mostly relating to boot partitions. Windows and FreeBSD, for instance, must boot from primary partitions. (Linux isn't so limited; you can boot Linux from either a primary or a logical partition.)

FWIW, the (relatively) new GUID Partition Table (GPT) system, which is necessary on disks with more than 2^32 sectors (2 TiB, given 512-byte sectors), does away with the primary/extended/logical distinction. With GPT, a disk can have up to 128 partitions by default (although this value can be raised if you like, if the partitioning software supports it). I recommend using GPT on Linux-only systems, even on sub-2TiB disks, in part because removing the primary/extended/logical distinction also eliminates a lot of awkwardness in managing partitions. GPT isn't a good choice if you've got to boot Windows on a BIOS-based computer, though, since Microsoft, in its infinite wisdom, has seen fit not to support the BIOS/GPT combination for booting its OS.

> So, this Extended partition is not the cause of the problem. My guess is that Grub has been deleted somehow.You're correct that an extended partition is not in itself a symptom of a problem. Robing should run the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") from the Ubuntu installation disc in "try it now" mode, then post the RESULTS.TXT file that it produces, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. This script will produce diagnostic information that will help the boot loader experts on this forum figure out what's wrong.

---

### Post by Robing Goodfellow on 2011-04-01
I figured the extended partition bit out on my own, or rather thought I had and indeed came up with surmise that has pretty well been confirmed here.  

The one difference of note was that the extended partition had extended itself over unallocated space, though whether this made a difference or not, I don't know.  

I ended up have the Natty live CD install itself as an upgrade to the Maverick install I've been on for several months now.  That did the trick, the Natty install repaired the Grub or whatever problem there was and returned my files to me, of which I've now made 2 backups.  I had thought that was pretty much that, however...

I'm sure many will like it, but I am not at all comfortable with Natty.  I don't like the Unity interface, and there are several minor things, for example, the "minimize, close resize" buttons having moved to the left.  Still quite a few bugs in that one, though as it is a beta, that in itself is not a complaint.  It's just the general feel of Natty that is somehow reduced, or dumbed down if you will.  I'm wiping the entire drive (bye bye windows at last) and putting Maverick back on.  I had thought I would like Unity better, but I don't.  I find that, as much as I am struggling to learn it as well as everything else that is new and wonderful in this world of ubuntu, I much prefer Gnome.  And worst of all, that damned side panel just jumps out aat me every time I move my cursor.  ugh!

regards, Richard

---

### Post by srs5694 on 2011-04-02
> **Robing Goodfellow said:**
> The one difference of note was that the extended partition had extended itself over unallocated space, though whether this made a difference or not, I don't know.

Whether unallocated space appears inside or outside an extended partition makes little difference. You can easily resize the extended partition using tools like GParted if you need to create a new partition of a particular type (primary vs. logical).

---

