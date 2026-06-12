---
title: "cannot create anymore primary partition"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by beew on 2010-12-09
Hello,

I have a hard disk partitioned to dual boot between  Ubuntu 10.10 and Fedora 14. I would like to add a few more distros but I realized that I had already 4 primary partitions and the installers for other distros don't seem to allow me to create a logical partition on the free space. I am sure there are some work around because some guys on the forum have 9 distros or something installed on the same hard disk. I just don't know how.

Thanks in advance for any advice.

P.S. If there is no other way I can reinstore Fedora though I would prefer not having to do it.
Also It seems that gparted labels partitions rather randomly. So in my Maverick installation I have something like / in sdb1, home and swap in sdb5 and sdb6, whereas when I added Fedora, it was installed in sdb2 and sdb3 (/ and /home) Is there a way to change the labels?

---

### Post by coffeecat on 2010-12-09
The only way of getting more than 4 partitions in a disc with an mbr partition table with 4 primary partitions, is to delete one primary partition and replace that with an extended partition. You do not use an extended partition directly; it is a container for as many logical partitions as you wish - up to a limit I can't remember but which is more than you'll ever need. :wink:

> **beew said:**
> Also It seems that gparted labels partitions rather randomly. So in my Maverick installation I have something like / in sdb1, home and swap in sdb5 and sdb6, whereas when I added Fedora, it was installed in sdb2 and sdb3 (/ and /home) Is there a way to change the labels?

In fact it is quite logical. Partitions numbered sdx1 to sdx4 are either primary partitions or an extended partition. Numbers sdx5 and upwards are logical partitions - they can be nothing else. That is why you sometimes get gaps between sdx1 and sdx5.

If you need help with your partitioning, post the output of:

```
sudo fdisk -lu
```

---

### Post by oldos2er on 2010-12-09
You'd need to get rid of one primary partition, which would allow you to create an extended partition with as many logical partitions inside it as you would need (or have space for). An extended logical partition counts as one primary.

Or add another hard disk, if possible.

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> I am sure there are some work around because some guys on the forum have 9 distros or something installed on the same hard disk. I just don't know how.


Cough ... cough, that's me :P

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8485    68155731    6  FAT16
/dev/sda2            8486       21538   104848222+  83  Linux
/dev/sda4           21540       60802   315374512    f  W95 Ext'd (LBA)
/dev/sda5           21540       34593   104856223+   7  HPFS/NTFS
/dev/sda6           34594       37204    20972826   83  Linux
/dev/sda7           37205       39815    20972826   83  Linux
/dev/sda8           39816       42426    20972826    7  HPFS/NTFS
/dev/sda9   *       42427       45037    20972826   83  Linux
/dev/sda10          45038       47648    20972826   83  Linux
/dev/sda11          47649       50259    20972826   83  Linux
/dev/sda12          50260       52870    20972826   83  Linux
/dev/sda13          52871       55481    20972826   83  Linux
/dev/sda14          55482       58092    20972826   83  Linux
/dev/sda15          58093       60315    17853440   83  Linux
/dev/sda16          60315       60802     3907584   82  Linux swap / Solaris

```

sda1 and sda2 are the only Primary Partitions I got and I did not format them yet, these two partitions are unused. I keep them for future usage.

You see I have many Logical Partitions. You know Linux has no problem to be installed on Logical Partitions.
Having 4 Primary Partitions on a machine running Linux is totally unnecessary if you ask me :)

The only way is to remove one of your Primary Partitions as Coffeecat suggested.

---

### Post by 3L33T on 2010-12-09
> **oldos2er said:**
> You'd need to get rid of one primary partition, 


EXACTLY!!!

If possible, backup the 4th partition and drop it using fdisk.  This will bring your total partitions to 3.  Now add a fourth partition as an 'extended' (not primary!) partition and accept the default beginning and ending cylinder.  This will allow you to have X amount of extra partitions on the disk.  Add the 5th, 6th, 7th partitions as 'primary'.

---

### Post by beew on 2010-12-09
Thanks for the quick reply.

Based on your input here I am going to do the following. Please tell me if it makes sense. 

I am going to delete the Fedora /home partition (25G) and create an extended partition ~200 G I will then create the Fedora home partition  inside and also partitions for other distros.

Or do you think it would be more elegant to delete Fedora all together. Turning the whole hard disk into Ubuntu + extended partition and then reinstall Fedora (and also other things) inside the extended partition so that Fedora would be entirely within the extended partition, rather than just the /home part.

Since I am using grub2 in Ubuntu to boot, am I correct in thinking that deleting Fedora would have no effect on booting except I need to do sudo update-grub in Ubnuntu to remove the Fedora entry in the boot menu?

---

### Post by beew on 2010-12-09
> You see I have many Logical Partitions. You know Linux has no problem to be installed on Logical Partitions.

So how come I can't just install another distro and make / a logical partition? It doesn't let me.

---

### Post by coffeecat on 2010-12-09
If you reinstall Fedora after Ubuntu, you won't be able to boot into Ubuntu until you repair Ubuntu's grub. Fedora will blithely install legacy grub with no option for other Linux distros, a hidden menu and a timeout of 0 iirc. :-s.

Enjoy. :wink:

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> Or do you think it would be more elegant to delete Fedora all together. Turning the whole hard disk into Ubuntu + extended partition and then reinstall Fedora (and also other things) inside the extended partition so that Fedora would be entirely within the extended partition, rather than just the /home part.

That's what I would do if I were you :)

> 
Since I am using grub2 in Ubuntu to boot, am I correct in thinking that deleting Fedora would have no effect on booting except I need to do sudo update-grub in Ubnuntu to remove the Fedora entry in the boot menu?

As long as Fedora's boot loader is NOT installed in the MBR and Ubuntu's boot loader is installed in the MBR, YES, there's no problem at all.

I installed 7 Linux Distributions and with one command:

```
sudo update-grub

