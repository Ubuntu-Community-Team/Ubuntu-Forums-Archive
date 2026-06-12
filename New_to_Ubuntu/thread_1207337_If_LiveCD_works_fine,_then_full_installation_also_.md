---
title: "If LiveCD works fine, then full installation also works?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by ben105 on 2009-07-08
Hi to all,

I am a newbie and many thanks to all who answer to my questions.

I have no idea about Linux (and Windows). Nevertheless, I have bought a Live CD at WHSmith, which offers Ubuntu 9.04 without installation and if I want, I also could install it as partition on my XP. I tested an installation on a virtual XP machine at work yesterday, and it worked fine. After, I was able to launch Ubuntu as well as XP.

Now, I am planing to do the same on my laptop at home.

I read some entries here about problems finding the network or internet connection.

My details: see below

If I launch the Live CD without installation and everything works fine (graphic card and internet are recognised), can I expect that also a full installation as partition on my XP works in the same way?

And 1 additional question: I have 1 hard disk with 2 partions (XP and Data each 75 GB). Free space on both about 50 GB. 
If I install Ubuntu, should I install it on the C:\ partition or on my data partition? 
If I install Ubuntu as its own partition on C:, would I be able to get contact to my Data partition?


Details: 

Acer laptop

Wireless internet connection (no sticky, a friend connected my laptop to the wireless box)

1x Hard Disk: 160 GB, 2 partitions (Windows+Data), Fat32

Display adapter: NVidia GeForce Go 7600

IDE ATA/ATAPI Controllers: Intel (R) 82801GBM/GHM (ICH7-M Family)

IEEE 1394 Bushost Controller: VIA OHCI Compliant IEEE 1394 Host Controller

Acer Obi Cam, Driver provider: Logitech, Version 9.4.4.1082

Network Adapter: 1. 1394 Net Adapter, 2. Broadcom Netlink (TM) Gigabit Ethernet, 3. Intel Pro Wireless 3945ABG Network Connection

PCMCIA adapters: ENE CB-712/714/810 Cardbus Controller

Processors: 2x Intel Core 2 CPU T7200 @ 2GHz

---

### Post by s3a on 2009-07-08
If the live cd works, the chances the installation will work are very high but not guaranteed because of a possible (but unlikely) upgrade that could cause issues.

---

### Post by ben105 on 2009-07-08
Many thanks.

Could you give me a short answer to these questions?

If I install Ubuntu, should I install it on the C:\ partition or on my data partition? 
If I install Ubuntu as its own partition on C:, would I be able to get contact to my Data partition?

May thanks

Ben

---

### Post by frunns on 2009-07-08
I think I've even experienced that the installation have worked better than running it live. Think my wireless didn't work running live, but then when I installed it worked. Something like that, but that was a few versions ago, my point is that it can go either way... But it really shouldn't be any difference!

Edit: You're mixing stuff up a bit now I think... You're both calling C: a partition and hard drive. I'm guessing you have one HDD, let's call it /dev/sda as it might be named. On /dev/sda you got a partition that's named C: from Windows, on the HDD it might be called /dev/sda1, and your data-partition might be /dev/sda2. If you install from Windows with Wubi you can choose either C: or your data-partition. If you install from the live-cd you [probably] have to shrink either /dev/sda1 or /dev/sda2 to make room for Ubuntu on a couple of whole new partitions. Hopefully I've understood you correctly and explained clearly. Just ask if you have further questions!

---

### Post by Paddy Landau on 2009-07-08
> **ben105 said:**
> I have bought a Live CD at WHSmith...
You *bought* a CD? Did you know it's free to download?

> **ben105 said:**
> If I install Ubuntu, should I install it on the C:\ partition or on my data partition?
Let's clear up some misconceptions here.


[LIST]
[*] You have a hard drive. The hard drive is divided into *partitions*.
[*]Each partition can hold something entirely unrelated to each other partition.
[*]At the moment, you probably have two partitions: One holds the Windows recovery partition, and would be invisible to you; the other holds your Windows XP.
[*]The second partition is what you call the C: drive.
[*]You say that you also have a third FAT32 partition. I don't know why you'd want that?
[/LIST]
OK, now...

