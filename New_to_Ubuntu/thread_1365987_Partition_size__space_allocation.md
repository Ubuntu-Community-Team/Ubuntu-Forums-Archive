---
title: "Partition size / space allocation"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by ericstrom on 2009-12-27
I am dual booting Windows XP and Ubuntu Karmic. When I originally set things up, I think I allocated too much space to XP and not not enough to Ubuntu since I'm now getting messages in when running Karmic that I'm running low on disk space. Is there an easy way to reallocate the space to take some from XP and move it over to Karmic ? ****

---

### Post by diablo75 on 2009-12-27
I would recommend download the Gparted Live CD iso, burning it to a disc, and booting from that.  You can then resize and move partitions around to your liking and it will take care of the rest (could take some time but it does a good job).

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

As of now, there is an alert about a bug with resizing NTFS partitions with the latest version of Gparted and the link above provides you with a download for an older version of Gparted with is known to be much more stable.  Use that for now and you'll be good to go.

---

### Post by raymondh on 2009-12-27
> **ericstrom said:**
> I am dual booting Windows XP and Ubuntu Karmic. When I originally set things up, I think I allocated too much space to XP and not not enough to Ubuntu since I'm now getting messages in when running Karmic that I'm running low on disk space. Is there an easy way to reallocate the space to take some from XP and move it over to Karmic ? ****

Most often, I would recommend you using windows' disk management utility to shrink a windows-based partition.  Unfortunately, XP does not have the ability to shrink.  For this, you need a 3rd party disk manager like gparted from the liveCD and from live session.

If you need a mini-guide, kindly post a screenshot of gparted to help visualize your HD.  If you want (easier to do but harder to visualize), access a terminal and post back results of 

```
sudo fdisk -l
```

small L.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Regards,

---

### Post by ST3ALTHPSYCH0 on 2009-12-27
When resizing a windows partition make absolutely sure that "round to cylinders" is unchecked. Linux partitions like to be rounded to cylinders, Windows won't boot if it is.

---

### Post by ericstrom on 2009-12-27
Raymouth, what does this all mean ?

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafb9cb99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3292    26442958+   7  HPFS/NTFS
/dev/sda2            3293        4865    12635122+   5  Extended
/dev/sda5            3293        4793    12056751   83  Linux
/dev/sda6            4794        4865      578308+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde03de03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4867    39094146    c  W95 FAT32 (LBA)

---

### Post by Captain_tux on 2009-12-27
Exactly how much (or little) did you allocate for Ubuntu? Type **df -h** in a command prompt and let us know.

I'm thinking it's just the root partition short on space. If so, you can just clear the cache and you should be good.

---

### Post by oldfred on 2009-12-28
Unchecking the round to cylinders is vital for Vista and Win7 but not required for XP. It is why we normally recommend using Vista or Win7's own partitioner to resize their partitions.

You also should defrag windows XP twice after housecleaning and deleting any old stuff. Windows needs about 20% extra space to be able to work and  defrag in the future.

You have linux in the sda2 extended partition so after you shrink the NTFS partition you have to move the extended left where the NTFS space is made and then move the sda5 ubuntu partition left. The extended partition is a container for all the logical partitions.

---

### Post by ericstrom on 2009-12-28
Captain-Tux here's what I got when I typed your suggested command into terminal :

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              12G   11G  182M  99% /
udev                  1.5G  328K  1.5G   1% /dev
none                  1.5G  360K  1.5G   1% /dev/shm
none                  1.5G  192K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw

What does that mean ?

---

### Post by diablo75 on 2009-12-28
> **ericstrom said:**
> Captain-Tux here's what I got when I typed your suggested command into terminal :

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              12G   11G  182M  99% /
udev                  1.5G  328K  1.5G   1% /dev
none                  1.5G  360K  1.5G   1% /dev/shm
none                  1.5G  192K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw

What does that mean ?

Let's take the first two lines:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              12G   11G  182M  99% /

