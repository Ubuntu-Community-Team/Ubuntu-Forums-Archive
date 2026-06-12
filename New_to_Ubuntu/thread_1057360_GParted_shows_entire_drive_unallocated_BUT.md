---
title: "GParted shows entire drive unallocated BUT"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Kellemora on 2009-02-01
Hi Gang

I just built a new computer!

Used GParted to set the partitions up just how I wanted them, that part went great!
Loaded the 64bit Hardy and it would not let me select which partition to use or where to set mountpoint, so I just let it do it's thing.
After it was loaded and running, I found I needed some drivers for the MOBO.
Mobo disk is Doze only (of course).  So, using GParted I moved Ubuntu down and made a new partition for the Doze, installed it and installed all of my MOBO bios upgrades.
The Doze would boot up just fine, but no Grub.

I knew the DOZE would replace the MBR, which is normally no big deal, just fix it with Grub.  No Dice, GParted showed the entire drive as unallocated and after that no MBR at all, no boot.

Put in super grub fix the MBR, boots into the DOZE just fine!
Put GParted back in to see what's up, shows whole drive unallocated again.  Killed boot again too!

Do I have to use a DIFFERENT GParted on 64 bit?
Both the stand along GParted as well as the GParted on the install disk show Unallocated, entire disk.  Which I KNOW is IMPOSSIBLE since I can boot into DOZE or Ubuntu using SuperGrubDisk!

Somethings not kosher here, hi hi.........

Drive is Sata 500 g3

FWIW:  Not much worked in the DOZE until the MOBO Bios was upgraded.  Everything worked in Ubuntu BEFORE I updated the bios except for the volume control and resolution settings.  NVidia!

TTUL
Gary

---

### Post by caljohnsmith on 2009-02-01
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
sudo sfdisk -d
```
And please post the output.

---

### Post by Kellemora on 2009-02-01
Hi CJS

I ran fdisk -l earlier using Ubuntu LIVE CD.
With the Live CD I can go to Places/Computer and it shows all of my active partitions as Icons with their correct labels.  I can even OPEN the Partitions to see the folders inside.

BUT, if I run GParted from LIVE CD all I see is UNALLOCATED for the entire drive.  No it's NOT mounted!

Here is the fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12768   102558928+   7  HPFS/NTFS
/dev/sda2           12769       19204    51697170   83  Linux
/dev/sda3           22533       60801   307395742+   5  Extended
/dev/sda4           22992       60801   303708825   83  Linux
/dev/sda5           22533       22991     3686854+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


```

No mount points are set yet as GParted would not let me set a mount point and I know I need one for / (root).

The above is after I just completely wiped the HD, reset all the partitions, and installed the DOZE on partition 1.

As I said earlier, AFTER using GParted LIVE even to just LOOK, I will have to use Super Grub in order to boot back into the Doze.

GParted shows Partition: Unallocated, Filesystem: unallocated, Size: 465.76GiB.

I have found several mentions of this BUG on-line tonight, but everyone seems to have found a workaround, but without mentioning what the work around is.

TTUL
Gary

---

### Post by Kellemora on 2009-02-01
Hi CJS

Here are the printouts the way you requested them!

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00097f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   205117919   102558928+   7  HPFS/NTFS
/dev/sda2       205117920   308512259    51697170   83  Linux
/dev/sda3       361976580   976768064   307395742+   5  Extended
/dev/sda4       369350415   976768064   303708825   83  Linux
/dev/sda5       361976706   369350414     3686854+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=205117857, Id= 7, bootable
/dev/sda2 : start=205117920, size=103394340, Id=83
/dev/sda3 : start=361976580, size=614791485, Id= 5
/dev/sda4 : start=369350415, size=607417650, Id=83
/dev/sda5 : start=361976706, size=  7373709, Id=82
ubuntu@ubuntu:~$ 


```

TTUL
Gary

---

### Post by caljohnsmith on 2009-02-01
> **Kellemora said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -l
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12768   102558928+   7  HPFS/NTFS
/dev/sda2           12769       19204    51697170   83  Linux
[COLOR="Red"]/dev/sda3           22533       60801[/COLOR]   307395742+   5  Extended
[COLOR="Red"]/dev/sda4           22992       60801[/COLOR]   303708825   83  Linux
/dev/sda5           22533       22991     3686854+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


```

