---
title: "Resize partition nondestructively"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by alanrlow on 2009-08-21
Hi all, a few questions actually.
I have just installed Ultimate Edition on a 80gb external USB drive and I let the installer use the whole drive. Silly I know as now I want a chunk of this drive back. As I couldn't do this within the OS I booted a rescue disk and used Parted to resize it back to 20gb. When I exited I was told I would need to adjust my boot loader but not how to. With the upshot that it wouldn't boot anymore and I had to reinstall and I'm back to square one with one huge partition. How do I safely shrink it? 
When I try to hibernate I'm told my swap isn't big enough. How do I increase it?
Thanks.

---

### Post by mikechant on 2009-08-21
What's the file system type? If it's ext2/3/4 then you can shrink or grow it without losing data.
Most people prefer to use gparted rather than parted for partition manipulation.
It may be that gparted uses a different resize method to parted, but I've never needed to change my grub config as a result of just shrinkiing a partition.

---

### Post by rbc on 2009-08-21
Shrinking from 80G to 20G is a pretty drastic change. Try shrinking from 80 to 75, then 75 to 70, etc

---

### Post by mapes12 on 2009-08-21
How about splitting the external drive into the partition sizes you want before installing. Then run the install on the partition you want it to be installed on. The boot loader will then be automatically setup for that partition size.

---

### Post by alanrlow on 2009-08-21
> **mapes12 said:**
> How about splitting the external drive into the partition sizes you want before installing. Then run the install on the partition you want it to be installed on. The boot loader will then be automatically setup for that partition size.

Yep, that's exactly what I ended up doing. Only problem now is that when I try to hibernate I get told swap space is to small. I'm guessing it's refering to my swap file partition size which is 3.9gb Any ideas as I'd rather hibernate than standby.

---

### Post by Penguin Guy on 2009-08-21
> **alanrlow said:**
> Yep, that's exactly what I ended up doing. Only problem now is that when I try to hibernate I get told swap space is to small. I'm guessing it's refering to my swap file partition size which is 3.9gb Any ideas as I'd rather hibernate than standby.
Resize the partition in GParted from the Live CD?

---

### Post by mapes12 on 2009-08-21
Hello alanrlow

Glad that my suggestion was of some help.

Given how fast Ubu boots and shuts down I haven't any experience of hibernate and standby. I guess this better suits MS machines that take forever to do anything productive. With Ubu I just boot or shutdown. Boot time on this old Pentium III is less than 60 seconds from pressing the "go" button to surfing the web. Same for shutdown, but the other way around of course.

---

### Post by LewRockwell on 2009-08-21
> **alanrlow said:**
> When I try to hibernate I'm told my swap isn't big enough. How do I increase it?

increase it when you do your partitioning

.

---

### Post by markbuntu on 2009-08-21
sudo apt-get install gparted

sudo gparted

This will open the gparted partitoner and you can increase the swap partition size.

I don't use hibernate with my netbook, it will suspend for a week. The partitions are all messed up from multiple distro tryouts so I am not sure if the swap will even work.

---

### Post by clemon79 on 2009-08-27
> **Penguin Guy said:**
> Resize the partition in GParted from the Live CD?
This is actually precisely what I tried to do. (Or, in my case, the Live USB Stick. :)) Problem is, when I try to shrink the main partition so I can expand the swap one (I want my swap to be 4GB, since I have 2GB of RAM in the netbook; this is UNR), as the point where it's actually supposed to do the resize, I get:

Please run 'e2fsck -f /dev/sda5' first.

...and the whole procedure eventually fails. Nondestructively, fortunately, but it's puzzling, because the previous step is in fact the very 'e2fsck -f -y -v /dev/sda5' it's asking for, and that seems to run just fine.

Attempts to run the precise command (with a 'sudo' in front, of course) in a Terminal window and then going back to try again have been fruitless as well. (Just to be sure I'm not even launching gparted from the UNR interface; I'm opening a Terminal and executing "sudo gparted".)

Anyhow, I'm really puzzled and would welcome any ideas people have.

---

### Post by nimblfingrs on 2009-08-27
I too have problems resizing partitions.  When I first installed, I told Ubuntu to live side by side with windows, and dual boot.

The amount of disk allocated to swap file is 173mb.  I want to raise it to at least 700mb.  I have 512 mb RAM.  

I ran gparted from live cd.  I shrunk a partition so I would have room for expanding the swap file.  Actually i would need to move my Linux partition first, and then expand the swap file into the vacant space.

I now show over 1GB of unallocated space.  However, whan I attempt to expand the Linux partition, the indicator shows that I can shrink, but not expand that partition.  BTW, this is 9.04.

I did notice that the linux part, and the swap file are both contained in the 'expanded?'  section, with a flag, and a set of keys indicated.  Is there an action I can take to un-lock the partition?  BTW, the expanded part is 2.5GB.

