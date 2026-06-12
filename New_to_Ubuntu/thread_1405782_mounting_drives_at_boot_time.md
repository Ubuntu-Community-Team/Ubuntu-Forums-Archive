---
title: "mounting drives at boot time"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Black Sun on 2010-02-13
hello friends,

I am currently using Karmic Kola, and When I installed the ubuntu I assigned 30Gb of space for the operating system, now I have a problem of low disk space for the same and it mainly due to the downloads and feeds that I have subscribed to, but I do have a partioned drive of about 100GB that is completely free at the moment and I want that whatsoever my downloads are, should be stored in that 100GB partition rather than in my home folder, but the problem is after each reboot I have to manually mount the 100GB drive and hence cannot start the softwares on the boot time with there storage paths pointing to a unmounted media.

So my question is - is there any way to mount my other drives automatically every time my system boots?

---

### Post by karthick87 on 2010-02-13
Yes you can do it by installing the  Storage Device manager..Try it.. 
[B]sudo apt-get install pysdm
[/B]

---

### Post by Black Sun on 2010-02-13
Is there no way to get this done by some kind of startup script rather than a "whole different software"?

---

### Post by mikewhatever on 2010-02-13
You'll need to add an entry for that drive to /etc/fstab. Post the output of **sudo fdisk -l**, and we will sort it out.

---

### Post by karthick87 on 2010-02-13
How to do it manually without third party software..This is my output....

karthick@Learners-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00af00af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       19457   120447337+   f  W95 Ext'd (LBA)
/dev/sda5            4463        9561    40957686    7  HPFS/NTFS
/dev/sda6            9562       14660    40957686    7  HPFS/NTFS
/dev/sda7           14661       19254    36901273+  83  Linux
/dev/sda8           19255       19457     1630566   82  Linux swap / Windows

---

### Post by mikewhatever on 2010-02-13
You seem to have two candidates, sda6 and sda5, do you know which one you want to mount? Note, none of the partitions shown is 100GB.

---

### Post by nick_goodfate on 2010-02-13
there is no 100 gb partition because Black Sun has an 100gb partition , not getyourkarthick ...

---

### Post by mikewhatever on 2010-02-13
> **nick_goodfate said:**
> there is no 100 gb partition because Black Sun has an 100gb partition , not getyourkarthick ...

Excuse me, ...what?

---

### Post by nick_goodfate on 2010-02-13
look who said that has a 100gb partition and who posted the output of "fdisk -l" ... different person ! ok ?

---

### Post by Morbius1 on 2010-02-13
***Step 1: Get a list of your partitions***

Open **Terminal**
Type **sudo blkid -c /dev/null**

You will get an output that looks like this:
> /dev/sda1: UUID="DA9056C19056A3B3" LABEL="WinD" TYPE="ntfs"
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat"
/dev/sdb2: LABEL="Data" UUID="e92eaf02-ff61-4db0-9397-35f1aadb98e8" TYPE="ext3"
*** Step 2: Create a home ( mount point ) for your partition to live in:***

Open **Terminal**
Type **sudo mkdir /media/Data**

[COLOR=Blue][I]NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.
[/I][/COLOR] 
*** Step 3: Create an entry in fstab that will automatically mount that partition at startup. Use the following examples as templates depending on how the partition was formatted:***

UUID=DA9056C19056A3B3 /media/Data** [COLOR=Blue]     ntfs[/COLOR]**    defaults,nls=utf8,umask=007,gid=46 0 2
UUID=C4DB-C1B0  /media/Data** [COLOR=Blue]    vfat[/COLOR]**    utf8,umask=007,gid=46 0       2
UUID=e92eaf02-ff61-4db0-9397-35f1aadb98e8 /media/Data** [COLOR=Blue]         ext3[/COLOR]**    relatime        0       2

The first two will mount a windows formatted partition with owner = root and with permissions for all local users to read and write.

The last one will mount a linux formatted partition with owner = root and with read / write permissions to root only so that will have to be adjusted after mounting. For example:

Open **Terminal**
Type [B]sudo chown -R blacksun /media/Data
[/B][COLOR=Blue]*This will change ownership from root to you.*[/COLOR]

There are a great number of different options you can use with these fstab entries depending on your particular needs. Some are only applicable to specific filesystems, but for the most part this is a good starting point. In fact the templates you see in step 3 are what happens when you allow Ubuntu to set up these non-system partitions when choosing the manual partitioning option during an install.

---

### Post by Black Sun on 2010-02-13
Here is the output of "sudo fdisk -l" on my laptop

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dbe0dbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            2678       19457   134785350    f  W95 Ext'd (LBA)
/dev/sda5            2678       15540   103322016    7  HPFS/NTFS
/dev/sda6           19209       19457     2000061   82  Linux swap / Solaris
/dev/sda7           15541       19208    29463178+  83  Linux

Partition table entries are not in disk order


Also tell me how you people find which partition is of what size...:D

---

### Post by Black Sun on 2010-02-13
One more question...
I have a total of 3 partions 30GB for ubuntu, 25GB for windows, and approx 100GB (for nothing), and I guess there would be one more partition for swap space in ubuntu that accounts for a total of 4 partitions... then how come that fdisk entry shows 5 partition entries?

---

### Post by Morbius1 on 2010-02-13
> Also tell me how you people find which partition is of what sizeOpen **Terminal**
Type **df -h**

> then how come that fdisk entry shows 5 partition entriesBecause one of them ( sda2 ) is an extended partition. It is a primary partition that acts as a wrapper for logical partitions. You can only have 4 primary partitions but if one of then is an extended partition then you can have may logical partitions within it.

---

### Post by Black Sun on 2010-02-13
> **Morbius1 said:**
> ***Step 1: Get a list of your partitions***