[LIST]
[*]In Linux, each drive has a name. The first one (most likely your hard drive) has the name sda. Each subsequent device (e.g. external hard drive; USB flash drive) would have the names sdb, sdc, and so on.
[*]Each partition on the drive has a number. So, your existing hard drive is most likely called sda, and it would have three partitions. The first, sda1, holds your Windows recovery (I'm assuming here; yours may be a little different). The second partition, sda2, holds your Windows XP. The third, sda3, your FAT32 partition.
[/LIST]
About installing...

[LIST]
[*]To install, you'd want to shrink your Windows partition (sda2) to make room for two new partitions. I question your FAT32 partition; perhaps you want to move your data onto your Windows partition and delete your FAT32.
[*]So, as a recommendation, I'd make about half the space available to Windows XP. Then, create a swap partition. I don't know how much RAM you have, but I'd suggest a little larger than your RAM, but at least 1Gb. Also create your Linux partition, filling the rest of the space.
[*]In summary, this is what I suggest:
[LIST=1]
[*]sda1: Your existing Windows recovery partition. Don't mess with this one.
[*]sda2: Your existing Windows XP partition, but shrunk to about half its existing size. Also put your FAT32 data into this partition, and delete the FAT32 partition.
[*]sda3: Your swap partition, about 1Gb (or larger if you have more RAM).
[*]sda4: Your Linux partition, filling the rest of the space.
[/LIST]
 
[/LIST]
If you have more than four partitions, things get a bit more complicated.

Look around these forums to find the best way to clean up your Windows XP before proceeding.

BACK UP YOUR DATA FIRST! Although the Ubuntu installation is unusually safe, things can nevertheless go wrong.

When you install Ubuntu, it will allow you to shrink the Windows partition and create the new partitions. Because of your FAT32 partition, you'll need to work through the manual process.
> **ben105 said:**
> If I install Ubuntu as its own partition on C:, would I be able to get contact to my Data partition?
Ubuntu will automatically see your Windows XP partition and allow you access to it.

Windows, on the other hand, won't allow access to your Linux partition unless you download a program. I suggest [Ext2Fsd]("https://sourceforge.net/projects/ext2fsd/files/").

---

### Post by Sef on 2009-07-08
> You *bought* a CD? Did you know it's free to download?

Sometimes it is better to buy, e.g., you are on dial up, limited in how much you can download, or are charged a per minute fee for internet use.

---

### Post by Paddy Landau on 2009-07-08
> **Sef said:**
> Sometimes it is better to buy, e.g., you are on dial up, limited in how much you can download, or are charged a per minute fee for internet use.
True. I think I forgot how much I take for granted where I live!

---

### Post by ben105 on 2009-07-08
> **Paddy Landau said:**
> You *bought* a CD? Did you know it's free to download?


Let's clear up some misconceptions here.


[LIST]
[*] You have a hard drive. The hard drive is divided into *partitions*.
[*]Each partition can hold something entirely unrelated to each other partition.
[*]At the moment, you probably have two partitions: One holds the Windows recovery partition, and would be invisible to you; the other holds your Windows XP.
[*]The second partition is what you call the C: drive.
[*]You say that you also have a third FAT32 partition. I don't know why you'd want that?
[/LIST]
OK, now...

[LIST]
[*]In Linux, each drive has a name. The first one (most likely your hard drive) has the name sda. Each subsequent device (e.g. external hard drive; USB flash drive) would have the names sdb, sdc, and so on.
[*]Each partition on the drive has a number. So, your existing hard drive is most likely called sda, and it would have three partitions. The first, sda1, holds your Windows recovery (I'm assuming here; yours may be a little different). The second partition, sda2, holds your Windows XP. The third, sda3, your FAT32 partition.
[/LIST]
About installing...

[LIST]
[*]To install, you'd want to shrink your Windows partition (sda2) to make room for two new partitions. I question your FAT32 partition; perhaps you want to move your data onto your Windows partition and delete your FAT32.
[*]So, as a recommendation, I'd make about half the space available to Windows XP. Then, create a swap partition. I don't know how much RAM you have, but I'd suggest a little larger than your RAM, but at least 1Gb. Also create your Linux partition, filling the rest of the space.
[*]In summary, this is what I suggest:
[LIST=1]
[*]sda1: Your existing Windows recovery partition. Don't mess with this one.
[*]sda2: Your existing Windows XP partition, but shrunk to about half its existing size. Also put your FAT32 data into this partition, and delete the FAT32 partition.
[*]sda3: Your swap partition, about 1Gb (or larger if you have more RAM).
[*]sda4: Your Linux partition, filling the rest of the space.
[/LIST]
 
[/LIST]
If you have more than four partitions, things get a bit more complicated.

Look around these forums to find the best way to clean up your Windows XP before proceeding.

BACK UP YOUR DATA FIRST! Although the Ubuntu installation is unusually safe, things can nevertheless go wrong.

When you install Ubuntu, it will allow you to shrink the Windows partition and create the new partitions. Because of your FAT32 partition, you'll need to work through the manual process.

Ubuntu will automatically see your Windows XP partition and allow you access to it.

Windows, on the other hand, won't allow access to your Linux partition unless you download a program. I suggest [Ext2Fsd]("https://sourceforge.net/projects/ext2fsd/files/").


Many thanks for all information.

Let's make it clearer: I've got 1 hard disk

This 1 hard disk is filled with:  

1x 4.88 GB Fat 32 PQSERVICE (that backup things for XP)
1x 71.84 GB FAT 32 Windows XP C:\
1x 72.33 GB FAT 32 DATA D:\

As far as I understood you correctly, I should put my data onto an extern drive/or C:\, so that my D:\ is empty for Linux plus swap. This is a solution which I not really prefer, because I like to have XP and data on 2 different partitions.

Yesterday, while testing the procedure on a virtual machine, I manually shared that one partition (original XP, no backup partition) into 3 partitions (XP, Ubuntu and swap).

If it's a problem to have 5 partitions, then I have to think about this. I hoped I can put the Ubuntu and Swap on the XP partition, and can see my DATA partition also in Ubuntu, so that it's not necessary to put the same data again into Ubuntu.

Let me mention that -of course- there is a live CD online, but it doesn't have such a nice 100-page guide for dummies like me. I am a newbie and I have found some interesting things like (don't laugh) how to get the directories/bin on the desktop like in Windows.

Nevertheless, many thanks for all answers!

---

### Post by random turnip on 2009-07-08
Basically yes, if everything worked in the "try Ubuntu without any change to my computer" option on the live CD, after you have ran all updates after the installation it will run the same but faster.

---

### Post by frunns on 2009-07-08
> I hoped I can put the Ubuntu and Swap on the XP partition, and can see my DATA partition also in Ubuntu, so that it's not necessary to put the same data again into Ubuntu.

Yeah, you can put it on the PARTITION in two ways, format it as ext3 or the filesystem of your choice (losing the XP installation ofc) or using Wubi which installs it on the Windows-partition of your choice, but I'm not that acquainted with Wubi so I'd go for something other than that.
Do you see what I'm trying to say? You don't want it on the same partition. 

Defrag either partition a few times (preferably the C: drive probably, as you might have more data than games and programs), boot up Ubuntu, shrink the partition (data loss can occur), and create an extended partition from the freed up space (in which you can create even more partitions!) in which you create swap, /home and /. This is probably how I'd do it, or something fairly similar.

---

### Post by carml on 2009-07-08
You can perform a full install into two ways: 1) you want to try Ubuntu,but you're not sure you'll use it often or don't want to mess your partition.If so boot with Windows and then insert the cd and select to install via Wubi,so Ubuntu will be seen as one of your software by Windows and you'll be able to remove it easily if you don't want it anymore.
2) Shrink C or D giving at least 5 or 6 GB of space,you can perform this action within the LiveCd when you boot directly from the boot. 
If you need more explanations,just ask and someone will answer you :).