This is an Acer laptop. The HDD is ~60 GB.  The hidden partition is ~5GB. my C: is ~25GB.  My D: was ~25GB, with ~2.5 GB taken by the linux part and the swap file.  I had shrunk the D: part contiguous with the linux part, if that makes sense...

Any help would be appreciated...

---

### Post by clemon79 on 2009-08-27
> **nimblfingrs said:**
> I too have problems resizing 
I did notice that the linux part, and the swap file are both contained in the 'expanded?'  section, with a flag, and a set of keys indicated.  Is there an action I can take to un-lock the partition?  BTW, the expanded part is 2.5GB.
Are you right-clicking on the swap partition and selecting "swapoff" first? That will remove the keys and allow you to manipulate the partitions. Dunno if that will fix it (because I'm doing that and having the problems I detailed in my earlier message), but it'll certainly get you in the right direction.

---

### Post by LewRockwell on 2009-08-27
ok, our heads are going to explode!?!

how many different OP trouble-calls can we fit into one thread?!?

.

---

### Post by LewRockwell on 2009-08-27
> **alanrlow said:**
> Hi all, a few questions actually.
I have just installed Ultimate Edition on a 80gb external USB drive and I let the installer use the whole drive. Silly I know as now I want a chunk of this drive back. As I couldn't do this within the OS I booted a rescue disk and used Parted to resize it back to 20gb. When I exited I was told I would need to adjust my boot loader but not how to. With the upshot that it wouldn't boot anymore and I had to reinstall and I'm back to square one with one huge partition. How do I safely shrink it? 
When I try to hibernate I'm told my swap isn't big enough. How do I increase it?
Thanks.

ok, you first

you say you just installed it...great, since you just installed it you won't lose much if you go back right now and repartition correctly

feel free to search and read various tutorials, threads, and posts regarding proper and foresightful partitioning(including my previous ones as well)

final note: learning partitioning and grub bootloader administration will repeatedly and richly reward you in your present and future endeavors

.

---

### Post by LewRockwell on 2009-08-27
> **markbuntu said:**
> sudo apt-get install gparted

sudo gparted

This will open the gparted partitioner and you can increase the swap partition size.

I don't use hibernate with my netbook, it will suspend for a week. The partitions are all messed up from multiple distro tryouts so I am not sure if the swap will even work.

feel free to use Synaptic to install the partition editor from a GUI...if you feel so inclined

please do NOT use sudo to open Gparted!

use:```
gksudo gparted
```

also, please do NOT use Gparted on the drive you are currently booted from!

re: messed up partitions and possible swap problems...elaborate?

.

---

### Post by LewRockwell on 2009-08-27
> **clemon79 said:**
> This is actually precisely what I tried to do. (Or, in my case, the Live USB Stick. :))

Please, in the future, initiate a separate and new thread for each trouble-call so specific instructions to specific posts are not mis-interpreted and mis-applied