```

I got them all to boot without any issue.
However, you need to make sure NOT to install any other boot loader in the MBR as long as you want ONE boot loader to take the control over the others.

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> So how come I can't just install another distro and make / a logical partition? It doesn't let me.

You already have 4 Primary Partitions as you said, that's why.

As I said, I have two Primary Partitions and ALL the other are Logical. I can play around with these Logical and create even more.

---

### Post by beew on 2010-12-09
Sorry for being dense,  are the partitions inside the extended one logical or primary?

---

### Post by amjjawad on 2010-12-09
> **coffeecat said:**
> If you reinstall Fedora after Ubuntu, you won't be able to boot into Ubuntu until you repair Ubuntu's grub. Fedora will blithely install legacy grub with no option for other Linux distros, a hidden menu and a timeout of 0 iirc. :-s.

Enjoy. :wink:

Beew, Coffeecat is right. I'm sorry about my other post. Unfortunately, I have tried to install Fedora after Ubuntu but it couldn't detect Ubuntu, it could only detect Windows.

---

### Post by coffeecat on 2010-12-09
> **beew said:**
> So how come I can't just install another distro and make / a logical partition?

Yes, you can. Any Linux partition can be a logical one. As amjjawad points out, your difficulty may be because you are hitting the 4 primary partition limit.

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> Sorry for being dense,  are the partitions inside the extended one logical or primary?

Any partition inside the "extended" area is **Logical** :)

---

### Post by beew on 2010-12-09
> **amjjawad said:**
> You already have 4 Primary Partitions as you said, that's why.

As I said, I have two Primary Partitions and ALL the other are Logical. I can play around with these Logical and create even more.


It seems that you are not using extended partitions, am I right?

Ok, now if I simply change the Fedora /home partition to logical I would have only 3 primary (Ubuntu / Ubuntu /home and Fedora /) Are you saying that I can then I can  simply create a bunch of logical partitions and install other distros in them?

---

### Post by coffeecat on 2010-12-09
> **beew said:**
> Sorry for being dense,  are the partitions inside the extended one logical or primary?

No, you're not being dense. It's very confusing. You have logicals inside an extended. You can only have one extended per HD, which replaces a primary. In fact, think of an extended as a special type of primary whose only purpose is to act as a container for logical partitions.

---

### Post by coffeecat on 2010-12-09
> **beew said:**
> It seems that you are not using extended partitions, am I right?

Put 'extended partition' in the singular, and you are right. In fact amjjawad's partition layout is a very good illustration. Thanks, amjjawad! :)

**Edit:** Oops -misread you. You are not right. amjjawad is using an extended partition.

sda1 and sda2 are primaries. sda4 is the **only** extended. And sda5 upwards are all logicals - remember what I said about numbering earlier - and if you look at the start and end figures you'll see how sda5 to sda16 are all inside sda4.

So that we can all have a game of post your partition layout, here's mine:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2079   199222064    99609993    7  HPFS/NTFS
/dev/sda2       199231488   419432447   110100480    7  HPFS/NTFS
/dev/sda3       419434494   976773119   278669313    f  W95 Ext'd (LBA)
/dev/sda5       419434496   427823103     4194304   82  Linux swap / Solaris
/dev/sda6       427825152   532682751    52428800   83  Linux
/dev/sda7       532684800   637542399    52428800   83  Linux
/dev/sda8       637544448   679487487    20971520   83  Linux
/dev/sda9       679489536   721432575    20971520   83  Linux
/dev/sda10      721434624   763377663    20971520   83  Linux
/dev/sda11      763379712   805322751    20971520   83  Linux
/dev/sda12      805324800   847267839    20971520   83  Linux
/dev/sda13      847269888   878727167    15728640   83  Linux
/dev/sda14      878729216   910186495    15728640   83  Linux
/dev/sda15      910188544   941645823    15728640   83  Linux
/dev/sda16      941647872   976773119    17562624   83  Linux

```Your assignment: which partition is my extended one? :wink:

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> It seems that you are not using extended partitions, am I right?

No, you're not right :D

I'll try to explain this in my way. The Extended Partition is not a Partition that you can use Physically. It's like a case and inside that case, Logical Partition(s) may be created.

The Logical Partitions are the Partitions you can Physically access.

I have attached a screen shot of my partitions. You see the 2 black partitions? these are unused Primary Partitions. On the right side, there's a big green area which is the Extended Partition. Inside that Partition (remember the case), ALL the other Logical Partitions are exist.

This is how I made it.


> 
Ok, now if I simply change the Fedora /home partition to logical I would have only 3 primary (Ubuntu / Ubuntu /home and Fedora /) Are you saying that I can then I can  simply create a bunch of logical partitions and install other distros in them?In another easier words: ALL what you have to do is:
1- Remove one of the 4 Primary Partitions
2- You'll get unallocated Space
3- Create Extended Partition
4- Inside that Extended Partition, you could create as many Logical Partition as you want.

:)

---

