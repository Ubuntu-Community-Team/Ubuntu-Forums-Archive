---
title: "Trouble trying to duel boot Ubuntu/Vista"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by amosmj on 2009-10-10
I've been working for about a week trying to install Ubuntu 8.04 on my Dell laptop that was running Vista. I've Googled it  a variety of times but have been primarily using the [Apcmag]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") instructions. I've encountered a variety of problems but they center around two areas:

Partitions: It seems like any partition I make in one system is not accepted by the other system. For example, a partition made in Vista has to end up being deleted and remade by gparted when I try to install Ubuntu and any partition made by gparted has to be deleted and remade by the windows partitioner when I try to install Vista.
Realizing I can only have 4 primary partitions, I'd like to have 3 that are 20 Gig and 1 that is the remainder of my harddrive. Is there something obvious that I am doing wrong to cause this behavior in which one system does not recognize partitions from the other system? How have other folks handled this and not had this issue? When installing Ubuntu, is there a way to get a look at what's already on a partition before selecting it in the manual process?

Bootloader: When I install Vista it doesn't even give me the option to get to Ubuntu. If I install Ubuntu last I have four listing for Ubuntu (two of which appear to be some kind of memory test). I thought I maybe had accidentally installed Ubuntu on two different partitions but but selections seem to be the same installation (changes on one appear in the other). Additionally, this last time I somehow lost access to Vista, it shows Longhorn in the bootloader but selecting it appears to kick me to the Windows bootloader which sticks me in an infinite loop.
Do my four Ubuntu listings mean I did install the system twice? What have other folks used to avoid bootloader issues? Is there a better bootloader out there, something that won't frighten non-users, maybe where I can load an image for each system and a person can use the arrow keys, numbers or mouse to select the system of choice?

Any other suggestions (besides not duel booting) or suggested sets of instructions?

Thanks

---

### Post by cariboo on 2009-10-10
The accepted way to create empty space on your hard drive is to use Vista's disk management tools to create empty space on your hard drive. Once the empty space has been created, don't do anything else with it.

Boot from the Live CD and do the normal installation until you get to the partitioning section. In the partitioning section choose manual partition and set up you Ubuntu partition manually. For a first installation I would suggest a single partiton for /, plus a swap partition equal to the size of your ram. Continue on with the install steps until you get to the final step, press the advanced button and make sure grub will be installed on the first partition of the first hard drive, from there the install should proceed normally, and when it comes time to reboot every thing should work as expected.

---

### Post by friv_livs on 2009-10-10
What is your intentions with 3 20GB and 1 remainder GB partitions?
Answer in 20GB #1= OS or storage format
               20GB #2= OS or storage format
               20GB #3= OS or storage format
               1 remainder = OS or storage format

What filesystems are you setting each of these to?

---

### Post by superdav42 on 2009-10-10
If you want to start over from scratch here is what I would do. 

Install windows first, Delete all partitions and create one partition like 20 gb or whatever to use for windows. Leave the rest of the disk unpartitioned. 

After windows is installed install ubuntu and choose the option to use existing free space. Ubuntu should detect your windows installation and provide it as a boot option.

---

### Post by oldfred on 2009-10-10
Vista will not see any partitions that are linux ext2,3 or 4, it sees only ntfs and fat partitions. If you install Ubuntu second it should install Grub in the MBR - master boot record and provide a menu entry for booting to Vista.

In the Grub menu - menu.lst you get an entry for each kernel in you system. Over time you can end up with many kernels. You normally want the most current and one backup just in case the most current has issues with your system. You can install from synaptic startup manager that lets you control how many kernels to show two suggested.

You can only have 4 primary partitions, but one of the primary can be an extended with many more logical partitions. Windows must be in a primary and is happiest if it is first. Ubuntu does not have to be in a primary and works just fine from a logical partition in the extended partition. Normal Ubuntu install puts swap into a logical so it does not use a primary.

---

### Post by amosmj on 2009-10-10
Thank you to each of you who have replied.

