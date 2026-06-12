---
title: "Should I just do a full install and delete partitions?"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by davequig on 2011-05-17
Well..? Should I? 

I only use my netbook for emails, surfing the web, etc. I use Mozilla, utorrent, skype and that is it. 

Should I delete all partitions and do a full install? I just want to know that there are no negative effects to doing this. 


thanks

---

### Post by mtangoo on 2011-05-17
you are not clear my friend. Which OS do you use now and why on earth would you want to delete partitions ;)

---

### Post by davequig on 2011-05-17
alright mate, i'm using windows 7. my problem is that I don't have a clue what partitions are good for. Don't the just split your hard drive? Why do I need them. What benefit are they?

---

### Post by bennachie on 2011-05-17
The short answer is, if you don't need Windows 7, or can readily install it again from scratch if you find that Ubuntu doesn't meet your needs, you can simply install Ubuntu from the LiveCD and let the installer take over the whole hard disk. It will actually create two partitions, a large one to hold your system and data and a much smaller one to use as a "swap area" to extend your RAM when necessary and to back up the contents of your RAM if you choose to hibernate the system, but that will be transparent to you.

If you would like to retain Windows 7 and "dual boot" with Ubuntu, you can let the installer take over some of the free space in your existing Windows partition(s) and install the two systems side-by-side.

For what you say you are doing, Ubuntu will do every bit as good a job as Windows 7 in almost every conceivable circumstance, will look and feel nicer and more natural to use, and will be more secure, but the choice is entirely yours.

---

### Post by virtual_m on 2011-05-17
if you have 2 partitions [C and D], you can use  D partition as data storage [music and other], and C partition for OS instalation... 
so, when you want to remove some OS from C partition, data on D partition can stay untouched...

now, if you want to remowe Windows 7 - you can install Ubuntu on C partition and leave D patrition undeleted [with all yours data on it]...

---

### Post by sanderd17 on 2011-05-17
> **davequig said:**
> Well..? Should I? 

I only use my netbook for emails, surfing the web, etc. I use Mozilla, utorrent, skype and that is it. 

Should I delete all partitions and do a full install? I just want to know that there are no negative effects to doing this. 


thanks

If you only use those programs, replacing the C and D partition by a big / partition to hold your OS and data and a small swap partition to extend your ram can not harm you. You can even drop the swap partition if you have 3GB RAM or more and you don't want to suspend to disk.

Just put the ubuntu CD (or USB) in and tell the installer to use the complete disk. Warning: everything will be erased. This includes Windows resque partitions. If you did not recieve a windows resque disk (or USB, I don know how that goes with netbooks) and you would maybe want to install windows again, then make a resque CD or USB from that partition first, before you delete the partition.

---

### Post by athenroy on 2011-05-17
Personally, from the standpoint of should you ever want to sell your machine, I'd keep Win 7 and use WUBI to do a dual boot install.  That way, if someone buys it they have a choice of keeping both or deleting one or the other.  Remember, with WUBI you can un-install Ubuntu and the boot manager like any Windows program.  Unless you are technically oriented, repartitioning can get a little tricky and you could end up with some real problems!:(  I used to run 4 OSs on one machine, took a lot of work and several re-installs of OSs to get it right!

---

### Post by audiomick on 2011-05-17
> **davequig said:**
> alright mate, i'm using windows 7. my problem is that I don't have a clue what partitions are good for. Don't the just split your hard drive? Why do I need them. What benefit are they?

You are right in a way: Partitions do split up your drive. A partition is, as the name suggests, a section of you drive that is partitioned of. The usefulness of it includes delineating which part of the drive will be worked upon by an operation.

For instance:
A windows install often includes a "recovery partition". It is not possible to format a drive "only from here to there" if the drive is only one big partition. If the drive is separated into several partitions, it then becomes possible to format only a bit of the drive, i.e. one (or more) of the partitions. This allows a recovery partition to work. It sits on one bit of the drive, and is able to format and re-install another bit of the drive that is a different partition.

Another example: if you have an Ubuntu install with the /home folder on its' own separate partition, it is possible to re-install the system to  the partition that it is on, but leave the partition with /home on it untouched and reuse it in the new installation, i.e. have all your files and configurations in the new installation without having to set them all up again.


As far as your current situation goes: if you let the installer write over all the partitions currently on your drive, there will be no trace of your Win 7 left, and no recovery partition anymore. You can choose to set up a new partition scheme to suit the Ubuntu install. You can also just install Ubuntu onto one partition that takes up the whole drive.
You could also choose to alter the size of the existing partitions, maybe remove one, to make some room for an Ubuntu install. This would allow you to keep the Win 7 install and set up a dual boot.

It is not possible to have two different Operating systems, for instance Ubuntu and Win7, installed in one and the same partition.

---

