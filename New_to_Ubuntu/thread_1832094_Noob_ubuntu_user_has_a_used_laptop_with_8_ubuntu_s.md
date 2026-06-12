---
title: "Noob ubuntu user has a used laptop with 8 ubuntu start up options!?"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Foolishtony on 2011-08-24
Hi just got a used laptop from pawn shop with ubuntu on it. I'm new with this but is it supposed to have 6 start up options outside of the normal start up and recovery mode? There is an option for "Previous linux versions" "Memory test(memtest86+)" "Memory test(memtest86+, serial console 115200)" and "Ubuntu (10.10)(on /dev/sda1)" three times. At first this didn't concern me until i noticed that my 150gb was showing 98.5 free space when it was supposedly wiped!! So I looked around here to see what was up and came across the topics of "dual booting" and "partitioning". So i was wondering what are these other options(obviously i didn't pick these out of fear) and they partitioning my hard drive? Can i fix it? And please speak slowly I'm noob.

---

### Post by androssofer on 2011-08-24
> **Foolishtony said:**
> Hi just got a used laptop from pawn shop with ubuntu on it. I'm new with this but is it supposed to have 6 start up options outside of the normal start up and recovery mode? There is an option for "Previous linux versions" "Memory test(memtest86+)" "Memory test(memtest86+, serial console 115200)" and "Ubuntu (10.10)(on /dev/sda1)" three times. At first this didn't concern me until i noticed that my 250gb was showing 98.5 free space when it was supposedly wiped!! So I looked around here to see what was up and came across the topics of "dual booting" and "partitioning". So i was wondering what are these other options(obviously i didn't pick these out of fear) and they partitioning my hard drive? Can i fix it? And please speak slowly I'm noob.

Welcome to the forums!

wen u update and stuff it can add new entries into the list. so the top 1 is the latest and the rest are prob older versions just. nothing to worry about. 

here is a how to on getting it cleaned up. tho read it carefully..

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

to view ur partitions, open the "ubuntu software center" then search for "gparted" and install that. then run it. it will open a nice GUI showing you all the partitions on your hard drive... so u can see wot state its in. if u need, post a screen shot of it and we'll tell u the score. how to clean it up etc if its in bad shape :-)

---

### Post by grahammechanical on 2011-08-24
You might want to consider installing Grub Customizer. It will make it easy to edit that menu that you get. It is very good.

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

Did this computer have another operating system installed? If so there might be partitions that are still there and seeming to take up space even if empty.

What version of Ubuntu do you have? Somewhere there should be a program called Disk Utility. That will give you a visual representation of your had disk.

You might also want to think about doing a complete fresh install of Ubuntu. It might tidy things up a bit. 

Different options.   Regards.

P.S. When you upgrade to a new version of Ubuntu all those entries in the menu for older kernels get removed. We are at 11.04 (2011 April). Soon we will have 11.10 (2011 October). Upgrade to that and things will get a bit more tidy. Older versions of the kernel are useful in case Ubuntu fails to boot. You can then choose one of these older kernels and it will boot. Each kernel takes up less than 25MB

---

### Post by Foolishtony on 2011-08-24
Oh ok thank you i will do the first one now but im at work with no internet on my laptop so ill have to go home on some of it but again thanks.. wow you guys are fast i love this. this is the nicest community i've ever been in.

---

### Post by The Cog on 2011-08-24
Recovery mode drops you into a command prompt where you can try and fix things if they're broken. You would hope not to ever need this. 

The memory tests are just that - a test of the PC memory for reliability - takes ages and just repeats over and over. You might want to run this if the computer keeps crashing for no obvious reason, just to be sure your memory isn't going bad.

The other Ubuntu versions will be slightly earlier versions then the default (which is the latest version). Every time you install an updated kernel, it adds the one being replaced to the list of previous versions. Once you are happy that the new version is reliable, you can delete the older versions (post here to ask how), but it's probably not worth doing until you are more familiar with the system.

As for your missing disk space, a normal Ubuntu system will use around 4G, so I guess the rest is in user files. If you can post the output of these two commands, we can have a look and try to figure out what's going on:
```
df -h
sudo fdisk -l
```
The first command asks for a listing of free disk space, the second will ask for your password (it needs admin rights to read the raw disk), and lists the disk partitions and their sizes.

P.S.
You will find the command prompt in the menu under Accesories->Terminal.

---

### Post by Foolishtony on 2011-08-24
um ok i went to how to geek and followed their instructions and i got rid of the "memtest" stuff but when i went to the synaptic package manager it wouldnt give me the mark for complete removal option or any except mark for instalation.... what does this mean? does it mean its already gone because i went to look at my ubuntu 11 "kernal" it said the same thing also neither has anything in their installed version columb so now im confused as to what im running on. also i looked up the disk utility and it seems it is partitioned and its partioned by another, non-bootable linux. Now i ask, What do???

---

### Post by Foolishtony on 2011-08-24
Gah its like reading chinese i get off work in an hour ill post screen shot then because im really confused at this point

---

### Post by The Cog on 2011-08-24
I assume you are trying to delete the older kernels. See the screenshot. Search for linux-kernel. In my screenshot you can see I have 3 different versions still installed, versions 8, 10&11. So 8 and 10 are candidates for deletion if I could be bothered. Use "Mark for removal" and then click apply. 

The difference with "Mark for complete removal" is that complete removal of an application also deletes the application settings - just removal followed by re-installation will keep the application settings. In the case of the linux kernel, there are no settings files to keep anyway so both types of removal will do the same thing.

---

### Post by Foolishtony on 2011-08-24
here is the screen shot finally but seriously is it weird that none of these have a installed version?

---

### Post by Foolishtony on 2011-08-24
then here is my disk utility it seems to be split by another linux os i think... any ideas?

---

### Post by Foolishtony on 2011-08-25
Ok i have this pawned off thinkpad with Ubuntu on it. This is my first so i have nothing but two days worth of lurking of info on linex computers. What I do know though is that half of my drive is partitioned.(see first screenshot). also that the partitioned half is unbootable, eraseable, formatable, or touchable in anyway by little means of knowlege. I even tried gparted (see second and third screenshots). This both startles me and angers me as i want to someday put windows on this machine for gaming but i can't because of what the last user did(maybe why he pawned it) Please any help will do. but please speak clearly with examples i'm not dumb but new.

---

### Post by fdrake on 2011-08-25
> **Foolishtony said:**
> Ok i have this pawned off thinkpad with Ubuntu on it. This is my first so i have nothing but two days worth of lurking of info on linex computers. What I do know though is that half of my drive is partitioned.(see first screenshot). also that the partitioned half is unbootable, eraseable, formatable, or touchable in anyway by little means of knowlege. I even tried gparted (see second and third screenshots). This both startles me and angers me as i want to someday put windows on this machine for gaming but i can't because of what the last user did(maybe why he pawned it) Please any help will do. but please speak clearly with examples i'm not dumb but new.

basically u want to erase everything? start from 0!?

---

### Post by coffeecat on 2011-08-25
The last user didn't do anything out of the ordinary. You are trying to delete your Ubuntu root partition from within the system. For obvious reasons you can't do that. It's a bit like trying to format your C: drive from within Windows; it can't be done. Look at your 3rd screenshot. There are padlock symbols against the mounted partitions and if a partition is mounted it cannot be modified or deleted.

Use Gparted from a live CD, not from your hard drive installation. When you first open Gparted in the live session right-click on the swap partition(s) and choose "swapoff". They are activated automatically and you won't be able to do much of anything until you de-activate them.

If you need to know how to create a bootable CD from an ISO image, look here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And you might want to read this for partitioning basics:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by The Cog on 2011-08-25
> is it weird that none of these have a installed version?
Search for **linux-kernel**, not linux-headers. You don't need the headers unless you are compiling programs yourself.

Yes, it looks like you have an ext4 primary partition in addition to your root partition on /dev/sda6. Can't tell what's on that primary partition without mounting it to look though.

And for some strange reason, you have two swap partitions.

The output of **sudo fdisk -l** would have been much easier to read than a screenshot of a naff font with half the detail cropped off. Easier to post with copy/paste too.

Afterthought:
The other Ubuntu version the bootloader might be offering you could be the other installation of Ubuntu on the primary partition. In which case, the boot choice screen should say something like "Linux version ???? **on /dev/sda?**"

---

### Post by VOT Productions on 2011-08-25
Simply do a [http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html) from your Windows installation DVD. 
Then burn a CD with Gparted and start it using the BIOS and remove the partition.
It doesn't work IN Ubuntu because the partition is IN use. Imagine you going to put someone's apple in the bin but you couldn't because he is still eating it.

---

### Post by Miljet on 2011-08-25
Is it not also possible that one of those partitions is a separate /home? I think that it would be a good idea at this point to download and run the Boot Info Script from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) Then post the results here.

---

### Post by Foolishtony on 2011-08-25
> **coffeecat said:**
> The last user didn't do anything out of the ordinary. You are trying to delete your Ubuntu root partition from within the system. For obvious reasons you can't do that. It's a bit like trying to format your C: drive from within Windows; it can't be done. Look at your 3rd screenshot. There are padlock symbols against the mounted partitions and if a partition is mounted it cannot be modified or deleted.

Use Gparted from a live CD, not from your hard drive installation. When you first open Gparted in the live session right-click on the swap partition(s) and choose "swapoff". They are activated automatically and you won't be able to do much of anything until you de-activate them.

If you need to know how to create a bootable CD from an ISO image, look here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And you might want to read this for partitioning basics:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
So wait your saying the one i clicked WAS the ubuntu i was operating on? if thats true then what is the other partition? can i delete that? i just want the hard drive space

---

### Post by Foolishtony on 2011-08-25
> **The Cog said:**
> Search for **linux-kernel**, not linux-headers. You don't need the headers unless you are compiling programs yourself.

Yes, it looks like you have an ext4 primary partition in addition to your root partition on /dev/sda6. Can't tell what's on that primary partition without mounting it to look though.

And for some strange reason, you have two swap partitions.

The output of **sudo fdisk -l** would have been much easier to read than a screenshot of a naff font with half the detail cropped off. Easier to post with copy/paste too.

Afterthought:
The other Ubuntu version the bootloader might be offering you could be the other installation of Ubuntu on the primary partition. In which case, the boot choice screen should say something like "Linux version ???? **on /dev/sda?**"
Ok ill upload that as soon as possible but one the afterthought part no i've never seen that when booting..

---

### Post by coffeecat on 2011-08-25
> **Foolishtony said:**
> if thats true then what is the other partition?

Do you mean /dev/sda1?

> **Foolishtony said:**
> 
 can i delete that? i just want the hard drive space

Since it looks to be nearly empty (but I can't see all the details since you've obscured much of the Gparted window in your third screenshot) why not just use it?

---

### Post by Foolishtony on 2011-08-25
> why not just use it?

It wont boot at all for me and i have no clue how to even start trying to figure that out.

---

### Post by nothingspecial on 2011-08-25
You can just use the partition, if its empty. It's actually useful because if one partition becomes corupted for some reason, anything on the other one is safe.

Do us a favour, copy and paste the output of

```
sudo fdisk -l
``` and ```
df -h
```

---

### Post by oxygenfarm on 2011-08-25
I'm in Cincinnati, if you need help.

---

### Post by The Cog on 2011-08-25
Yes it might be a separate /home partition. If it's being mounted, then the output from **df -h** would show that. I did ask for it, but he has chosen not to post it.

---

### Post by The Cog on 2011-08-25
> **nothingspecial said:**
> You can just use the partition, if its empty. It's actually useful because if one partition becomes corupted for some reason, anything on the other one is safe.

Do us a favour, copy and paste the output of

```
sudo fdisk -l
``` and ```
df -h
```

I've already asked him to do that twice in his other thread on the same subject. He won't. 
[http://ubuntuforums.org/showthread.php?t=1832094](http://ubuntuforums.org/showthread.php?t=1832094)

---

### Post by Miljet on 2011-08-25
Or even a peek at the /etc/fstab file.

---

### Post by nothingspecial on 2011-08-25
@Foolishtony

Help us help you.

1. Open a Terminal, if you are using 10.10 it will be under your menus in system > administration.

2. Copy and paste these lines into your terminal

```
df -h
```

```
sudo fdisk -l
```

3. Copy and paste the gobbldygook the terminal spits out back here or in your other thread.

Don't worry about what any of it means if you don't want to, it's just that the screenshots aren't cutting it.

---

### Post by Foolishtony on 2011-08-26
> **The Cog said:**
> I've already asked him to do that twice in his other thread on the same subject. He won't. 
[http://ubuntuforums.org/showthread.php?t=1832094](http://ubuntuforums.org/showthread.php?t=1832094)

Here they are sorry i got really busy and couldnt get back i oppologize. and the first try was a typo sorry

---

### Post by Foolishtony on 2011-08-26
Sorry i actually lost track of this thread and tried to start another one but got side tracked at home but here they are... sorry about the typo

---

### Post by nothingspecial on 2011-08-26
Do you see anything in your file browsers side bar?

"Something GB file system" or similar? If you click it, does anything show up in there?

By the way, when you are asked for the output of a command in the terminal, rather that a screenshot, just copy and paste the output into your post. Then highlight it and click the # at the top of the box you post in, to the left of <>.

---

### Post by Foolishtony on 2011-08-26
```
admin@lodakid-ThinkPad-Edge:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e83c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14987   120375432+  83  Linux
/dev/sda2           14987       30402   123821057    5  Extended
/dev/sda5           29637       30402     6142976   82  Linux swap / Solaris
/dev/sda6           14987       29036   112852992   83  Linux
/dev/sda7           29036       29637     4819968   82  Linux swap / Solaris

Partition table entries are not in disk order
admin@lodakid-ThinkPad-Edge:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             106G   11G   91G  11% /
none                  931M  696K  931M   1% /dev
none                  938M  720K  937M   1% /dev/shm
none                  938M  220K  938M   1% /var/run
none                  938M     0  938M   0% /var/lock
admin@lodakid-ThinkPad-Edge:~$ 

```

---

### Post by cariboo on 2011-08-26
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Foolishtony on 2011-08-26
yes its 250gb file system it says, and yes it has stuff not sure what but it has info there

---

### Post by nothingspecial on 2011-08-26
> **Foolishtony said:**
> yes its 250gb file system it says, and yes it has stuff not sure what but it has info there

What info?

The problem is, it looks like your boot manager is installed on that partition, otherwise I'd suggest formatting it and using it for data. If you have no external drives plugged in, do this, Double click it. Then don't press enter after the this first line

```
cd /media
```

Then without pressing Enter, press the Tab key. If only one option appears press Enter.

Then type

```
ls
```

and post back the output as before.

---

### Post by Foolishtony on 2011-08-27
Umm it gives me 2748 options

---

### Post by nothingspecial on 2011-08-27
Just press it once

---

### Post by Foolishtony on 2011-08-27
ls doesn't do any thing. i put in cd /media, i hit tab twice and it asks show all possibilities then i scroll for awhile to the bottom and then i type in ls and nothing happens

---

