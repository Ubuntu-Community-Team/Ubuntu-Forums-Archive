---
title: "Partitioning for dual boot with bad-sector"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by grj23 on 2009-11-01
Hi

I'm gradually upgrading my computers to Ubuntu.  I would have done this one a while back, but I came up on a little problem, and was hoping for some advice.

This laptop has a large ntfs partition, but it's got a bad sector.  My understanding is I have to use ntfsresize with the --bad-sector option.  However, I'm just a little bit nervous to fiddle, so thought I'd try to get some idea of the commands from someone who knows what they're doing.

My current harddrive looks like this:
/dev/sda1        fat16      DellUtility      117.63MiB
/dev/sda2        ntfs                        226.66GiB (this is the one with the bad-sector - it seems to be stable, and I've run the chkdsk /f /r)
unallocated                                    7.84MiB
/dev/sda3        extended                      2.5GiB
    /dev/sda5    fat32      MEDIADIRECT        2.5GiB
/dev/sda4        fat32      DellRestore        3.6GiB

This set up seems to me a little bit wasteful of partitions, but I'm not sure how to proceed.  My initial thought was to try to carve off 20-30GiB for the Ubuntu partition from sda2 and install Ubuntu there.  sda2 has both my windows XP installation and my files (I know, I know).  But then I see I'm suppose to have a swop partition and something else and it seems like I can't have too many partitions, so it's all just a bit awkward.

I'm leaving the question a bit open because I'd like higher level advice about how to reorganise things.  I have an external harddrive, so could do an ntfsclone, which I gather is more than the simple back up of my documents which I've done so far!  What I want is a dual boot, preferrably without having to reinstall the windows.

Some thoughts:
 - can I make a DVD or something to replace the DellRestore and free up some partitions?  And is it worth doing?
 - What are the DellUtility and MediaDirect partitions, and do I need them?
 - how would you reorganise and shuffle things around?

Thanks for your help!

---

### Post by grj23 on 2009-11-04
Bump!  Can someone please share their expertise with me...;)

---

### Post by grj23 on 2009-11-04
Hi

I found the solution here: [ntfs howto]("http://ubuntuforums.org/showthread.php?t=1244058")

I had to use sudo in front of all the commands, but it worked a treat.  I booted up from 9.10 live CD, freed up the space and then installed.

:D

---

### Post by egalvan on 2009-11-04
> **grj23 said:**
> Hi

fat16  DellUtility      117.63MiB
fat32      MEDIADIRECT        2.5GiB
fat32      DellRestore        3.6GiB

Some thoughts:
 - can I make a DVD or something to replace the DellRestore and free up some partitions?  And is it worth doing?
 - What are the DellUtility and MediaDirect partitions, and do I need them?


DellUtility is a partition that holds software that is used to test the hardware.
You can download this software as a CD image, and save the hard drive space.

MediaDirect is the partition used to play music and movies without powering up the whole computer.
If you remove this, then this will not function in this manner.

DellRestore is the partition which holds a factory image of your computer... this will allow you to restore your amchine to a ¨as-new¨ state.
On some Dells, there is a program that allows you to create a set of CD or DVD disks.
Dell tech support should be able to helpo with this.
Also, depending on the machine, you can buy the recovery disks from Dell, and this will also allow you to eliminate the restore partition. I have done this for several machines, and the cost is reasonable.


Are these partitions/software useful? Only you can determine that. It depends on your needs.

---

