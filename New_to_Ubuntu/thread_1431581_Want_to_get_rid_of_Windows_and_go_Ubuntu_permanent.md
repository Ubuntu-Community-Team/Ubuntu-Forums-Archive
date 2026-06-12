---
title: "Want to get rid of Windows and go Ubuntu permanently on this PC."
date: 2010-03-16
forum: New to Ubuntu
---

### Post by RandomP on 2010-03-16
I think I am ready. 
I hardly ever use Windows and when I do it was to print stuff with a printer that is not supported in Linux. Now my brother has a laptop and can hook it up to the printer.

Anyway, this PC has two HDD's. One running linux (80GB) and the other has Windows (250GB). How do I get rid of Windows from that drive safely? If I am not correct, then Grub is also pretty much stored on it somewhere. Also, will I need Grub if I only have ubuntu?

---

### Post by laidback on 2010-03-16
You'll still have grub with a solo Ubuntu. Cannot say about the other issue.

---

### Post by albert s on 2010-03-16
try the live CD, use Gparted and delete the windows partition, and the3n extrend the ubuntu one to fit.
this is only a general thing,
someone with more accurate info will be along soon I hope.
I very new to all this too so I dont like giving out too much actual specific info.  :D

---

### Post by holadebob on 2010-03-16
My situation was similar, had a 160 and 40 gig drives. I just copied all my good files onto a dvd and put the ubuntu disk in and partitioned and formatted the drives and let ubuntu do the rest, loaded my DVD files and didn't have a problem after that. RIP XP.  It was smooth. The grub will still be there to give you diagnostic and repair choices.
I had a lump in my throat when I hit the key to start the process, what was life going to be like without Windows??? After six months, I have forgotten that other system. I have much spare time now from not working on the system to keep it happy.
Bob

---

### Post by sandyd on 2010-03-16
> **RandomP said:**
> I think I am ready. 
I hardly ever use Windows and when I do it was to print stuff with a printer that is not supported in Linux. Now my brother has a laptop and can hook it up to the printer.

Anyway, this PC has two HDD's. One running linux (80GB) and the other has Windows (250GB). How do I get rid of Windows from that drive safely? If I am not correct, then Grub is also pretty much stored on it somewhere. Also, will I need Grub if I only have ubuntu?
you might want to look into using mdadm/dmraid to create a raid0 setup that will merge the 80GB and the 250 GB partitions into one super mega partition

---

### Post by RandomP on 2010-03-16
> **holadebob said:**
> My situation was similar, had a 160 and 40 gig drives. I just copied all my good files onto a dvd and put the ubuntu disk in and partitioned and formatted the drives and let ubuntu do the rest, loaded my DVD files and didn't have a problem after that. RIP XP.  It was smooth. The grub will still be there to give you diagnostic and repair choices.
I had a lump in my throat when I hit the key to start the process, what was life going to be like without Windows??? After six months, I have forgotten that other system. I have much spare time now from not working on the system to keep it happy.
Bob

Thanks for the replies.

I would prefer not to do a clean install as I have done that not more than a month ago. (My 9.04 ubuntu could not update correctly to 9.10 and left me with a pretty messed up system. I downloaded a 9.10 LiveCD and moved my important files to my windows drive, then I formatted and de-partitioned the drive ubuntu was on. After that I installed 9.10 on to the drive).

I also would not fancy transferring my files to CD's to do a clean install since I have a lot of files. 

> **carlee said:**
> you might want to look into using mdadm/dmraid to create a raid0 setup that will merge the 80GB and the 250 GB partitions into one super mega partition

I have thought about having a raid0 setup, but I do not think that would be a good choice for me. I like to do clean installs every once in a while to keep the PC running at a good speed. I like backing up my files on to my 250GB HDD since I do not have a usable external HDD. Raid0 might make that not possible or harder to implement. I would rather just keep the 250GB HDD as a media drive for my movies and other files.

---

