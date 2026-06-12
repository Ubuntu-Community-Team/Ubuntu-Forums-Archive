---
title: "Ubuntu Installer: My partitions in the HDD don't appear at all!"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Zero Ziat on 2011-02-28
Oh boy, when I went to install Ubuntu 10.10 (the latest one from the website) the installer (and gparted) show my 250gb drive as 'unallocated' space (all gray)! I have a Windows XP OS installed too, that's the whole gist of it. I intend to keep it. My HDD is partitioned like this:

2 partitions for windows (one holds windows, stuff and some minimal file storage, the other one is pure file storage) and the rest would be for Ubuntu.

I had Ubuntu 6.something installed before but I'm gonna have to wipe it cause it's pretty darn old and I installed Windows afterwards, and it overwrote the MBR and all that fancy stuff it does and now Ubuntu 6.something is pretty much concealed and I really haven't touched it.

Err, anyways, thanks for your attention, what can I do?

Oh, also I remember reading that selecting 'Install alongside other OSs' deletes everything or maybe it used to (10.04?), is it safe to use that option after I fix that problem?

Here's the article I read, I may have misinterpreted it: [http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

Okay, now I booted into GParted to see if I could wipe my old Ubuntu partition... Gparted can't see anything either. This must be probably related to windows tendency to overwrite the MBR or something? How do I make things seeable for every OS properly without screwing my windows?

---

### Post by srs5694 on 2011-02-28
Several underlying problems can cause the symptoms you report. These include:


