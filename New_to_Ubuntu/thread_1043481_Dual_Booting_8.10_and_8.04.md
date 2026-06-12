---
title: "Dual Booting 8.10 and 8.04"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by UltraAnders on 2009-01-18
Hi all,

I have Windows XP and Ubuntu 8.04 (64-bit) installed. I've created another partition and would like to install 8.10 (32-bit) on it.

- Am I right in thinking that both Ubuntu installs can use the same swap partition?
- I also have a separate large (EXT3) partition with all my music etc., in the home directory of the 8.04 install. Can the different installs put home directories on the same partition without issue? If so, will I be able to access files stored in the other home directory?
- Is there anything else I need to watch out for?

I don't want to upgrade my 8.04 install for a few reasons.

Cheers,

Anders.

---

### Post by fuser312 on 2009-01-18
here i am really interested in your reasons regarding updating. it ain't gonna effect your documents. if you have to install another linux, why don't you give trey to another distro like sabbyon, suse, fedora, bsd and many more.

---

### Post by nhasian on 2009-01-18
sure you can dual boot two OSes.  doesnt matter if its 8.04 & 8.10 or two separate installs of 8.04.  Yes they can both share the same swap partition, but dont share the same /home partition.  Yes you can access files from any other partition.

Alternatively you may want to consider using Virtualbox.  then you could easily install different OSes in virtual machines so you can test out different linux distros like ubuntu jaunty, arch linux, fedora, etc.

---

### Post by uidb4056 on 2009-01-18
> **UltraAnders said:**
> Hi all,

I have Windows XP and Ubuntu 8.04 (64-bit) installed. I've created another partition and would like to install 8.10 (32-bit) on it.

- Am I right in thinking that both Ubuntu installs can use the same swap partition?
- I also have a separate large (EXT3) partition with all my music etc., in the home directory of the 8.04 install. Can the different installs put home directories on the same partition without issue? If so, will I be able to access files stored in the other home directory?
- Is there anything else I need to watch out for?

I don't want to upgrade my 8.04 install for a few reasons.

Cheers,

Anders.

1. Yes both Ubuntu can use the same swap partition
2. If you have separate partition for home you can use it for different installs as long as you are using different user names for each install because in the home are stored the config for different applications that could be overwritten by the differents installs.

---

### Post by kansasnoob on 2009-01-18
> **UltraAnders said:**
> Hi all,

I have Windows XP and Ubuntu 8.04 (64-bit) installed. I've created another partition and would like to install 8.10 (32-bit) on it.

- Am I right in thinking that both Ubuntu installs can use the same swap partition?
- I also have a separate large (EXT3) partition with all my music etc., in the home directory of the 8.04 install. Can the different installs put home directories on the same partition without issue? If so, will I be able to access files stored in the other home directory?
- Is there anything else I need to watch out for?

I don't want to upgrade my 8.04 install for a few reasons.

Cheers,

Anders.

Absolutely! Look:

[ATTACH]100301[/ATTACH]

I have Win XP multi-booted with Ubuntu 8.04.1, Ubuntu 8.10, and Linux Mint 6. All three Linux OS's share the same SWAP.

