---
title: "partition plan for dual boot"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by cguzmani on 2009-02-23
Hi to all,

I had a very good experience trying Ubuntu Hardy in my old PC (pentium IV 3.0 GHz, 120Gb), so now I going to install **Intrepid Ibex** in my new notebook. It's a Dell Studio 15 (C2D P8400, 3Gb ram, 320 Gb, ati hd 3450), and will arrive in the next few days.

Unfortunately, comes with **vista premium **pre-installed. I need it for some programs and some games, but it's not going to be my primary OS. I had read many tutorials about partition so, I plan this partition fot the dual boot:

-----------------------------------------------------------------------------------------------
Vista  --  NTFS -- 35 Gb

Ubuntu -- \     -- EXT3 -- 16 Gb
          \home -- EXT3 -- 6 Gb
          \swap -- swap -- 3 Gb

Shared partition: Documents, music, videos, etc -- NTFS -- 240 Gb
-----------------------------------------------------------------------------------------------


My doubt comes from the EXT3 and NTFS file system. I had heard that Ubuntu 8.10 can write and read safely NTFS. It's that true?

Another doubt is the size of every partition. I'm a casual gamer, so I'm not going to install games over 4Gb in the Vista Partition. 


I'm newbie, so please reubicate this thread if it's necessary;)

---

### Post by marshall.robert on 2009-02-23
With Vista it is recommended to have atleast 40GB.

Also with 3gb of ram you shouldnt need swap atall.

Other than that its all good, given it suits your needs.

---

### Post by cguzmani on 2009-02-23
> **marshall.robert said:**
> With Vista it is recommended to have atleast 40GB.

Also with 3gb of ram you shouldnt need swap atall.

Other than that its all good, given it suits your needs.

Thank you for your answer Robert,

Vista needs 40Gb? wow... well, with 320Gb that's not a problem.

If i gonna to put my notebook hibernating, I need that swap anyway?

---

### Post by vanadium on 2009-02-23
For a dual boot with Windows, I would have all my data stored on my Windows partition. Thus, I would not include a separate home. Moreover, I would limit the root linux partition to 10 or perhaps 12 GB.

Afterwards, you will need to have the windows partition automatically mounted during startup. This must be done by adding an appropriate line in /etc/fstab.

Then you can make sure that you can access your data on the windows partition easily from within Ubuntu. This can be easily done by creating symbolic links in your home directory that refer to the data on the Windows partition.

There is a caveat. Ubuntu will only mount a clean ntfs volume. because of that, you must exit Windows completely (no hibernate) before booting into Ubuntu.

---

### Post by cguzmani on 2009-02-23
> **vanadium said:**
> For a dual boot with Windows, I would have all my data stored on my Windows partition. Thus, I would not include a separate home. Moreover, I would limit the root linux partition to 10 or perhaps 12 GB.

Afterwards, you will need to have the windows partition automatically mounted during startup. This must be done by adding an appropriate line in /etc/fstab.

Then you can make sure that you can access your data on the windows partition easily from within Ubuntu. This can be easily done by creating symbolic links in your home directory that refer to the data on the Windows partition.

There is a caveat. Ubuntu will only mount a clean ntfs volume. because of that, you must exit Windows completely (no hibernate) before booting into Ubuntu.


Thank you for your advices, vanadium;)

Only one question, I know that one of the pros of make a new partition is the "independence of the data" from one partition to another. For example, if I afterwards decide to change vista for other SO, or Vista have virus problems, is more easy to recover the system without any loss of data.

---

### Post by vanadium on 2009-02-23
To avoid data loss, I have an up to date copy of my data on an external drive.

I do not care about backing up an installed system or software settings (except for my email, that is). Such a backup is tedious to make and is outdated very soon.

In addition, an operating system benefits from a fresh install now and then. It is easy to restore my data if at one day I decide to do a fresh install (will be with the next Ubuntu release, likely).

