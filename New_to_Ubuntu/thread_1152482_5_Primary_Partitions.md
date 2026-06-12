---
title: "5 Primary Partitions?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by fiveacez on 2009-05-07
When creating a new paritition on windows, the parititioner decided to delete my "/home" and "root" partitions for Ubuntu.
 
I re-installed Ubuntu and recreated the partitions, but I forgot to change them both to logical partitions.
 
I booted with windows later to find out that I now have 5 primary partitions. I thought the maximum I could have was 4.
 
Is this a big problem? I can just reinstall Ubuntu and re-create the partitions, but is that really needed?

---

### Post by Didius Falco on 2009-05-07
This is all on the same hard drive?

I'd do the reinstall if it were me. It may work forever, or it may crash and burn your whole system at any time. Since it's a fresh install, you've little to lose other than the few minutes it would take to fix this now.

Much better that way than trying to recover from a fatal system crash down the line, with all your data in limbo...

Regards,

Didius

P.S. I'd love to see a screen shot or an ```
sudo fdisk -l
``` output of that...

---

### Post by raymondh on 2009-05-07
> **Didius Falco said:**
> 

P.S. I'd love to see a screen shot or an ```
sudo fdisk -l
``` output of that...

Me too.

Falco has a point ... a fresh install might be best.

---

### Post by fiveacez on 2009-05-07
Ok here ya go.
 
The first 3 partitions are /home, root, and swap.
[IMG]http://i126.photobucket.com/albums/p109/FiveAcez/5_primary_wtf.jpg[/IMG]

---

### Post by colau on 2009-05-07
Hi,
How many primary partitions can be created?
I did try to create 4 primary partition but failed.

---

### Post by starcannon on 2009-05-07
Is one of those Primary partitions on another HDD? you can have 4 per drive, otherwise, I don't know what just happened with that.

---

### Post by Didius Falco on 2009-05-07
> **fiveacez said:**
> Ok here ya go.
 
The first 3 partitions are /home, root, and swap.


It might be because you have that HP Recovery Partition - that should normally be set to Hidden.

Still, looking at that screen shot, it looks like you have 6, counting the Vista C: drive.

Unless they've updated the standard and I didn't get the memo...4  total Primary partitions should be the maximum.

Still, I'd go with the reinstall. Ubuntu will happily live in a logical drive in an Extended partition.

Just delete the Ubuntu ones, create an extended partition and put them the Logical drives in that. I'd do it with Gparted from the Live CD. Windows prefers to pretend there is no such thing as linux. <G> 

I'm saving that screenie, though.

Regards,

Didius

---

### Post by Didius Falco on 2009-05-07
> **colau said:**
> Hi,
How many primary partitions can be created?
I did try to create 4 primary partition but failed.

Four total is the standard, so if you were trying create 4 and already had 1, it should fail.

Regards,

Didius

---

### Post by colau on 2009-05-07
> **starcannon said:**
> Is one of those Primary partitions on another HDD? you can have 4 per drive, otherwise, I don't know what just happened with that.
I have only one hard disk.

---

### Post by fiveacez on 2009-05-07
So...I don't have 5 but 6 primary partitions on a single hard drive.  That's just great.
 
Yeah, seeing as I seemed to have defied the laws of computer science, I would save that too (it's online too, just incase my computer decides to delete another few partitions for no reason).
 
Thanks for the advice.  I'll see what I can do.

---

### Post by raymondh on 2009-05-07
back-up, back-up, back-up

---

### Post by dborba on 2009-05-07
Anyone have any idea why there is a limit of four (just for curiosity)? While I'm plenty familiar with the organization of a disk & what not, I'm not that familiar with the particulars of partitioning.

---

### Post by Didius Falco on 2009-05-07
> **colau said:**
> I have only one hard disk.

Hi colau,

This is part of the reason why you should start a separate thread for questions of your own. The post by starcannon was for fiveacez, who started the thread.

It gets too confusing when multiple people start asking things on the same thread, plus it is considered rude to "highjack" someone else's thread.

We all have to learn, though - so now you know. :wink:

Regards,

Didius

---

### Post by Didius Falco on 2009-05-07
> **dborba said:**
> Anyone have any idea why there is a limit of four (just for curiosity)? While I'm plenty familiar with the organization of a disk & what not, I'm not that familiar with the particulars of partitioning.

It's an old standard, dating from the earlier days of actually having hard drives instead of punchcards and paper tape. The Extended partition with Logical drives inside was tacked on later to maintain backwards compatibility while allowing for the needs of modern day users.

When I was a kid, Simplicity Patterns (from when it was much more common for people - mostly women, to sew their own clothing) used the old punchcards, and every year they'd throw out tons of them when they changed designs. People used to line up for boxes of them. My mother used to make xmas wreaths out of them...


Regards,

Didius

---

### Post by fiveacez on 2009-05-07
The Ubuntu installer should give you a choice of making a partition logical or primary right?  Because if it is, it's not giving me the choice(this is in the extended partition...which it seems to completely ignore).

---

### Post by dborba on 2009-05-07
> **fiveacez said:**
> The Ubuntu installer should give you a choice of making a partition logical or primary right?  Because if it is, it's not giving me the choice(this is in the extended partition...which it seems to completely ignore).

I don't recall exactly the specifics of the partitioner in the installer. What you could always do, although it is a tad more work, is to use the live to live boot and modify your partitions as desired with gparted. Then reboot & use the partitions you created as your mounting points.

---

### Post by Didius Falco on 2009-05-07
Personally, I always use Gparted to make my own partitions the way I want them, then when the installer gets to the partitioner, I choose **Manual (advanced)**.

That lets you set them up yourself - you just have to highlight the partition, and click the little button at the bottom to set it to **Use**, **EXT3** and** /**. Repeat for a separate Home partition, except, of course, set it to Home.

The swap file, as long as you formatted it to Linux/swap, doesn't need to be touched. Ubuntu will pick it up on it's own.

A separate Home partition is a good idea - makes reinstalls that much easier.

Personally, I like to have another partition just for my own data. You can name it whatever you want and just make a mount point for it in Ubuntu so it'll mount automatically. That's optional, but it was recommended to me by a person that knows a lot more than I do about linux, and I've never regretted doing it.

Regards,

Didius

---

### Post by lvleph on 2009-05-08
I thought the limit stemmed from the size of the MBR?

EDIT: Yep that was the case.
[http://www.lissot.net/partition/partition-03.html](http://www.lissot.net/partition/partition-03.html)

---

### Post by fiveacez on 2009-05-08
> **Didius Falco said:**
> 
Personally, I like to have another partition just for my own data. You can name it whatever you want and just make a mount point for it in Ubuntu so it'll mount automatically. That's optional, but it was recommended to me by a person that knows a lot more than I do about linux, and I've never regretted doing it.

Regards,

Didius

Wait, if I have a partition meant to share data between two OSs, I don't need a /home partition?

---

### Post by lvleph on 2009-05-08
I have a seperate home partition only because it has all the settings on it. All my documents are on a shared partition and is linked from both OSes.

---

### Post by Didius Falco on 2009-05-08
> **lvleph said:**
> I thought the limit stemmed from the size of the MBR?

EDIT: Yep that was the case.
[http://www.lissot.net/partition/partition-03.html](http://www.lissot.net/partition/partition-03.html)

Yes, and we should probably consider ourselves lucky that they were visionary enough to add in the capability for an additional three. At the time it was designed, there was only one type of file system. <G>

---

### Post by dborba on 2009-05-08
> **lvleph said:**
> I thought the limit stemmed from the size of the MBR?

EDIT: Yep that was the case.
[http://www.lissot.net/partition/partition-03.html](http://www.lissot.net/partition/partition-03.html)

Thanks! Nice link as well.

---

### Post by fiveacez on 2009-05-08
Ok, Ubuntu says that there IS an extended partition, and Vista just sees primary partitions.
 
I was thinking of trying one more thing:  create the partitions in vista, and then format them when installing Ubuntu.
 
Thoughts?

---

### Post by Didius Falco on 2009-05-08
> **fiveacez said:**
> Ok, Ubuntu says that there IS an extended partition, and Vista just sees primary partitions.
 
I was thinking of trying one more thing:  create the partitions in vista, and then format them when installing Ubuntu.
 
Thoughts?

You could, but now I'm thinking there is some kind of bug (they may call it a "*feature*") in the Vista partitioning software. That could explain the 5 (or 6) "Primary" partitions the Vista partitioner saw. I know in XP, it sees my linux partitions as blank, and offers to format them for me.

It may be related to the whole "linux? what linux?" attitude of Windows. <G>

For Ubuntu, I'd stick to Gparted. YMMV

Regards,

Didius

---

### Post by raymondh on 2009-05-08
> **fiveacez said:**
> Ok, Ubuntu says that there IS an extended partition, and Vista just sees primary partitions.
 
I was thinking of trying one more thing:  create the partitions in vista, and then format them when installing Ubuntu.
 
Thoughts?

OK, am playing around with a spare computer and Vista.  I cannot recreate a 5 partition set-up.  Most I can get is 4 (of which Vista claims 2 ... C and recovery).  

Wow, I must have been playing hookey when they changed the 4 partition rule.

Nothing wrong in using Vista to create partitions.  Although, why not take this opportunity to learn gparted?

Best of luck.

---

### Post by fiveacez on 2009-05-08
I have been using GParted on Ubuntu and Computer Managment on Vista.
 
I'm just wondering which program to believe (I wonder what you guys are gonna say...).

---

### Post by Elfy on 2009-05-08
Never used vista so can't comment - but I would believe what

```
sudo fdisk -l
```

told me

---

### Post by raymondh on 2009-05-08
> **fiveacez said:**
> I have been using GParted on Ubuntu and Computer Managment on Vista.
 
I'm just wondering which program to believe (I wonder what you guys are gonna say...).

LOLOL ... I think *most* ubuntu forum members would say "whatever suits you best".

I just think now's a good time to learn and practice gparted and try to understand

```
sudo fdisk -l
```

In fact, you yourself were wondering why Vista would not see "extended" when you know it's there.

---

### Post by fiveacez on 2009-05-08
Where in the information that is produced does it say primary/logical?  I tried doing that before, but I don't know that much about using the terminal.

---

### Post by dvl300 on 2009-05-08
Thats funny because i have had 3 normal partition's
then one extended and two more under that which
equals 5! and i have one 500GB sata hardrive!:)

---

### Post by nandemonai on 2009-05-08
> **dvl300 said:**
> Thats funny because i have had 3 normal partition's
then one extended and two more under that which
equals 5! and i have one 500GB sata hardrive!:)

Partitions under an extended partition are called logical partitions. You can have an infinite number of logical partitions.

---

### Post by raymondh on 2009-05-08
> **dvl300 said:**
> two more under that which

those "2 more" ... are they logical partitions *within/inside* a primary?  If so, then you still have 4 primary.  Hey, ain't knocking this down .... I tried and still could not get 5 PRIMARY and am very curious now to know how. 

I could get more than 20 logical partition inside a primary :)

---

### Post by dvl300 on 2009-05-08
under the extended partition

---

### Post by raymondh on 2009-05-08
> **dvl300 said:**
> under the extended partition

that's considered as 1.  Extended (and logical) partitions are what linux gave us to get around the 4 primary rule.

nandemonia may have explained it better.

---

### Post by wizard10000 on 2009-05-08
> **dvl300 said:**
> Thats funny because i have had 3 normal partition's
then one extended and two more under that which
equals 5! and i have one 500GB sata hardrive!:)

That's only four primary partitions.

---

### Post by raymondh on 2009-05-08
> **fiveacez said:**
> Where in the information that is produced does it say primary/logical?  I tried doing that before, but I don't know that much about using the terminal.

back to the OP ... fiveacez, time for some reading :)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by fiveacez on 2009-05-08
Almost forgot, when I first installed Ubuntu, Windows read that there was an extended partition and that there were 2 logical parititons inside of it, so I don't know what changed, but it's not reading it anymore.

---

### Post by dvl300 on 2009-05-08
i just said 5 partitions didn't specify what type!

---

### Post by Niniel on 2009-05-08
> **wizard10000 said:**
> That's only four primary partitions.
No, that's 3. :)

---

### Post by Niniel on 2009-05-08
> **fiveacez said:**
> Almost forgot, when I first installed Ubuntu, Windows read that there was an extended partition and that there were 2 logical partitions inside of it, so I don't know what changed, but it's not reading it anymore.
To me, this looks like Vista not knowing what to do with Linux partitions and then just labeling them "primary" partitions.

---

### Post by fiveacez on 2009-05-08
> **Niniel said:**
> To me, this looks like Vista not knowing what to do with Linux partitions and then just labeling them "primary" partitions.
 
Well, two days and 5 reinstallations ago, it was reading this fine.
 
I hope it is just Vista's fault, but it still concerns me....

---

### Post by wizard10000 on 2009-05-08
> **Niniel said:**
> No, that's 3. :)

Um - no  :)

The extended partition that contains the logical partitions is a primary partition  ;)

---

### Post by tomszyszko on 2009-05-08
Maybe the partitioner automatically changed one of the partitions to logical?

---

### Post by wizard10000 on 2009-05-08
> **tomszyszko said:**
> Maybe the partitioner automatically changed one of the partitions to logical?

Not likely since logical partitions have to reside inside the extended partition.

---

### Post by fiveacez on 2009-05-08
Here's what is output to the terminal.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14131413

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5978    48010752    7  HPFS/NTFS
/dev/sda2            5978       26226   162648064    7  HPFS/NTFS
/dev/sda3           26227       28982    22137570    5  Extended
/dev/sda4           28983       30401    11390976    7  HPFS/NTFS
/dev/sda5           26227       26886     5301418+  83  Linux
/dev/sda6           26887       28193    10498446   83  Linux
/dev/sda7           28194       28982     6337611   82  Linux swap / Solaris
```

