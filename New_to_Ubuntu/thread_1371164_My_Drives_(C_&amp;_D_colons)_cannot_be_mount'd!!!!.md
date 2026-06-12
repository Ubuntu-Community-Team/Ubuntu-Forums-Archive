---
title: "My Drives (C &amp; D colons) cannot be mount'd!!!! :("
date: 2010-01-03
forum: New to Ubuntu
---

### Post by mathes on 2010-01-03
Hey guys...

Am a newbie to ubuntu and was using windows XP till these days..

Now, I've installed Ubuntu 8.04 Grub and Mine is a 320 Sata HDD..

I made 4 partitions.. 

C - 100 GB where I'd my old XP (which I deleted completely by booting thro' Hiren's Boot CD because, I'd a problem with XP). Now, am using it as 'swap' space (you might be wondering about this huge swap space.. :D I did this without knowledge.. :) )

D - 100 GB Where I've my Own Important Datas

E - 100 GB Like D

G - 20 GB where I've Ubuntu 8.04 now..

Problem is that, on the first day, I was able to open my D and E drives (after installing Ubuntu, my D and E drives changed to C and D.. I dont 've a clue.. leave it..).. Then, from the second day, When I tried to open my Drives, it says "Unable to mount the volume" and in details "cannot read from /media/.hal-mtab".

My drive names are: 110.4 GB Media and 104.9 GB Media.. 

And 1 more thing.. 

I went searching into /media/ and found a folder with name ".hal-mtab" (after pressing ctrl+H) but with an "x" mark one the folder Icon.

It says "You donot have Permissions necessary to view the contents of ".hal-mtab"", when I try to open.

Also, There are folder of the following names with an "x" mark on the icon (The properties window says that the contents are unreadable with 0 byets free space and No permissions are there)

* cdrom
* cdrom1
* disk-1
* disk-2
* disk-3
.
.
.
Up to
* disk-49

These disks have 16.0GB free space with unknown contents..

I tried mounting (they are NTFS file systems).. But, failed...

And, I thought I 've lost the datas first.. Then, I used Hirens boot cd and went to the drive using mini xp where the drives names are c: and d:..

How can I mount my disk??

I wanna access those datas... I also wanna make a seperate partation with the swap space (100GB)!!!

How can ALL these be done??

Mine is acer laptop with Ubuntu 8.04 in it.. :)

---

### Post by Methuselah on 2010-01-03
In ubuntu 8.04, please enter the command below in a Terminal (Accessories->Terminal) and post the output.
This will give definitive information about how Ubuntu is seeing your various hard drives and partitions.

```

sudo fdisk -l

```

---

### Post by mathes on 2010-01-03
> **Methuselah said:**
> In ubuntu 8.04, please enter the command below in a Terminal (Accessories->Terminal) and post the output.
This will give definitive information about how Ubuntu is seeing your various hard drives and partitions.

```

sudo fdisk -l

```

mathes@MatheS-LaP:~$ sudo fdisk -l
[sudo] password for mathes: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006fbd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10138    81433453+  82  Linux swap / Solaris
/dev/sda2           10139       38913   231135187+   f  W95 Ext'd (LBA)
/dev/sda5           10139       22886   102398278+   7  HPFS/NTFS
/dev/sda6           22887       36302   107763988+   7  HPFS/NTFS
/dev/sda7           36303       38913    20972826   83  Linux
mathes@MatheS-LaP:~$ 


Thnx for the reply :)

---

### Post by Methuselah on 2010-01-03
Try the below in a terminal:

```

sudo mkdir /media/D
sudo mount -t ntfs /dev/sda5 /media/D

```

Tell me if access to the drive appears on your desktop and you can browse it.
I want to know if there are really issues with mounting them.

---

### Post by mathes on 2010-01-03
> **Methuselah said:**
> Try the below in a terminal:

```

sudo mkdir /media/D
sudo mount -t ntfs /dev/sda5 /media/D

```Tell me if access to the drive appears on your desktop and you can browse it.
I want to know if there are really issues with mounting them.


WOOW.... Great... Thnx friend.. ThanQ very Much... :) ThanQ...

---

### Post by mathes on 2010-01-03
What are these thing??

* cdrom
* cdrom1
* disk-1
* disk-2
* disk-3
.
.
.
Up to
* disk-49


Can I delete them??

---

### Post by Methuselah on 2010-01-03
> **mathes said:**
> WOOW.... Great... Thnx friend.. ThanQ very Much... :) ThanQ...

No prob!

You can do similarly for the other ntfs partition

```

sudo mkdir /media/E
sudo mount -t ntfs /dev/sda6 /media/E

```

There is one thing to keep in mind though.
When you restart, they will be unmounted.
So you'll have to execute the commands again.
[Not the 'mkdir' just the 'mount']

There is a way to make the settings stick though.
It involves editing a file called /etc/fstab. (ie file system table)

However, if you do not want to do taht by hand, you can learn about a GUI here:
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Or if you prefer watching a video toturial:
[http://www.youtube.com/watch?v=SpzJkQf0RAY](http://www.youtube.com/watch?v=SpzJkQf0RAY)

All the best!

---

### Post by Methuselah on 2010-01-03
> **mathes said:**
> What are these thing??

* cdrom
* cdrom1
* disk-1
* disk-2
* disk-3
.
.
.
Up to
* disk-49


Can I delete them??

I would just leave them.
When you put in a CD it will usually be automounted to /media/cdrom.
I am not sure why all those others were created but I'd just leave them as well.

---

### Post by mathes on 2010-01-03
> **Methuselah said:**
> No prob!

You can do similarly for the other ntfs partition

```

sudo mkdir /media/E
sudo mount -t ntfs /dev/sda6 /media/E

```There is one thing to keep in mind though.
When you restart, they will be unmounted.
So you'll have to execute the commands again.
[Not the 'mkdir' just the 'mount']

There is a way to make the settings stick though.
It involves editing a file called /etc/fstab. (ie file system table)

However, if you do not want to do taht by hand, you can learn about a GUI here:
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Or if you prefer watching a video toturial:
[http://www.youtube.com/watch?v=SpzJkQf0RAY](http://www.youtube.com/watch?v=SpzJkQf0RAY)

All the best!

Yesterday, I asked this doubt to my friend. He said that, you need to edit fstab file. I open'd it with the command "gedit" and found zero clue on that. So, I just closed it. Thnx for the video. I 'll try my best. Thanx a lot!! :)

---

### Post by Methuselah on 2010-01-03
> **mathes said:**
> Yesterday, I asked this doubt to my friend. He said that, you need to edit fstab file. I open'd it with the command "gedit" and found zero clue on that. So, I just closed it. Thnx for the video. I 'll try my best. Thanx a lot!! :)

You're welcome. :)

BTW, I forgot you were using 8.04 and the previous video is for 9.10
Here is a video tailored to that release and is also about automounting ntfs (ie windows) drives.
[http://www.youtube.com/watch?v=xZIPLn5Lu1U&feature=related](http://www.youtube.com/watch?v=xZIPLn5Lu1U&feature=related)

---