Just do not reformat the SWAP or you'll end up with a UUID problem. But even if you do end up with a UUID problem it's fast and simple to fix! (You'll know you have a UUID problem if Usplash quits and is replaced by a long line of boot-text!)

---

### Post by karlmp on 2009-01-18
why so much swap?

---

### Post by kansasnoob on 2009-01-18
> **karlmp said:**
> why so much swap?

I wondered that too:confused:

I can't imagine a need for much more than 1 GB of SWAP.

---

### Post by mfox on 2009-01-18
And here I thought I was unusual in wanting to have dual Linux boots with Ubuntu 8.04 and 8.10.  My reason originally was fear of messing up a good thing when Intrepid came out.  I had Hardy nicely set up on my MSI Wind using Ubuntu Netbook Remix.  I wanted to try Intrepid and slowly migrate to it, so I made additional space on my drive and installed it.  I also used the two to help me decide whether I was best off with or without the Remix.  It also turns out that there are some programs that run on one but not the other.  The webcam on my netbook runs fine with Cheese in Intrepid, but not Hardy.  On the other hand, two statistical programs I use occasionally (JMP and rkward) wouldn't run on Intrepid.  (I was able to fix the former.)  Then I noticed when I finally tried the Netbook Remix on Intrepid that some of the icons on the netbook-launcher are not as sharp as on Hardy.  Bottom line is I'll continue to use both for now.

What I would ultimately like to do is make a new partition for music and documents, delete that stuff from each distro volume and have it autoload in both Hardy and Intrepid.  That would not only conserve a gig of space, but it would also keep me from having to duplicate files.  Along the same line, it would be nice to have my Evolution mail shared between them.  Any way I can do that?

---

### Post by UltraAnders on 2009-01-18
Great, thanks everyone for such quick replies.

@fuser312 - My reasons for not wanting to upgrade:
[LIST][*]The 8.04 is an install that was upgraded from 7.10.
[LIST]
[*]... which was quite a painful job.
[/LIST]
[*]This Ubuntu install has become a little unstable recently (by Ubuntu's high standards).
[*]There are a few niggles which I'm hoping will go away with a fresh install and/or by using the 32-bit version, for example:
[LIST]
[*]Everytime a new kernel is installed I have uninstall EnvyNG and reinstall even though the FAQ says this is no longer necessary.
[*]Getting the Java Facebook picture upload application working is a real pain. Possibly also broken by a new kernel install.
[/LIST]
[*]I want to move over gradually to 8.10.
[/LIST]

---

### Post by UltraAnders on 2009-01-19
So I pretty much fell at the first hurdle. My partitions are setup as I want them. However none of the options presented allow me to actually select the 20GB partition I had created. So, I delete the empty partition I created, in the hope that Ubuntu would decide to offer to create a partition in this space.

Now I have 4 options:
[LIST]
[*]Guided - resize SCSI3 (0,0,0), partition #7 (sda) and use free space
[LIST]
[*]This appears to resize my largest partition, then use the space to install Ubuntu. It still leaves the 20GB free!
[/LIST]
[*]Guided - use entire disk
[LIST]
[*]No thanks!
[/LIST]
[*]Guided - use the largest continous free space
[LIST]
[*]This is the option I want. However, the "After" shot shows 100% of the HDD allocated to 8.10, hmm.
[/LIST]
[*] Manual
[LIST]
[*]Again, great, except the "After" shows 100% HDD allocated to 8.10
[/LIST]
[/LIST]

I'm too scared to go beyond this point with either options 3 or 4, because first time I installed Ubuntu I managed to delete all my partitions by doing just one click too many! :confused:

---

### Post by Miljet on 2009-01-19
I always use the manual installation method. You have complete control that way.

As a side note, just before final install, click on advanced options and uncheck the box for installing GRUB. Otherwise, you will overwrite your existing GRUB. Sometimes that is not a problem and the new GRUB will find your other operating systems and install them. But I have had it to create problems before. I prefer to keep the existing GRUB and add the new installation to the existing menu.lst file.

---

### Post by logos34 on 2009-01-19
> **UltraAnders said:**
> 
[*] Manual
[LIST]
[*]Again, great, except the "After" shows 100% HDD allocated to 8.10
[/LIST]
[/LIST]


so you mean to say that you cannot manually specify it to format just the unallocated space as ext3 logical partition at mountpoint '/'?

---

### Post by LuisAugusto on 2009-01-19
> **kansasnoob said:**
> Absolutely! Look:

[ATTACH]100301[/ATTACH]
[B]
I have Win XP multi-booted with Ubuntu 8.04.1, Ubuntu 8.10, and Linux Mint 6. All three Linux OS's share the same SWAP.[/B]

Just do not reformat the SWAP or you'll end up with a UUID problem. But even if you do end up with a UUID problem it's fast and simple to fix! (You'll know you have a UUID problem if Usplash quits and is replaced by a long line of boot-text!)

Why in the world do you have the same distro installed three times? I just hope that, at least, you have a shared home partition XD

The problems with UUID are easily fix by just using the device name instead.

-------------------

> **UltraAnders said:**
> So I pretty much fell at the first hurdle. My partitions are setup as I want them. However none of the options presented allow me to actually select the 20GB partition I had created. So, I delete the empty partition I created, in the hope that Ubuntu would decide to offer to create a partition in this space.

Now I have 4 options:
[LIST]
[*]Guided - resize SCSI3 (0,0,0), partition #7 (sda) and use free space
[LIST]
[*]This appears to resize my largest partition, then use the space to install Ubuntu. It still leaves the 20GB free!
[/LIST]
[*]Guided - use entire disk
[LIST]
[*]No thanks!
[/LIST]
[*]Guided - use the largest continous free space
[LIST]
[*]This is the option I want. However, the "After" shot shows 100% of the HDD allocated to 8.10, hmm.
[/LIST]
[*] Manual
[LIST]
[*]Again, great, except the "After" shows 100% HDD allocated to 8.10
[/LIST]
[/LIST]

I'm too scared to go beyond this point with either options 3 or 4, because first time I installed Ubuntu I managed to delete all my partitions by doing just one click too many! :confused:

Just use Manual (clicking next doesn't do anything, it's just take you to the partitioner tool), make a space wherever you want and format it. I would recommend you to use a shared home folder, but if you don't want to mess like that, just make space for 8.10 as I said and set it's mount point as "/", next, next, finish.

Advantages of separated home partition:

[LIST]
[*]No more pain, you won't have to worry about losing data when you install a new version of Ubuntu ever again, or any other distro.

[*]You won't lose your personal settings
[/LIST]

---

### Post by UltraAnders on 2009-01-20
Ah thanks, so I'm just being over cautious (stupid) :wink: Showing the "After" with 100% of HDD allocated to 8.10 is misleading.

8.04's home directory is stored on the largest partition, as will 8.10's.

---