### Post by beew on 2010-12-09
Ok, I just realized what I said didn't make sense, I can just recreate a Fedora /home partition without running the Fedora installer again. In that case I may as well delete Fedora and reinstall.

Now if I do that do I need to create an extended partition if I stay below the 4 primary limit, or can I just install in logical partitions?

Also would running sudo upgrade-grub remove the no longer exist Fedora entry in the boot menu?

Thanks everyone for the help. I will do this tonight and hopefully it all works.

---

### Post by beew on 2010-12-09
> **coffeecat said:**
> 
[/code]Your assignment: which partition is my extended one? :wink:


Why. sda3? :)

---

### Post by beew on 2010-12-09
> **amjjawad said:**
> No, you're not right :D

I'll try to explain this in my way. The Extended Partition is not a Partition that you can use Physically. It's like a case and inside that case, Logical Partition(s) may be created.

The Logical Partitions are the Partitions you can Physically access.

I have attached a screen shot of my partitions. You see the 2 black partitions? these are unused Primary Partitions. On the right side, there's a big green area which is the Extended Partition. Inside that Partition (remember the case), ALL the other Logical Partitions are exist.

This is how I made it.


In another easier words: ALL what you have to do is:
1- Remove one of the 4 Primary Partitions
2- You'll get unallocated Space
3- Create Extended Partition
4- Inside that Extended Partition, you could create as many Logical Partition as you want.

:)

Thanks my friend. Got it. Why do you keep two unused primary partitions? For Windows? :)

---

### Post by amjjawad on 2010-12-09
You're too fast my friend, give me sometime to breath :P hahaha.

Please, first of all, read [this post]("http://ubuntuforums.org/showpost.php?p=10219533&postcount=18").

Are you okay with that? if yes, then we could carry on :)

---

### Post by nm_geo on 2010-12-09
Beew you need to run boot_info_script and post.  

Here   [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by beew on 2010-12-09
Yep, that is very clear. So I am going to have to reinstall Fedora. Thankfully it installation is really fast (even faster than U!)

---

### Post by beew on 2010-12-09
> **nm_geo said:**
> Beew you need to run boot_info_script and post.  

Here   [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I can't right now as I am not at home. What is that for?

I don't have Fedora's bootloader installed, so I am using Ubuntu's grub.

---

### Post by nm_geo on 2010-12-09
> **beew said:**
> Yep, that is very clear. So I am going to have to reinstall Fedora. Thankfully it installation is really fast (even faster than U!)
  I would still run the boot_info_script and save results.  It may help you in the future.

It clearly shows your partitions and info on the Grub/Grub2 stuff.

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> Thanks my friend. Got it. Why do you keep two unused primary partitions? For Windows? :)

ROFL :D
I was just posting and asking you to slow down :) hahahah.

Okay, are you sure you got it? :)

Well, I don't need that much space and I thought I would install (God Forbid) Windows or any other OS on these two Primary Partitions but I don't think so. I'm keeping them for any future plans. After all, this current setup of mine is not final :) I'm still learning about Linux every day and once I feel confident, I'm going to blow it up and do something more complicated :P

If you have large HDD, it's good idea to keep unused space for future plans.

---

### Post by coffeecat on 2010-12-09
@beew, one for your bookmarks. :wink:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by beew on 2010-12-09
> **amjjawad said:**
> ROFL :D
I was just posting and asking you to slow down :) hahahah.

Okay, are you sure you got it? :)

Well, I don't need that much space and I thought I would install (God Forbid) Windows or any other OS on these two Primary Partitions but I don't think so. I'm keeping them for any future plans. After all, this current setup of mine is not final :) I'm still learning about Linux every day and once I feel confident, I'm going to blow it up and do something more complicated :P

If you have large HDD, it's good idea to keep unused space for future plans.

How big is your hdd? I am installing in an external hdd about 320 G. The Ubuntu installation is final, probably the Fedora one as well, Then i am planning to install a bunch of other things for experiment and those can change. That's why I was a bit hesitant to install Fedora in an extended partition with all the others. But now it seems that i have to.  :)

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> I don't have Fedora's bootloader installed, so I am using Ubuntu's grub.

Don't be confused here :)
Take a breathe and allow me to explain that.

Fedora gives you two options based on your setup.

a) Are you installing Fedora as the first OS on that machine?

b) Are you installing Fedora as another OS on that machine and you have another OS installed already?

Based on these two cases, you can install the boot loader either in the MBR (case a) or in the root partition where Fedora is installed (case b).

That's the default and that's what had been mentioned in Fedora's Installation Guide. I just re-phrase it my way.

In your case, Ubuntu's Bootloader (GRUB2) is taking the full control.
GRUB2 is amazing. I would never install 9 OS's on my machine without GRUB2. I don't really want to sit and configure GRUB Legacy to boot all these Systems.

If you're going to remove Fedora's Partitions to create extended partition and inside that you'll create Logical Partitions, be careful that Fedora will not detect Ubuntu.

Are you going to remove /home Partition from Fedora? or are you going to remove both Fedora's root and home partitions?

---

### Post by amjjawad on 2010-12-09
> **coffeecat said:**
> @beew, one for your bookmarks. :wink:

[https://help.ubuntu.com/community/howtopartition](https://help.ubuntu.com/community/howtopartition)

+10

:)

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> How big is your hdd? I am installing in an external hdd about 320 G. The Ubuntu installation is final, probably the Fedora one as well, Then i am planning to install a bunch of other things for experiment and those can change. That's why I was a bit hesitant to install Fedora in an extended partition with all the others. But now it seems that i have to.  :)

