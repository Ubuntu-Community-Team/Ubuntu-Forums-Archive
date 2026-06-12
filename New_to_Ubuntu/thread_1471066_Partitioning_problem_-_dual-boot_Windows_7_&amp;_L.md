---
title: "Partitioning problem - dual-boot Windows 7 &amp; Lucid 10.04"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Richard Kempe on 2010-05-03
A puzzling problem - well, it puzzled me, anyway!

While trying to use the Xubuntu 10.04 LTS installer to set up a dual-boot with Windows 7 on my HP laptop I got as far as the partitioning screen and was then offered not three options, as expected, but only two:

[LIST=1]
[*]replace my Windows 7 installation with Xubuntu, or
[*]partition my drive manually,
[/LIST]
i.e., no "side-by-side" nicely pre-configured option as has been the case with the other Ubuntu installers I've used.

I balked at manually partitioning the drive as I wouldn't really know what I was doing (although I suppose, with a little effort I could find out!) but in any case thought it odd that the side-by-side option should not be present.

Can anyone offer any suggestions as to possible causes and potential solutions? I'd appreciate any input you may be able to provide.

---

### Post by cap10Ibraim on 2010-05-03
first boot in windows 7 and use to disk management to shrink your windows partition then boot the Xubuntu live cd you must see an option use the unallocated space

---

### Post by Don Bowen on 2010-05-03
I'd like to put in a vote for starting from scratch.  For what it's worth, here's how I do it for notebook.

1. boot from WU DVD and remove all partitions
2. Use W7 install to make a 40gig partition for W7 (it will also make a 100mb partition on its own).
3. finish installing W7
4. boot from Ubuntu 10.4
5. create manual partition for Ubuntu: 40gigs for OS, 4 for swap (NB: these are EXTENDED partitions that exist under one of the four PRIMARY patitions)
6. finish installing Ubuntu
6.5 CloneZilla the entire disk with the Data drive portion UN-partitioned
7. boot from W7, set remainder of the HD as "data" drive

From doing this, I learn that a drive may only have FOUR "Primary" partitions:
sda1: Windows7 100mb swap
sda2: Windows7 OS
sda3: Ubuntu as two "Extended" partitions:  sda5=Ubuntu 10.4 OS, sda6=swap
sda4: DataDrive

as I recall, Ubuntu lets you designate the partition type for its OS and swap as "Extended" not "Primary" since there are only 4 possible primary partitions.

I don't create the final Data partition until AFTER I've backed up the drive with CloneZilla.  Leaving the unpartitioned space alone and imaging the entire disk lets me move the image from my old 320gb drive to a newer 250gb.  Without the empty UN-partitioned space, CloneZilla seems unable to relocate the image from one drive to another of a different size.
I hope something in all this will help.

---

### Post by Richard Kempe on 2010-05-05
> **cap10Ibraim said:**
> first boot in windows 7 and use to disk management to shrink your windows partition then boot the Xubuntu live cd you must see an option use the unallocated space

Thanks for that. Shrinking the Windows partition certainly solved the immediate problem. 

Now I just need to work out what the most appropriate partitioning scheme is - there seem to be various schools of thought on that issue.

---

### Post by Richard Kempe on 2010-05-05
> **Don Bowen said:**
> I'd like to put in a vote for starting from scratch.  For what it's worth, here's how I do it for notebook.

1. boot from WU DVD and remove all partitions
2. Use W7 install to make a 40gig partition for W7 (it will also make a 100mb partition on its own).
3. finish installing W7
4. boot from Ubuntu 10.4
5. create manual partition for Ubuntu: 40gigs for OS, 4 for swap (NB: these are EXTENDED partitions that exist under one of the four PRIMARY patitions)
6. finish installing Ubuntu
6.5 CloneZilla the entire disk with the Data drive portion UN-partitioned
7. boot from W7, set remainder of the HD as "data" drive

From doing this, I learn that a drive may only have FOUR "Primary" partitions:
sda1: Windows7 100mb swap
sda2: Windows7 OS
sda3: Ubuntu as two "Extended" partitions:  sda5=Ubuntu 10.4 OS, sda6=swap
sda4: DataDrive

as I recall, Ubuntu lets you designate the partition type for its OS and swap as "Extended" not "Primary" since there are only 4 possible primary partitions.

I don't create the final Data partition until AFTER I've backed up the drive with CloneZilla.  Leaving the unpartitioned space alone and imaging the entire disk lets me move the image from my old 320gb drive to a newer 250gb.  Without the empty UN-partitioned space, CloneZilla seems unable to relocate the image from one drive to another of a different size.
I hope something in all this will help.


Thanks for your response Don - I'm now trying to educate myself on the subject of partitioning in order to make an informed choice in terms of system performance and reliability. I'll take your suggestion(s) on board...

---

### Post by cyberjar09 on 2010-05-06
> **Don Bowen said:**
> I'd like to put in a vote for starting from scratch.  For what it's worth, here's how I do it for notebook.

1. boot from WU DVD and remove all partitions
2. Use W7 install to make a 40gig partition for W7 (it will also make a 100mb partition on its own).
3. finish installing W7
4. boot from Ubuntu 10.4
5. create manual partition for Ubuntu: 40gigs for OS, 4 for swap (NB: these are EXTENDED partitions that exist under one of the four PRIMARY patitions)
6. finish installing Ubuntu
6.5 CloneZilla the entire disk with the Data drive portion UN-partitioned
7. boot from W7, set remainder of the HD as "data" drive