[list]
[*]A partition (typically the extended partition) that extends beyond the end of the disk. [This Web page of mine](http://www.rodsbooks.com/missing-parts/index.html) describes this problem in more detail, as well as several possible solutions.
[*]Partitions that overlap or are otherwise invalid. The solution is conceptually similar to the one for the preceding problem, but details differ and depend on the exact nature of the problem.
[*]Leftover GUID Partition Table (GPT) data on a Master Boot Record (MBR) disk. [This Web page of mine](http://www.rodsbooks.com/gdisk/wipegpt.html) describes this problem in more detail and how to solve it.
[*]Leftover RAID data on a disk that's no longer part of a RAID array. I'm less expert at solving this, but it can be done by wiping the RAID data. A quick and incomplete solution may be to uninstall the dmraid package.
[/list]


If those descriptions, and associated links or whatever you find in a Web search, aren't enough to enable you to solve the problem, please boot the Ubuntu installer into the "try before installing" mode (or whatever it's called), open a Terminal window, and type the following command:

```

sudo fdisk -lu

```

Note that in "-lu", that's a lowercase letter L, not a digit 1. Post the output here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by Zero Ziat on 2011-02-28
Hmm... I read it all and I sorta understand it but I've no idea how to proceed, even after referring to the 'Fixing this problem' section.

---

### Post by srs5694 on 2011-02-28
> **Zero Ziat said:**
> Hmm... I read it all and I sorta understand it but I've no idea how to proceed, even after referring to the 'Fixing this problem' section.

Then please read the part of my original post that follows the bulleted list.

---

### Post by Zero Ziat on 2011-02-28
Made my mind, I'll modify the extended partition length thing, saving those pages to a usb file and will report back soon with results if I don't blow it. Of course I'll do the backup thing so I don't.

Alright... I'm not sure but I think I found something weird so I didn't proceed as expected...

```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26962695

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   161999459    80999698+   7  HPFS/NTFS
/dev/sda2       161999460   488392064   163196302+   f  W95 Ext'd (LBA)
/dev/sda3       168907473   488392064   159742296    7  HPFS/NTFS
/dev/sda5       161999586   168907409     3453912   82  Linux swap / Solaris

Disk /dev/sdb: 997 MB, 997195776 bytes
64 heads, 32 sectors/track, 951 cylinders, total 1947648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         369     1945599      972615+   6  FAT16

Disk /dev/sdc: 16 MB, 16777216 bytes
1 heads, 32 sectors/track, 1024 cylinders, total 32768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
```

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=161999397, Id= 7, bootable
/dev/sda2 : start=161999460, size=326392605, Id= f
/dev/sda3 : start=168907473, size=319484592, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=161999586, size=  6907824, Id=82

```

---

### Post by srs5694 on 2011-03-01
Something (possibly the Windows installer; it's known to do this) juggled your partitions around so that a primary partition overlapped with your extended partition. There are several possible fixes, and I'll present one shortly. First, though, an observation: You currently have two NTFS partitions and a Linux swap partition. These seem to occupy the entire hard disk (minus a few unallocated sectors). You mentioned a previous Ubuntu installation, but there's no trace of an actual Linux filesystem (boot partition). If it was on another disk that you've since disconnected, or if you deleted it and resized one or both of your Windows partitions to reclaim its space, then there's nothing amiss. If, however, that previous Linux installation should still be present, then something's odd, and you may want to perform some more advanced tests before you mess with anything. Post back if this is the case for more advice.

I'll assume that the lack of a Linux filesystem partition isn't a problem. Here's one way to fix the obvious problem with the overlapping partitions:

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=161999397, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=168907473, size=319484592, Id= 7
/dev/sda4 : start=161999586, size=  6907824, Id=82

```

Cut-and-paste that into a file (say, parts.txt), then use the following command:

```

sudo sfdisk --force /dev/sda < parts.txt

```

The result should be a legal partition table. When you reboot into the Ubuntu installer, it should see your disk. You'll have to resize one or both of your Windows partitions to install Ubuntu. Depending on where you want to take the space from, I recommend you do one or more of the following things:


[list]
[*]Back up your important data. Resizing partitions (as you must do to install Ubuntu, unless you buy another hard disk) is inherently risky. If something goes wrong, like a power outage during the resize operation, having a backup can save your data.
[*]You can shrink /dev/sda1 (your Windows C: partition) by changing its end point. This is most safely done from Windows, using the Windows partition management tools; however, not all versions of these tools support partition resizing. If you must do it from Linux, use GParted, and be sure the "align to cylinders" option is selected. This should minimize the risk of problems.
[*]If you want to shrink /dev/sda1 but *not* /dev/sda3, you should first shrink /dev/sda1 and then create an extended partition in the resulting free space. You can then create your Linux partitions as logical partitions inside the extended partition, as described below.
[*]If you want to shrink /dev/sda3 (the Windows data partition) but *not* /dev/sda1, you can shrink its end point using either Windows or Linux tools. You can then create an extended partition at the end of the disk and populate it with logical partitions, as described shortly.
[*]If you want to take some space from each of the Windows partitions, I recommend you delete /dev/sda4 (the Linux swap partition) and move/resize /dev/sda3 so that it's adjacent to /dev/sda1. You'll then have a single large unallocated space at the end of the disk. Create an extended partition to fill that space and create your Linux partitions within it, as described shortly. Note that the move/resize operation will be quite lengthy and more risky than shrinking a partition just by moving its end point; however, the result will in many ways be superior to shrinking just one of the NTFS partitions, since each OS's partitions will be entirely adjacent to each other, which will improve disk speed.
[*]With an extended partition created for Linux, you can populate it with logical partitions. Create a new swap partition of 1-2x your RAM size *if* you deleted the existing one, a 5-20GB root (/) partition, and optionally a /home partion. Create these all as logical partitions inside the extended partition. Linux will boot fine from a logical partition.
[/list]


I hope this helps.

---

### Post by Zero Ziat on 2011-03-01
Okay, here's the update, I talked on IRC (This was yesterday night) with some helpful people, I explained the situation and they told me it'd be easier if I jumped into terminal and deleted the partitions I didn't want, which were the old Ubuntu ones, and left me with 3Gbs, I am sort of confused by this, considering my hdd consisted of 250gbs and I was left with 238gbs or so and I can't seem to get those back from anywhere...

Anyways, Gparted worked again after deleting the ubuntu partitions that I was gonna remove, I got into gparted, moved around the stuff I needed and made like 10.30gbs for ubuntu, which I'll install in a while.

---

### Post by srs5694 on 2011-03-01
Yes, I missed the easy solution! ;)

BTW, you had *one* Linux partition (/dev/sda5, the Linux swap space). The solution you describe would only work if you deleted that and /dev/sda2, which is an extended partition that's not associated with any particular OS (although in your case it only held a Linux swap partition).

As to the 250GB vs. 238GB thing, your disk has 488,397,168 sectors, which (at 512 bytes per sector) works out to 250,059,350,016 bytes -- that is, 250GB (250 x 10^9 bytes) or 233GiB (233 x 2^30 bytes). The difference between gigabytes (GB) and gibibytes (GiB), and similar differences at other unit levels, such as TB vs. TiB, has been a confusing one for decades. Read [this page](http://physics.nist.gov/cuu/Units/binary.html) for more on this topic. Many people, and some utilities and manufacturers, persist in applying the power-of-10 labels to power-of-2 units.

---