As shown in the screen shot I posted in Post#18, I got 465GB (500GB).
It's not external though.

As long as I'm learning, there's nothing final. I always say it's final but that never happened in my case. I brought another PC for experiments but looks like I'll use both for that :D

---

### Post by beew on 2010-12-09
> **amjjawad said:**
> Don't be confused here :)
Take a breathe and allow me to explain that.

Fedora gives you two options based on your setup.

a) Are you installing Fedora as the first OS on that machine?

b) Are you installing Fedora as another OS on that machine and you have another OS installed already?

Based on these two cases, you can install the boot loader either in the MBR (case a) or in the root partition where Fedora is installed (case b).

That's the default and that's what had been mentioned in Fedora's Installation Guide. I just re-phrase it my way.

In your case, Ubuntu's Bootloader (GRUB2) is taking the full control.
GRUB2 is amazing. I would never install 9 OS's on my machine without GRUB2. I don't really want to sit and configure GRUB Legacy to boot all these Systems.

If you're going to remove Fedora's Partitions to create extended partition and inside that you'll create Logical Partitions, be careful that Fedora will not detect Ubuntu.

Are you going to remove /home Partition from Fedora? or are you going to remove both Fedora's root and home partitions?

I installed Fedora with the manual option and chose not to install a bootloader. 

I am thinking of removing Fedora all together and reinstall it inside the extended partition. It seems this is the only way.

---

### Post by amjjawad on 2010-12-09
> **coffeecat said:**
> In fact amjjawad's partition layout is a very good illustration. Thanks, amjjawad! :)


Thank you, mate :)
I should have posted the screen shot earlier because (IMHO) it's much easier to understand that from a picture than words :)

---

### Post by coffeecat on 2010-12-09
@beew, another comment about Fedora's installer and then I have to log off for a couple of hours.

I suggest you prepare your partitions beforehand with Ubuntu's Gparted. Then use the Fedora equivalent of Ubuntu's manual/advanced option at the partitioning stage (sorry, can't remember what it is called at the moment) so you can point it to the partitions you want and choose the filesystems you want, rather than what the Fedora devs think is right for the world. :rolleyes:. If you don't, you will end up with a separate Fedora boot partition and, worse, an LVM partition for Fedora's root. LVM is a great idea but, believe me, you don't want to go there just yet!

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> I installed Fedora with the manual option and chose not to install a bootloader. 

I am thinking of removing Fedora all together and reinstall it inside the extended partition. It seems this is the only way.


Do me a favor because I can't seem to remember how did I install Fedora on my machine (I got two, GNOME and LXDE).
When you go back home, if you're planning to remove Fedora completely, then do it. When you're trying to re-install it after you create Logical Partitions inside The Extended Partition, choose not to install Fedora's boot loader OR choose to install the boot loader in Fedora's root partition. 

For example: If Fedora's will get sda6 and sda7 where sda6 is root and sda7 is home, try to install the boot loader in sda6. 
Then:
```
sudo update-grub

```
Should do the job needed.


OR ... don't install the bootloader BUT I've never done that ... I mean, I always install the boot loader but I choose where to install it (either MBR or the root partition).

If that's so much complicated to understand, please ignore this post :D

---

### Post by amjjawad on 2010-12-09
Beew, I also advise you to register in [Fedora's forum]("http://fedoraforum.org/").
I've done that long time ago. Someone there, can't remember the name ... he/she was so much helpful and direct to the point.

Sooner or later, you'll need to consult them so it's good idea to do it :)

---

### Post by beew on 2010-12-09
> **coffeecat said:**
> @beew, another comment about Fedora's installer and then I have to log off for a couple of hours.

I suggest you prepare your partitions beforehand with Ubuntu's Gparted. Then use the Fedora equivalent of Ubuntu's manual/advanced option at the partitioning stage (sorry, can't remember what it is called at the moment) so you can point it to the partitions you want and choose the filesystems you want, rather than what the Fedora devs think is right for the world. :rolleyes:. If you don't, you will end up with a separate Fedora boot partition and, worse, an LVM partition for Fedora's root. LVM is a great idea but, believe me, you don't want to go there just yet!

Thanks. That was what I did before (the advanced option).  I chose ext4.

---

### Post by beew on 2010-12-09
> **amjjawad said:**
> Beew, I also advise you to register in [Fedora's forum]("http://fedoraforum.org/").
I've done that long time ago. Someone there, can't remember the name ... he/she was so much helpful and direct to the point.

Sooner or later, you'll need to consult them so it's good idea to do it :)

Thanks for the patient help my friend. I will sign up for that. :)

---

### Post by beew on 2010-12-09
> **amjjawad said:**
> Do me a favor because I can't seem to remember how did I install Fedora on my machine (I got two, GNOME and LXDE).
When you go back home, if you're planning to remove Fedora completely, then do it. When you're trying to re-install it after you create Logical Partitions inside The Extended Partition, choose not to install Fedora's boot loader OR choose to install the boot loader in Fedora's root partition. 

For example: If Fedora's will get sda6 and sda7 where sda6 is root and sda7 is home, try to install the boot loader in sda6. 
Then:
```
sudo update-grub

```Should do the job needed.


OR ... don't install the bootloader BUT I've never done that ... I mean, I always install the boot loader but I choose where to install it (either MBR or the root partition).

If that's so much complicated to understand, please ignore this post :D

I just installed Fedora's KDE edition.  Quite impressed with both Fedora and KDE except for the software manager. :(

I have read many posts on the forum before I installed, it seems that not installing the boot loader and run sudo update-grub in Ubuntu was the best way for my purpose so I did that.

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> Thanks for the patient help my friend. I will sign up for that. :)