The "independence of the data" on separate partitions is an important concern for server systems in a production environment. For desktop systems and laptops, it is unnecessary overhead (imho) that does not substitute for a good and up-to-date backup.

---

### Post by roccivic on 2009-02-23
> **cguzmani said:**
> 
-----------------------------------------------------------------------------------------------
Vista  --  NTFS -- 35 Gb

Ubuntu -- \     -- EXT3 -- 16 Gb
          \home -- EXT3 -- 6 Gb
          \swap -- swap -- 3 Gb

Shared partition: Documents, music, videos, etc -- NTFS -- 240 Gb
-----------------------------------------------------------------------------------------------

You do  realize that you have 5 partitions there and that you can only have 4 primary partitions on a hard drive and SWAP must be a primary partition. Therefore you could have it set up like this instead, for example:

/dev/hda1   - Primary - NTFS - Vista
/dev/hda2   - Primary - SWAP
/dev/hda3   - Primary - Extended (container for logical partitions)
/dev/hda4   - Logical - EXT3 - Ubuntu (/)
/dev/hda5   - Logical - EXT3 - Ubuntu (/home)
/dev/hda6   - Logical - NTFS - Shared

---

### Post by WatchingThePain on 2009-02-23
Yeah Vista takes a lot of space and will use space quickly. (I am an ex Vista user) Your swap can be about 1.5 times your ram.
Ubuntu will read and write the vista partitions. It's recommended that each OS goes on a seperate disc.Certainly best that you have windows installed first. Theres a Ubuntu wubi installer which is small and works nicely within vista, surprisingly nicely as well.

---

### Post by Wizho on 2009-02-23
> **WatchingThePain said:**
> Theres a Ubuntu wubi installer which is small and works nicely within vista, surprisingly nicely as well.But, it's always better for Linux to work on ext3 partitions instead of NTFS, isnt' it?

I'm thinking of doing the same thing that cguzmani is suggesting.
A primary partition for XP (I hate vista), another 3 primaries ext3 for Ubuntu, and one logical NTFS for general backups.
I only have a 40GB IDE hard drive, and I want to buy an 80GB Western Digital SATA HD, within this one I will install XP and Ubuntu, so maybe I'm going to use the old one for backups, and I will make a dedicated partition for the XP pagefile because it's supposed to be more efficient rather than having the pagefile in the same drive XP is installed in, so I want to give it a try.

I don't like Ubuntu to use the NTFS file system, it's way faster using ext3 so that's why I'm doing this on the next days, right now it boots up kind of slow.

---

### Post by vanadium on 2009-02-23
> and SWAP must be a primary partition.
This is not correct. Your swap can be on a logical partition. In fact, none of the partitions linux used needs to be primary.

---

### Post by cguzmani on 2009-02-25
thank you guys:p

Windows Vista is really fatty; I'm considering seriously to change it for Windows UE in the next months. Anyway, I heard that the dell studio have some problems with the drivers in XP, so I will keep Vista only for now.

@roccivic: I forgot to mention that in fact Swap was logical;)

_OK, here's my new plan._

1 - Primary	- Vista	- NTFS	- 40 Gb
2 - Primary	- root	- ext3	- 15 Gb
3 - Primary	- extended partition

4 - Logical	- \home			- ext3		- 6 Gb
5 - Logical	- swap  		- linux-swap	- 2 Gb
6 - Logical	- Shared Partition	- NTFS		- the rest


I don't know if with 2Gb of swap I can hibernate my notebook :?:

---

### Post by handy on 2009-02-25
There is some intelligence input involved in this how-to, which is focussed on the subject of this thread:

*_[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)_*

---

### Post by cguzmani on 2009-02-25
> **handy said:**
> There is some intelligence input involved in this how-to, which is focussed on the subject of this thread:

*_[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)_*

That was my main source;)

[IMG]http://www.psychocats.net/ubuntu/images/partitioning4.png[/IMG]

Thanks anyway.

The only difference (I guess) is that Intrepid Ibex can write and read in a NTFS partition.

---

