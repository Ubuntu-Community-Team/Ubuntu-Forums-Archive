---
title: "seperate root partition is filling up???"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by mustard greens on 2010-06-03
I have a 250G HD partitioned with two separate 15G root partitions and a 197G home partition. recently I noticed that my main root partition is filling up to capacity.  

when I run the disk usage analyzer it shows the root size as 87G and seems to lump in the separate home partition with this info, home being 83G that would leave 5G worth of actual root info which makes perfect sense.

but I am getting warning messages that there are only a few MBs left on this root partition, and sure enough if I look in Gparted that partition is showing full capacity.

I am at a complete loss.

one last clue.  when I boot into the second root partition (also 10.04 for now) it finds my separate home partition, but not all my applications are there.  could some of my apps be installed on the root partition?  again, the disk usage analyzer says no.

---

### Post by mikewhatever on 2010-06-03
To verify the situation, please post the outputs of the following:

sudo fdisk -l
df -h

---

### Post by mustard greens on 2010-06-03
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d3fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15726611   83  Linux
/dev/sda2           29647       30395     6007809    5  Extended
/dev/sda3            1959        3916    15727635   83  Linux
/dev/sda4            3917       29646   206676225   83  Linux
/dev/sda5           29647       30395     6007808   82  Linux swap / Solaris

Partition table entries are not in disk order




aaron@aaron-desktop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     15G   14G   70M 100% /
none      devtmpfs    998M  276K  998M   1% /dev
none         tmpfs   1002M  184K 1002M   1% /dev/shm
none         tmpfs   1002M   88K 1002M   1% /var/run
none         tmpfs   1002M     0 1002M   0% /var/lock
none         tmpfs   1002M     0 1002M   0% /lib/init/rw
/dev/sda4     ext4    195G   84G  101G  46% /home


thanks for the quick reply!

---

### Post by gmargo on 2010-06-03
Are you running databases or websites on that root partition?  I can't believe it's so full.  (My recent Lucid desktop install takes less than 3G on root.)

Here's two things you can do immediately: a) "apt-get clean", b) cd /tmp and look for large downloaded files that you don't need.

Then try to find where all the space went.  Start in /var and use "du -s * | sort -n".

---

### Post by philinux on 2010-06-03
> **mustard greens said:**
> I have a 250G HD partitioned with two separate 15G root partitions and a 197G home partition. recently I noticed that my main root partition is filling up to capacity.

Try this.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by mustard greens on 2010-06-03
ok,

I found out that Disk usage analyzer was giving incomplete info as I did not open it with gksudo through the terminal.

once opened this way I found a group of backup files being made in my media folder, not sure why.  

I did set the simple backup to send info to an external hard drive, and also to abort backup if destination does not exist, but I found those settings reset???

anyway, I will mark this thread as solved and start a new thread or bug report if simple backup continues to reset to default settings.

thanks again for the prompt responses.

---

