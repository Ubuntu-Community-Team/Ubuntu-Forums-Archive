---
title: "How can I make a parition without data loss ??"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Windy Peaks on 2009-05-12
Ladies and Gentlemen of the Forum

Here's the thing, I am trying to use gnome parition manager on My laptop so I can add XP as a dual boot but can't get around the warning about losing all of My Ubuntu if I proceed with the parition steps.

Can anyone advise so I don't have to reformat everything.


Thanks in advance

Windy.

Problem solve (sort of anyway)

---

### Post by lisati on 2009-05-12
It's usually not so much that data loss *will* happen, but *might* happen. Your best safety measures are to (a) make a backup of ALL your important data (don't forget to make sure you have a usable recovery disk/partition available), and (b) defrag your Windows partition(s) two or three times.

---

### Post by acidsolution on 2009-05-12
if i am not wrong, you want to install windows on existing linux. 
In my opinion Gparted shuld work fine for partition. But once you install windows on linux machine your grub will be overwritten by windows .
so u need to restore grub.

---

### Post by Bigneil on 2009-05-12
it is easier to start with a blank hard disk and install windows first, then the ubuntu.:popcorn:   Back up all your personal files to an external drive or to DVDs before you do anything! .

---

### Post by Elfy on 2009-05-12
> **Ellen2 said:**
> And would like to suggest to use Wubi to install ubuntu.

The OP already has ubuntu installed ;)


@Windy Peaks - can you let us know what warning you are given - > but can't get around the warning about losing all of My Ubuntu 

You should be able to partition from the livecd, boot with it and then run Partition Editor from the Sys Admin menu.

Make sure to turn off the swap - right click the swap partition and there's an option to turn swap off.

Now you should be able to resize and create a partition from the unallocated space.

---

### Post by Windy Peaks on 2009-05-12
this is the error message when I select partition table.

WARNING: This will erase all data on the entire disk/dev/sda

I am aware of how to start from a naked (blank) hard disk and set up the partition to acomadate both Ubuntu and XP, I am trying to find away so that I don't have to trash my Ubuntu setup.
Yes You are correct I have Ubuntu already on this laptop.

Thanks for any light You can shed on this proplem.

Windy

---

### Post by Sef on 2009-05-12
> I am aware of how to start from a naked (blank) hard disk and set up the partition to acomadate both Ubuntu and XP, I am trying to find away so that I don't have to trash my Ubuntu setup.

Do you have a home partition or does Ubuntu take up the whole partition?

---

### Post by Windy Peaks on 2009-05-12
Yes You got it, I have Ubuntu and want to add xp as a dualboot put the problem is that when I use gparted and select the partition table I get "WARNING: This will ERASE ALL DATA on the ENTIRE DISK/dev/sba"

Any thoughts ???

Windy

---

### Post by Windy Peaks on 2009-05-12
Ubuntu is the only OS on the computer

---

### Post by Didius Falco on 2009-05-12
Windy,

Are you using Gparted from the System/Administration/Partition Editor menu? Because that warning you are getting sounds an awful lot like the first option on the installer partitioner...

Regards,

Didius

---

### Post by Windy Peaks on 2009-05-12
> **Didius Falco said:**
> Windy,

Are you using Gparted from the System/Administration/Partition Editor menu? Because that warning you are getting sounds an awful lot like the first option on the installer partitioner...

Regards,

Didius

Hey Bud:

I'm in Melbourne nice to hear from an Aussi.

How do I get into System/Administration/Partition Editor menu to run this Gparted program ??

---

### Post by Didius Falco on 2009-05-12
Windy,

Boot the Live CD with the "make no changes to the PC" option and when it finishes loading, go to **System/Administration/Partition Editor**.

That will open Gparted and you will be able to create your partition(s).

Sorry I took a while to answer - had dinner and a movie with the wife.

Regards,

Didius

---

### Post by Sef on 2009-05-14
**Back up** your **data** before trying any partitioning.   There is no 100% guarantee all will be successful without any data loss.

---

### Post by presence1960 on 2009-05-14
I would not get rid of Ubuntu and install windows first, which will take hours to install Windows, it's drivers, your programs, printer(s) & updates. That is a lot of work to only have to install Ubuntu again. I would install Windows without removing Ubuntu. You will need to restore GRUB, which only takes 5 minutes if you are slow!

But to your original problem. To create a partition for Windows from your Ubuntu partition boot from the Ubuntu Live CD and go System > Administration > Partition Editor. You want to right click on the partition you want to shrink to create the partition for Windows. Choose resize and then follow the prompts. You can resize the partition by dragging it's side or using the numeric sliders. Click OK. When the screen shows the new partition click Apply up top with green check mark next to it. see attached screen shot for choosing partition and right click menu.

---

### Post by Windy Peaks on 2009-05-14
Thanks for all Your help folks but I went ahead and reloaded both OS's after screwing up the live CD partitioning portion of Your advise.
I should have made a copy of my grub and created a rescure disk first I think????
next time then.

Windy

---

### Post by -kg- on 2009-05-15
Windy, if you read this again, the Community Documentation has a page that will explain the partitioning process in more detail:

[How To Partition]("https://help.ubuntu.com/community/HowtoPartition")

---