You definitely have a problem with your HDD partition table right now, because the sda4 primary partition is located within your sda3 extended partition; therefore sda4 should actually be a logical partition, or sda4 could stay as a primary partition if you resize your extended partition so it only contains sda5. I would recommend changing sda4 into a logical partition since that usually leads to maximum flexibility if you need to change your partitions in the future. If that sounds good to you, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
And please post the output. The above command will create a backup of the few sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, please copy that file to a different drive, or you could for instance save it to your email account or something like that. Then reboot, and please post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
And we can work from there.

---

### Post by Kellemora on 2009-02-01
Hi CJS

Only Partitions 1 and 2 are supposed to be Primaries!
3 was the Extended
and 4 was Logical
And Swap was swap/

I've redone this three times now, I could have messed up this last time and forgot to select Logical instead of Primary.  Nonetheless GParted shouldn't have allowed it!

It's ODD then that Ubuntu LIVE CD sees the Partitions from Places/Computer just fine and even lets me open them to the folders.

I'll watch for your next post!

TTUL
Gary

---

### Post by Kellemora on 2009-02-01
Hi John

Here is the text from the Operation we just performed.
I'm working on getting the rest and will wait to reboot until you give the A-OK to do so.

```
ubuntu@ubuntu:~$ sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  12767   12768- 102558928+   7  HPFS/NTFS
/dev/sda2      12768   19203    6436   51697170   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3      22532   60800   38269  307395742+   5  Extended
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4      22991   60800   37810  303708825   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5      22532+  22990     459-   3686854+  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,2,1)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 205117919  205117857   7  HPFS/NTFS
/dev/sda2     205117920 308512259  103394340  83  Linux
/dev/sda3     361976580 976768064  614791485   5  Extended
/dev/sda4             0         -          0   0  Empty
/dev/sda5     369350415 976768064  607417650  83  Linux
/dev/sda6     361976706 369350414    7373709  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~$ 



```

TTUL
Gary

---

### Post by Kellemora on 2009-02-01
Hi John

Here is the fdisk info:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12768   102558928+   7  HPFS/NTFS
/dev/sda2           12769       19204    51697170   83  Linux
/dev/sda3           22533       60801   307395742+   5  Extended
/dev/sda5           22992       60801   303708825   83  Linux
/dev/sda6           22533       22991     3686854+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=205117857, Id= 7, bootable
/dev/sda2 : start=205117920, size=103394340, Id=83
/dev/sda3 : start=361976580, size=614791485, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=369350415, size=607417650, Id=83
/dev/sda6 : start=361976706, size=  7373709, Id=82
ubuntu@ubuntu:~$ 