From doing this, I learn that a drive may only have FOUR "Primary" partitions:
sda1: Windows7 100mb swap
sda2: Windows7 OS
sda3: Ubuntu as two "Extended" partitions:  sda5=Ubuntu 10.4 OS, sda6=swap
sda4: DataDrive

as I recall, Ubuntu lets you designate the partition type for its OS and swap as "Extended" not "Primary" since there are only 4 possible primary partitions.

I don't create the final Data partition until AFTER I've backed up the drive with CloneZilla.  Leaving the unpartitioned space alone and imaging the entire disk lets me move the image from my old 320gb drive to a newer 250gb.  Without the empty UN-partitioned space, CloneZilla seems unable to relocate the image from one drive to another of a different size.
I hope something in all this will help.


What about if I wanted to create a /home partition for ubuntu to save my settings incase i reinstalled ...? pls help. 

Thank you.

---

### Post by nitstorm on 2010-05-06
> What about if I wanted to create a /home partition for ubuntu to save my settings incase i reinstalled ...? pls help. 

When you manually select the partition sizes, you'll have to select mount points.
There create a separate partition for your home folder specify the size and then in the** mount point **select **/home**

---

### Post by cyberjar09 on 2010-05-06
> **nitstorm said:**
> When you manually select the partition sizes, you'll have to select mount points.
There create a separate partition for your home folder specify the size and then in the** mount point **select **/home**

so its not a problem right? it can be done ?

for instance: 
i have a 750 gb HDD 

35gb - win 7 (primary)
next create a /boot partition?? (what size?)(ext4?)
10 gb - create a /home partition (ext4)
20 gb - create an ubuntu partition (ext4)
15 gb - create an ultimate edition partition? (im trying it our for the first time so i am not sure about the /boot partition) (ext4)

remaining - data (fat32 ?)

pls tell me if i can go ahead with the above mentioned config...

Thank You.

---

### Post by Richard Kempe on 2010-05-06
> **cyberjar09 said:**
> so its not a problem right? it can be done ?

for instance: 
i have a 750 gb HDD 

35gb - win 7 (primary)
next create a /boot partition?? (what size?)(ext4?)
10 gb - create a /home partition (ext4)
20 gb - create an ubuntu partition (ext4)
15 gb - create an ultimate edition partition? (im trying it our for the first time so i am not sure about the /boot partition) (ext4)

remaining - data (fat32 ?)

pls tell me if i can go ahead with the above mentioned config...

Thank You.


I'm now in much the same position that you are (having resolved the minor problem that generated the first msg in this thread) - I understand that manual partitioning has advantages over just letting the Lucid installer do its thing automatically, but as a complete noob as far as partitioning's concerned I'm at a bit of a loss as to exactly what partitioning scheme to use - for starters!

I have a 320gb drive in my laptop with Windows 7 installed in a partition of about 150gb, leaving a roughly similar sized partition for my Lucid installation.