---

### Post by ben105 on 2009-07-08
> **frunns said:**
> Yeah, you can put it on the PARTITION in two ways, format it as ext3 or the filesystem of your choice (losing the XP installation ofc) or using Wubi which installs it on the Windows-partition of your choice, but I'm not that acquainted with Wubi so I'd go for something other than that.
Do you see what I'm trying to say? You don't want it on the same partition. 

Defrag either partition a few times (preferably the C: drive probably, as you might have more data than games and programs), boot up Ubuntu, shrink the partition (data loss can occur), and create an extended partition from the freed up space (in which you can create even more partitions!) in which you create swap, /home and /. This is probably how I'd do it, or something fairly similar.


Many thanks! What you call Wubi, I think, is part of that LiveCD I bought. I got the choice to overwrite XP or "Specify partitions manually". After I reduced the XP partition from 10 GB (it was only a VMw) to 6 GB, gave Ubuntu 3.5 and SWAP 501 MB as recommended in that guide I got with the LiveCD.

I have only the OS+programs on C:\ and have defrag it yesterday. I made backups of all data and Windows told me, my DATA drive doesn't need to be fragmented. 

My laptop has got 2 GB RAM, so that I could advise SWAP about 1 GB. Because I don't need much more for my XP, I will give Ubuntu 20 GB.

---

### Post by Paddy Landau on 2009-07-08
> **ben105 said:**
> 1x 4.88 GB Fat 32 PQSERVICE (that backup things for XP)
1x 71.84 GB FAT 32 Windows XP C:\
1x 72.33 GB FAT 32 DATA D:\
The Windows XP (C:) and data (D:) are FAT32. That's strange, as XP and Vista are optimised for NTFS.

> **ben105 said:**
> If it's a problem to have 5 partitions...
No, it's not a problem. It just requires more explanation, as it's not quite that straightforward.

You can have only four partitions; but if you make one (or more) of them an 'extended' partition, then you can put partitions inside of them. That's how you get more than four.

Usually, but not necessarily, you want bootable partitions (XP and Ubuntu) as normal ones; the swap and data partitions are perfectly happy inside extended partitions. Don't mess with your PQSERVICE partition, unless you're absolutely sure you'll not want Windows on your machine again.

> **ben105 said:**
> I hoped I can put the Ubuntu and Swap on the XP partition...
That doesn't make sense. PQSERVICE, XP, swap, Ubuntu and data each needs its own partition.

> **ben105 said:**
> ... and can see my DATA partition also in Ubuntu, so that it's not necessary to put the same data again into Ubuntu.
Remember what I put in the [previous post]("http://ubuntuforums.org/showthread.php?p=7580422#post7580422"): Your Ubuntu and Windows ***can*** see the other partitions. In my case, I've converted almost completely to Ubuntu, so all my data is in my Ubuntu partition. In the (very) rare cases that I want to access the data from Windows, I do so with ease.

