---
title: "A few questions about installation"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by shiftman on 2010-11-22
Hi All, 

This is my first post here so Hi to all. My question has probably been asked many times before but I would like to try Ubuntu as an alternative to Windows Vista so could any of you kind people give me a walkthrough of how I partition my hard drive and install Ubuntu on the new partition and have a dual boot system. 
Also if everything goes ok with Ubuntu can I delete the partition with Windows on.
Another few questions I have is are most things compatible with Ubuntu, I have a netgear DGN1000 wireless router which requires an operating system running a TCP/IP network, also have an Epson SX425W printer and the full AVG internet security. 
Can I use Microsoft Office programmes or do I have to use Open Office. 
Is it plug and play and auto detect USB drives etc. How about media players as I use windows media player for pretty much everything.
Many thanks in advance for any info.

Paul

---

### Post by Zzl1xndd on 2010-11-22
I haven't done a dual boot in a long time but I believe there is an option to in the installation process specifically for this (someone will correct me if I am wrong).

Your Router should be no issue.

Looks like your Printer is Fine [http://ubuntuforums.org/showthread.php?t=1544398](http://ubuntuforums.org/showthread.php?t=1544398)

The Security suite wont be needed, however I believe AVG supports Linux.

MS programs wont work by default (some EG: MS Office may work in WINE).

Most USB devices work without issue.

And there are lots of great Media Players, however no Windows Media Player as it is an MS product.

---

### Post by cwa on 2010-11-22
Welcome to the forums shiftman.

You can dual boot windows vista and ubuntu, I am doing that right now vista and kubuntu 10.10. 

There are a few options that you can do in order to do this. First, I would make a cd recovery set for vista if you haven't done so already or if you don't have factory cds to restore your system.

What I have done (I wouldn't recommend this unless you are comfortable doing this) is to delete my D: recovery partition that houses the system files/factory recovery stuff. I used this empty partition to install kubuntu on.  

If you do this this way, and make a system recovery cd set from within the OS (not sure about a factory cd set) then if you want to re-install a windows only computer, it will re-create the recovery partition. However, as you might guess, you won't be able to hit the F-key to access that partition during the POST.

The other option is to shrink your C: partition (I would make backups of your data in case something goes wrong) and then use the newly created empty space to install linux on.


Linux can/does use the TCP/IP network protocol, so you can still access your router and the internet. Your printer you will have to see if it has drivers for it. (I don't have time to search for any this second, maybe later.) Google linux and the model number of your printer or check out the support page for the manufacturer of the printer for native linux drivers. It also might be supported out of the box. 

As far as your questions about Office and AVG. These will not run without the use of a program called wine. (there might be others that would allow the use of windows software to run in Linux, but wine is what I am familiar with).

however,check out openoffice / libreoffice . Both are free and available for linux and windows. There is virus software for linux, some free some commercial. 

There are other free programs to do what you want to do as well. Firefox exists for Linux, as well as other windows browsers (I think netscape still, mozilla suite) no I.E. for Linux though.

One last thing, gotta run, but if you don't want to install Linux onto your hard drive, you can download kubuntu live or another distribution's live cd and boot off of the cd. This way, you can check out linux without having to install it to the hard  drive. 

cwa

---

### Post by venicequeen7706 on 2010-11-22
using a live CD, one you select to install it, it will give you three options if i remember correctly, the first is to install as a second partition, the second option will wipe your hard drive and install ubuntu getting rid of windows, and the third is advanced stuff. choose the first it should have a thing showing how much storage is on your hard drive divided into two different colors, one for windows and one for ubuntu, you will have to decide how much storage to allocate to each because you won't be able to access the windows memory from ubuntu and ubuntu memory from windows(to the best of my knowledge). the rest is easy and it walks you through it all.  

you will use open office, but it works great and can save files in the format microsoft office uses, so they will be compatible.

pretty much all of your hardware should work with little effort on your part. Setting up your printer will be different from in windows. once your printer is plugged in and turned on go to system > administration > printing > server > new > printer and you will select your printer, it will need you to select your printer from a list to get the software then it will set it up for you.

for music I use rhythmbox which i believe is default. For movies I suggest VLC because with a few packages from synaptic it can play every type of movie file i know of, encrypted DVDs, and it can copy DVDs into a video file.

---

### Post by cwa on 2010-11-22
tweakedenigma: I wasnt familiar with AVG and Linux, new F-prot and clamav


cwa

---

### Post by Zzl1xndd on 2010-11-22
> **cwa said:**
> tweakedenigma: I wasnt familiar with AVG and Linux, new F-prot and clamav


cwa

Never used it just remembered hearing about it. 

[http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf)

---

### Post by cwa on 2010-11-22
venicequeen7706:
"you will have to decide how much storage to allocate to each because you won't be able to access the windows memory from ubuntu and ubuntu memory from windows(to the best of my knowledge). the rest is easy and it walks you through it all"

Not trying to be a jerk, but understanding what you mean. If you are talking about allocating storage which sounds like hard drive space, you can access Windows partitions from Linux using mount or ntfs-3g.
If I remember right, you can download drivers or some software to allow you access to Linux partitions in windows. however not sure if all partition types are supported. google fs-driver and it support ext2/ext3 

If you are talking not accessing actual RAM memory, then I agree, you can't do that, since I believe RAM gets wiped when the computer gets shutdown/rebooted.

cwa

---

### Post by Zzl1xndd on 2010-11-22
Right on all counts cwa.

Here is a link on how to access ext4 from Windows.

[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