You know I'm always here if you need me :)

Beew, one more thing :)
When you go back home, read this entire thread again. Make sure you understand everything. After that, go for it.

By the way, what time you'll go back home? I might be online. It's 6:35pm GMT now.

---

### Post by beew on 2010-12-09
It is 1:40pm right now (Toronto) so I will probably work on it around 8 or 9 pm and you would probably be in bed. :) But thanks for the great help! Will definitely read the thread again to make sure I understand everything.

---

### Post by srs5694 on 2010-12-09
> **beew said:**
> I have a hard disk partitioned to dual boot between  Ubuntu 10.10 and Fedora 14. I would like to add a few more distros but I realized that I had already 4 primary partitions and the installers for other distros don't seem to allow me to create a logical partition on the free space.
...
Also It seems that gparted labels partitions rather randomly. So in my Maverick installation I have something like / in sdb1, home and swap in sdb5 and sdb6, whereas when I added Fedora, it was installed in sdb2 and sdb3 (/ and /home) Is there a way to change the labels?

First, are the partitions you mention in this last paragraph on the same computer you're describing in the first paragraph? If so, you've clearly already got an extended partition. Perhaps you can't create logical partitions because the free space is outside of the extended partition. You really *must* post either the output of "sudo fdisk -lu" (between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility) or a screen shot of GParted showing your disk. Without that information, we're advising you blindly. I'll proceed with some more blind advice, but I won't post again unless/until I can see what sort of setup you've got.

Second, for some further blind advice: If you do indeed have four primary partitions and no extended partition, one other way to proceed is to convert the disk to use the GUID Partition Table (GPT) format rather than the older Master Boot Record (MBR) format. GPT eliminates the confusing and awkward distinction between primary, extended, and logical partitions. Instead, you can have up to 128 partitions (by default). If your space is laid out awkwardly in MBR format because of primary/extended/logical issues, converting to GPT may fix the problem. You can do the conversion by running [GPT fdisk (gdisk)](http://sourceforge.net/projects/gptfdisk/files/) on the disk; just launch gdisk ("gdisk /dev/sda") and then save the partition table with the "w" option on the menu.

Before you jump in with this conversion, though, be aware that you *will* have to re-install GRUB when you're done. Although not strictly necessary, a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) is very helpful on GPT disks, so be prepared to create one (using gdisk or GParted) before you re-install GRUB. Also, Windows can't boot from GPT disks on BIOS-based computers, so if you have a Windows installation or think you might add one in the future, converting to GPT may not be the best approach. (There are ways around Windows' aversion to GPT, but they're ugly and dangerous.)

---

### Post by beew on 2010-12-09
srs5649

All the partitions exist in one single external hard drive. I plug it into whatever computer I could lay my hands on and as long as it doesn't require proprietary graphic driver I am good to go.

It has one extended partition which includes the Ubuntu /home partition and the swap space. It has another three primary partitions : Ubuntu /root, Fedora /root and Fedora /home and the rest of the disk is unformatted.

I have to take some times to digest your post as it seems to involve something complicated. :)  As I said before my Ubuntu installation is considered final so I don't want to do anything that may risk it unnecessarily. I am not a pro, you know. :)

But thanks for the advice, will definitely try to understand it. It will come in  handy eventually i am sure, if not this time.

---

### Post by nm_geo on 2010-12-09
Beew as you were advised earlier when you re-install Fedora make sure you again place the old grub loader in the first Fedora partition.  I speak from recent experience here for short while my Ubuntu was not available because I let Fedora install the old grub setup.

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> It has **one extended partition** which includes the Ubuntu /home partition and the swap space. It has another three primary partitions : Ubuntu /root, Fedora /root and Fedora /home and the rest of the disk is **unformatted**.

I guess srs5649 is right and I think we all were too rushy to reply your post without seeing the result of "fdisk -l" or a screen shot for GParted (like the one I posted earlier).

Final suggestion: First thing to do when you get back home, post back the result of:

```
sudo fdisk -l

```

and a screen shot for GParted that shows ALL your Partitions clearly.

I don't want to assume anymore but formatting the "unformatted" space might fix the issue IF AND ONLY IF that unformatted space is within the "extended partition already". If it's NOT inside the extended partition then you need to to do some changes.

I know you'll post back when you get home so I'll be waiting. Even though I'll be ZzZz, I'll check that once I'll wake up :)

---

### Post by beew on 2010-12-09
> **nm_geo said:**
> Beew as you were advised earlier when you re-install Fedora make sure you again place the old grub loader in the first Fedora partition.  I speak from recent experience here for short while my Ubuntu was not available because I let Fedora install the old grub setup.

Actually I chose not to install Fedora's grub at all. I know about the problem you speak of, so I have researched on that before I installed. But thanks for the reminder man!

---

### Post by beew on 2010-12-09
> **amjjawad said:**
> I guess srs5649 is right and I think we all were too rushy to reply your post without seeing the result of "fdisk -l" or a screen shot for GParted (like the one I posted earlier).

