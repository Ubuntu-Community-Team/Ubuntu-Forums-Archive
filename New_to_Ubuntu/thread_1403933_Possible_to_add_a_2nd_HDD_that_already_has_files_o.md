---
title: "Possible to add a 2nd HDD that already has files on it?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by heus33 on 2010-02-10
I'm running Karmic on a desktop.  Ubuntu is installed on a 15GB drive.  I have a 2nd HDD that I want to install - its 120GB and is currently filled with about 20GB of music and pictures.  Im not sure how the 2nd HDD is formatted, its from my previous XP machine, doesn't have XP on it, but is Windows formatted.

Is it possible to mount this 2nd HDD and access the files?  I really don't have a good way of getting the data off of this HDD and don't want to lose it.

Thanks,

Tom

---

### Post by ubunterooster on 2010-02-10
Sure, I have :)

---

### Post by Miljet on 2010-02-10
The other drive is probably formatted as NTFS, and yes, Ubuntu will read files on a NTFS drive.

---

### Post by abhishek.malhotra35 on 2010-02-10
After connecting your harddisk, execute following command:
sudo fdisk -l
This will tell you the formatting of the partition on that disk. Then you can either mount the partitions manually using command line, or mount them permanently by fstab entry.

---

### Post by heus33 on 2010-02-11
Thanks guys - I've been reading about fstab and will give this a shot!

---

### Post by heus33 on 2010-02-13
Hmm - fdisk is not recognizing my 2nd HDD.  It is installed correctly and set up as a Slave.  It is recognized in the BIOS.   

Here's the output - the master drive (15.4GB) is detected but the slave (120GB) is not - any ideas where to go from here?

tdiddy@desktop:~$ sudo fdisk -l
[sudo] password for tdiddy: 

Disk /dev/sda: 15.4 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68326832

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1784    14329948+  83  Linux
/dev/sda2            1785        1868      674730    5  Extended
/dev/sda5            1785        1868      674698+  82  Linux swap / Solaris

---

### Post by heus33 on 2010-02-15
bump - any advice guys? I've been searching around and can't seem to find where to go from here.  (see post above)   Thanks

---

### Post by docshawnc on 2010-02-15
Try df -H and see what it says.

---

### Post by Morbius1 on 2010-02-15
You could also try the following command:

**sudo blkid -c /dev/null**

Should list all your partitions - mounted or not.

---

### Post by ubunterooster on 2010-02-15
I assume these are ide drives both on one port?
   If possible use a different port for ea. and try removing the slave marking.

---

### Post by heus33 on 2010-02-15
Results of df -H:
 tdiddy@desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               15G   9.1G   4.7G  67% /
udev                   327M   279k   327M   1% /dev
none                   327M   1.2M   326M   1% /dev/shm
none                   327M    87k   327M   1% /var/run
none                   327M      0   327M   0% /var/lock
none                   327M      0   327M   0% /lib/init/rw

---

### Post by heus33 on 2010-02-15
Results of **sudo blkid -c /dev/null**:

tdiddy@desktop:~$ sudo blkid -c /dev/null
[sudo] password for tdiddy: 
/dev/sda1: UUID="1c4081e4-ac58-4f8a-a476-275dbf1a47ba" TYPE="ext4" 
/dev/sda5: UUID="fead2e9b-700e-47e2-bba8-98d9411cd8a9" TYPE="swap"

Going to try moving the 2nd HDD to another port and removing the slave setting....brb

---

### Post by thatguruguy on 2010-02-15
You can also consider buying a [hard drive enclosure]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=92&name=External-Enclosures") that you put your hard drive in, and then hook it up to your computer as an external drive.

a 15 gig drive for your main drive is awfully small.  You may consider burning all of your files on the larger drive to CDs or DVDs, and then setting up the 120 GB drive as your main drive.

---

### Post by heus33 on 2010-02-15
Success!  Installing the HDD on a different port did it.  

@thatguruguy - you're right - I think I'll just install ubuntu on the larger drive sometime soon.

---

### Post by ubunterooster on 2010-02-15
Congrats

A larger drive IS preferred; my fathers ubuntu partition, though, is 9.5gb

---

