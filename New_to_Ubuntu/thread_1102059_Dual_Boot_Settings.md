---
title: "Dual Boot Settings"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-21
Ok, i decided to stick with dual boot so i can use certain programs that wont work on Ubuntu,

What i want is to know the best way to set partition size..

I want Ubuntu to be the main OS that has the most drive space access.

I however do need some windows space in order to run Itunes.. Yahoo messenger and internet sometimes...

I have 4g ram and 320 hdd

How should i manage partitions, i need windows for verry little things... Itunes and yahoo messenger...
What is the best partitions optionns.. How much ram and hdd should i let Windows have?


Thank u all so much

---

### Post by ivanvajar on 2009-03-21
Do you want to store a lot of data on Ubuntu partition?

---

### Post by Skol312000 on 2009-03-21
Yes sir, i want Ubuntu as the main OS... I just want to run Itunes and yahoo messenger once in a while on windows... Thats it... So really i want windowsnto not have more memoru access(either ram or hdd or both) than necessery...

---

### Post by ivanvajar on 2009-03-21
I would suggest 25GB (ext3 filesystem) partition for Ubuntu and 1 swap partition 1GB (I don't think you will EVER need more than that). Everything else can be formated to NTFS partition that you use for data storage.

---

### Post by mikewhatever on 2009-03-21
Go with the manual partitioning option, this way you get to type the sizes of partitions in MBs. As for the main OS, it doesn't make much sense, because when dual booting, the OSs are independent, so that neither is main or secondary, regardless of the drive space each one has.

---

### Post by Skol312000 on 2009-03-21
Ok... Ivan that technical words got me confused man, i dont know what those mean... I now understand about main OS.... Thanks mike forclarifing that for me,

So when i install 64 bit Ubuntu again, how much should i let itnhave? Out of both ram and hdd

---

### Post by ivanvajar on 2009-03-21
There are no RAM issues when dual-booting and Ubuntu will be your default operating system (first in the list of systems).

Boot into LiveCD mode and start partition editor (gparted), shrink your Windows partition and make sure you leave at least 10GB free on it. Everything else you can dedicate to new ext3 partition for your Ubuntu installation.

**ext3** is filesystem for your Linux partition.

---

### Post by taurus on 2009-03-21
I think you are confused about RAM and disk space.  Doesn't matter whether you run windows or Ubuntu x86_64, it will use all your 4GB of RAM so forget about the RAM.  Disk space allocation is what you are concerning right now.

---

### Post by Skol312000 on 2009-03-21
Will it show that ext3 thing?  Choose that?  And let only 10gb fr windows...

How do i choose ext3 thing?

---

### Post by Skol312000 on 2009-03-21
Thank u for making me understand...

---

### Post by linux6994 on 2009-03-21
I am running dual boot for itunes as well. I installed XP on the drive first then Ubuntu second. The installation asked for the partitioning and gaive a 50-50 suggestion on my drive. So I went with it. Then it created and set GRUB up nicely. Works great. Remember Windows first then Ubuntu but only for the install.

---

### Post by suomalainen on 2009-03-21
F.Y.I. but Pidgin messenger also has Yahoo messenger. Now that's one less thing for windows to do for you!

---

### Post by Skol312000 on 2009-03-21
It dowsnt support video chat... But thanks


Why choose windows first?  Grub is nice by default.  It just lets u choose

---

### Post by ivanvajar on 2009-03-21
It goes like this:

1. Boot Ubuntu from CD
2. Open gparted program for managing partitions
3. You will see how much space there is used by Windows.
4. Choose option 'shrink' for your Windows partition and move slider to the left until you are happy with your remaining Window's partition size.
5. On new partition that appears choose 'create' and you will see filesystem option. You use EXT3 for that option.

Is this clear enough so far? :-)

---

### Post by Bölvaður on 2009-03-21
remember to defragment your windows partition atleast 1-2 times before repartitioning. it may speed up the partitioning and avoid dataloss (remember to take backups before doing any formating)

---

### Post by Skol312000 on 2009-03-21
Thank u much for ur help....
Do i chooae the gparted beforeninstalling Ubuntu?

---

### Post by ivanvajar on 2009-03-21
gparted is in System/Administration menu.

---

### Post by ivanvajar on 2009-03-21
> **Bölvaður said:**
> remember to defragment your windows partition atleast 1-2 times before repartitioning. it may speed up the partitioning and avoid dataloss (remember to take backups before doing any formating)

Don't forget this.

---

### Post by presence1960 on 2009-03-21
> Ok, i decided to stick with dual boot so i can use certain programs that wont work on Ubuntu,

What i want is to know the best way to set partition size..

I want Ubuntu to be the main OS that has the most drive space access.

I however do need some windows space in order to run Itunes.. Yahoo messenger and internet sometimes...

I have 4g ram and 320 hdd

How should i manage partitions, i need windows for verry little things... Itunes and yahoo messenger...
What is the best partitions optionns.. How much ram and hdd should i let Windows have?

Skol, I have 250Gb drive and I only use Windows for 2 programs for work. Use the manual partitioner to set up your partitions: here is what my setup looks like: 

```
raz@raz-desktop ~ $ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16840   135267268+  83  Linux
/dev/sda2           16841       19457    21021052+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdb2            2612        4569    15727635   83  Linux
/dev/sdb3            4570       29879   203302575   83  Linux
/dev/sdb4           29880       30401     4192965   82  Linux swap / Solaris



```

sdb1- Xp 20GB
sdb2- Ubuntu 15 GB
sdb3- /home 193 GB
sdb4- swap 4 GB

I made Windows small because I only use it for work.

---

### Post by stalkingwolf on 2009-03-21
to answer a couple of your questions, Windows always wants to be the first system installed.  You can install Ubuntu first and then windows  but this can create issues and get very involved.

I think you said you have windows installed, so just defrag and then resize the partition.

As for yahoo messenger, there is an app that works well and depending on what web cam you are using supports video.  It is Gyachi  here is a link
[http://ubuntuforums.org/showthread.php?t=773802]("http://ubuntuforums.org/showthread.php?t=773802") 
you can download the deb for which ever ubuntu version you are using from the first post.
In 8.04 i have not gotten my cam to work.  In 8.10 it works just fine after adjusting the cam settings.

---

