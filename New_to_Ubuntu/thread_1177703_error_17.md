---
title: "error 17"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by devnull123 on 2009-06-03
I recently installed Ubuntu. But i wanted to go back to windows, so i ran Gparted and deleted all partitions and made a new one,applied changes and i rebooted and tried to install xp via iso and i got error 17. what can i do to fix it? im a noob so can you be as specific as possible?

what is the ideal settings for the working xp partition?

i plan on re installing ubuntu later.

---

### Post by LewRockwell on 2009-06-03
just use the windoze disk to format the disk

---

### Post by devnull123 on 2009-06-03
i cant the windows disk wont boot...when i deleted the original partition and tried to boot windows again i get the ubuntu error 17. i got gparted down to where it mentioned unallotted space but when a made the new partition and applied changes and rebooted i got error 17. no idea what to do.

---

### Post by anewguy on 2009-06-03
> **devnull123 said:**
> I recently installed Ubuntu. But i wanted to go back to windows, so i ran Gparted and deleted all partitions and made a new one,applied changes and i rebooted and tried to install xp via iso and i got error 17. what can i do to fix it? im a noob so can you be as specific as possible?

what is the ideal settings for the working xp partition?

i plan on re installing ubuntu later.

If you deleted all of the Ubuntu partitions, then what happened is this:

The master boot record on your boot (perhaps your only) hard disk says to load via grub from an Ubuntu partition.  With the partition gone, grub can't find anyway to boot.

Is there a solution?  Yes!  So please don't worry about that.  Now, I must admit that just off the top of my head I know about ways, but can't give you the specifics.  1 way is to use another PC, download a program called "fixmbr" from downloads.com, create a boot diskette or CD, place fixmbr on it, and after you boot from the media you can run fixmbr to correct it and you should be set to go. 

There is also a way to do it while booted from the LiveCD.  

It can also be done, if I remember correctly, with the super grub cd.

Right now I can't give you specifics - someone else may know them off the top of the head.

My suggestion is to check this link first:

[http://ubuntuforums.org/showthread.php?t=508927&highlight=restore+windows]("http://ubuntuforums.org/showthread.php?t=508927&highlight=restore+windows")

As far as booting Windows as mentioned above in another post, understand we're talking about booting the Windows INSTALLATION disk.  If you were dual-booting so you know you still have a Windows partition, follow the thread above.  If you have deleted all your partitions, you must start with the Windows INSTALLATION disk.  If an ISO, I'm not sure how you would do it BUT it must be a BOOTABLE image.  Right now you have nothing TO boot on your hard disk.

Dave :)

---

### Post by devnull123 on 2009-06-03
fixed...ty for the help...just reinstalled ubuntu...now i have to get back XP

---

### Post by balloooza on 2009-06-03
> fixed...ty for the help...just reinstalled ubuntu...now i have to get back XP
Rule #1 of ubuntu, if you can, install AFTER XP, in the long run it is just esier
I can't (like the other poster) remember how to do much grub stuff, and MBR stuff, but I can promis you, your life will be esier installng ubuntu AFTER xp, and just a tip, if you no longer want ubuntu, deleatyour home directory files, and launch a live disk deleat all in your /usr directory, and ubuntu will be a wee little partition on your hard drive, then boot windows, and (I do not know how to use windows, I assume it has some sort of recovery mode) and get windows to reinstall its bootloader (again, no clue) and THEN deleate ubuntu.

But I encourage you to try ubuntu, it has many things to teach.

---

### Post by anewguy on 2009-06-04
It's all up to you how you approach this - if you want dual boot or not.  But another option you might consider, if your machine specs are good, is to just run Ubuntu and run Windows in a virtual machine inside of Linux.  I would recommend VirtualBox myself.  It is one of a few available for free just by download.  If you do decide to use VirtualBox, be sure to download the free but NOT open source version - I think one version is called open-source and the other is somethings like PUEL or PEUL or some such thing.  At any rate, if you have a Windows installation disk, you can use it to install Windows in the virtual machine.  That way there is no fixed partition just for Windows - Windows "disk" actually just become a file to Ubuntu, and it dynamic and can grow.