So far it seems that my partition scheme should look *something* like this (although I'm more than happy to entertain alternatives/refinements):

/  (root) - perhaps 5gb (including a 2gb logical swap partition)
/boot - not sure how big this should be
/usr - 5gb
/var - 3gb
/tmp - 1gb
/home - remaining free space

I realise there are a number of other considerations (primary partitions, extended partitions, logical partitions); what file system - ext4?

I'd really appreciate any comments from anyone with tried and tested partitioning schemes.

---

### Post by okplayer02 on 2010-05-06
well i would suggest you can give more space for all your partitions especially depending how many programs you want to install you say u have like 120GB i guess for Ubuntu  your /boot partition you could set that to 500 MB it doesnt need to be so much.  Do you have more specific questions?

---

### Post by Richard Kempe on 2010-05-06
> **okplayer02 said:**
> well i would suggest you can give more space for all your partitions especially depending how many programs you want to install you say u have like 120GB i guess for Ubuntu  your /boot partition you could set that to 500 MB it doesnt need to be so much.  Do you have more specific questions?


Thanks for your suggestion re: the /boot partition.

The only specific questions that occur to me at the moment are:

1. are my suggested partitions appropriate? (FI, I've seen it suggested that a number of logical partitions should be created in the /boot partition, such as /etc, /bin, /sbin, /lib, /dev); similarly with the /usr partition (/usr/bin, /usr/lib, /usr/share/doc).

2. if my suggested partitions are appropriate, are there any others I should be creating?

3. what file system should I be using, ext4?

All input most welcome.

---

### Post by okplayer02 on 2010-05-06
well for my scenario this is my partition layout and its just for desktop use
i have
what you had already is fine just give your self more space for each of the 

/boot   500 MB
/swap   1gb
/    15 GB
/usr  15 GB
/var  9 gb
/home the remaining space to this partition

ext4 is fine for the filesystem this is the default choice if im correct for lucid. 
so of course if your hard drive is bigger you can allocate more space for each partition.

---

### Post by Richard Kempe on 2010-05-06
> **okplayer02 said:**
> well for my scenario this is my partition layout and its just for desktop use
i have
what you had already is fine just give your self more space for each of the 

/boot   500 MB
/swap   1gb
/    15 GB
/usr  15 GB
/var  9 gb
/home the remaining space to this partition

ext4 is fine for the filesystem this is the default choice if im correct for lucid. 
so of course if your hard drive is bigger you can allocate more space for each partition.


Thanks for that - very helpful. I'll bite the bullet and actually set up the new partitions within the next couple of days.

---

### Post by marcusjames on 2010-05-06
[SIZE=2]My 2 cents on partitioning. My two guiding principles are :

#1  I never mix up partitioning with installing. Its two seperate operations and one precedes the other. I use gparted on a seperate disc. And I do all the partitioning on the drive in one go.

#2 I always use the same scheme regardless. It works for me, it is consistent, flexible  and simple. I always create

sda1 - Primary
sda2 - Swap
sda3 - Primary
sda4 - Extended.

That keeps my disk numbers nice and consecutive when I add the logical partitions inside the Extended partititions eg

sda5 Logical[/SIZE]
[SIZE=2]sda6 Logical
sda7 Logical
sda8 Logical

The fine tuning can then be added. What goes where, and how big should the partitions be. Typically I put my first OS in sda1. sda3 I use as common /home. sda5/8 I use for test installs etc.

A user who wants to run a proprietary OS as well could put that in sda1, use sda3 as his first linux OS, and use a logical partition as /home eg sda5. Swap can be in a logical partition allowing you to create another primary but I don't like doing it. My system lets me mess about in my extended partition and the logicals it contains, without disturbing any other part of the drive including swap. 

Hope this helps. 




[/SIZE]

---

### Post by Richard Kempe on 2010-05-06
> **marcusjames said:**
> [SIZE=2]My 2 cents on partitioning. My two guiding principles are :

#1  I never mix up partitioning with installing. Its two seperate operations and one precedes the other. I use gparted on a seperate disc. And I do all the partitioning on the drive in one go.

#2 I always use the same scheme regardless. It works for me, it is consistent, flexible  and simple. I always create

sda1 - Primary
sda2 - Swap
sda3 - Primary
sda4 - Extended.

That keeps my disk numbers nice and consecutive when I add the logical partitions inside the Extended partititions eg

sda5 Logical[/SIZE]
[SIZE=2]sda6 Logical
sda7 Logical
sda8 Logical

The fine tuning can then be added. What goes where, and how big should the partitions be. Typically I put my first OS in sda1. sda3 I use as common /home. sda5/8 I use for test installs etc.

A user who wants to run a proprietary OS as well could put that in sda1, use sda3 as his first linux OS, and use a logical partition as /home eg sda5. Swap can be in a logical partition allowing you to create another primary but I don't like doing it. My system lets me mess about in my extended partition and the logicals it contains, without disturbing any other part of the drive including swap. 

Hope this helps. 

[/SIZE]


Thanks very much for your contribution - I do love the signs of an organised mind! 

One small point - when you say you use one of your Primary partitions (sda3) as "common /home" what exactly do you mean? "Common" as in shared by more than one OS? That being the case, wouldn't that tend to negate one of the main advantages of manual partitioning, namely the ability easily to replace the files associated with a given OS in the event of upgrading/replacing that installation? Or am I straying from the point?

On the subject of partitioning vs installing, this is probably a silly question (to which the answer will become obvious when I actually install Lucid in my manually created partitions!) but does the installer simply automatically utilise the newly-created partitions (based on their mount point, or whatever) or does one need to tell it where to install what?

Thanks again for your help, your partitioning scheme looks both logical and orderly to me, and unless I come across anything that convinces me to do otherwise I'll be making use of it (or something closely approximating it) in the very near future.

---

### Post by srs5694 on 2010-05-06
I'm not marcusjames, but I can answer your questions....

> **Richard Kempe said:**
> One small point - when you say you use one of your Primary partitions (sda3) as "common /home" what exactly do you mean? "Common" as in shared by more than one OS?

The /home partition can be shared between multiple Linux installations, whether that's multiple installations of the same version of Ubuntu (say if you've installed one for emergencies), installations of different versions of Ubuntu (say if you want to upgrade but leave the old version running in case the new one gives you problems) or entirely different distributions (if you want to run Ubuntu and something else, like Fedora or OpenSUSE). When you do this it's best to use different usernames, or at least different home directories, on the different installations to keep programs from getting confused by configuration file changes they didn't make. It's possible to access a Linux /home partition from another OS if a suitable filesystem driver is available; however, this doesn't seem to be a very popular method of cross-OS file sharing.

>  That being the case, wouldn't that tend to negate one of the main  advantages of manual partitioning, namely the ability easily to replace  the files associated with a given OS in the event of upgrading/replacing  that installation?

Not at all. The Linux /home partition holds *user data,* not system data or program files. Your digital photos, word processing documents, MP3s, Web browser cache, and so on go in /home, but your graphics software, word processor, MP3 player, and Web browser software all go in /usr or elsewhere, and can be upgraded or replaced independently of your user files in /home.

> On the subject of partitioning vs installing, this is probably a silly question (to which the answer will become obvious when I actually install Lucid in my manually created partitions!) but does the installer simply automatically utilise the newly-created partitions (based on their mount point, or whatever) or does one need to tell it where to install what?

You must set the mount point(s) when you install the OS; that information is not intrinsic to the partition itself. In fact, you could mount the same partition at different points in different installations, although this wouldn't always make sense. As an example, if you've got Ubuntu and Fedora installed, you might mount the Fedora root (/) partition as /fedora under Ubuntu, enabling you to edit the Fedora configuration files from Ubuntu -- for instance, you'd edit /fedora/etc/fstab from Ubuntu to alter Fedora's view of its partitions. That file would become /etc/fstab when you reboot into Fedora.

Where the installer puts files is based on the directory pathname in the Linux unified directory tree, which is based off of the root (/) directory, with subdirectories under that. Thus, /usr/bin/lspci is stored in /usr/bin no matter what; but /usr/bin will be the /bin directory of the /usr partition if /usr is a separate partition, but it will be the /usr/bin directory of the root (/) partition if /usr is *not* a separate partition.

---

### Post by Richard Kempe on 2010-05-07
> **srs5694 said:**
> 
The /home partition can be shared between multiple Linux installations, whether that's multiple installations of the same version of Ubuntu (say if you've installed one for emergencies), installations of different versions of Ubuntu (say if you want to upgrade but leave the old version running in case the new one gives you problems) or entirely different distributions (if you want to run Ubuntu and something else, like Fedora or OpenSUSE). When you do this it's best to use different usernames, or at least different home directories, on the different installations to keep programs from getting confused by configuration file changes they didn't make. It's possible to access a Linux /home partition from another OS if a suitable filesystem driver is available; however, this doesn't seem to be a very popular method of cross-OS file sharing.

