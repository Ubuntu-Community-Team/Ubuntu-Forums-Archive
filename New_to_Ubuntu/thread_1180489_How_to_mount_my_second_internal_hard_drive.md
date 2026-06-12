---
title: "How to mount my second internal hard drive?"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Famicommander on 2009-06-06
I just installed Xubuntu 9.04 on my Asus EEE 901. The install went smoothly, and all my hardware was detected without me having to do anything.

Now, my only problem is getting my second hard drive to stay mounted all the time.

My netbook has one 4GB drive, and one 16GB drive. When I installed, I chose a guided install and told it to erase the entire four GB disc. So, when I open my filesystem, it says I only have 1.8 GB of free space, even though I have an empty 16GB hard drive.

---

### Post by Famicommander on 2009-06-06
Do my threads smell bad or something?

I mean, I don't think for a second that my problems are more important than anyone else's, but this is the third thread in a row I've made that didn't even get any views beyond my own.

I don't want to keep bumping this, but I really do need some help.

---

### Post by rickycodie on 2009-06-06
when you installed did you want to make the 16gb drive the home partition? or do you just want to mount it? how is the drive formatted? is it a usb or a sd card?

---

### Post by Famicommander on 2009-06-06
It's an internal solid state drive.

And I would like to have my Home Folder on the larger drive, since I'm quickly running out of space on the 4GB drive.

Thanks for the reply.

---

### Post by rickycodie on 2009-06-07
unfortunatly the only way that i know to make the home partition a different drive is to do it on the partitioning part of the install. if the disk is formatted in fat or fat32 or ntfs it will need to be formatted. sorry. 

you might try here though 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

althoiugh it looks like a new install might be easier. either way you choose, be sure to back everything up, including the hidden files in your /home directory.

---

### Post by bhaverkamp on 2009-06-07
Of course you can do this now without reinstalling.

Just mount the drive ontop of the home directory in your /etc/fstab

this line is from my fstab. replace sdb1 with the name of your device.

/dev/sdb1	/home	ext3	relatime,errors=remount-ro 0       0

Note that once you do this your home directory will no longer be accessible. So you should copy your /home/user directory to the new drive before mounting.

---

### Post by rickycodie on 2009-06-07
there we are, that seems easy enough.

---

### Post by Famicommander on 2009-06-07
> **bhaverkamp said:**
> Of course you can do this now without reinstalling.

Just mount the drive ontop of the home directory in your /etc/fstab

this line is from my fstab. replace sdb1 with the name of your device.

/dev/sdb1	/home	ext3	relatime,errors=remount-ro 0       0

Note that once you do this your home directory will no longer be accessible. So you should copy your /home/user directory to the new drive before mounting.

I don't know how to copy anything to the new drive, since the OS doesn't see it. It sees it in Gparted, but I don't know how to access it in terms of copying files to it.

Also, I'm not sure what fstab is.

---

### Post by Famicommander on 2009-06-07
I suppose I don't really *need* my Home Folder to be mounted on the new drive.

What I really want, first and foremost, is just to be able to use the space on the drive. Because as it stands right now, I don't even know how to access it.

---

### Post by furialis on 2009-06-07
I just bought two SSD and I can't use them with the stock release of Jaunty.
I needed to [compile the latest kernel]("http://ubuntuforums.org/showthread.php?t=311158") for Jaunty to see my drives. 

I can't install to them because the stock release of Jaunty doesn't include the needed Sata drivers.

---

### Post by bhaverkamp on 2009-06-07
You can do the mount anywhere you want but first you need to determine the file system type of the 16 gb disk. Use fdisk to determine the file type (if any) of your second disk

bernie@monterey:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b1f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59687   479435796   83  Linux
/dev/sda2           59688       60801     8948205    5  Extended
/dev/sda5           59688       60801     8948173+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cbadb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdd: 8254 MB, 8254390272 bytes
16 heads, 32 sectors/track, 31488 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x5503977d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       31488     8060912    b  W95 FAT32
bernie@monterey:~$

---

### Post by Famicommander on 2009-06-07
Here you go:
```
jason@ubuntu:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb38fb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux
jason@ubuntu:~$ 

```

---

### Post by Famicommander on 2009-06-07
Still don't have what I need...

---

### Post by mgranet on 2009-06-07
First, you need to create a folder in your /media directory to mound the drive to.
```
cd /media
```
Then, create a directory to mount to:
```
sudo mkdir sdb1
```
Next, mount your drive
```
sudo mount /dev/sdb1 /media/sdb1
```

If you want the mount to be persistent, you'll need to edit your /etc/fstab.
```
sudo nano /etc/fstab
```

Add:
```
/dev/sdb1 /media/sdb1 ext3 defaults 0 0
```
Ctrl-O to save, Ctrl-X to exit. Reboot.

---

### Post by michy99 on 2009-06-07
What is the output of:```
cat /etc/fstab
```

I have to go eat. I will be back in a little while.

---