```

Thanks

TTUL
Gary

---

### Post by caljohnsmith on 2009-02-01
Looks good, Gary, your partition table appears to be OK now. To reinstall Grub, how about doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, and it should be either (hd0,1) or (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If they complete successfully, how about rebooting and let me know how far you get.

---

### Post by Kellemora on 2009-02-01
Hi John

I didn't reboot the computer, since I was in the LIVE CD I hit install to see if GParted showed the right stuff and IT DID!
So I went ahead and set the / partition and the /home partition and moved forward from there.

When I checked all the screens everything looked A-OK so I'm reinstalling Ubuntu AMD64 Hardy.

I REALLY REALLY REALLY Appreciate all the much needed help you have given me!

I run 6 Ubuntu machines here, 2 Doze machines, and most of the Original Ubuntu installs were Triple Boot machines, so I've learned how to wiggle my way out of Grub problems and handle fstab pretty good.

It LOOKS LIKE I made a USER ERROR and being overly tired must have missed selecting Logical the last go around.

It is interesting that GParted didn't catch that and say, You Can't Do That, or at least LET ONE go back in so they can FIX IT!

I recently converted from using data on all the hard drives, to making a Data File Server, NOT a File Server File Server, it's more like just a Shared Folder on a dedicated machine is all.

It's only up to 45% done so far!  But I will post back how things went, but it looks like now it will be OK......

AGAIN, Thanks for you wonderful help!

If they ever put the medals back up again, I'll make sure to get one pinned on you!

TTUL
Gary

---

### Post by caljohnsmith on 2009-02-01
> **Kellemora said:**
> 
It LOOKS LIKE I made a USER ERROR and being overly tired must have missed selecting Logical the last go around.

It is interesting that GParted didn't catch that and say, You Can't Do That, or at least LET ONE go back in so they can FIX IT!

Actually, I've seen this happen enough times now that I think it is likely it is a bug in gparted; and as you say, even if you had tried to make your linux partition primary instead of logical, gparted shouldn't have let you create it inside of your extended partition. If you have the time, it would be good if you can report it as a bug to the gparted.sourceforge.net project so they will know this kind of thing happens. And about installing Ubuntu 64-bit, I hope it goes OK, because I would have rebooted first if I were you to be on the safe side; you'll probably be fine though. Anyway, I'm glad your Ubuntu installation is going smoothly so far, hope it continues to go well. Cheers and enjoy your new Ubuntu install. :)

---

### Post by Kellemora on 2009-02-01
Hi JOHN

WOW - Smoothest Install EVER!

Networking WORKS, Sound Works, Resolutions Work, Internet Works, and I haven't even been into the configuration files for anything yet.

I do have one question for you though!

I've been using WINE to run my e-mail program Eudora.
I keep hearing about this thing called Virtual Box that you can install the Doze in, instead.
Now in WINE, I have access to the Z (Ubuntu) directory tree as well as the Remote File Server.  In other words, I can look at something like an e-mail attachment using Ubuntu while still in Wine.  Other than using Eudora and changing toner cartridges, that's about all I use the Doze for anymore.
It wouldn't have been on this machine at all, if it were not for having to work with the bios on this new MOBO with a disk that only works in the Doze.

You have a Good Night and again, a million THANKS!

TTUL
Gary

---

### Post by meierfra. on 2009-02-01
> So, using GParted I moved Ubuntu down and made a new partition for the Doze, installed it and installed all of my MOBO bios upgrades.
The Doze would boot up just fine, but no Grub.

I knew the DOZE would replace the MBR, which is normally no big deal, just fix it with Grub. No Dice, GParted showed the entire drive as unallocated and after that no MBR at all, no boot.

> I think it is likely it is a bug in gparted

I would be very surprised  if  gparted created the  primary partition inside the extended partition. It sounds like  the partition table was rewritten during the installation of Windows.

---

### Post by kansasnoob on 2009-02-01
> **meierfra. said:**
> I would be very surprised  if  gparted created the  primary partition inside the extended partition. It sounds like  the partition table was rewritten during the installation of Windows.

Long time no see! Good to see you around!

---

### Post by Kellemora on 2009-02-02
Hi Meierfra

I don't know what CAUSED the partitions to get messed up, everything looked A-OK when I set them up, right down to the Labels I wanted on the partitions.

From the Ubuntu Live CD if I looked at Places/Computer, all the partitions except swap and extended showed up as icons and I could open the partitions and see the folders inside.

GParted should have been able to SEE the Partitions IT Created and allow me to fix whatever got messed up, not show NOTHING THERE at all!

I'm still trying to figure out HOW John knew it was a Primary Partition.  I've studied those same tables I showed above until I'm blue in the face and can't figure out what's different.

The new table I wrote back reads identical except 4 was moved to 6.  I'm just glad he came along when he did, or I would have lost yet another day wiping the disk and starting over.

Although I've fixed minor problems with pooters over the years, and most I owned were Built-Up's, I never actually built one up from parts before.  Have NO IDEA what I'm doing either!
I'm afraid to plug my multi-card reader into the MOBO, because of all the warnings that it could fry the new MOBO, hi hi.....

TTUL
Gary

---

### Post by caljohnsmith on 2009-02-02
> **Kellemora said:**
> 
GParted should have been able to SEE the Partitions IT Created and allow me to fix whatever got messed up, not show NOTHING THERE at all!

If there is any type of inconsistency/corruption with your partition table, then unfortunately gparted won't show your partitions and just shows the drive as unallocated. I think it would be much better if gparted at least displayed its error in a pop-up dialog to let you know that gparted had detected something wrong with the partition table. In fact if you run gparted from the terminal:
```
gksudo gparted
```
I believe you will see the error message in the terminal when you select the drive in gparted with the corrupt partition table. I think gparted should give the user more feedback about this, because as you have pointed out, it's not like there is no partition table at all and the drive is unallocated space, it's just that the partition table is not consistent or is slightly corrupt. 
> **Kellemora said:**
> 
I'm still trying to figure out HOW John knew it was a Primary Partition.  I've studied those same tables I showed above until I'm blue in the face and can't figure out what's different.

The new table I wrote back reads identical except 4 was moved to 6.  I'm just glad he came along when he did, or I would have lost yet another day wiping the disk and starting over.

It turns out it is actually rather easy to know which is a primary partition and which is a logical partition; primary partitions are always numbered 1-4 and logical partitions are always numbered starting from 5. :) So all I did was move your sda4 primary partition to become the sda5 logical partition in the partition table, and all is happy in LinuxLand again. It is important to note that it is sometimes not that simple, because in your case, your sda4 partition had to become sda5 and could not become sda6. The reason is because your linux partition (originally sda4) starts at the sector immediately after the swap partition (originally sda5):
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00097f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   205117919   102558928+   7  HPFS/NTFS
/dev/sda2       205117920   308512259    51697170   83  Linux
/dev/sda3       361976580   976768064   307395742+   5  Extended
/dev/sda4       [COLOR="Blue"]369350415[/COLOR]   976768064   303708825   83  Linux
/dev/sda5       361976706   [COLOR="Blue"]369350414[/COLOR]     3686854+  82  Linux swap / Solaris
```
So if we had tried to turn your linux sda4 partition into sda6 instead of sda5, that wouldn't have worked because you would need free space before the linux partition for the EBR (Extended Boot Record) that holds the record of that partition. But if we instead made the linux partition sda5, that worked because the record of sda5 is always kept in the extended partition (sda3 in your case), so no additional EBR needed to be created. So the bottom line is, unless you were to shrink your swap partition a little (only 63 sectors for instance), your linux partition will always have to be sda5 and can't be any other logical partition number. But since it's not a problem having the linux partition be sda5 rather than sda6 (linux can be on any logical partition or primary partition), I figured we might as well do that rather than mess with shrinking your swap partition and making the linux partition sda6. Anyway, I hope I didn't make that too much more confusing. :)

