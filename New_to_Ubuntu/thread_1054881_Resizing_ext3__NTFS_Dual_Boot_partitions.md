---
title: "Resizing ext3 / NTFS Dual Boot partitions"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by sirsmegalot105 on 2009-01-30
Hi,

I partitioned my 120GB HDD as follows:

/dev/sda1 (NTFS) 81.5GB - Windows XP

The rest was unpartitioned space and so when I installed Ubuntu 8.10 I broke the rest up as 2 :

extended 30GB (/dev/sda2)
       /dev/sda5 (ext3) 27.94GB - /
       /dev/sda6 (linux-swap) 2.06GB

The problem I have now is, since installing Ubuntu last week on my laptop dual boot, I am ready to use it as my main operating system. I would like to re-distribute the HDD space so that Ubuntu gets the majority of space, so taking space from NTFS and assigning to / in ext3 would be the answer I believe.

I would prefer to keep a small Win XP partition as theres some things I still need it for. After searching your forum and the Internet I've discovered it seems very difficult to be able to resize the ntfs and ext3 paritions and keep the data already on them. Are there any other suggestions on this?

I only just re-installed Windows XP from a backup image so I don't mind losing the NTFS partition, as long as I can restore it at a smaller size of prob 30GB and giving the rest to /

Alternatively...... is there a way I can backup the 2 linux partitions (or just the / since I wouldn't think the swap needs backing up?) to a USB drive and then re-partition all drives and restore it?

Thanks for any help or suggestions :D

---

### Post by yeats on 2009-01-30
The easiest way to do this is with gParted ([http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")), which works from a live CD like the Ubuntu installation CD (which actually includes gParted, but I found the gParted CD to be faster and more straightforward).  gParted allows you to set the size of each partition in a graphical interface.  Give it a shot.

---

### Post by sirsmegalot105 on 2009-01-30
> **chrissharp123 said:**
> The easiest way to do this is with gParted ([http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")), which works from a live CD like the Ubuntu installation CD (which actually includes gParted, but I found the gParted CD to be faster and more straightforward).  gParted allows you to set the size of each partition in a graphical interface.  Give it a shot.

Thanks, though will this let me keep the existing data on the partitions and redistribute space from the ntfs to the ext3?

---

### Post by bruce89 on 2009-01-30
> **sirsmegalot105 said:**
> Thanks, though will this let me keep the existing data on the partitions and redistribute space from the ntfs to the ext3?

You can move partitions nowadays with GParted (what you want to do is a move and a resize), but I'd make a backup of useful stuff on both partitions just to be on the safe side.

I'd recommend that you create a seperate /home partition.

---

### Post by mikechant on 2009-01-30
When running from the live CD Ubuntu will still normally use the swap partition on the hard drive, so before you can shuffle the partitions about you'll need to right click on the swap partition line in gparted and select 'swapoff'.

Also, once you've shrunk your windows partition you'll have to expand your extended partition at its start before you can do anything with the logical partitions inside it.
I don't know if this applies with XP but when I shrank my Vista partition with gparted, Vista went into some mega disk-checking mode on boot and took several *hours* to come up - so if this happens *don't interrupt the boot* even if it looks 'dead'.
I'd try making this one change (shrink windows) and then try the windows boot before doing anything further with gparted.

Partition operations can take a long time and it's essential the operations are not interrupted.

Depending how you shuffle the partitions, their UUIDs (used to identify them to Ubuntu) may change. This is another topic though - but if Ubuntu won't boot after your changes, don't worry too much, it's probably easy to fix and has been covered here before.

---

### Post by sirsmegalot105 on 2009-02-03
Thanks for the help, got them resized/moved with no problems - and Windows XP started up just at its normal speed by the way. 

Please close / mark as solved, thought I could do this myself but it just affected my first post. :popcorn:

---

