---
title: "Installing Intrepid on Dell E1505"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Mig Daddy on 2009-01-05
Hi all.  I am new to Ubuntu and this is my first post on the forum.  I have been interested in the Dell Mini 9 as Dell computers have always been good to me.  In light of this, I have a new found interest in Ubuntu.  I have tried Mandrake and Redhat in the past with minimal success, so I am a bit hesitant to return to Linux.

I have been reading through this forum and others to find info about installing 8.10 on my Dell E1505 as part of a dual boot.  So far I have been reading about problems with wireless, battery, sound, touchpad, and video.  I was wondering if anyone had any advice to go about installation.  My system specs are as follows: Intel Core Duo T2400 w/ Centrino, 2GB DDR2-667 RAM, 60GB HD (WinXP Media Center taking up about half, but the entire drive is partitioned as NTFS), integrated graphics, Intel 3945 a/g mini card, no bluetooth.

I have also downloaded Parted Magic 3.4 and am considering creating 4 total partitions (NTFS, FAT32, Ubuntu OS, Ubuntu Home).  I've been told that a swap partition is not necessary.  I will need about 25-30GB to remain as the NTFS partition.  How should I partition the other 3 (what size and where on the drive)?

I would also like to be able to play most types of media using Ubuntu (mp3, mp4, divx, ogg, etc).  Do wma and wmv files work on Ubuntu?

I know I've asked a lot of questions, but I don't want to install without knowing everything I need to know.  I not only want to get it right the first time, I want to do it in the best possible way.  Any help, any help at all, would be greatly appreciated.  Thanks.

---

### Post by wolfen69 on 2009-01-05
[Here]("https://help.ubuntu.com/community/DellMini9") is official ubuntu documentation for installing and configuring ubuntu on the mini 9. i don't mean to be discouraging, but few people if any get it perfect and keep it that way the first time. i fix computers for a living, and it took me several tries. patience is the key.

i would add a swap partition if i were you. it can't hurt. good luck and post back with any questions you may have after reading about the install.

---

### Post by Mig Daddy on 2009-01-05
Thanks for the quick response wolfen.  I appreciate the advice and I did suspect that it would be rather difficult to get it right the first time.  I was more concerned with installation on the E1505, but the link helps as I just purchased a Mini 9 impulsively from the Dell Outlet Website.  $380 w/ next day delivery to Virginia, bluetooth, 1.3M webcam, 32gb ssd, 1gb ram.

On a side note, I noticed that the Mini 9's now ship with the option of 64gb ssd and 2gb ram.  Does this mean that Dell has updated their kernel to support 2gb RAM?  If so, do you think requesting the updated version of the OS is worthwhile or am I better off installing Intrepid?

---

### Post by wolfen69 on 2009-01-05
i would give intrepid a try. but be warned: there will be some tweaks needed for wifi and possibly sound and power management. [Here]("http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html") is a great guide for installing intrepid on the mini 9. (different link than the other one) BE PATIENT! it's worth it in the end.

---

### Post by adult swim on 2009-01-05
ive got ubuntu on a e1705 with almost the same specs.  your graphics will do just fine.  your wireless card should do just fine, that model comes on some dells that ship with ubuntu pre-installed.  i wouldnt use more than 10GB for your ubuntu file system partition (/) and use the rest for your /home partition.  make sure and defrag your hard drive in windows before you go partitioning.  the only thing that may be a problem is fan control, but there is a program that will let you set the temperatures when the fans should come on called gkrellm.  the file formats you mentioned all work on ubuntu, but take a few extra easy steps.  after you install you can search the forums or make new threads with anything that you may encounter, but i think youll have a rather smooth process!

---

### Post by Mig Daddy on 2009-01-06
Thanks to the both of you for your responses.  I have already defragmented the HD several times.  I will probably eliminate any unnecessary files and do it a few more times.

Regarding the swap partition on the E1505:
To my knowledge both Hardy and Intrepid do not need them as a swap file can be used instead.  Does it matter if the file is in the root or home partition?  Is it still a better idea to use a separate swap partition instead?  I 2gb allocated for swap sufficient for 2gb RAM, or should I go with 3-4gb?

Regarding Intrepid and Hardy on the Mini 9:
I have no idea if the Mini 9's come with swap partitions/files from the factory; is it bad for the SSD?  What are the advantages of running Intrepid over the Dell Mini OS or just the standard Hardy distro?  Are there any performance variations like battery life, media playback, or hardware functionality?

Regarding learning about Ubuntu and other distros of Linux:
I know that forums such as this are the best source.  I have also run into a few free ebooks and pdf files.  Are there any good books out there where an amateur such as myself can learn about Linux and Ubuntu, or just Unix in general?  I am pretty good with anything Windows and have some experience with Fortran and Java, but have no clue about Linux.  I guess I'm looking for something technical, but not overly complex.

---

### Post by adult swim on 2009-01-06
ive got 2gb of ram and occasionally my computer will use some swap, although ive never seen my ram usage go above 1gb.  if you plan on hibernating your computer youll need at least as much swap as your ram, i wouldnt go above 2gb in any case though.  if you install without swap and later on decide that you need it, its possible to create a swap file instead of having a separate swap parition. 
Check out the book Ubuntu Unleashed, it does a pretty good job of explaining about everything ubuntu.

---

### Post by shvahabi on 2009-01-06
Hi dear,

I'm using Inspiron 6400 with Ubuntu 8.10 interpid. It works very well, nuch better than XP Pro. The only problem I had, was conflict between modem and sound card. If you're using some other kind of connection to internet, you will have no problem.
About partitioning, just make a partition of about 20 GB, and leave it unformatted. The installer will itself do identify the free space and do other things for you. In the process of installation there will be a step which you should choose partition to install, there will be an Item (namely the 3rd one) which proposes whether to use the most big continuous free space. Choose it, it will be installed without any hesitation. It will make two partitions for you, a file system and a swap. the swap one is less then 1 GB so worth to have.

Shahed Vahabi
From Iran

---

### Post by Mig Daddy on 2009-01-07
Is the Ubuntu boot disc capable of creating FAT32 partitions as well?

---

### Post by landshrk on 2009-02-21
Another question for you all that seems along these lines.

Just installed Intrepid on a friend's E1505, and, as expected, the wireless didn't work right away (I have a 1501, and I have needed to run the update manager each time I've installed [twice now. If you're curious, look at what else I've posted...]).

Now, my typical method for running the initial update is to just plug into a hard line, run the updater, and then everything works fine. But (and there's always one of those...), when I plug her E1505 into the hard line, I still get no connectivity. Ethernet, nada. Wireless, nada.

So. I'm curious as to if you might know of a location I could find the necessary driver/file/whatever. Figured I'd just download it on my comp, put it on my flash drive, and install it manually on her computer.

Any ideas where I might go? Any idea if this'll work? Thank you guys so much!

---

