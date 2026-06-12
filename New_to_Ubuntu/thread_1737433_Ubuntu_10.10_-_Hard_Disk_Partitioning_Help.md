---
title: "Ubuntu 10.10 - Hard Disk Partitioning Help"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by ebun2 on 2011-04-23
Hi everyone,

I would appreciate some advise from all you experts in completing my hard disk partitioning properly. Pls note that I am a non tech savvy newbie and very new to Ubuntu :o

I am currently on dual boot mode with Windows7. Well let me explain my requirement. My hard disk (160GB) is currently split as,
C: 40GB
D: 60GB
E: 60GB

So right on Ubuntu 10.10 when I go to Places > Computer the above D: and E: drives are separately shown so that I can save/use them as I prefer. For eg: I may create a folder for movies, studies etc.

For quite sometime I am struggling to achieve the same on a full Ubuntu install (that is to get rid of Windows7). During the partitioning stages when I select "Erase and use entire disk" I cannot achieve this because it by default uses the entire disk. What I exactly want to achieve is to do a complete new installation (that is Ubuntu as the only OS) and to have the hard disk split into 2 or 3 private partitions.

Having read so many articles and threads I guess I am able to handle the basic partitioning but can someone please enlighten me (having in mind that I am a non tech savvy newbie) as to how I can do this during th installation. I will explain below as to what I can do as of now ;)

(a)

- Primary
- 500MB
- Beginning
- Ext4journaling File System
- /boot

(b)

- Primary
- 30GB
- Beginning
- Ext4journaling File System
- /

(c)

- Primary
- 1000MB
- Beginning
- swap area

I am clueless after this stage as to how I should proceed if I need to partition the remaining disk space into 2 personal disks (example D: and E: above) which should show in Places > Computer.

When I visit Disk Utility these are bearing the following specs:

C:
Partition type : HPFS/NTFS (0X07)
Device : /dev/sda2
Mounted at /host

D:
Partition type : HPFS/NTFS (0X07)
Device : /dev/sda3
Not Mounted

E:
Partition type : HPFS/NTFS (0X07)
 Device : /dev/sda4
Not Mounted

Thanks for all in advance - cheers =D>

---

### Post by coffeecat on 2011-04-23
A few comments.

- When using Ubuntu or any Linux distro it's best to forget about the C:. D: drive concept. This is a Windows-only convention which has no meaning in Unix like operating systems.

- Having said that I see that you have a wubi installation, not a conventional dual-boot with Ubuntu in its own partitions. Your C: drive "mounted at /host" is the giveaway. This means that if you want to get rid of Windows, you will need to re-install because you will lose your wubi installation. Well - it is possible to migrate a wubi to a conventional partition, but you might want to start fresh anyway.

- My advice is: don't bother with a separate /boot partition - an unnecessary complication.

- Splitting your personal files in separate partitions is not the most efficient use of your hard drive space. This is a hangover from Windows thinking with D:, E: "drives".

- If you want Ubuntu alone, perhaps the best setup is a small-ish root (/) partition of about 15-20GB, a swap partition and then a large /home partition. Organise your personal files by means of folders, not partitions.

Lastly, here's a good resource:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Read through all the links in that and you will get a good overview both of concepts and practicalities. Good luck!

---

### Post by ebun2 on 2011-04-23
thank you for your valuable comments - appreciated .... sure I will review the provided additional reading, thanks again.

---

### Post by mabzki on 2011-04-24
> So right on Ubuntu 10.10 when I go to Places > Computer the above D:  and E: drives are separately shown so that I can save/use them as I  prefer. For eg: I may create a folder for movies, studies etc.The reason for that D: and E: drive are shown in Places > Computer, Is because these drives are NTFS filesystems that is the format used by Windows, which does not use in Unix and is a seperated filesystem in Linux. 

You can of course install Linux in NTFS filesystem but these format are not really well suited to Linux, you'd be better off with Ext4 far better than NTFS.

> I am clueless after this stage as to how I should proceed if I need to  partition the remaining disk space into 2 personal disks (example D: and  E: above) which should show in Places > Computer.
If you use "Ext2, 3, 4" format and have 1 or more partitions, with different mounting points eg:"/, home, usr, etc" in Linux it would be in the same filesystem therefore you will only see 1 drive in Places > Computer 

Its not like in Windows where you could have seperated drives in different partitions shown in My Computer. The way it differs from Windows is Linux tends to store its partitions and hardrives in the device directory. 

eg: /dev/sda1 - /dev/sda2 - /dev/sda3 

"Everything is a File in Unix" So everything even hardrives and devices are files that sits inside a single filesystem model.

As for storing data, movies, studies, you can have the /home partition instead, make this large enough for your needs.

Good luck!
 
-- mabzki

---

### Post by ebun2 on 2011-04-24
hi mabzki, thanks for the detailed explanantion, appreciate it a lot, cheers!

---

### Post by mabzki on 2011-04-24
Hi ebun2, No problem I'm also a newbie too in Linux world. ;)

---

### Post by thane1 on 2011-04-24
Another good source:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=%2Fhome+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=%2Fhome+partition)

Cheers

---

### Post by ebun2 on 2011-04-25
hey thanks thane1 .... cheers

---

### Post by K_45 on 2011-04-25
I set up all my systems as:

 / - root, 15GB, ext4, boot + format, primary, beginning of disk, (sda1)      

swap, double your RAM, primary, beginning (sda2)

 /home, ext4, primary, rest of disk. (sda3)

---