Thanks for setting me straight on that point - I had no idea that sort of thing was possible (just goes to show what spending twenty or so years in the constrained environment of the big commercial OSs will do in terms of limiting one's expectations!).

> **srs5694 said:**
> 
Not at all. The Linux /home partition holds *user data,* not system data or program files. Your digital photos, word processing documents, MP3s, Web browser cache, and so on go in /home, but your graphics software, word processor, MP3 player, and Web browser software all go in /usr or elsewhere, and can be upgraded or replaced independently of your user files in /home.

You must set the mount point(s) when you install the OS; that information is not intrinsic to the partition itself. In fact, you could mount the same partition at different points in different installations, although this wouldn't always make sense. As an example, if you've got Ubuntu and Fedora installed, you might mount the Fedora root (/) partition as /fedora under Ubuntu, enabling you to edit the Fedora configuration files from Ubuntu -- for instance, you'd edit /fedora/etc/fstab from Ubuntu to alter Fedora's view of its partitions. That file would become /etc/fstab when you reboot into Fedora.

I see - I'm just not used to having that type of control (it's really a whole different filesystem paradigm).

> **srs5694 said:**
> 
Where the installer puts files is based on the directory pathname in the Linux unified directory tree, which is based off of the root (/) directory, with subdirectories under that. Thus, /usr/bin/lspci is stored in /usr/bin no matter what; but /usr/bin will be the /bin directory of the /usr partition if /usr is a separate partition, but it will be the /usr/bin directory of the root (/) partition if /usr is *not* a separate partition.

I was thinking I'd put Xubuntu in an extended partition, then create logical partitions within it (/ (root), /boot, /usr, /var, /tmp, /home, etc.) - what would be the advantages and/or disadvantages of that scenario (other than the obvious advantage of being able to deal with the logical partitions on an individual basis for back-up/repair/upgrade purposes)? 

Or would it be preferable simply to put a / (root) partition in my Xubuntu partition, and let the installer populate it with all the requisite directories?

Thanks again for your help - the fog is starting to clear (a little)...

---

### Post by srs5694 on 2010-05-07
> **Richard Kempe said:**
> I was thinking I'd put Xubuntu in an extended partition, then create logical partitions within it (/ (root), /boot, /usr, /var, /tmp, /home, etc.) - what would be the advantages and/or disadvantages of that scenario (other than the obvious advantage of being able to deal with the logical partitions on an individual basis for back-up/repair/upgrade purposes)? 

Or would it be preferable simply to put a / (root) partition in my Xubuntu partition, and let the installer populate it with all the requisite directories?

First, what may be a minor terminology point: You don't put anything but logical partitions *directly* inside an extended partition. In the scenario you describe, Xubuntu goes in the logical partitions you've laid out (or you could even split it between primary and logical partitions). Extended partitions are just placeholders for logical partitions. Also and FWIW, it's entirely possible for multiple OSes to use different logical partitions in a single extended partition. For instance, Linux could use one logical partition and Windows could use another one, both in one extended partition.

To your main question, though, my usual advice for new Linux users is to create three partitions for Linux: a root (/) partition of 5-20GB, depending on how much software you intend to install and how much disk space you've got; a swap partition that's between 1 and 2 times the size of your RAM; and a /home partition that consumes the rest of your disk allocation for Linux. Swap is, if not strictly necessary, very useful. (Swap space is not mounted in the same way other partitions are, though.) Separating /home from the rest of the filesystem is useful because you can completely re-install Linux -- even a new version or a completely different distribution -- without affecting your user files, which normally reside in /home.

Beyond that, although it's possible to split off many subdirectories, as you've described, it's hard for new users to guess the right sizes, so there's a lot of potential for it to do more harm than good. Experienced Linux users and professional system administrators may have cause to split off /var or /usr/local or whatever, but unless you already know you'll be running a big mail server or compiling lots of your own software or something, the benefits to splitting off more than /home are slim.

---

### Post by Richard Kempe on 2010-05-07
> **srs5694 said:**
> To your main question, though, my usual advice for new Linux users is to create three partitions for Linux: a root (/) partition of 5-20GB, depending on how much software you intend to install and how much disk space you've got; a swap partition that's between 1 and 2 times the size of your RAM; and a /home partition that consumes the rest of your disk allocation for Linux. Swap is, if not strictly necessary, very useful. (Swap space is not mounted in the same way other partitions are, though.) Separating /home from the rest of the filesystem is useful because you can completely re-install Linux -- even a new version or a completely different distribution -- without affecting your user files, which normally reside in /home.

I'm definitely all for keeping it simple. Having said that, and taken your advice on board, I've revised my proposed partitioning scheme, as follows:

[1] Windows 7 (primary)            156gb - this is already in place
[2] / (root)      (primary)              20gb
[3] /swap        (linux-swap)            2gb
[4] Linux         (extended)          100gb
[5] /home       (logical)                55gb
[6] /home (logical)                55gb - spare
Free space                                    8gb