The reason that I suggested getting rid of the data partition was twofold:

[LIST=1]
[*]The Windows operating system takes a lot of space, and your disk drive isn't all that large. Thus, putting all the data into your Windows partition will save some space.
[*]It's formatted as FAT32, which is not the most optimum. For Windows, the optimum is NTFS; for Ubuntu, it's ext3.
[/LIST]
 
I strongly recommend that you put the data onto the Windows XP partition; get rid of the data partition; and install Ubuntu.

If, later, you find (like me) that you want to convert everything to Ubuntu, then you simply move all your data from the Windows partition onto your Ubuntu partition, and you can change the partition sizes to suit. (You can always shrink and expand partitions later.)

---

### Post by joshedmonds on 2009-07-08
I don't mean to be disagreeable, but I'm going to agree with Paddy for an entirely different reason.

I personally think a shared FAT partition is the best idea for shared data. It mounts easily, everyone can get access to it (does Windows support EXT read/writes?) and you don't have permission problems (I know, you also don't have permission solutions).

The reason you need to get rid of the FAT partition is that you won't be able to create another primary partition for your Ubuntu root (assuming Paddy is correct, that it should be on a primary partition) without changing the existing structure.

I would copy all of the personal files e.g. my documents type folders from Windows onto the data partition, defrag the Windows partition (again) then backup everything on the data partition (twice!!), and create a partition table approximately:

sda1    5gb    Windows recovery (unchanged)
sda2    ~20gb (as small as you can get it plus about 5 gb)    Windows
sda3    10gb   Delete the data partition and create Ubuntu root partition (ext4)
sda5    extended partition, no data here
...sda6    everything except the swap space    FAT filesystem for shared data
...sda7    swap space

Thoughts?

EDIT: I also don't mind Paddy's reasoning of being able to get rid of Windows later, but I've used Ubuntu exclusively for about a year, and I still can't bring myself to delete an operating system that only costs me a bit of space to keep around. You never know when that latent XP install will make your PC saleable at the least.

---

### Post by frunns on 2009-07-08
> **ben105 said:**
> Many thanks! What you call Wubi, I think, is part of that LiveCD I bought. I got the choice to overwrite XP or "Specify partitions manually".

As carml mentions in the post previous to your's, Wubi installs just like a program in Windows and doesn't need to change your partitioning. What you mention with overwrite XP and "Specify partitions manually" is just the normal installation.

I get the feeling we've complicated this for you now. Backup, try, fail, learn. :guitar:

---

### Post by Paddy Landau on 2009-07-08
> **joshedmonds said:**
> does Windows support EXT read/writes?
Yes, it does. The best driver that I've found is [Ext2Fsd]("http://sourceforge.net/projects/ext2fsd/files/"). It even handles without hesitation my external hard disk drive, which I formatted as ext3. No permission problems!

> **joshedmonds said:**
> The reason you need to get rid of the FAT partition is that you won't be able to create another primary partition for your Ubuntu root (assuming Paddy is correct, that it should be on a primary partition) without changing the existing structure.
In my experience, you in fact can have Ubuntu on a shared partition. I've read that some computers won't boot off one.

Your suggestion is fine if you want a separate data partition. However, I suggest two changes:

[LIST=1]
[*]I would format the data partition as either NTFS (if the primary access is from Windows) or ext3 (if the primary access is from Linux), for performance reasons. FAT32 can also give errors with large files (4Gb or more).
[*]Use ext3, not ext4, as the latter is not yet fully debugged. (I believe that the next version of Ubuntu will have a fully debugged ext4.)
[/LIST]
 If the OP later converts to Ubuntu, then it would make sense to have the /home directory mounted on the data partition. It would be better integrated with Ubuntu. But that's for later!

> **joshedmonds said:**
> I also don't mind Paddy's reasoning of being able to get rid of Windows later, but I've used Ubuntu exclusively for about a year, and I still can't bring myself to delete an operating system that only costs me a bit of space to keep around. You never know when that latent XP install will make your PC saleable at the least.
True. Also, you may have some occasion to run a Windows program that won't successfully load on Wine. (For the OP, Wine allows you to run Windows programs under Linux, but it does have its faults and limitations.)

EDIT: Ext2Fsd doesn't (yet) handle ext4, so that's another reason to stick with ext3.

---

### Post by ben105 on 2009-07-08
> **Paddy Landau said:**
> The Windows XP (C:) and data (D:) are FAT32. That's strange, as XP and Vista are optimised for NTFS.

That doesn't make sense. PQSERVICE, XP, swap, Ubuntu and data each needs its own partition.



That I got FAT 32 partitions is strange but I live in the UK and there are many things strange. You can buy here Vista machines with 1 GB RAM :p

Of course, each partition gets its own partition. I have currently 2 partitions (I would never touch that backup things). Now I have to make a decision. Either I can reduce the C: partition, which worked perfectly yesterday, or I can reduce the D: partition. 