### Post by Miljet on 2010-03-16
Yes, you will still need Grub. The important thing here is which drive has Grub currently installed. If you don't know, you can install the Boot Info Script and run it to find out.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by RandomP on 2010-03-16
I know that if I disconnect the windows HDD, Grub still pops up.

I also know that there is a terminal command that will show where grub is located, I forgot the command though.

---

### Post by themusicalduck on 2010-03-16
If grub still pops up and works properly when the Windows drive is disconnected then it's probably stored on the Ubuntu drive. You could always re-install grub afterwards if it does stop working for some reason, and you'd probably have to do that anyway if grub was installed on the Windows drive after formatting it.

Here's another idea which would be good for your setup. You could setup your 250gb drive to be your home space for Ubuntu. That means you can store video files, etc in your homespace and have it more integrated with Ubuntu. Also, all of your configuration files are then stored on a separate drive, so if you ever need to re-install or upgrade, you don't need to backup so much stuff first. :)

This page covers it fairly well - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) except of course you don't need to repartition your ubuntu drive but just use your other hard drive.

---

### Post by RandomP on 2010-03-17
Na, I think I just want to have the 250GB drive as a storage drive for my files. 

Since grub will still be there, I will probably have to delete the Windows options, right?

EDIT:
I just deleted all of the partitions on the Windows drive and formatted it to just a NTFS drive. Grub still shows up, but the windows options are still on it. Need to get rid of those.

---

### Post by cascade9 on 2010-03-17
You might want to use the 80GB as backup and the 250GB as your OS drive, the 250GB drive will probably be faster ;)

---

### Post by themusicalduck on 2010-03-17
To get rid of the Windows options, just run ```
sudo update-grub
``` in a terminal.

---

### Post by Drenriza on 2010-03-17
Carlee.

You cannot use Raid 0 to merge disks (who is not of equal size). Raid 0 works with taking a pice of data, split it up in 2 equal sizes. And then writing it to the 2 disks.

For raid 0 to work you need 2 disks of equal size. If you want to merge Harddisks (who is not of equal size) you need to use something called "spanning".

Also i dont recoment software raid. If you want to go raid go hardware raid.

---

### Post by psusi on 2010-03-17
> **Drenriza said:**
> 
Also i dont recoment software raid. If you want to go raid go hardware raid.

No.  Real hardware raid cards are expensive and provide no benefit over software raid unless you are using raid5, and even the computations needed for that are nothing to a modern cpu.  They also sometimes foul up the raid set and when they do, you have no software tools to diagnose and repair the problem, just a bios screen that says "OH NOES! YOUR DATA ARE GONE!"  I have had this happen on production machines where there was nothing wrong with the data, just the card decided to write the wrong volume serial number to two of the disks, so it thought that there were two raid sets that each only had 2/4 disks so were inaccessible.

Most consumer level "hardware raid" cards and built in raid on motherboards are fake raid.  They pretend to be hardware raid, but they are just standard AHCI SATA controllers with extra bios code and proprietary Windows drivers to implement the software raid transparently.  The only benefit this provides is that you can get Windows to boot from a raid, and also Ubuntu understands how to access it.  If you don't need to dual boot with Windows the Linux software raid is your best bet.

As for the OP, I think your best bet is to use the smaller drive for the system and the larger drive for /home, or just install to the larger drive and then use the other drive for backup or temporary storage or such.  If you want you could also use LVM to manage volumes across the two drives combined, or you could raid the first 80 gigs of each drive together in a stripe for speed and use the rest of the larger drive for extra storage, though that isn't recommended if both drives are not about the same speed to start with.

---

### Post by RandomP on 2010-03-17
The 250gb I think is a 7200rpm while the 80gb is a 5400rpm. I am not quite sure though. Either that or they are both 5400rpm drives.

The reason I do not want to use the 80GB as a storage drive is because media needs a lot of space and I would rather not clutter up the drive that has the OS on it.

Anyway, thanks for all of the replies, I think I have got it now.

---