---

### Post by Elfy on 2009-05-08
You have 4 primaries and 3 logicals. Extended is counted as primary - the primaries are
sda1-4 the logicals sda5-7

If you look at the start/ends you should see the logicals inside the extended.

---

### Post by fiveacez on 2009-05-08
> **forestpixie said:**
> You have 4 primaries and 3 logicals. Extended is counted as primary - the primaries are
sda1-4 the logicals sda5-7

If you look at the start/ends you should see the logicals inside the extended.

Ok, how were you able to tell that those were logical.  was it because the ID was 82 or 83?

---

### Post by wizard10000 on 2009-05-08
> **fiveacez said:**
> Ok, how were you able to tell that those were logical.  was it because the ID was 82 or 83?

No, because they're *inside* the extended partition.

Notice the start and end blocks of sda3 - the extended partition.  sda 5, 6 and 7 all fit within that partition  ;)

---

### Post by Elfy on 2009-05-08
I looked at the numbering of the partitions before I did anything else. 


Also from memory sda5 or higher are the numbers for logicals - even if you had only  extended with a bunch of logicals then the numbering would be 

sda1
sda5 
sda6 etc

(I could though be wrong.)

The numbers 82 and 83 relate to filetypes, you'll notice that the extended has no number in your list.

```
1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data    
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access     
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor      
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT        
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux RAID auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep        
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT            
1c  Hidden W95 FAT3 75  PC/IX 
```