Final suggestion: First thing to do when you get back home, post back the result of:

```
sudo fdisk -l

```and a screen shot for GParted that shows ALL your Partitions clearly.

I don't want to assume anymore but formatting the "unformatted" space might fix the issue IF AND ONLY IF that unformatted space is within the "extended partition already". If it's NOT inside the extended partition then you need to to do some changes.

I know you'll post back when you get home so I'll be waiting. Even though I'll be ZzZz, I'll check that once I'll wake up :)

Thanks dude. Will definitely do that. :)

---

### Post by amjjawad on 2010-12-09
> **beew said:**
> Thanks dude. Will definitely do that. :)

I know you will and hey, no thanks between friends ;)

Now, I'll go to eat something and have some rest. Will check later and hope I will see "SOLVED" before I read anything else :D

Good luck and believe in yourself, you could do it ;)

---

### Post by amjjawad on 2010-12-09
I really can't get rid of my addiction to computers :)

Anyway, I can't wait until you reach home, post back and wake up to read that. I'm going to do it :D
I have another PC. I have Ubuntu 10.04 installed on sda and XP installed on sdb. I'm going to Install Fedora 13 (GNOME) while Ubuntu is already installed.

I'll let you know the outcome so that you could do it faster and easier ;)
Beside, I need to refresh my memory about Fedora.

---

### Post by coffeecat on 2010-12-09
> **amjjawad said:**
>  I'm going to Install Fedora 13 (GNOME) while Ubuntu is already installed.

Not Fedora 14? It's been out at least a month. I'm looking forward to 15. :p

---

### Post by amjjawad on 2010-12-09
> **coffeecat said:**
> Not Fedora 14? It's been out at least a month. I'm looking forward to 15. :p

