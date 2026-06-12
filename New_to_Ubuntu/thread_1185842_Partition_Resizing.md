---
title: "Partition Resizing"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by eric50 on 2009-06-12
I just tried to use GParted to resize partitions.  I followed the directions on how to select a partion and then unmount it.  Then I was supposed to be able to resize the partition (ntfs format), but that option is not enabled for some reason.  Now I find that all of my ntfs partitions are unmounted, even after restart.  I just bought the computer with Vista preinstalled, and have installed Ubuntu 9.04 as my preferred operating system (no previous experience with it, though).  I have found that I only have about 200 MB free for data storage, and most of the storage capacity (out of 160 GB) is in what is called SW_Preload.  As most of that is unused, I thought I could make it smaller and make the home partition larger for more data storage.  Can someone please help?

---

### Post by NESFreak on 2009-06-12
try to resize them from the livecd instead.

---

### Post by eric50 on 2009-06-15
OK, I am working off the Live CD now.  I can't seem to copy a screenshot of the partition table, but here is the data.
Partition     File System          Label               Size          Used          Unused           Flag
unallocated                                                 1.00 MiB
/dev/sda1           ntfs             SERVICEV003   1.46 GiB     789.57 MiB  710.43 MiB     boot
unallocated                                                  5.09 MiB
/dev/sda2           ntfs             SW_Preload      29.50 GiB    27.73 GiB    1.77 GiB
unallocated                                                  105.83 GiB
/dev/sda4          extended                              2.49 GiB
   /dev/sda5       ext3                                     2.32 GiB     2.18 GiB      146.33 MiB
   /dev/sda6       linux-swap                            169.77 MiB
unallocated                                                   4.83 MiB
/dev/sda3          ntfs              Lenovo              9.77 GiB     5.67 GiB     4.09 GiB

The only thing that I have done so far is to resize the /dev/sda2 partition and move most of it into the following unallocated space.  I need to be able to access that unallocated space for data storage.  The system tries to store data in the /dev/sda5 partition, where there is almost no space.  Any additional help would be appreciated, preferably as step-by-step instructions, as I am a complete newbie. 
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by Mark Phelps on 2009-06-17
The Ubuntu liveCDs don't always have the most current version of GParted on them.  You would do better to download and burn a GParted LiveCD (which you can get from the distrowatch.com website) and do your partition work booted from that.

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Hi,

Being the devout coward that I am .... Can I reccomend that you have a look & act upon this article...

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu)

followed by this one ...

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

At least, with the back-up of Ubuntu - you get to keep that. If you want to back up the windoze partions(s) the backup system can do that also.

In *nix  - EVERYTHING is a file, a data file, a special file (aka directory, device etc) - As such EVERYTHING can be backed up !! - If you read the article on backup and restore, it should be apparent why you wouldn't backup /proc, /lost+found etc.

Many years ago (like 20) I managed to delete the entire directory, from root, of the entire PAY-ROLL system at the company I worked for ..... All several thousand employees, from the guy who swept up to the chairman. I was mightily miffed, as my payroll was in there somewhere !!!  As I was the one who had written the backup script, once I had calmed down, I just restored it.

So, back everything up - at least then you can 'play' to your hearts content, safe in the knowledge that you have everything !!

Regards,

Phill
[/FONT][/SIZE]

---