Cariboo - I will do as you have suggested
friv - my initial goal is to have those first two section with Ubuntu and Vista, leaving a third for an additional file system. I'm going to try playing with OS X, just for giggles but I kinda want to try out Chrome OS at some point as well.  The final space is for all the files and applications. I've got a larger hard drive than I realized here (250 gig) so I should be fine for quite a while. If I understand things correctly, I can set this to FAT32 and share it among Vista and Ubuntu at a bare minimum.
Superdav - if I do that, will I encoutner any issues with not being able to repartition that space later without wiping out Ubuntu? When I began thsi adventure, one of the issues I had was that Vista was on the entire hardrive but only used a small portion of it. Because it tends to put the file table at the end of its partition I was unble to carve out a slice for Ubuntu without nuking Windows first. 
Olfred -  the issue of what is a logical partition and what it can do is one I haven't fully gotten ahold of yet. I didn't realize that Ubunut could run within a logical partition. Can you point me at a good reference regarding that. I've only gone as far as Wikipedia so far, it was something I had hoped to get back to though.

Thanks again to you each. I'll wipe the disk and start over tomorrow with Vista first. The good news is that Ubuntu goes in pretty clean and easy. I run the install, plug into the network and let it update. It takes a couple hours all told  even but I don't even have to be present for most of it.

---

### Post by lkraemer on 2009-10-10
Since you have a 250Gig drive here is my suggestion.

There is a MAXIMUM of 4 Primary partitions.....unless you use Extended.
I prefer not to use extended...just my choice.

Assign Windows a Minimum of 25-85 Gig (choice of whatever format Windows
now uses if it isn't NTFS) because after you install, and add your Antivirus
you will have used ~10 Gig.  That is Partition #1 and is created first, and
then you install XP or Vista, Antivirus, etc.......
Boot Windows, and let it do it thing, finding and allocating what it has
to, and reporting in to Mama.......Mama it's me.......

The next three Partitions are for Linux.  They will be created with Gparted
after you Download the Gparted ISO, and boot from the LiveCD.
I'd suggest 15 Gig (EXT3) for Ubuntu (/) then a partition named Linux-Swap (/swap)
equal to 2 times your RAM, and located at the end of your partitions, and the
remainder for Data (/home)that is also (EXT3).
Some use EXT4....
Format all Linux Partitions.

Now all 4 Primary are Created......
(Who cares if Windows doesn't know what partition is nextdoor.)
Linux will be satisfied with Windows existing on the Hard Drive, and that
is the Way Windows should behave, but Windows wants to be the BULLY
on the Block...Doesn't like Linux being on the Hard Drive.....

Boot Ubuntu LiveCD and install, using Manual Partition, where you will
just assign the names ( /, /home), as you already created and formatted
the Partitions.  Don't mess with the Windows Partition.

This will allow you to wipe the Root partition, and not loose any of your
data files that is in /home, when you upgrade...... Just a suggestion.

Read up on Dual Booting at:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(Site appears to be down tonight.  Hope it isn't permanent)
Visit this site and read about making a dual boot system.

Download Supergrub, and have it for the repair of your Master Boot Record
(MBR) when you need it.

For running and testing other OS's install VirtualBox (PUEL version) from
their website, and run any ISO of any OS you want.  No need to install
on a Partition.  Easy, no mess.

LK

---

### Post by oldfred on 2009-10-11
+1 on Herman's site, he has lots of info if you are interested, can be overwhelming for a beginner as sometimes you have to search about since he has so much. This may be the newer link.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

More Partitioning info:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by amosmj on 2009-10-11
lk - thanks for the detailed help
old fred - thanks for the links, I'll read them all later today. I appreciate it.

I did as suggested with regard to installing windows clean, I gave it 50Gig and have installed all the major packages I wanted to have on it (Office, Adobe Web) and seem to be doing fine there. I have also installed Ubuntu  and it seems to be in good shape.  I'm going to do the data partition a bit later today, leaving a gap for the third partition. 

Thanks again guys.

---

### Post by utnubuuser on 2009-10-11
I was under the impression that only **3** primary partitions are allowed.  - that might very well be different nowadays.

---

### Post by oldfred on 2009-10-11
It has always been 4 primary. But then you could not have an extended. You convert one primary to the extended, so you are correct you have 3 primary ( and one extended with many additional partitions).

---