No, I'm going to install 13 :)
I hope the developers would replace GRUB Legacy with GRUB2 and make Anaconda (Fedora's Installation Program) detect other Linux Systems, not only Windows.

I downloaded 14 but looks like the file is corrupted. I didn't bother to download it again. I have so much iso files downloaded already so I'm really tired of downloading :D

I chose to install Fedora's Bootloader in the first sector of the boot partition which is root. I know Fedora recommends to create 3 partitions (boot, root and home) of course beside swap but I'm doing it in Ubuntu's way :D

---

### Post by amjjawad on 2010-12-09
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Fedora release 13 (Goddard) on /dev/sda6
Found Microsoft Windows XP Professional on /dev/sdb1
done

```

```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381   83  Linux
/dev/sda2            1306        3916    20972857+  83  Linux
/dev/sda3            3917        9729    46692892    5  Extended
/dev/sda5            9469        9729     2096451   82  Linux swap / Solaris
/dev/sda6            3917        5221    10482349+  83  Linux
/dev/sda7            5222        7179    15727603+  83  Linux

```


That's the magic of GRUB2 :)

I was sure about that but didn't post it, I thought it would be much better to try it first.
You could INSTALL GRUB Legacy (Fedora's bootloader) on Fedora's Root/Boot Partition - which is sda6 in my case - and that would cause any problem as long as GRUB2 is able to detect it.

I was able to boot into Ubuntu successfully after Fedora's Installation. As long as you don't mess with the MBR, you're good to go.

Will post later some screen shots that might be helpful for beew and everyone else.

:)

---

### Post by amjjawad on 2010-12-09
Note that XP is installed on sdb so the screenshots will not show that ;)

Enjoy!

P.S.
The unallocated area is INSIDE the Extended Partition. I don't need that space as of now. Before Installing Fedora, I was keeping around +40GB unused for future plan. Guess that future was sooner than what I expected :D

---

### Post by beew on 2010-12-09
Ok, here is a screenshot of my partition configuration. From left to right, the last two blocks before the unallocated space are Fedora /root and /home.

Now I tried to delete these two and merge them with the unallocated space and then create a big extended partition, but the only option is "primary". "Logical" and "extended" are not avaliable. Am I only allowed one extended partition? In that case would I be able to extend the one that currently contains Ubuntu's /home and swap? Do I need to format the unallocated space first?

Thanks.


Edited: Ok Now I have deleted the Fedora partitons and grew the extended partition to include all the unallocated space, off to reinstall Fedora..

---

### Post by amjjawad on 2010-12-10
> **beew said:**
> Ok, here is a screenshot of my partition configuration. From left to right, the last two blocks before the unallocated space are Fedora /root and /home.

Now I tried to delete these two and merge them with the unallocated space and then create a big extended partition, but the only option is "primary". "Logical" and "extended" are not avaliable. Am I only allowed one extended partition? In that case would I be able to extend the one that currently contains Ubuntu's /home and swap? Do I need to format the unallocated space first?

Thanks.


Edited: Ok Now I have deleted the Fedora partitons and grew the extended partition to include all the unallocated space, off to reinstall Fedora..

You're allowed to have ONE Extended Partition. Inside that partition, you're allowed to have many Logical Partitions.

The screenshot you provided was before you delete the last two partitions, right?
Your main problem was: Your Extended Partition was very limited and didn't take the whole available space.

I hope you could post another screenshot to make sure you're in the right path.

I found similar case to yours in the forum. Someone else has exactly the same problem. You guys have two options:

1- Expand the Extended Partition
[B]
or[/B]

2- Create two large Primary Partitions

The advantage of the first option is: You could have more Partitions (Logical).
The DISadvanage of the second option is: You can have ONLY two more partition.

I would unquestionably go for option one. Having many partitions is the best option.

I assume you managed to fix that problem ;)
Waiting to see your updated partitions ;)

---

### Post by beew on 2010-12-10
Thanks to everyone it is fixed! 

I have expanded the extended partition to include Ubuntu's /home, the swap area and the unformatted space. I then installed Fedora in the unformatted space within the extended partition. Like before I chose not to install Fedora's GRUB, booted back to Ubuntu and run "sudo update-grub" to add Fedora to the boot menu. Everything works.


Afterwards I tried to install Mint LMDE in a partition carved out from the left over space, the installer didn't complain that there were too many primary partition. Only that the installation hung at "calculating file indexes" or something like that but that is a different issue that has to do with Mint.

So problem solved.!! :)

---

### Post by beew on 2010-12-10
> **amjjawad said:**
> You're allowed to have ONE Extended Partition. Inside that partition, you're allowed to have many Logical Partitions.

The screenshot you provided was before you delete the last two partitions, right?
Your main problem was: Your Extended Partition was very limited and didn't take the whole available space.

I hope you could post another screenshot to make sure you're in the right path.

I found similar case to yours in the forum. Someone else has exactly the same problem. You guys have two options:

1- Expand the Extended Partition
[B]
or[/B]

2- Create two large Primary Partitions

The advantage of the first option is: You could have more Partitions (Logical).
The DISadvanage of the second option is: You can have ONLY two more partition.

I would unquestionably go for option one. Having many partitions is the best option.

I assume you managed to fix that problem ;)
Waiting to see your updated partitions ;)

Thanks my friend, I did go for option 1, all great minds think alike. :)

---

### Post by amjjawad on 2010-12-10
> **beew said:**
> Thanks my friend, I did go for option 1, all great minds think alike. :)

Before I say: 
> HOOHAA, WELL DONE :DI want to see a screenshot of your partitions ;)

The next step is: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

:D

You just need to understand the basics and I'm sure you won't have any problem.
If you have an old HDD or even a USB Drive that you don't need, it's good idea to do some tests on these so that you'll understand even better.

Come on, where's the screenshot :D hahaha

[U][B]Edit:
[/B][/U]The screenshot (the updated one) will help others to understand what exactly you have done + I want to make sure you're in the right track.

:)

---

### Post by beew on 2010-12-10
> **amjjawad said:**
> No, I'm going to install 13 :)
I hope the developers would replace GRUB Legacy with GRUB2 and make Anaconda (Fedora's Installation Program) detect other Linux Systems, not only Windows.

  

I wouldn't bet on that. In Fedora 14 it offers several install options and the default one (pre checked) is to erase other Linux partitons! They apparently only expect you to dual boot with Windows. I think the Fedora guys do have an attitude problem. :) I remember someone on this forum describing Fedora as the most anti-social Linux distro when it comes to dealing with other Linux distros, he may have a point.

---

### Post by amjjawad on 2010-12-10
> **beew said:**
> I wouldn't bet on that. In Fedora 14 it offers several install options and the default one (pre checked) is to erase other Linux partitons! They apparently only expect you to dual boot with Windows. **I think the Fedora guys do have an attitude problem.** :) I remember someone on this forum describing Fedora as the most anti-social Linux distro when it comes to dealing with other Linux distros, he may have a point.

Hahaha, looks like that :)
I tried OpenSUSE 11.3 and I installed it on PC2 (mine). It has amazing feature *(just like GRUB2) *to detect other OS's installed and to **edit **the GRUB entries even before the installation is done. I loved it. However, because OpenSUSE is still using GRUB Legacy, it was unable to detect VectorLinux. Check my signature and check PC2 :)
I changed that now. PC2 has: Ubuntu 10.04, Fedora 13 (thanks to you :D ) and XP on sdb.

With GRUB2, I don't care whether Fedora's guys are anti-social or whatever they're :D with GRUB2, I could do whatever I want.

I get bored too fast. So, who knows? perhaps my next step will be installing all the OS's I got on one machine :D hahaha. Just kidding ;)

---

### Post by beew on 2010-12-10
Here is the screenshot my friend. :)

---

### Post by amjjawad on 2010-12-10
> **beew said:**
> Here is the screenshot my friend. :)


**HOOOHAAA, WELL DONE **:D

That was exactly what I wanted to see. Great :D
Now, you could have many other "Logical" partitions inside that unallocated area.

WELL DONE :D
Please, read that HOWTO Coffeecat and me have posted. You'll have FULL idea.
We learn from our mistakes and I'm sure you'll never do the same mistake again. I mean having unallocated area outside the Extended Area :)

---

### Post by beew on 2010-12-10
Thanks again man. I will read those how tos for sure. Now it is 2am I am afraid I have to get some sleep. :) Take care!

---

### Post by amjjawad on 2010-12-10
> **beew said:**
> Thanks again man. I will read those how tos for sure. Now it is 2am I am afraid I have to get some sleep. :) Take care!

You welcome my friend and I'm so much glad you made it :)

Hahaha, definitely not now. You should sleep. I woke up 1 hour ago and jumped to my PC :)
Now, it's time for breakfast :D

I love this forum. Someone is about to sleep and someone else is about to start his day :D

---

### Post by JASONFUSARO on 2011-07-12
> **beew said:**
> Hello,

I have a hard disk partitioned to dual boot between  Ubuntu 10.10 and Fedora 14. I would like to add a few more distros but I realized that I had already 4 primary partitions and the installers for other distros don't seem to allow me to create a logical partition on the free space. I am sure there are some work around because some guys on the forum have 9 distros or something installed on the same hard disk. I just don't know how.

Thanks in advance for any advice.

P.S. If there is no other way I can reinstore Fedora though I would prefer not having to do it.
Also It seems that gparted labels partitions rather randomly. So in my Maverick installation I have something like / in sdb1, home and swap in sdb5 and sdb6, whereas when I added Fedora, it was installed in sdb2 and sdb3 (/ and /home) Is there a way to change the labels?




Your fourth partition needs to be an extended partition.

[CODE}
[root@archbang /]# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029370

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   133226495    66612224    7  HPFS/NTFS
/dev/sda2       133226496   133636095      204800   83  Linux
/dev/sda3       133636096   143876095     5120000   82  Linux swap / Solaris
[COLOR="Red"]**/dev/sda4       143878201   976773119   416447459+   f  W95 Ext'd (LBA)**[/COLOR]
/dev/sda5       143878203   164360191    10240994+  83  Linux
/dev/sda6       164361078   197124095    16381509   83  Linux
/dev/sda7       197126144   248326143    25600000   83  Linux
/dev/sda8       248328192   340488191    46080000   83  Linux
/dev/sda9       340490240   391690239    25600000   83  Linux
/dev/sda10      391692288   453132287    30720000   83  Linux
/dev/sda11      453134336   504334335    25600000   83  Linux
/dev/sda12      504336384   555536383    25600000   83  Linux
/dev/sda13      555538432   606738431    25600000   83  Linux
/dev/sda14      606740480   698900479    46080000   83  Linux
/dev/sda15      698902528   801302527    51200000   83  Linux
/dev/sda16      801304576   976773119    87734272   83  Linux








[root@archbang ~]# blkid
/dev/sda1: LABEL="WindowsVista" UUID="C65A6C105A6C0013" TYPE="ntfs" 
/dev/sda2: LABEL="MY_BOOT_GRUB" UUID="935626ef-4817-48f4-b690-f6bbaeea7df6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="49b2f37d-e3af-4a16-b7d3-be022adf39b8" TYPE="swap" 
/dev/sda5: LABEL="Distro-1_To Be D" UUID="196a9858-cc5e-4e14-b9e9-5ca5e21df982" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Chakra" UUID="ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda7: LABEL="UbuntuStudio64" UUID="f3a87410-015f-4d94-844e-4ec276cfedbc" TYPE="ext4" 
/dev/sda9: LABEL="CtkArch64" UUID="0920168c-5419-4412-8134-713ed2c3814c" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda10: UUID="ee7be487-f281-4072-9af3-72612c9a684c" TYPE="ext3" LABEL="ArchBang" 
/dev/sda11: UUID="52777f50-fd1d-42d8-9a17-5ad1ddf0b794" TYPE="ext3" SEC_TYPE="ext2" LABEL="UltimateEdition" 
/dev/sda12: LABEL="Toorox Gnome 64" UUID="91033a5b-7407-4a80-b1aa-07ff96202ee3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="Puppy" UUID="856f3983-f4e9-45da-b500-e199fefbbad1" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda14: LABEL="Zorin" UUID="06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda15: LABEL="Linux From Scrat" UUID="20610f96-41af-401a-956e-d077128f64d3" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda16: LABEL="Shared" UUID="9fb6e192-7b65-4aed-9922-cbc1a94eed6e" TYPE="ext2" 
/dev/sda8: LABEL="Distro-4 To Be d" UUID="b35a2191-0991-4040-8023-1bef352cf212" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="ReadyBoost-SysUtilities" UUID="8A9C26F89C26DE87" TYPE="ntfs" 

[/CODE]


Also there is a limit to how many logical partitions you can create in the extended partition, 16 this shouldn't be so but as I been Googling the problem it is apparently a Bug and I guess there are workarounds but I am gonna be happy with the 16 I have, it was hard enough getting my distros working, a couple of weeks over 8 hours a day, I am new to linux but I have alot of free time and it took some time indeed. I just got things going again and put up another thread, Multiple Distros Grub2 it may or may not be helpfull as I am real fresh at linux and have run into major problems more than once and I still have to tweak things here and there.

Good Luck

---

### Post by srs5694 on 2011-07-12
> **JASONFUSARO said:**
> Also there is a limit to how many logical partitions you can create in the extended partition, 16 this shouldn't be so but as I been Googling the problem it is apparently a Bug and I guess there are workarounds but I am gonna be happy with the 16 I have

The theoretical limit on logical partitions is approximately 2^31 (about 2 billion). Of course, that's an impractical theoretical limit that involves having a series of 1-sector partitions. As a practical matter, there are OS-specific limitations. I don't happen to know the Linux kernel's limit, but I do know it's well over 16; I once created a disk with over 100 logical partitions (I don't recall the exact value) as a test case and it was fine. That was with a Gentoo system, though; it's entirely possible that Ubuntu's got a limit as low as 16 because of the way it configures udev or some other relevant subsystem.

FWIW and IMHO, the more Linux partitions a disk has, the more it can benefit from using LVM rather than partitions for at least some of them. Managing a large number of Linux partitions over time becomes a nightmare. Indeed, just keeping them straight requires very diligent note-keeping. LVM makes this much easier by providing human-chosen labels for volumes and by removing the need to determine volume placement.

---