Something things you should be aware of:

- if you're into gaming, wine or a virtual machine most likely won't satisfy you from what I've read.  I'm not a gamer myself, but there have been many posts on this forum about using windows in Linux, and most have indicated the video probably wouldn't be satisfactory for gamers.

- be sure to download and install the NON open open source version of virtualbox if you want any USB support (printers, cameras, basically anything USB connected).

Also, it is highly recommended to install Windows first, then Ubuntu.  When you have wiped your hard disk of partitions there is obviously no Windows installed to boot, hence why I mentioned before needing a bootable Windows installation media.  Since you just reinstalled Ubuntu, you might as well install Windows (again, a bootable installation disk is needed) then reinstall Ubuntu - that's the easiest way for beginners.

You mentioned before having an ISO of Windows.  I will assume you mean a CD (or dvd?) with the ISO burned to it.  If this disk doesn't boot - be sure to check the booting sequence in your BIOS setup - you may need to change it to say try the CD first, then the hard drive - yours may be set now to say try the hard drive.  Be sure you actually burned the CD from the ISO as an image, not just burning a typical data disk, or of course it won't work.

If worse comes to worse, grab a copy of one of the Windows boot disk images off the net (there are several places to get these) and use it to boot, then install from your Windows disk.  Earlier versions of Windows 98 and Windows98SE and backwards required a boot diskette.  I believe everything afterwards has always been a bootable installation CD (or DVD). If the disk you made from your ISO doesn't boot, and it's late Windows98 or higher, then you either made the disk incorrectly or the ISO you have doesn't have everything it should - in this case the boot loader and startup files.

Dave :)

---

### Post by neo.patrix on 2009-06-04
Usually it is better to plan your partitioning before installing Dual Operating systems like Windows & Linux , side by side. Generally you need main partitions for both OSes

C: - for Windows XP , it is a memory behemoth, as time passes it can consume lot of memory depending on usage patterns, how you get your security upgrades, IE, etc. About 15-17 GB , "primary" partition.

Just like C: , you need a root (/) partition for your Ubuntu, 4-5 GB is minimal requirement, although it depends on how you manage your other partitions, rather variable factor. If you are interested in allocating only one partition to Ubuntu, as your /home & /usr will also be on same partition, about 15-20 GB should be good enough. You can make this as primary or on extended partition. Personally, I prefer to keep root (/) as primary and separate from /home at least. So if things go really bad, I know my data is safe on separate partition. For most part, I am assuming you have about 120GB to play around with.

Other Partitions which you will need are partition for windows D: usually , but it generally goes on extended partition also SWAP for Ubuntu , but keep that on extended as well , it is not very economical to make a primary partition of only 1-4 GB.

It is best to install Windows before installing Ubuntu, due to MBR monopoly autocracy inappropriate ethics that Windows XP (Microsoft in general) prefer to use. So, Windows XP will overwrite your MBR during system installation, hence only OS you can see and boot into is Windows XP. But GNU/Linux being good guy lets you installs boot loader which is rather OS neutral and gives you option to boot into Windows as well.


Herego your partitioning with XP: 

1) C: (NTFS) (15-20 GB)
2) unformated partition (here goes Ubuntu)
3) Extended Partition (all the remaining memory)
3a) Make your Data partitions for Windows XP (D:, E:, etc.) depending on size of your Hard Disk and preferences.
3b) Make unformated partition for Ubuntu Data (usually /home)
3c) About 2-4 GB free memory at end of your Extended Partition for linux SWAP partition

Considering, 3b & 3c keep about 2 GB (min, only swap) to 22 GB (/home + 2 GB SWAP). Only approx. example

Install Windows first easy & then install Ubuntu equally easy. Remember one thing as well these are OSes not just any software, if tinkered around way too much, your hardware might get hurt (primary candidates are hard-disk and that small part which is very important known as MBR)

---