### Post by Dutch70 on 2011-04-25
K_45 Swap only needs to be equal to your physical RAM, not double... unless you have very little RAM, as in 512MB, in which case you'd be better off installing a lighter weight distro than Ubuntu IMHO, but some people say they run it fine on 512MB. The recommended minimum is 1GB.
[[COLOR="Red"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

None of the partitions have to be primary. Ubuntu is perfectly happy in a logical partition. Although if it's your only system, I would put / aka "root" in a primary prtn.

---

### Post by oklokl on 2011-04-25
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189968&stc=1&d=1303731754[/IMG]
Manual
{Expand (swap 2G) }

---

### Post by grahammechanical on 2011-04-25
So ebun2, has your question been answered? 

Please let me assure you. I have four partitions on my hard disc and they all show up in the file manager which loads when I click on places. They are not labelled as drive D: or drive E: but by the size or the partition. It is possible to label these partitions but be careful that doing that does not cause you to lose the data in those partitions.

As I see it you have a choice. 1) change the partitions on the hard disc completely to any number and size that you want. 2) use the existing partitions. In this case you could install Ubuntu in the 40GB partition. Give it a mount point of / and mark it to be formatted. You would also need to create some space for a swap partition (Windows uses a swap file) and give it a mount point of /swap. You could shrink the 40GB partition by a few GB. This will leave the two 60GB partitions untouched. Do they have data on them? do not give them a mount point. do not mark them for format.

This is not the most efficient way to use the hard disc but it will give you a working Ubuntu installation and some experience with the partitioner. You could always do another install and be more adventurous. The value of having a separate /home partition is that if you need to re-install you do not lose the data in the /home folder when you re-format. You give the home partition the mount point of /home but you do not mark it to be formatted.

I am sorry if this is a long reply but I remember how nervous I was when I first installed Ubuntu. Think about what you want to do. do not click Install Now until you sure that all the changes are what you want. Once you click Install Now., it will be to late.

Regards.

---

### Post by ebun2 on 2011-04-29
K_45, thank you for the precise explanation - cheers !!!

---

### Post by ebun2 on 2011-04-29
Hi [grahammechanical]("http://ubuntuforums.org/member.php?u=1087323"), thank you for your concerns and the detailed update. Indeed I am still reading and reviewing everyones advice and am rather gradually absorbing some knowledge. thanks again, cheers.

---

### Post by Dutch70 on 2011-04-29
Well, give us some idea where your at & maybe we can give you a little boost. :D

---

### Post by ebun2 on 2011-04-30
Hi Dutch70 (and fellow members),

I was about to provide an update and when I visited the thread, here I see your reply :P
Well all, finally I have got rid of Windows7 completely (no more dual boot) and did a new installation of 11.04 onto my machine as per following specs yesterday: 

My 160GB HD was split as: 

/ 30GB
swap 1 GB
/home 129GB (the remaining)

All seems well and upon installation the "Disk Utility" confirms following:

/
30GB
Ext4
/dev/sda1
mounted at /

swap
1GB
/dev/sda2

/home
129GB
Ext4
/dev/sda3
mounted at /home

I am happy so far and based on above I was expecting (with my limited knowledge ;)) that the Free Space on my home folder should be somewhere 'closer' to 129GB.

But when I open the home folder the shown Free Space is only 112GB (that is 17GB difference).

What could be the reasons for this? 

On the Home Folder there are 9 folders (namely Desktop, Documents, Downloads, Music, Pictures, Public, Templates, Videos and Example). All these folders are empty except for the Examples folder which has 2 files, an audio and a video file. Even if I delete this Examples folder, still the Free Space is showing as 112GB :cry:

Appreciate if someone can shed me some light on this matter .... thanks everyone in advance, cheers!

---

### Post by Dutch70 on 2011-04-30
Nice work ebun2

That's probably what it turns out to be after formatting. 

You have / about twice as big as it needs to be though. It depends on how many programs you want to install & the sizes of the programs, but mine is 15GB and I'm using about 6GB with quite a bit installed. 20GB is really a good size for / IMHO. 10GB is a substantial amount of space if you're working with 160.

Easy way...open Gparted & see how much of your / partition you're using. Depending on how you partitioned, you may be able to resize them easily from the live cd/usb if you decide you want more space for /home.

---

### Post by ebun2 on 2011-05-03
Hi Dutch70,
Thanks for your concerns and suggestions on the probable sizes.
Yes, I am looking at possibly resizing the partitions soon.
Btw I have attached a screenshot of GParted here fyi.
I am still wondering where the additional 17GB dissappeared :D

Cheers all!

---

### Post by Dutch70 on 2011-05-03
Edit: I forgot that you're talking about the reported size in Nautilus. I think that may be a bug. Google for it, you'll see it all over the place. There was a guy in here the other day & his said he had over 100 Terabytes. He only had 2TB. 

Also, the sizes reported in Gparted are "GiB" or "Gibibytes" I believe, which is different than Gigabytes.

If you want to know how much you've got, use Gparted or the command.
```
df -h
```
*This is what I had written before I realized you were talking about Nautilus.*
I believe your hdd space is correct. As I said, that's what you lose to formatting. Have a look at my 2 hard drives. The first one is a 360GB hdd & the 2nd is a 500GB hdd, but they show up as 335.35GB & 465.76GB. There is nothing wrong there.

With that out of the way, notice how my swap partitions are at the far right. Unfortunately, with yours in the middle, you'll have to delete & recreate your swap partition at the far right to recover your space after you shrink /. 
Actually, you'll have...
1. delete swap
2. shrink / down to 15-20GB
3. move /home to the left as far as possible. (this is slow) 
4. grow /home but leave enough space for swap 
5. create a new partition for swap. 

You can create your new swap partition before you grow /home if you shrink swap from the left side, so it doesn't end up in the middle.
Remember this all sounds complicated when you're reading it, but it is so simple if you follow the steps.

---