I will never run out of space on C:, because I don't do change anything there. If I burn a DVD, then perhaps I will need about 5 GB. 

Currently it uses 19 GB. Therefore, 40 GB all in all for C:\ should be enough. I give now Linux and Swap the other space, it shouldn't be a problem.

---

### Post by Paddy Landau on 2009-07-08
> **ben105 said:**
> I live in the UK
I gathered, with your reference to WH Smith. I live in the UK too.

> **ben105 said:**
> I will never run out of space on C:, because I don't do change anything there. If I burn a DVD, then perhaps I will need about 5 GB. 

Currently it uses 19 GB. Therefore, 40 GB all in all for C:\ should be enough. I give now Linux and Swap the other space, it shouldn't be a problem.
So, I suggest that you shrink the C: partition, not your data partition.

Before doing so, do a Disk Cleanup. I recommend that you also install CCleaner and run it. Also run a full defrag.

In short, you'll want the following sizes:

[LIST=1]
[*]PQSYSTEM: Leave this alone.
[*]Windows XP: 24Gb (19Gb plus 5Gb spare).
[*]Swap file: 1GB (1,024Mb), or your RAM size if larger.
[*]Ubuntu: 12Gb should suffice if you don't store your data here.
[*]Data partition: The remaining space.
[/LIST]
If possible, back up all your data, reformat your data partition as NTFS (if you primarily use Windows) or ext3 (if you'll primarily use Ubuntu), and restore your data. Be sure that your data is fully and safely backed up first!

---

### Post by ben105 on 2009-07-08
> **Paddy Landau said:**
> 

Before doing so, do a Disk Cleanup. I recommend that you also install CCleaner and run it. Also run a full defrag.

If possible, back up all your data, reformat your data partition as NTFS (if you primarily use Windows) or ext3 (if you'll primarily use Ubuntu), and restore your data. Be sure that your data is fully and safely backed up first!

I don't have many data and I always copy them on a regular basis. I will clean the system, and defrag again and then, I am curious. If it doesn't work, then I only have to reinstall my system.

Many thanks!!!

---

### Post by frunns on 2009-07-09
> **ben105 said:**
> I don't have many data and I always copy them on a regular basis. I will clean the system, and defrag again and then, I am curious. If it doesn't work, then I only have to reinstall my system.

Many thanks!!!

That's the spirit! :)

---

### Post by ben105 on 2009-07-10
Yesterday I wanted to test the LiveCD, but it failed, because this LiveCD is one of the eco-disk  with a warning "don't put into a Mac slot". My Acer laptop also has a slot system and a copy  of course is not bootable. We tested it on another a 1GB-RAM computer without Internet. It worked absolutely fine (and I had a WOW effect when I saw the speed of the OS) and again, I felt inspired to try Ubuntu.
Because of my strange laptop, which I won't damage, I'm going to buy another one for testing everything. I read that the Acer 5735Z-423G works with Ubuntu 9.04, also the WIFI is recognised.

Thanks too all, I have learned so much (about Windows and FAT32:p)

---

### Post by Paddy Landau on 2009-07-10
> **ben105 said:**
> I'm going to buy another one for testing everything...
These days, you can buy computers with Ubuntu pre-installed (my last purchase had Ubuntu Hardy 8.04 pre-installed. I reinstalled Jaunty netbook remix without a hitch).

That way, you know that the hardware is compatible and that the manufacturer covers it in its warranty. (If you load Ubuntu onto a Windows machine, the manufacturer usually won't cover the hardware in the warranty.)

It's also cheaper (mine was 24% cheaper than the Windows version), because you don't pay for the Windows or Mac operating system.

And easier; you're up-and-running within minutes.

Faster too, because there's no antivirus and antimalware slowing down the system.

---

### Post by egalvan on 2009-07-10
> **Paddy Landau said:**
> You *bought* a CD? Did you know it's free to download?


> **Sef said:**
> Sometimes it is better to buy, e.g., you are on dial up, limited in how much you can download, or are charged a per minute fee for internet use.

Another reason to buy is that some cash is (at times) forwarded  to the software authors/maintainers.

It's always nice to support the folks who support our Linux!

Notice my signature line.

ErnestGalvan

---

### Post by frunns on 2009-07-10
> **Paddy Landau said:**
> Faster too, because there's no antivirus and antimalware slowing down the system.

Not to mention all bloatware they feel the need to install...

---

### Post by ben105 on 2009-07-11
> **egalvan said:**
> Another reason to buy is that some cash is (at times) forwarded  to the software authors/maintainers.

It's always nice to support the folks who support our Linux!

Notice my signature line.

ErnestGalvan

I also thought it, when I bought the DVD at a reseller like WHSmith and £10 doesn't cost the world.

@Paddy Landau: I looked for a Linux laptop, but I only found netbooks. 

I bought this laptop and S**t Vista is now working and I'm going to install Ubuntu tomorrow. I have to admit, I have to learn how Vista works for professional reasons. There is not enough time at work. Vista Laptops are very cheap at the moment or you pay 200 more for upgrade eligibility , which is the real Windows 7 upgrade price. I asked regarding the guarantee and I was told that as long as I install Ubuntu on D: my warranty will not run out.

It must be depressing for MS that we use the IE to download another browser and their OS to install another OS:lolflag:

---

### Post by Mornedhel on 2009-07-11
> **ben105 said:**
> I was told that as long as I install Ubuntu on D: my warranty will not run out.

Does this include GRUB, which would by default be installed on the first hard drive ? I'd be careful if I were you.

---

### Post by LewRockwell on 2009-07-11
> **ben105 said:**
> I also thought it, when I bought the DVD at a reseller like WHSmith and £10 doesn't cost the world.

@Paddy Landau: I looked for a Linux laptop, but I only found netbooks. 

I bought this laptop and S**t Vista is now working and I'm going to install Ubuntu tomorrow. I have to admit, I have to learn how Vista works for professional reasons. There is not enough time at work. Vista Laptops are very cheap at the moment or you pay 200 more for upgrade eligibility , which is the real Windows 7 upgrade price. I asked regarding the guarantee and I was told that as long as I install Ubuntu on D: my warranty will not run out.

It must be depressing for MS that we use the IE to download another browser and their OS to install another OS:lolflag:

as long as you have the recovery/re-installation CD/DVD/etc. then I wouldn't worry too much about making changes, it is your machine after all...

Microsoft may not be fully aware of it yet, but their days of marketplace dominance are numbered...one way or another...

I honestly look for them to move their corporate headquarters to their new facility in Canada in the not too distant future...

(you didn't hear that from me!)

.

---

### Post by susanw on 2009-07-11
ecodisc in a mac -->

When I found out about the 'do not put ecodisk into apple mac,' it was just after I'd successfully ran a program on my mac but failed to get it out of the mac... Program on the disk worked fine and you can get it out but it's tricky (thus only your final resort)- google gave me solution of using another ecodisk! to hold mecanism open while ejecting the first disk. Whilst firmly holding onto second disk so it didn't also get swallowed I pressed eject causing the first disk to fly out of the mac across the room!

---

### Post by FoxFireX on 2009-07-11
Boot into windows, back up any data you have to an external drive or another internal drive if you have one, If not back up your data to the data drive,

What I would do is,
Format drive C and the backup drive for window, you don't really need that, usually that comes with computers that are store bought. So its not a clean install of XP you get you get it bundled with software.

Anyway, format C and the backup drive.
and you will have partition D, and Unpartitioned space which would previously be C.

Make 1 new partition, for windows as ntfs.

If your hard drive is 100GB for example give windows 50GB partition size, and your remaining free space will be 50GB, don't format the unpartitioned space.

Pop the Ubuntu CD in and install ubuntu on the free space.

Now you will have a dual boot, of XP and Ubuntu.

Private Message me if you need help obtaining a windows xp cd.

---

### Post by LewRockwell on 2009-07-11
> **susanw said:**
> ecodisc in a mac -->

When I found out about the 'do not put ecodisk into apple mac,' it was just after I'd successfully ran a program on my mac but failed to get it out of the mac... Program on the disk worked fine and you can get it out but it's tricky (thus only your final resort)- google gave me solution of using another ecodisk! to hold mecanism open while ejecting the first disk. Whilst firmly holding onto second disk so it didn't also get swallowed I pressed eject causing the first disk to fly out of the mac across the room!

ecodisk, what a joke(IMHO, if it can't be used in EVERY optical drive...then it should never have been produced to begin with)

I refuse to use/buy them strictly on that principle alone

.

---

### Post by servicetech on 2009-07-11
> **LewRockwell said:**
> as long as you have the recovery/re-installation CD/DVD/etc. then I wouldn't worry too much about making changes, it is your machine after all...

**Microsoft may not be fully aware of it yet, but their days of marketplace dominance are numbered...one way or another...**

I honestly look for them to move their corporate headquarters to their new facility in Canada in the not too distant future...

(you didn't hear that from me!)

.

As long as Windows comes preinstalled on most store bought machines MS has nothing to worry about. Few people change the OS that comes with the computer when they buy it. When manufacturers start offering ubuntu on new machines in stores for $100 less than their Windows counterparts MS will have some problems. I can see manufacturers using ubuntu to create 'loss leader" computers, knocking $100 off a $300 computer will make MS dance for their money ;)

---

### Post by ben105 on 2009-07-12
Obviously, my last replay was deleted by myself.

I am just testing the LiveCD and (I am so proud) also the Internet works.

My connection was listed but it didn't connect. I tested a new connection, didn't work. Then I discovered "Edit" and I deleted my new connection and checked the key for the existing one. Only the key was wrong and I changed it.

Now, I am going to install Wubi inside of Vista (so that I will not loose my guarantee). Data backup wasn't necessary, it's a brand new machine and no data ore on it.


Thanks to all for sharing your ideas with me.):P

---

### Post by Paddy Landau on 2009-07-12
> **FoxFireX said:**
> Boot into windows, back up any data you have to an external drive or another internal drive if you have one, If not back up your data to the data drive,

What I would do is,
Format drive C and the backup drive for window, you don't really need that, usually that comes with computers that are store bought. So its not a clean install of XP you get you get it bundled with software.

Anyway, format C and the backup drive.
and you will have partition D, and Unpartitioned space which would previously be C.

Make 1 new partition, for windows as ntfs.

If your hard drive is 100GB for example give windows 50GB partition size, and your remaining free space will be 50GB, don't format the unpartitioned space.

Pop the Ubuntu CD in and install ubuntu on the free space.

Now you will have a dual boot, of XP and Ubuntu.

Private Message me if you need help obtaining a windows xp cd.
Bearing in mind the OP's need to learn Vista and to keep the warranty valid, that's probably a bad idea.

It would be best to do a standard Ubuntu install on his machine, putting it onto the partition that currently acts as the D: drive. It's a heck of lot simpler like that, anyway. It will leave his Windows installation intact.

@ben105:

Post the results of [FONT=Courier New][SIZE=2]sudo fdisk -l[/SIZE][/FONT] (that's the letter l, not the digit 1), to double-check the partitions.

I've just noticed your last post: If you use Wubi, you could put the Wubi disk in the D: partition for space reasons. Bear in mind that Wubi does have some limitations and is not as reliable or as fast as a native installation.

---

### Post by Chronon on 2009-07-12
> **Paddy Landau said:**
> The Windows XP (C:) and data (D:) are FAT32. That's strange, as XP and Vista are optimised for NTFS.


Yes, but you could easily end up with this situation if you upgraded from Windows 98/ME, for example.

---

### Post by -kg- on 2009-07-12
> Bearing in mind the OP's need to learn Vista and to keep the warranty valid, that's probably a bad idea.

It would be best to do a standard Ubuntu install on his machine, putting it onto the partition that currently acts as the D: drive. It's a heck of lot simpler like that, anyway. It will leave his Windows installation intact.

+1  So many ideas!

I am assuming that the new laptop you bought has two internal hard drives, which you are indicating as "C:" and "D:".  The letters normally indicate partitions, and considering that you have just bought this laptop and have a "C:" and "D:" partition, that would likely be a valid assumption.

> Post the results of sudo fdisk -l (that's the letter l, not the digit 1), to double-check the partitions.

One thing that Paddy Landau forgot to tell you (in case you don't know) is that this is a Linux command.  You will need to boot to the Ubuntu Live CD to the desktop, launch the terminal (Applications/Accessories/Terminal...I forgot the keystrokes to launch it) and type that command into the terminal.

This will list your partitions and tell us whether these partitions are on one hard drive or two separate hard drives.  If they are on one hard drive, then both partitions will be indicated as on "sda"...one will be sda0 (or sda1, with the addition of a recovery partition) and the other will be sda1 (or sda2 in the other circumstance).  If they are separate hard drives, then the "C:" drive will be sda0 (or sda1) and the "D:" drive will be listed as sdb0.

It will help you if you read the "How To Partition" page in the Community Wiki.  You can access it from the link in my signature block.  This will show you what you are doing and what you need to do.

I am assuming that, since they said that you can install Ubuntu on your "D:" drive to maintain your warranty, that they meant that you can install it on your slave (2nd) drive, which contains the "D:" partition.  In that case, you can shrink that partition and install Ubuntu on that partition.  You should be able to shrink that partition using the Ubuntu installer, but I would do it a different way, to make it much safer.

I personally would boot to the Live CD to the desktop.  Launch the GPartEd partition editor (System/Administration/Partition Editor).  There have been problems shrinking the OS partition ( C: ), but since you have little or no files in the "D:" partition at this point, there should be absolutely no problem in shrinking that partition.

Following the guidelines in "How To Partition," shrink that partition to whatever size you desire.  I would give myself around 20-25 GB of space if possible; more if you can and desire.  Personally, I would then create an Extended partition in that space.  It will hurt nothing, and Linux will totally boot and run from an Extended partition.

Then once you apply the changes, close GPartEd and launch the installer from the Ubuntu desktop.  Once you get to the "Prepare Disk Space" screen you will be presented with four radio button selections:

o Install them side by side

o Use the entire disk

o Use the largest contiguous free space

o Specify partitions manually (Advanced)

Select the "Use the largest contiguous free space" selection (you just created the free space to use), and the installation will continue.  From there just select the default options, insert your desired user name and password (for safety sake, make it a fairly secure password, and DON'T forget it! :p ) and the installer will install it for you on your secondary hard drive.  It will also install GRUB (the GRand Unified Bootloader) into your MBR and autodetect your Vista installation, allowing you to boot into Vista as well as Ubuntu.

What ever you do, make _sure_ that you don't have "Use the entire disk" selected!  That will delete all the partitions and install Ubuntu, deleting your Vista partitions.  You probably don't want the "side-by-side" selection either.  I've never used it (I do my partitioning manually), but it's possible that it might shrink your Vista "C:" drive, which has caused booting problems with Vista.

Too bad you couldn't have put it on your XP computer.  There have been virtually no problems with partitioning with XP partitions.  It can be done with Vista, though.  You just have to follow a bit of a routine, and if you have a secondary hard drive, it's a piece of cake, really.

<edit>  You know, I just had a thought:  Boot into Vista, launch Windows Explorer, and check out the "D:" drive.  If there is indeed no files on "D:", then it will simplify things considerably.

If there is indeed no files on that drive, then you won't need to resize it.  Just delete it.  Deleting a partition is *much* faster than resizing it.  Then create an Extended partition in that free space and, if desired, recreate the "D:" partition as a Logical partition inside it, to the size desired and leaving the necessary free space.  Windows will access a Logical partition easily, and you can then install Ubuntu into the remaining free space on Logical partitions.

---

### Post by ben105 on 2009-07-12
I am installing that Wubi things, but to be honest, it will take more than 5 hours. That's not the only problem I have. It's downloading an amd64.iso, and I am asking myself why the hell does that wubi things download something what I defintely not have/need? I have Intel 32bit.

The other thing is that I had to leave house for 1 hour. When I came back, the laptop was in Sleep Modus, and also the internet connection seemed to have a nap. Now, the installer is still running, but it keeps remaining "approx. 4 hours 44 min" since 20 minutes and doesn't seem to move.

I bought this laptop only for testing, however, keeping Vista is not the priority. Therefore I am stopping this Wubi installation and begin installing from the Live CD, which worked perfectly this morning.

---

### Post by ben105 on 2009-07-12
> **-kg- said:**
> +1  So many ideas!

This will list your partitions and tell us whether these partitions are on one hard drive or two separate hard drives.  If they are on one hard drive, then both partitions will be indicated as on "sda"...one will be sda0 

There is defintively 1 HD with (3) 2 partitions. 

I have done the same installation on a virtual machine and didn't have a problem.  Okay, I installed Ubuntu to XP on the same partition. Now, I am installing Ubuntu on its own partition.  I am sure about what I am doing and begin now to install from the CD.

---

### Post by ben105 on 2009-07-12
I have done it. I installed Ubuntu with that Live CD inside of Windows (to be honest, I didn't see this morning at 5! that this LiveCD also has this Windows Installer). 

Now, Ubuntu is on D:\ 

Everything works fine, Internet connection worked immediately. 
I can launch Vista and Ubuntu with the Windows booter. 


Thank you so much for all help and ideas. :guitar:

---

### Post by Paddy Landau on 2009-07-12
> **-kg- said:**
> One thing that Paddy Landau forgot to tell you ... is that this is a Linux command.
Oops! :oops:

> **ben105 said:**
> I can launch Vista and Ubuntu with the Windows booter. 
I'm glad that you got everything sorted.

I found that doing it was much easier than I had expected, because I was so accustomed to Windows' complicated way of doing things.

---

### Post by ben105 on 2009-07-12
> **Paddy Landau said:**
> Oops! :oops:


I'm glad that you got everything sorted.

I found that doing it was much easier than I had expected, because I was so accustomed to Windows' complicated way of doing things.

Thank you! I am also glad. It took all in all 30 minutes and was like installing a Windows program on a Windows machine.

By the way, I spent the afternoon reading in my 100-page guide and I can't find again this note about getting the bin on the desktop. 


I have sooo much to learn.

---

### Post by Paddy Landau on 2009-07-12
> **ben105 said:**
> I can't find again this note about getting the bin on the desktop.
I'm not quite sure what you mean. If you want the wastebasket on your panel (not on your desktop), then:

[LIST=1]
[*]Right-click your panel.
[*]Select Add to Panel...
[*]Scroll down to Deleted Items and click it.
[*]Press Add.
[*]Close.
[/LIST]

---

### Post by ben105 on 2009-07-12
I wanted to get the basket (and other folders like home) on the Desktop (like in Windows).

By the way, I am writing in Ubuntu with Seamonkey :)

---

### Post by LewRockwell on 2009-07-12
> **ben105 said:**
> I wanted to get the basket (and other folders like home) on the Desktop (like in Windows).

By the way, I am writing in Ubuntu with Seamonkey :)

whatever floats your boat...lol.

.

---

### Post by Paddy Landau on 2009-07-13
> **ben105 said:**
> I wanted to get the basket (and other folders like home) on the Desktop (like in Windows).
I think you'll find that Ubuntu's way is a bit easier, but still, if you want the icons:


[LIST=1]
[*]Right-click your desktop.
[*]Choose Create Launcher...
[*]*Type:* Application.
[*]*Name:* Any name you like (e.g. home, wastebasket).
[*]*Command:* **nautilus <directory>**. For your home directory, use **nautilus /home/<yourname>**. For the wastebasket, use **nautilus trash:///**.
[*]*Comment:* Anything you like.
[/LIST]

---

### Post by ben105 on 2009-07-13
Have done it and it worked. Thanks!!!

---