---

### Post by meierfra. on 2009-02-02
> GParted should have been able to SEE the Partitions IT Created

Not if Windows messed up the partition table in between.
(I'm assuming that you only noticed that  gparted was  unable to see the partitions after you installed Windows. Is that correct?)
 
Usually these kind of things happen if  a program rewrites the partition table created by another program.  There is a certain amount of freedom how to write a partition table and different programs use slightly different rules. This can lead to confusion. Partitioning programs tend to rewrite the whole  partition table according to their own rules, even if they only have to change a tiny detail. May  Windows just wanted to set a boot flag and in the process rewrote the partition  table.

---

### Post by Kellemora on 2009-02-02
Hi John

NO you didn't make it more confusing, in fact, you actually cleared up what I thought was a major problem or something I was doing wrong ever since day one!

No MATTER WHAT I would do, my swap file would ALWAYS come out as sda5, EVEN IF I only had TWO primary partitions.

You would NOT believe how many times I REINSTALLEDl by first Linux OS trying to get the numbers to quit skipping like that on me.

On my triple boots I WANTED the DOZE on 1, Ubuntu on 2, CentOS on 3, Extended on 4, HOME on 5 and swap on 6.  But swap always came out on 5.  And on my machines that ONLY have Ubuntu and nothing else, Swap was still on 5, so I figured well maybe, that's where swap belonged.  I like to LEAVE some unallocated space at the end and have HOME last, so I can extend it if need be.

But now that I use a DataFile Server, sticking a 500 gig drive in this box was Overkill to the Max, hi hi...........
But at todays prices!  You can't really buy smaller cheaper!
I think my 100 Meg drive was 360 dollars.  My 1 gig drives around 250 bucks each, the 10 gigs around 200 bucks, the 40 gigs around 150 and the 80 gigs around 100.  Then I picked up some 200 gig drives for like 100 bucks, then some 500 gig drives for a hundred bucks and the 500 I put in this machine was only 90 bucks.

Today, you can buy a calculator for $1.99 that does MORE than the $185.00 calculator I bought when they first came out.

Now, if Taxes and Groceries would follow that same trend, I would be one happy camper, hi hi.............

I had to work, so haven't loaded much of my goodies yet, but everything is working perfectly, and FAST TOO!

TTUL
Gary

---

### Post by Kellemora on 2009-02-02
Hi Meierfra

You could be correct!
Although most of my machines are/were triple boot, the one and only time I tried installing a Linux Distro on a Doze machine, GParted said the drive was corrupt and wouldn't let me shrink the Doze.....  No Problem, Delete Doze, NO LOSS!
So ALL of the machines I have that are still triple boot are Ubuntu, Debian, CentOS and I don't use the latter two anymore at all.  There are just there until I need the space!  Left overs from when I first started looking into using Linux.
I chose CentOS first because I could get help from those familiar with RedHat, but that didn't pan out as well as I thought it would.
I found Ubuntu, but it said it was Debian based, so I looked up Debian and found Debian itself was a Distro, so I figured, hey, go straight to the horses mouth.  I liked it better than CentOS!
BUT, every time I hit a snag and did a search for anything, it was an Ubuntu based response.  THIS brings me to the Ubuntu Forums where I looked around, saw the friendly people, intelligent and helpful guru's and said to myself, THESE are the people I want to be associated with!  Not those Stuff Shirts elsewhere!
I downloaded Ubuntu and used it for one month, getting help here on the forums with problems.  Learning manufacturers don't know Linux exists, but Ubuntu had raced to the #1 position in record time.  I saw WHY!
I converted my entire office over to Ubuntu within 30 days of my first laying eyes on it.
Best Move I EVER made in my whole life!

Sure I get disgruntled about things not available in Linux and the remaining shortfalls of Ubuntu.  But then I realize, Ubuntu advances in 1 year, what took Gates 10 or more to do, and it's far from perfect.  The Ultimate Spyware OS known as Vista is WHY I began looking HARD at Linux in the first place.  Gates cut off his nose to spite his face by putting that OS out!

I hope it drove enough people like myself to Ubuntu that Manufacturers will finally stand up and take NOTE that the DOZE is a dying OS.........

TTUL
Gary

---

### Post by linuxe on 2009-04-28
Hi john i am in a real fix.
I have this type of problem.
Only 3 of my all partitions shows:

shibly@shibly-desktop:~$ sudo sfdisk -d
[sudo] password for shibly: 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=488392002, Id= f, bootable
/dev/sda2 : start= 97675263, size= 97675137, Id= 7, bootable
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=      189, size= 40001661, Id=83
/dev/sda6 : start= 40003584, size= 57669632, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     8192, size=  7835648, Id= b, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
shibly@shibly-desktop:~$ 


shibly@shibly-desktop:~$ sudo fdisk -l
[sudo] password for shibly: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x471be9c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    f  W95 Ext'd (LBA)
/dev/sda2   *        6081       12160    48837568+   7  HPFS/NTFS
/dev/sda5               1        2490    20000830+  83  Linux
/dev/sda6            2491        6080    28834816    7  HPFS/NTFS

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Disk identifier: 0x000c53e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3487     3917824    b  W95 FAT32
shibly@shibly-desktop:~$ 

I post for help here too: [http://www.linuxforums.org/forum/ubuntu-help/145455-please-help-ubuntu-9-04-a.html](http://www.linuxforums.org/forum/ubuntu-help/145455-please-help-ubuntu-9-04-a.html) but not everything resolved.
please help me.

Thanks in advance

---

### Post by caljohnsmith on 2009-04-28
> **linuxe said:**
> 
Hi john i am in a real fix.
I have this type of problem.
Only 3 of my all partitions shows:
```

shibly@shibly-desktop:~$ sudo fdisk -l
[sudo] password for shibly: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x471be9c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       [COLOR="Red"]30401[/COLOR]   244196001    f  W95 Ext'd (LBA)
/dev/sda2   *        [COLOR="Red"]6081[/COLOR]       12160    48837568+   7  HPFS/NTFS
/dev/sda5               1        2490    20000830+  83  Linux
/dev/sda6            2491        6080    28834816    7  HPFS/NTFS
```

So how many partitions do you have if more than three? Can you tell me exactly what your partitions should be? As shown in red above, your sda2 primary partition starts at a cylinder that is inside your sda1 extended partition, so even if you just have the three partitions shown by fdisk, your partition table needs fixing. Also, sda2 ends at cylinder 12160 while your HDD has a total of 30401 cylinders, so there is a large unaccounted for block of unused space on your HDD. Also, do you know what you did that might have corrupted your partition table?

---

