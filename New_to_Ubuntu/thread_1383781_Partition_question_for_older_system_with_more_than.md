---
title: "Partition question for older system with more than one drive"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by blevault on 2010-01-17
I have an old Dell that I am using as my Ubuntu Server.  I wiped the two drives and did a fresh install of Ubuntu.  I have a couple of questions on how to properly partition and format the drives.
 
The server will be a backup, media and picture holder on a home network that supports all PC's running XP home edition.
 
Drive #1 250GB - The machine is old enough to only recognize 130GB, so I created a 40GB drive that I loaded Ubuntu and it mounts at the root. Created 1.0 GB Swap. The remaining 210GB is set up as Linux filesystem and mounts at home.  Is this correct?  Can or should this be NTFS and can I format the entire drive as NTFS?
 
Drive #2 120GB - Created 1.5GB swap.  Remaining 119GB is unused.  Should it be NTFS and where should it mount?  I think that only one drive can mount at home.
 
Thanks for any help.

---

### Post by halitech on 2010-01-17
*Nix will not run on NTFS so you need to have /, /home on ext* type partitions. If this system is going to be basically a server, you don't need 210gig for /home. I would do it this way:

1. Make the 120gig the primary drive. 
2. Make a 20gig /
3. make a 1gig swap
4. make a 30 gig /home
5. make the rest a storage partition and mount it at /storage

6. Make the 250gig drive a storage drive and mount it at /storage2

Are you using the actual server install or the Desktop version?

---

### Post by tom4everitt on 2010-01-17
Of course your questions are not so much about right or wrong as of taste. A few points though:

You don't need swap space on both partitions, one will be enough. 

Its probably a good idea to have the home partition as a linux file system, but I would not recommend you to have your files on your home partition.

I would only go with a small home partition (a few gig perhaps) and make big NTFS partitions on the rest of the drives. Mount them pretty much wherever you want, but /media and /mnt are common choices (you can configure this in /etc/fstab). 

Its not really important to have your file partitions as NTFS, but it might be slightly better since your using them with windows computers.

---

### Post by Captain_tux on 2010-01-17
Maybe I'm missing something, but even if you could see it, how could you read it? You said it's encrypted, yes? So you'll see something, but you won't be able to read it...

---

### Post by J V on 2010-01-17
IMO...

several (2) gigs swap on *one* partition
10 gigs for root is plenty...

Not sure what to do about the seperate HDs though, I'd say keep the 120gig as a backup drive and backup stuff from drive 1 once a day...

Course you could just make it an extra data partition...

---

### Post by blevault on 2010-01-17
> **J V said:**
> IMO...
 
several (2) gigs swap on *one* partition
10 gigs for root is plenty...
 
Not sure what to do about the seperate HDs though, I'd say keep the 120gig as a backup drive and backup stuff from drive 1 once a day...
 
Course you could just make it an extra data partition...
 
Read somewhere and from my studies I believe that two swaps will give more throughput when used in parallel..

---

### Post by blevault on 2010-01-17
> **halitech said:**
> *Nix will not run on NTFS so you need to have /, /home on ext* type partitions. If this system is going to be basically a server, you don't need 210gig for /home. I would do it this way:
 
1. Make the 120gig the primary drive. 
2. Make a 20gig /
3. make a 1gig swap
4. make a 30 gig /home
5. make the rest a storage partition and mount it at /storage
 
6. Make the 250gig drive a storage drive and mount it at /storage2
 
Are you using the actual server install or the Desktop version?
 
I am using the server version 9.10 of Ubuntu.  Can I make part of the drive ext* and part NTFS?

---

### Post by J V on 2010-01-17
Well, yes, but theres really no point... ubuntu isn't windows, it probably won't even use the swap for the first 2 years of its existence :P

But yeah, no point really in making a second swap, if you are actually using it its probably to watch a movie or something (which isn't really that HD intensive)

@ OP: Yes you can, but you will have to install windows first (linux can't make decent NTFS) then delete everything off the windows partition after installing linux... But the sharing software (samba) sends it as a protocol, so it doesn't matter, connect it to a windows linux or mac machine, they will all be able to get the data off it...

---