Does this sound like a workable scheme? (The second "/home" partition is a spare I've included in case I decide to install a later version of Ubuntu - or another distro - at some stage.)

My only concern has to do with the /swap partition - I have 4gb of RAM installed, and would therefore (ideally) like to allocate 8gb to my /swap partition, however, I understand that there's an upper limit of 2gb for 32bit systems.

---

### Post by Sir Jasper on 2010-05-07
Hi,

I have not read all this thread, however your extended partition is the sum of all subsequent partitions and unused space (so probably 100 + 55 +55 +8 = 218 GB).

My regards

---

### Post by srs5694 on 2010-05-07
> **Richard Kempe said:**
> I'm definitely all for keeping it simple. Having said that, and taken your advice on board, I've revised my proposed partitioning scheme, as follows:

[1] Windows 7 (primary)            156gb - this is already in place
[2] / (root)      (primary)              20gb
[3] /swap        (linux-swap)            2gb
[4] Linux         (extended)          100gb
[5] /home       (logical)                55gb
[6] /home (logical)                55gb - spare
Free space                                    8gb

Does this sound like a workable scheme? (The second "/home" partition is a spare I've included in case I decide to install a later version of Ubuntu - or another distro - at some stage.)

The /home partition holds user data, so there's no point in duplicating it as you suggest. If you want space for a potential future Linux installation, it would make more sense to set aside another ~20GB partition for a future alternate root (/) partition, then re-use the original /home in the new installation, thus giving you access to the same user files in both installations. You would *not,* however, specify both these root partitions as having the same "/" mount point in your current installation; that would be meaningless at best. Instead, you'd either give the second one no mount point at the moment or mount it someplace else so that you could access it if you'd need to. For instance, if you were planning to install Ubuntu and Fedora, you might give the Fedora root (/) partition a mount point of /fedora under Ubuntu. You can change mount points in the future, so if you're not sure how you'll be using this space, you can leave it unmounted now and assign it a mount point in the future, if and when you decide how to use it.

> My only concern has to do with the /swap partition - I have 4gb of RAM installed, and would therefore (ideally) like to allocate 8gb to my /swap partition, however, I understand that there's an upper limit of 2gb for 32bit systems.

First, swap space is not mounted. In my posts, and in many other peoples' posts, we refer to many partitions by their mount points, as in /home or /usr; but swap space is not accessed this way. It has no mount point, so it's just "swap," not "/swap."

Second, I don't know offhand what the upper limit is for the size of swap space, but I'm pretty sure it's well above 2GB, even on 32-bit systems. I just checked, and I've got a 32-bit system booted right now with 4GB of swap space. If you've got the disk space, there's no reason not to give it 8GB. In a worst-case scenario, some of that space will be unusable, so you'll lose a bit of disk space.

---

### Post by cyberjar09 on 2010-05-07
> **Richard Kempe said:**
> I'm now in much the same position that you are (having resolved the minor problem that generated the first msg in this thread) - I understand that manual partitioning has advantages over just letting the Lucid installer do its thing automatically, but as a complete noob as far as partitioning's concerned I'm at a bit of a loss as to exactly what partitioning scheme to use - for starters!

I have a 320gb drive in my laptop with Windows 7 installed in a partition of about 150gb, leaving a roughly similar sized partition for my Lucid installation.

So far it seems that my partition scheme should look *something* like this (although I'm more than happy to entertain alternatives/refinements):

/  (root) - perhaps 5gb (including a 2gb logical swap partition)
/boot - not sure how big this should be
/usr - 5gb
/var - 3gb
/tmp - 1gb
/home - remaining free space

I realise there are a number of other considerations (primary partitions, extended partitions, logical partitions); what file system - ext4?

I'd really appreciate any comments from anyone with tried and tested partitioning schemes.

i have a question on a side note... i am only aware of the function of the "/" and the "/home" partitions. what do these additional options achieve in the context of reinstalling/performance of the system?

---

### Post by gordintoronto on 2010-05-07
> **srs5694 said:**
> .. my usual advice for new Linux users is to create three partitions for Linux: 
a root (/) partition of 5-20GB, depending on how much software you intend to install and how much disk space you've got; 
a swap partition that's between 1 and 2 times the size of your RAM;
and a /home partition that consumes the rest of your disk allocation for Linux....


Perfect!

---

### Post by Richard Kempe on 2010-05-07
> **Sir Jasper said:**
> 
I have not read all this thread, however your extended partition is the sum of all subsequent partitions and unused space (so probably 100 + 55 +55 +8 = 218 GB).

Not quite - my maths just needed some adjustment (I forgot to increase the size of the extended partition after increasing the size of the two subsequent logical partitions by 5gb each) - it *should* have read:

"[4] Linux         (extended)          **118gb**
[5] /home       (logical)                55gb
[6] /home (logical)                55gb - spare
Free space                                    8gb"

So that's extended = logical + logical + free space - a total of 118gb.

Thanks for your input.

---

### Post by Richard Kempe on 2010-05-07
> **cyberjar09 said:**
> i have a question on a side note... i am only aware of the function of the "/" and the "/home" partitions. what do these additional options achieve in the context of reinstalling/performance of the system?

Not much, it would seem, unless you have a special purpose for creating separate partitions like running a mail server or something of the sort and have a fair degree of expertise, enabling you to estimate partition size required for these additional partitions (see earlier posting in this thread by **srs5694**).

---

### Post by Richard Kempe on 2010-05-07
> **srs5694 said:**
> The /home partition holds user data, so there's no point in duplicating it as you suggest. If you want space for a potential future Linux installation, it would make more sense to set aside another ~20GB partition for a future alternate root (/) partition, then re-use the original /home in the new installation, thus giving you access to the same user files in both installations. You would *not,* however, specify both these root partitions as having the same "/" mount point in your current installation; that would be meaningless at best. Instead, you'd either give the second one no mount point at the moment or mount it someplace else so that you could access it if you'd need to. For instance, if you were planning to install Ubuntu and Fedora, you might give the Fedora root (/) partition a mount point of /fedora under Ubuntu. You can change mount points in the future, so if you're not sure how you'll be using this space, you can leave it unmounted now and assign it a mount point in the future, if and when you decide how to use it.

[1] Windows 7 (primary)            156gb
[2] / (root)      (primary)              20gb
[2] Root (spare)      (primary)              20gb (no mount point)
[3] Swap        (linux-swap) 8gb
[4] Linux         (extended) 92gb
[5] /home       (logical) 92gb

Hopefully that's the final version of my proposed scheme - I've kept the Linux partition as an extended partition to allow for the possibility of carving out an additional logical partition or two if I need to later (I'm presuming that would be possible?) - or should I just make the Linux partition a /home (primary) partition? (Would I need to leave some free space at the end of the extended partition to allow for the addition of logical partitions, or can I simply re-size the existing logical partition for that purpose?)

> 
First, swap space is not mounted. In my posts, and in many other peoples' posts, we refer to many partitions by their mount points, as in /home or /usr; but swap space is not accessed this way. It has no mount point, so it's just "swap," not "/swap."

Second, I don't know offhand what the upper limit is for the size of swap space, but I'm pretty sure it's well above 2GB, even on 32-bit systems. I just checked, and I've got a 32-bit system booted right now with 4GB of swap space. If you've got the disk space, there's no reason not to give it 8GB. In a worst-case scenario, some of that space will be unusable, so you'll lose a bit of disk space.Thanks for your patience with my lack of familiarity with the terminology.

As to the swap space limitation I'm sure I read that somewhere, but I'll take your word for it - as you say, the worst that could happen is that some of the space will be unusable.

---

### Post by srs5694 on 2010-05-07
> **Richard Kempe said:**
> [1] Windows 7 (primary)            156gb
[2] / (root)      (primary)              20gb
[2] Root (spare)      (primary)              20gb (no mount point)
[3] Swap        (linux-swap) 8gb
[4] Linux         (extended) 92gb
[5] /home       (logical) 92gb

Hopefully that's the final version of my proposed scheme - I've kept the Linux partition as an extended partition to allow for the possibility of carving out an additional logical partition or two if I need to later (I'm presuming that would be possible?) - or should I just make the Linux partition a /home (primary) partition? (Would I need to leave some free space at the end of the extended partition to allow for the addition of logical partitions, or can I simply re-size the existing logical partition for that purpose?)

I'd move everything but Windows into an extended partition (each on its own logical partition, of course). That will give you the option of creating another primary partition in the future should you need to do so -- for instance, if you decide you want to try FreeBSD (it requires a primary partition). Also, you might want to consider creating a separate NTFS data-exchange partition, so that neither OS needs to mount the other's root/boot partition in order to exchange files.

In theory, you can resize partitions should you need to do so in the future. In practice, that's always at least a little risky. If you have no specific plans for future partitions at the moment, I'd say it's better to keep the space in partitions so that you can use it. If you've got some specific ideas about what you might want to do with more partitions in the next few months, though, you could leave some space empty or pre-partition it (as you've done with your spare 20GB partition for a future Linux installation).

---

### Post by Richard Kempe on 2010-05-08
> **srs5694 said:**
> I'd move everything but Windows into an extended partition (each on its own logical partition, of course). That will give you the option of creating another primary partition in the future should you need to do so -- for instance, if you decide you want to try FreeBSD (it requires a primary partition). Also, you might want to consider creating a separate NTFS data-exchange partition, so that neither OS needs to mount the other's root/boot partition in order to exchange files.

In theory, you can resize partitions should you need to do so in the future. In practice, that's always at least a little risky. If you have no specific plans for future partitions at the moment, I'd say it's better to keep the space in partitions so that you can use it. If you've got some specific ideas about what you might want to do with more partitions in the next few months, though, you could leave some space empty or pre-partition it (as you've done with your spare 20GB partition for a future Linux installation).

The only other OS I'm likely to want to install is Mac OSX, and I'm unsure as to its requirements in terms of being installed on a primary partition, etc., but I may pre-partition a primary partition anyway (after my Windows partition) and leave it empty for the moment in case I decide to go that way. 

However, for now let's assume I've got my primary Windows 7 partition and my extended Linux partition (which contains the logical partitions: / (root), Root (spare), Swap and /home).

I'm not familiar with the notion of an NTFS data-exchange partition, but it sounds like a very good idea in principal. Assuming I want to incorporate such a partition: where do I put it? Given that, as I understand it, extended partitions must be positioned as the last partition on a drive, I take it that means that it has to be placed straight after the Windows partition (and perhaps my empty primary partition if I decide to create one) and therefore before my Linux partition.

What else do I need to know about setting up the data-exchange partition? I don't seem to be able to find much information online with regard to this (mind you, I haven't had time to look very hard as yet).

On a different (but related) topic - what filesystem should I be using to set up my logical partitions (if I'm only ever going to want to install current or forthcoming Linux OSs) - I was thinking that ext4 might be appropriate. What's your view?

---

### Post by srs5694 on 2010-05-08
> **Richard Kempe said:**
> The only other OS I'm likely to want to install is Mac OSX, and I'm unsure as to its requirements in terms of being installed on a primary partition, etc., but I may pre-partition a primary partition anyway (after my Windows partition) and leave it empty for the moment in case I decide to go that way.

The moderators don't like discussions of OS X on standard PCs, since running OS X this way violates the EULA. The are Web forums devoted to this topic, though.

> I'm not familiar with the notion of an NTFS data-exchange partition, but it sounds like a very good idea in principal. Assuming I want to incorporate such a partition: where do I put it? Given that, as I understand it, extended partitions must be positioned as the last partition on a drive, I take it that means that it has to be placed straight after the Windows partition (and perhaps my empty primary partition if I decide to create one) and therefore before my Linux partition.

The best place to put a cross-OS data-exchange partition is between the two OSs; that minimizes the head seek times to access the partition from either OS.

That said, you're working under two false assumptions. First, there's no need for a data-exchange partition to be a primary partition. It can be a logical partition inside the same extended partition that will hold your Linux partitions. (The extended partition is in no way "owned" by a single OS.) The second false assumption is unimportant given the other issues, but it's still worth pointing out: Extended partitions need not come entirely after all the primary partitions. Placing them in this way does make partition numbering and the ordering of partitions in terms of disk sectors match up properly, but there's no rule that says you can't have one or more primary partitions that come after the extended partition (and therefore all the logical partitions it contains). In fact, I've got a computer with two disks, both of which are set up this way.

> What else do I need to know about setting up the data-exchange partition? I don't seem to be able to find much information online with regard to this (mind you, I haven't had time to look very hard as yet).

For a Linux/Windows data-exchange partition, you can use FAT, NTFS, or ext2fs/ext3fs. FAT is reliable in both OSes, but it's got file size limitations (it maxes out at 4GB). NTFS works reasonably well in both OSes and eliminates the file-size issues, but there are only the most rudimentary filesystem-checking tools for it in Linux, so you may need to reboot to Windows after a system crash to get it working again. Ext2fs/ext3fs works better in Linux, but I'm not sure how good the Windows drivers are (they don't come with Windows; you'll have to track them down). FAT and NTFS lack support for Linux ownership and permissions features, which isn't normally a big deal on a desktop system, but it could be important for some purposes.

> On a different (but related) topic - what filesystem should I be using to set up my logical partitions (if I'm only ever going to want to install current or forthcoming Linux OSs) - I was thinking that ext4 might be appropriate. What's your view?

My personal preference is to use ReiserFS for most Linux system partitions and other partitions that hold mostly smallish files (up to a few hundred megabytes), and XFS for partitions that hold bigger files (such as multimedia files, system backups, etc.). The Ext2/3/4 series is very popular, though, and most Ubuntu users seem to favor ext3fs or ext4fs. Ext4fs is new enough that I still don't entirely trust it, although by now most of its kinks have been ironed out. IMHO, there's little or no advantage to ext4fs for system (root) partitions, but it might be worth using on disks that store big files.

---

### Post by Richard Kempe on 2010-05-08
> **srs5694 said:**
> 
The moderators don't like discussions of OS X on standard PCs, since running OS X this way violates the EULA. The are Web forums devoted to this topic, though.

Fair enough, it was only an aside, I wasn't really intending to raise it as a point for further discussion (and in any event I have noticed one or two of the other forums you mention).

> 
The best place to put a cross-OS data-exchange partition is between the two OSs; that minimizes the head seek times to access the partition from either OS.

That said, you're working under two false assumptions. First, there's no need for a data-exchange partition to be a primary partition. It can be a logical partition inside the same extended partition that will hold your Linux partitions.OK, looks like that's where I'll put it then. Does it matter *where* it goes within the extended partition (e.g., before or after my Linux / (root) partition) or is that of no consequence?

> 
For a Linux/Windows data-exchange partition, you can use FAT, NTFS, or ext2fs/ext3fs. FAT is reliable in both OSes, but it's got file size limitations (it maxes out at 4GB). NTFS works reasonably well in both OSes and eliminates the file-size issues, but there are only the most rudimentary filesystem-checking tools for it in Linux, so you may need to reboot to Windows after a system crash to get it working again. Ext2fs/ext3fs works better in Linux, but I'm not sure how good the Windows drivers are (they don't come with Windows; you'll have to track them down). FAT and NTFS lack support for Linux ownership and permissions features, which isn't normally a big deal on a desktop system, but it could be important for some purposes.Sounds as though FAT or NTFS might be the most appropriate in my situation. 

If I elect to go with FAT (on the basis that the file size limitation probably won't be an issue for me) how does the Linux/Windows data-exchange partition actually work (i.e., what are the mechanics of it, what do I need to install in it and how are those items utilised)? 

[I'm probably asking for a bit too much detail here - if you know of any detailed information anywhere online, by all means just point me to it rather than spending your time on a discussion of this topic.]

> 
The Ext2/3/4 series is very popular, though, and most Ubuntu users seem to favor ext3fs or ext4fs. Ext4fs is new enough that I still don't entirely trust it, although by now most of its kinks have been ironed out. IMHO, there's little or no advantage to ext4fs for system (root) partitions, but it might be worth using on disks that store big files.That being the case I might go with Ext3fs for my / (root) partition and Ext4fs for my /home partition (as I'll be likely to store at least some larger media files there).

---

### Post by srs5694 on 2010-05-08
> **Richard Kempe said:**
> Does it matter *where* it goes within the extended partition (e.g., before or after my Linux / (root) partition) or is that of no consequence?

As I said, put it in-between your Linux and Windows partitions in order to minimize head seek times.

> If I elect to go with FAT (on the basis that the file size limitation probably won't be an issue for me) how does the Linux/Windows data-exchange partition actually work (i.e., what are the mechanics of it, what do I need to install in it and how are those items utilised)? In Windows, it'll show up as E:, F:, or some other drive letter.

Edit: Also, if you prepare the partition before you install Linux, you can tell it where to mount it during installation, on the same screen you use to point it to your root (/) and /home partitions.

In Linux, you can either give it an explicit mount point by editing /etc/fstab or you can rely on Ubuntu's auto-mounting features, which will probably make it available as a subdirectory of /media. I prefer the former. An example entry looks like this:

```

/dev/sda5   /home/username/shared   vfat     uid=1000    0 0

```This example mounts the FAT partition in /dev/sda5 at /home/username/shared and gives ownership of all files to the user with a user ID (UID) number of 1000. (Ubuntu gives the first user created a UID of 1000.) Type "man mount" and scan down to the "Mount options for fat" section to learn about other options you can use. You could also Google "Linux vfat fstab" or something similar; I'm sure that'll turn up lots of examples.

Edit: If you prepare the partition before installing, you can configure it during installation, on the same screen you use to specify your root (/) and /home partitions.

---

### Post by Richard Kempe on 2010-05-09
Thanks for all your help & advice - it's been invaluable as I'd never before even contemplated attempting to partition my drive manually (for previous installations I just allowed the installer to partition automatically).

I've now successfully partitioned my drive and all seems to be functioning as expected - the data-exchange partition speeds things up considerably (it shows up in Xubuntu as "Shared" in my home dir and in Windows as "Data_Exch (D:/)" - although I can rename it to anything I like).

Thanks once again - I really appreciate your patience and the time you spent helping me out.

---

### Post by cyberjar09 on 2010-05-13
> **marcusjames said:**
> [SIZE=2]

sda1 - Primary
sda2 - Swap
sda3 - Primary
sda4 - Extended.

That keeps my disk numbers nice and consecutive when I add the logical partitions inside the Extended partititions eg

sda5 Logical[/SIZE]
[SIZE=2]sda6 Logical
sda7 Logical
sda8 Logical

The fine tuning can then be added. What goes where, and how big should the partitions be. Typically I put my first OS in sda1. sda3 I use as common /home. sda5/8 I use for test installs etc.

A user who wants to run a proprietary OS as well could put that in sda1, use sda3 as his first linux OS, and use a logical partition as /home eg sda5. Swap can be in a logical partition allowing you to create another primary but I don't like doing it. My system lets me mess about in my extended partition and the logicals it contains, without disturbing any other part of the drive including swap. 

Hope this helps. 
[/SIZE]
[FONT=Verdana][SIZE=2]
Hello to everyone once again,

I have a slight extension to my problem now.

I have attached a screenshot of gparted and the partitions on my system.

Heres the scenario: I got my brand spanking new dell laptop but it had  win 7 preinstalled. and shrinking the drive was only giving me 250gb out  of the 500 gb avail on my hdd. *sigh*

So I decided to wipe the windows partition and reinstall an older  windows (also oem cd) by creating a new partition of 20gb and putting my  windows inside it.

now heres my problem, 
sda1 (primary) is taken by windows swap space (i think)
sda2 (primary) is taken by the recovery drive (I dont have access to this   anymore btw)
sda3 is windows
sda4 is where i had to create extended partition with many logical partitions to accomodate my  ubuntu! =(

dell has agreed to ship me an oem copy of the windows 7 that had come  preinstalled on my laptop. 

my question is: 
1. should i wipe my recovery drive and make my partitioning table like so..?

[/SIZE][/FONT][FONT=Verdana][SIZE=2]sda1 - Primary - 20 gb - ntfs - win 7
sda2 - Swap - 5gb ( i have 4gb ddr3 ram, do i need this much?)
sda3 - Primary - /home - 15gb - ext4 
sda4 - Extended.
--sda5 Logical[/SIZE][/FONT][FONT=Verdana][SIZE=2] - / (root) - 10 gb - ext4 - Ubuntu lucid lynx
[/SIZE][/FONT][FONT=Verdana][SIZE=2]--sda6 Logical - / (root) - 10 gb - ext4 - ultimate edition (i want to try it)
--sda7 Logical - DATA - fat32 - all remaining space 

any modifications / sggestions are welcome

2. I have never used the recovery drive on any laptop and dont know if it can be recreated once lost. 

Thank you all very much.

[/SIZE][/FONT]

---

### Post by cyberjar09 on 2010-05-13
really in need of help here ... please help.
Thanks.

---

### Post by mrund on 2010-08-05
I'm also trying to impose a Lucid installation beside an already existing W7 installation. I have a large partition free for Lucid, but I also need a swap partition. So I shrunk the large partition a bit, creating a 10 GB piece of unused space on the disk. But Lucid's partitioner calls it "unusable" and won't let me designate it as swap. What gives?

---

### Post by malmsteen84 on 2010-08-15
guys, 
i'm in real trouble right now. i just bought a new laptop and the existing partitions are =

1. some 1mb of unallocated space
2. dev/sda1 ntfs (primary) for pqservice
3. dev/sda2 ntfs (primary) for system reserved (i think this is win7 swap)
4. dev/sda3 ntfs (primary) for the win7 itself

i've got 1 more primary partition left (sda4), correct? or i can just make it as extended partition and i can make any other logical partitions inside it, true?

now, if i create 1 primary partition which im gonna install lucid on it, where should i put the linux swap?

if i create 1 extended partition with 2 logical partition inside it (sda5 and sda6),and use one for lucid and the other for its swap, and put the grub on the lucid partition so it wont mess up my win7 mbr, after rebooting the grub is not loading, is it true that lucid is only installable on primary partition?

need ur advise here how to solve this. thanks.

---