> **clemon79 said:**
> Problem is, when I try to shrink the main partition so I can expand the swap one (I want my swap to be 4GB, since I have 2GB of RAM in the netbook; this is UNR), as the point where it's actually supposed to do the resize, I get:```
Please run 'e2fsck -f /dev/sda5' first.
```...and the whole procedure eventually fails. Nondestructively, fortunately, but it's puzzling, because the previous step is in fact the very 'e2fsck -f -y -v /dev/sda5' it's asking for, and that seems to run just fine.

Attempts to run the precise command (with a 'sudo' in front, of course) in a Terminal window and then going back to try again have been fruitless as well. (Just to be sure I'm not even launching gparted from the UNR interface; I'm opening a Terminal and executing "sudo gparted".)

notes:

use "sudo" for CLI functions that originate and complete in the terminal

use "gksudo" for initiating GUI functions when su is required

DO NOT USE PARTITION EDITOR ON THE SAME DRIVE YOU ARE BOOTED FROM!?!?!

also...sidenote:

it should be pointed out that in today's machines you should partition the swap size at 1x Max Ram...so if your unit can only handle 2GB of ram then there is no reason to have more than 2GB

.

---

### Post by LewRockwell on 2009-08-27
> **nimblfingrs said:**
> I too have problems resizing partitions.

Please, in the future, initiate a separate and new thread for each trouble-call so specific instructions to specific posts are not mis-interpreted and mis-applied

> **nimblfingrs said:**
> When I first installed, I told Ubuntu to live side by side with windows, and dual boot.

The amount of disk allocated to swap file is 173mb.  I want to raise it to at least 700mb.  I have 512 mb RAM.  

I ran gparted from live cd.  I shrunk a partition so I would have room for expanding the swap file.  Actually i would need to move my Linux partition first, and then expand the swap file into the vacant space.

I now show over 1GB of unallocated space.  However, whan I attempt to expand the Linux partition, the indicator shows that I can shrink, but not expand that partition.  BTW, this is 9.04.

I did notice that the linux part, and the swap file are both contained in the 'expanded?'  section, with a flag, and a set of keys indicated.  Is there an action I can take to un-lock the partition?  BTW, the expanded part is 2.5GB.

This is an Acer laptop. The HDD is ~60 GB.  The hidden partition is ~5GB. my C: is ~25GB.  My D: was ~25GB, with ~2.5 GB taken by the linux part and the swap file.  I had shrunk the D: part contiguous with the linux part, if that makes sense...

where to start...lol

{{sigh}}

ok, rundown:  Acer laptop with a 60GB hard drive, Windows in the second partition(25GB), and a hidden Acer recovery partition in the first partition(5GB).

Not exactly sure what is or isn't on the "D" partition(s) and how exactly those are "laid-out" and/or "arranged" either.

as you might have noticed from previous threads on this forum, we assume you've backed-up any valuable data and that you have defragmented Windows several times(and at least one final time in safe mode)...before...Before...

BEFORE!!!!

(did we mention to backup and defrag before LiveCD partitioning commences?)

booting from a LiveCD and performing partition creation and/or enlargement/shrinkage/movement/etc

if your laptop were on our tech bench we would maintain your hidden recovery partition(first primary partition), shrink your windows partition(ubuntu has already had a go at that in your case) to 20GB(second primary partition), create a 35GB extended partition using the remainder of the drive(third primary partition), then create a logical 1GB swap partition and a logical 34GB partition for Ubuntu inside your extended partition

hopefully this post, along with many others that many searches would find...will prepare you to successfully enjoy years of proper and prosperous partitioning and bountiful beautiful booting via the wonderfully grand grub bootloader!

Wheeee, this computin' stuff's fun!

.

---

### Post by Mark Phelps on 2009-08-27
Hey Lew ...

You get the "most-posts-answered-in-a-row-in-a-single-thread" award!!

This magnificent award entitles you to a FREE, that's right, FREE, copy of Ubuntu.

... wait ...

It already is FREE.

Sorry ... guess you'll have to contend yourself with framing my email reply.

And yeah, I share your frustration of just getting started helping someone only to have the "me-too's" start taking over the thread.

---

### Post by LewRockwell on 2009-08-27
> **clemon79 said:**
> Are you right-clicking on the swap partition and selecting "swapoff" first? That will remove the keys and allow you to manipulate the partitions. Dunno if that will fix it (because I'm doing that and having the problems I detailed in my earlier message), but it'll certainly get you in the right direction.

here, we see a common occurance while using a LiveCD when swap partitions already exist on one or more drives...said drives being present during the boot-up of the LiveCD operating system

the operating system will recognize and secure these multiple swap partitions

sometimes you will notice that the GUI "swapoff"(found via your previously described "right-click" menu and also found on the drop down menu as well when that swap partition is highlighted/selected) doesn't have the desired operation and leaves the swap engaged and locked

then you might go to the terminal:```
sudo swapoff /dev/*yourswappartitionhere*
(meaning something looking like this "hda3" "sda3" "sdc2" etc)
```if you have more than one swap requiring release then obviously you will need to "swapoff" multiple times
(yes we know "sudo swapoff -a" is supposed to work..."supposed" being the clue here)

Wheeee!

.

---

### Post by LewRockwell on 2009-08-27
> **Mark Phelps said:**
> Hey Lew ...

You get the "most-posts-answered-in-a-row-in-a-single-thread" award!!

This magnificent award entitles you to a FREE, that's right, FREE, copy of Ubuntu.

... wait ...

It already is FREE.

Sorry ... guess you'll have to contend yourself with framing my email reply.

And yeah, I share your frustration of just getting started helping someone only to have the "me-too's" start taking over the thread.

oh wow, we had that happen too just last week and smoke came out of it and it popped several times and then went ppppppffffffffttttt

then the neighbor lady's stepfather's second cousin's great-grandson came over and said it was a piece of junk because it didn't have Windows 7 on it

after that the plumber came by to report that the sewer would continue to be backed up until next Thursday and he said he had a TRS-80 once but lightning struck it before his daughter could teach him how to boot it up

later on in the afternoon we went to the sportsman's club and the waitress spilt not one but THREE strawberry daiquiris right down the front of Sissie's sheer white blouse

needless to say we didn't stay long so we didn't get to watch the trap and skeet competition at all

what a day that was!

.

---

### Post by nimblfingrs on 2009-08-28
Hey Clem, 

Thanks!! That was exactly what I needed.  It took 2 tries, as I'm new at using Gparted, but I have it sized like I want it now...

PB:P

---

