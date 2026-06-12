---
title: "help with partitioning my hard drive"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by hard knock on 2011-02-17
I've been trying to partition my hard drive and I cannot absolutely believe it's this difficult - 

i try to unmount in order to create a new partition but this is the message I get

{The partition could not be unmounted from the following mount points:
/Most likely other partitions are also mounted on these mount points. you are advised to unmount them manually/}

why the hell cant I just do it the way the normal directions say to do it? 
nothing works
AAARRRGGGGHHHH!!!!!!


PLEASE HELP!!!


P.s. why does every file or partition that is in the Gparted menu have a key next to it ? do I need to unlock ?

---

### Post by Stephann on 2011-02-17
Right click on the partitions with a key, and try to unmount.

Bear in mind, you can't unmount a partition that has a running system on it.  Also (unfortunately) many of the live CDs 'auto mount' the drive.  Make sure you don't have any terminals and file managers open in the path of a mounted partition (i.e. you can't be in the /media/WINDOWS/ folder)

A good way to see what's going on is to type 'mount' in the terminal.  It'll spit out what partitions are mounted and where.  Then you just use 'sudo umount /dev/sdX#' to unmount (i.e. sdb2, hda1, or whichever partition you're working on.)  Also, notice it's 'umount' not 'unmount.'

---

### Post by presence1960 on 2011-02-17
You need to do partitioning from the ubuntu Live CD/USB if that is the case. You can not unmount / while ubuntu is running. Even if that were possible there would be no OS running since / is the OS.

---

### Post by hard knock on 2011-02-17
OK the problem I'm having is for one it wont let me boot from cd now so I can go back and set partition from start up instead of struggling with gparted. and is their a way I can just do this in the terminal?

partitioning a disk should never be this difficult - this is unnecessary to go through.

what function key do I press in start up to boot from CD cause I'm pressing all of them and it goes straight to UBUNTU

---

### Post by natex on 2011-02-17
You should check your bios settings (f2) to make sure booting that your bios is booting from CDROM first (not HD).

For partitioning you could use cfdisk (not fdisk). You'll need to know which hard drive you are trying to partition. And you'll need to know what the linux kernel is calling that drive on boot-up. This is most likely (/dev/sda (for sata drives) or /dev/hda (for ide drives). Then do 'cfdisk /dev/sda'.

---

### Post by hard knock on 2011-02-17
OK I finally got to the point where I can just boot from the cd room and I'm now at the partitioning point in the beggining.

I'm trying to install UBUNTU Server and Ubuntu 10.10 
a. how much space should I use for SERVER and How much for the 10.10 OS
b. what type of file system should I make 10.10 I was thinking FAT32 
c.how and where do I define a root file system.
d. what type of file system do I use for UBUNTU SERVER?


Thank you

---

### Post by Stephann on 2011-02-17
> **hard knock said:**
> OK I finally got to the point where I can just boot from the cd room and I'm now at the partitioning point in the beggining.

I'm trying to install UBUNTU Server and Ubuntu 10.10 
a. how much space should I use for SERVER and How much for the 10.10 OS
b. what type of file system should I make 10.10 I was thinking FAT32 
c.how and where do I define a root file system.
d. what type of file system do I use for UBUNTU SERVER?


Thank you
a. how much space should I use for SERVER and How much for the 10.10 OS

That's a tough question; why are you installing both systems?  What do you hope to do with the server?

You can get a very basic server install in under 2 gigs, but if you're hoping to host a website, stream music, or use it as a file server, you'll need more space to store said data.  A typical Desktop system would be comfy at around 8 gigs, but that's not including the music, videos, pictures, downloaded ISO files, and other documents you might want to make use of.

b. what type of file system should I make 10.10 I was thinking FAT32 

Fat32 is an old and difficult system to use today; it has a file size limit of 4 gigabytes (an iso that's larger can't be stored.)  If you really need it to be something Windows can read from, you could install it in ext2, as there are several programs for Windows that will let you read and write an ext2 system.  Additionally, you could do what I do, and have a 'media' partition.  I format it NTFS since Linux reads and writes it pretty well, though not well enough to merit installing the base system to.

c.how and where do I define a root file system.

It's where your system drive goes, on a partition.

d. what type of file system do I use for UBUNTU SERVER?

ext3 is a tried and true file system.
Thank you"

---

### Post by grahammechanical on 2011-02-18
Please remember that Ubuntu is not completely foolproof. But then again, we are not complete fools. Are we? You complain that it should be easier to do this or that, but what would you do with such power? Something foolish perhaps? Then who would you blame?

I find I like being protected from my own foolishness. And it was not so difficult to learn how to partition in Ubuntu.

Regards.

P.S. Look though some of the treads on the forums. Notice those people that have completely removed their Windows installation and now want it restored. They demand that we tell them how to do it. But it is impossible because they choose to wipe the Windows installation. The Ubuntu installer makes it easy to remove an existing operating system but it will only happen if we choose to instruct the installer to do it. Like I said, Ubuntu is not completely foolproof.

---

### Post by natex on 2011-02-18
@hardknock
What exactly do you want to do with your computer? There is no need to install two separate ubuntu distributions (server and desktop) on one machine. If you will be mostly using the computer as a desktop device, but need it to host server services (ftp server, web server, etc...), you can add those services to your desktop machine. You don't need a whole separate server install. 

So back to your partitioning - the simplest partitioning scheme that I would use for a desktop machine is the following:

1) swap partition ("swap") should be at least 1 GB (I use a 2GB swap with 8GB of ram) 
2) root partition ("/") can be relatively small (~20 gigs to be safe) -- ext4 is fine
3) home partition ("/home") needs to be larger (most of your hard drive space) when partitioning for a desktop machine -- ext4 is fine here too.

Don't use windows-type (fat, ntfs) file systems for linux. They won't work well.

---

