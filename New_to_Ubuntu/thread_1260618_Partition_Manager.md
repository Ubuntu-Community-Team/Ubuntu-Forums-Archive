---
title: "Partition Manager"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by memecs on 2009-09-07
Hello everyone,
i moved to ubuntu like one month ago and i am really happy about it. I am still dual booting vista, but now i want to get rid of it and load it in a virtual machine.

So basically my two hard drive (500GB and 1T) with 3 different partition on the last one.
Disk 1 (500GB):
partition 1: windows

Disk 2(1TB):
partition 1(170GB): ext3 ubuntu /home
partition 2(736GB): ntfs -> movies pics etc... ( from windows)
partition 3(18GB(: ext3 ubuntu /

... and i am not sure about what do with them, i mean how to re arrange everything. 
Especially i don't know what to do with the 736GB ntfs partion. I don't know if add that to /home or what...

Any ideas?

if is it safe to resize ext3 partion or should i backup the data?

Thanks

---

### Post by drs305 on 2009-09-07
Glad you are liking Ubuntu.

Changing partitions with gparted (Partition Editor) or any other tool is never guaranteed. While gparted has proven itself very reliable, you should *always* back up your data if possible.

How much data do you have on partition 2 (736GB)? 

I ask because if you try to move it the operation will likely take a very long time. If you can back it up first, shrinking it may be a good first step.

If your data would fit temporarily in your /home folder, you might move it there temporarily while you work with your partitions. 

If at all possible, copy the data from this partition to /home or another drive so that if something happens while you are working with your partitions you will still have a good copy of the data.

You currently have 3 primary partitions on the drive. My personal preference would be to make an extended partition and then make a logical partition. The reason is that you are limited to 4 primary partitions but you can divide the extended partition into as many partitions as you are likely to make. Even if I was only going to have 3 partitions, I would make at least one a logical partition for future flexibility.

Anyway, tell us if you can copy all your ntfs data onto another partition, and then we can make some recommendations.

---

### Post by memecs on 2009-09-08
Hello drs305,
yes a could move everything on /home and the working on the other to partitions.
my idea would be extending /home to 900GB and / to 100GB. but what should i do with the 500GB? should i make it something like /home2 ?

thanks for your help

---

### Post by drs305 on 2009-09-08
memecs,

I'm about to log off but would advise you to go ahead and start copying your ntfs data files to either /home or to the other drive, if you have space. No matter what you decide to do about partitions, you will want to have your data backed up. Also, since your /home partition is the first, I don't see you moving that one during your reorganization, although you may eventually make it smaller or larger.

One other question. I don't see a swap partition? Do you have one, are you using a swap file instead, or neither?

Partitioning is very much a personal preference. You already have a separate /home, so there isn't one 'best' answer. Maybe someone will post here with some suggestions. I will check back tomorrow and offer some suggestions if nobody else has answered. 

Got to run. Best wishes.

---

### Post by drs305 on 2009-09-08
I was waiting for a reply about a swap partition, but here are some comments.

Any partition scheme is highly subjective. 
Make sure you have made a backup of your data.

**Disk 1**
I would leave the Windows partition alone for now. If you need it you will have it available. I would use any extra space on that disk as backup. Perhaps divide it into two partitions: Windows and backup. The advantage of having a backup partition there is that it is on a separate drive. Backups on the same drive don't do much good if the hard drive fails.  ;-)

**Disk 2**
**/home** - I would leave this partition where it is. As for size, it depends primarily where you want to store your data/music/videos, etc. If you want to put them in the standard home folders (documents, video, etc), you would want this folder to be pretty large - only you know how much space you will need. 

I prefer keeping my data outside of the ubuntu partitions. /home without data in it is fairly small. My /home folder is only 200MB, but I made the partition 10GB.

**NTFS** - I would delete this partition after copying the data at least temporarily to another partition if you don't plan on using Windows any longer. If you think you will share Windows and linux files, you might want to leave it alone, and resize it to your needs for shared data.

I would just delete it and then:

**/** - I would move this over to the left, adjacent to the /home. 18 GB is probably a good size for a standard / partition as long as you have the space to spare. It doesn't need to be quite that large, especially with a separate /home, but I'd leave room for growth anyway.

**Extended**
I would now make all remaining space an extended partition. As mentioned in the previous post, you can divide it up into multiple partitions.

**Swap** - First logical partition (sdb5). Make the first logical partition in the extended partition your swap partition. 1-2 GB, formatted as swap.

**Data** - Second and more logical partitions (sdb6 +) What you do with the rest is up to you. I make lots of partitions but it can lead to more work. I tend to make and delete lots of test partitions, so I leave space at the end of the disk (far right) unallocated so I can make/delete practice partitions without messing with my good ones. I generally leave the space as unallocated so I don't get partitions out of order.

One large data partition would probably be fine. You might want to make a separate partition for your VM's. VMs can take up a lot of space. I have about 10 and they are using 70GB of space. My Winows XP file is just about 15GB. (VIrtualbox).

I wrote a guide about expanding /. It doesn't really apply to this scenario but there is a section on basic partitioning precautions that might be of interest.
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")
There are more good links on partitioning on that page.

One more tip: before rebooting check your /etc/fstab and /boot/grub/menu.lst files and make sure the device designations (sdXX) and UUIDs are still correct. If they have changed and are incorrect you will have problems booting. You can check the information with:
```
sudo blkid
```

---

### Post by memecs on 2009-09-10
drs305, sorry for the late reply, i've been really busy these days... 
By the way, i followed your advices and your really good tutorial... Now i would have just last question...

How do i browse and for example ls the partitions from the shell? i tried ls /dev/sda1 but it doesn't work...

thanks a lot again

---

### Post by drs305 on 2009-09-10
Once you have booted into the system, your system is mounted as /. You browse the mount point/folder name, not the device name (sda1). So if you are looking for folders or files, you would use:
```

ls /  # root file system
/home/yourusername/  # your /home folder

```
Examples:
ls /boot/grub
ls /home/memecs/Desktop

You can also browse with Nautilus or from Main Menu > Places. 

Here are some links on the Linux file system: The first one is a bit old but still has valid information.
[https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html]("https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html")

[http://library.gnome.org/users/user-guide/stable/gosnautilus-8.html.en]("http://library.gnome.org/users/user-guide/stable/gosnautilus-8.html.en")

---