---

### Post by Niniel on 2009-05-08
> **wizard10000 said:**
> Um - no  :)

The extended partition that contains the logical partitions is a primary partition  ;)

Yes, but to avoid confusion, I think it's not a good idea to call an extended partition a "primary" partition as well since it is clearly not the same as a "real" primary partition. 
Therefore I believe that it would be best to say that a disk can hold 4 partitions - primary or extended - and that extended partitions can hold logical drives, which are like additional partitions.

---

### Post by dvl300 on 2009-05-08
well said:)!

---

### Post by Didius Falco on 2009-05-08
> **forestpixie said:**
> I looked at the numbering of the partitions before I did anything else. 


Also from memory sda5 or higher are the numbers for logicals - even if you had only  extended with a bunch of logicals then the numbering would be 

sda1
sda5 
sda6 etc

(I could though be wrong.)

You got it right. My fdisk -l:

d> ev/sda1   *           1       13055   104864256    7  HPFS/NTFS
/dev/sda2           13056       91201   627707745    f  W95 Ext'd (LBA)
/dev/sda5           13056       13186     1052194+  82  Linux swap / Solaris
/dev/sda6           13187       14491    10482381   83  Linux
/dev/sda7           14492       17102    20972826   83  Linux
/dev/sda8           45907       78452   261425713+   7  HPFS/NTFS
/dev/sda9           78453       91201   102406311    7  HPFS/NTFS
/dev/sda10          17103       19118    16193488+  83  Linux
/dev/sda11          19119       23404    34427263+  83  Linux
/dev/sda12          23405       29840    51697138+  83  Linux
/dev/sda13          29841       36652    54717358+  83  Linux
/dev/sda14          36653       41242    36869143+  83  Linux

---