### Post by Famicommander on 2009-06-07
@mgranet:
I tried what you said, and I got this far:
```

jason@ubuntu:~$ cd/media
jason@ubuntu:/media$ sudo mkdir sbd1
[sudo] password for jason:
jason@ubuntu:/media$ sudo mount /dev/sbd1 media/sdb1
mount: mount point media/sdb1 does not exist

```

---

### Post by mgranet on 2009-06-07
> **Famicommander said:**
> @mgranet:
I tried what you said, and I got this far:
```

jason@ubuntu:~$ cd/media
jason@ubuntu:/media$ sudo mkdir **sbd1**
[sudo] password for jason:
jason@ubuntu:/media$ sudo mount /dev/sbd1 media/sdb1
mount: mount point media/sdb1 does not exist

```

Typo highlighted in your quote.

---

### Post by michy99 on 2009-06-07
> **Famicommander said:**
> @mgranet:
I tried what you said, and I got this far:
```

jason@ubuntu:~$ cd/media
jason@ubuntu:/media$ sudo mkdir sbd1
[sudo] password for jason:
jason@ubuntu:/media$ sudo mount /dev/sbd1 media/sdb1
mount: mount point media/sdb1 does not exist

```

Be sure to put the / in front of media/sdb1.```
sudo mount /dev/sdb1 /media/sdb1
```

---

### Post by Famicommander on 2009-06-07
Everything worked, but when I rebooted the drive wasn't mounted anymore. This is what my fstab looks like:
```
GNU nano 2.0.9             File: /etc/fstab                                

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f1333456-d919-4c95-8d4c-7c37bbc74835 /               ext3    relatime,e$
# swap was on /dev/sda5 during installation
UUID=7b8c0b75-bb73-4635-b149-c3fcfeb48fd7 none            swap    sw        $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb1 /media/sdb1 ext3 defaults 0 0
```

---

### Post by mgranet on 2009-06-07
That's odd. You're sure you created the directories without typos? Ie, you should see a folder at /media/sdb1

Kind of at a loss why it didn't stay persistent.

---

### Post by Famicommander on 2009-06-07
Yes, there's a folder there. Before I rebooted, it said 15GB of free space. Now it says 1,1GB of free space.

Did I add the line to my fstab in the right spot? I don't really know what's going on.

---

### Post by mgranet on 2009-06-07
Yeah. It's in the same spot where I've got mine. Like I said, I'm at a loss. It should be working right now. Just to be sure, you created the sdb1 folder as root (sudo mkdir), correct?

---

### Post by Famicommander on 2009-06-07
Indeed I did.

Do you think I should just try again?

---

### Post by mgranet on 2009-06-07
Yeah. delete the folder to mount
```
cd /media
```
```
sudo rmdir sdb1
```

then try again. Copy paste the code from my first posts, just to make sure there are no typos.

---

### Post by Famicommander on 2009-06-07
```
jason@ubuntu:~$ cd /media
jason@ubuntu:/media$ sudo rm sdb1
[sudo] password for jason: 
rm: cannot remove `sdb1': Is a directory

```

Ummm...?

---

### Post by mgranet on 2009-06-07
Oops. That should read rmdir

---

### Post by michy99 on 2009-06-07
I think I should point something out here. When you are in nautilus, it will only show the free space on the partition where the current folder is located. If you home partition in on the small drive, then you will only see the free space in that drive in your home directory. If you change to a directory/folder on the larger partition, you will see the free space on that one.

---

### Post by Famicommander on 2009-06-07
Xubuntu uses Thunar, not Nautilus. And yeah, I'm aware of all that.

I figured out the problem. My large drive was formatted to ext2, and you had me edit my fstab to automount an ext3 drive. I fixed it, and now it's all working great.

Thanks for the help.

Now, how might I go about mounting my /home folder to my larger partition, so that I don't run out of space?

---

### Post by mgranet on 2009-06-07
You should probably keep your drives ext3, unless you have specific need. As for the /home move, you will need to repartition, creating a paritition with the mountpoint /home From here, I am not 100% sure, as I have never done it. I'm intelligently guessing you have move your /home directory to the home partition. It might look like this:
```
sudo mv /home /media/sdb*x*
``` *x being what the new /home partition is assigned. fdisk -l to find out

Again, I've never done this, so you might want to wait for someone who has.

---

### Post by michy99 on 2009-06-07
Copy everything in /home (not /home itself but the contents including hidden) to the other partition. Rename /home to something else (in case you need to restore it). Create a new /home to mount to. Change fstab to mount to /home instead of /media/sdb1.

---

### Post by eazyigz on 2013-02-11
> **furialis said:**
> I just bought two SSD and I can't use them with the stock release of Jaunty.
I needed to [compile the latest kernel]("http://ubuntuforums.org/showthread.php?t=311158") for Jaunty to see my drives. 

I can't install to them because the stock release of Jaunty doesn't include the needed Sata drivers.

Yes, updating to the latest kernel was the solution that worked for me.  The nautilus file explorer will mount the drive for you automatically when you select it.

---

### Post by oldos2er on 2013-02-11
Old thread closed.

---