Open **Terminal**
Type **sudo blkid -c /dev/null**

You will get an output that looks like this:
*** Step 2: Create a home ( mount point ) for your partition to live in:***

Open **Terminal**
Type **sudo mkdir /media/Data**

[COLOR=Blue][I]NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.
[/I][/COLOR] 
*** Step 3: Create an entry in fstab that will automatically mount that partition at startup. Use the following examples as templates depending on how the partition was formatted:***

UUID=DA9056C19056A3B3 /media/Data** [COLOR=Blue]     ntfs[/COLOR]**    defaults,nls=utf8,umask=007,gid=46 0 2
UUID=C4DB-C1B0  /media/Data** [COLOR=Blue]    vfat[/COLOR]**    utf8,umask=007,gid=46 0       2
UUID=e92eaf02-ff61-4db0-9397-35f1aadb98e8 /media/Data** [COLOR=Blue]         ext3[/COLOR]**    relatime        0       2

The first two will mount a windows formatted partition with owner = root and with permissions for all local users to read and write.

The last one will mount a linux formatted partition with owner = root and with read / write permissions to root only so that will have to be adjusted after mounting. For example:

Open **Terminal**
Type [B]sudo chown -R blacksun /media/Data
[/B][COLOR=Blue]*This will change ownership from root to you.*[/COLOR]

There are a great number of different options you can use with these fstab entries depending on your particular needs. Some are only applicable to specific filesystems, but for the most part this is a good starting point. In fact the templates you see in step 3 are what happens when you allow Ubuntu to set up these non-system partitions when choosing the manual partitioning option during an install.

Morbius1, I tried what you said and opened the fstab as you said in step 3... but there were no UUID kind of entries... so do i have to add new lines to it or my fstab file is corrupt?

here is my "blkid -c /dev/null" output

/dev/sda1: UUID="023C01683C0157D5" TYPE="ntfs" 
/dev/sda5: UUID="C620627F20627679" TYPE="ntfs" 
/dev/sda6: UUID="813a82e0-2a35-4f1a-b425-161803dc8e11" TYPE="swap" 
/dev/sda7: UUID="772387e1-0756-4a61-86a1-29bec434a220" TYPE="ext3"

---

### Post by Morbius1 on 2010-02-13
> I tried what you said and opened the fstab as you said in step 3... but there were no UUID kind of entries... so do i have to add new lines to it or my fstab file is corrupt?That's odd because Ubuntu should have defaulted to that method. Let's see what your fstab looks like. Post the output of the following command:

Open **Terminal**
Type **cat /etc/fstab**


>  /dev/sda5: UUID="C620627F20627679" TYPE="ntfs" If this is the 100GB partition you want to automount then this would be the line I would add to fstab:

> UUID=C620627F20627679 /media/Data  ntfs defaults,nls=utf8,umask=007,gid=46 0 2That's assumming you alread created the mount point of /media/Data.

---

### Post by Girya on 2010-02-13
it might be a good idea to copy your fstab file before editing it so if you make a mistake you can revert back to the original file. 

this is what i do:

```
sudo cp /etc/fstab /etc/fstab.bak
```

---

### Post by oldfred on 2010-02-13
blacksun - I think you misunderstood the post on pysdm. It is software that allows you to create a mount point and edit fstab all at once. Once done you do not have to use it again. It is best that you do understand fstab entries and mounting before running pysdm.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

Once you have created your mount and fstab entries you can link your data folders into /home.

I mounted my data directory in /usr/local/fred which I had to create and give permissions to; I did this location so it would not appear in nautilus and I only see the data thru the links:

ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

my fstab entry as an example:
# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2

---

### Post by mikewhatever on 2010-02-14
> **Black Sun said:**
> Here is the output of "sudo fdisk -l" on my laptop

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dbe0dbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            2678       19457   134785350    f  W95 Ext'd (LBA)
/dev/sda5            2678       15540   103322016    7  HPFS/NTFS
/dev/sda6           19209       19457     2000061   82  Linux swap / Solaris
/dev/sda7           15541       19208    29463178+  83  Linux

Partition table entries are not in disk order


Also tell me how you people find which partition is of what size...:D

I don't know if it's been solved, but here is a simple way to mount sda5, the 100Gb ntfs partition.

1. Create a mount point

sudo mkdir /media/sda5

2. The following line should be added to /etc/fstab

/dev/sda5 /media/sda5 ntfs defaults 0 0

---

### Post by Black Sun on 2010-02-15
sorry guys, my brother spilled milk over my laptop, so wasn't able to try out your suggestions, will post back in this thread as soon as my laptop is up and running...

Thanks for the help...

---

### Post by Morbius1 on 2010-02-15
> /dev/sda5 /media/sda5 ntfs defaults 0 0That will work of course, but I'm kind of old school when it comes to permissions. There's an implied umask=000 in that statement, which means everyone will have read write access to that mount point. I prefer to explicitly state the permissions ( umask=007 ) so there's no confusion when I look at the fstab entry and to give read write access only to local login users.

That's why I recommended this:
> UUID=C620627F20627679 /media/Data  ntfs defaults,nls=utf8,umask=007,gid=46 0 2                      [COLOR=Blue]*Which is exactly what the Ubuntu installer would have done had you specified this partition and mount point at install time.*[/COLOR]

Or if you prefer not to use UUID's then this:
> /dev/sda5 /media/Data  ntfs defaults,nls=utf8,umask=007,gid=46 0 2                      Quite frankly, Id be happy with any of these as long as you didn't succumb to using pysdm, ntfs-config or any of the other "utilities" ;) ( sorry, just a personal thing with me )

BTW, if you don't want the mount point to show up on the desktop or under places in nautilus then create the mount point in /mnt/Data or /Data.

---