```

The Filesystem is the name of the drive volume.  The Size is the volume size, and the Used amount is how much of that volume has been consumed, followed by an available amount of free space, the percentage of usage and the mount point.

/ means "root", or the root of your entire file system.  It looks like you told Ubuntu to allocate 12 GB of space for itself, and you have used up over 11 GB of space, and you only have 182 MB of free space left.  The system will have a very difficult time functioning with such low disc space left.

There are other pathways you listed above, such as /dev, /var, /lib

I would ignore these as they are actually just folders contained within /

The amounts listed (1.5 GB, 1% used) is misleading because we're not talking about filesystem volumes but just folders.  It is technically possible to create a seperate partition for a specific folder to be housed in (e.g., when you install the system, you can setup a partition for your root, a partition for your home folder, and so on if you wanted to... doing this makes restoring from a crash easier) but I know that's not what you actually did because the filesystem listed for each folder says "none"... because they're just folders.

---

### Post by ST3ALTHPSYCH0 on 2009-12-28
> **oldfred said:**
> Unchecking the round to cylinders is vital for Vista and Win7 but not required for XP. It is why we normally recommend using Vista or Win7's own partitioner to resize their partitions.

You also should defrag windows XP twice after housecleaning and deleting any old stuff. Windows needs about 20% extra space to be able to work and  defrag in the future.

You have linux in the sda2 extended partition so after you shrink the NTFS partition you have to move the extended left where the NTFS space is made and then move the sda5 ubuntu partition left. The extended partition is a container for all the logical partitions.

+1 for defragging first, I totally forgot about that. I also forgot that XP didn't come with it's own partitioner.

---

### Post by Bartender on 2009-12-28
Resizing a Windows partition with data is not risk-free.  As mentioned, defrag a few times, and take a look at the results to see if Windows has vacated the right-hand part of the NTFS partition or if it's still got data way out there.

If you google it, there are directions for turning off the page file and several other tricks in order to get the best results from defrag.

If you can get a decent defrag from XP's defrag tool, there are several ways to go.  
I'd probly use the stand-alone GParted LiveCD to resize the XP partition.

But you could also boot from the Ubuntu install CD and reinstall Ubuntu, this time pushing that slider over some to give yourself more room.

Or you could use a 3rd party partitioning tool to shove Windows aside.

None of these methods are entirely risk-free because you're manipulating a partition with data.  It would be good to have the tools to rebuild Windows from scratch, or restore it from an image, or whatever.

---

### Post by raymondh on 2009-12-28
> **ericstrom said:**
> Raymouth, what does this all mean ?

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafb9cb99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3292    26442958+   7  HPFS/NTFS
/dev/sda2            3293        4865    12635122+   5  Extended
/dev/sda5            3293        4793    12056751   83  Linux
/dev/sda6            4794        4865      578308+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde03de03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4867    39094146    c  W95 FAT32 (LBA)

Have a image back-up of your windows install IF YOU DO NOT HAVE A XP INSTALL DISK.

- Back-up your files and test that they are recoverable
- Defrag windows
- Boot into the ubuntu liveCD and go live session (try ubuntu...) and access gparted (system > admin > partition editor)
* The live session ought to unmount the partitions.  Double check by right clk. on each partition and if given the option to unmount, do so.  For swap, select SWAPOFF.
- Click to highlight sda1.  Select RESIZE.  With your mouse, grab the right border and drag left ... thus creating a unallocated space which you will give to Ubuntu later.
- Review and Apply
- Click to highlight sda2.  That is the EXTENDED partition.  Grab the left border and drag left to occupy the unallocated space.  You will note that the unallocated is now inside the extended and in front of sda5).
- Review and apply
- Click to highlight sda5.  Grab the left border and drag left ... to occupy the unallocated..
- Review and apply.
- You're Done.

Some notes,

- your partition boundary will now change but, since GRUB2 now uses UUID, I don't forsee and problems 
- If I remember (cannot be accurate in this), go ahead and uncheck the round-to-cylinder box (if presented).  XP, I think, starts on 63 and its' Vista/newer that starts on 2048.

Review and post back any confusions/clarifications.

Regards,

---

### Post by oldfred on 2009-12-28
What have you done to fill up your root partition. My portable which I have not installed very much has used 3.2GB and my desktop with lots of stuff is just over 5GB. 

I think you need to do some housecleaning and check for a runaway error log or something that is filling your system.

HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb
sudo apt-get autoclean

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

