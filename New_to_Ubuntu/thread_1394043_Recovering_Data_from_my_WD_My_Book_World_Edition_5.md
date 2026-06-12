---
title: "Recovering Data from my WD My Book World Edition 500Gb"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by G-ManD on 2010-01-30
Can someone please help, I have a WD My Book World Edition 500G (Blue Rings). I am now totally frustrated after spending the entire day trying to resolve backing up the data. The drive has been removed from the initial case and I have attached it to a sata USB Docking station. I downloaded the Ubuntu software and follow the web forum [http://randomlylearned.blogspot.com/2008/09/recover-data-from-my-book-world-edition.html](http://randomlylearned.blogspot.com/2008/09/recover-data-from-my-book-world-edition.html) to the tee.
 
In Ubuntu I was able to create a folder via the command in the terminal window as follows
sudo mkdir /media/xyz
sudo mount -t ext3 /dev/sdb4 /media/xyz
when trying to mount the drive i get a message as follows
mount: special directory 4 does not exist.
I admit I am not a expert at lunix.....but how do i know what ext the drive is or how it is partitioned. It all seemed so simple a task to complete. 
I am able to see the drive but it will not mount automatically

---

### Post by mechro on 2010-01-30
Try gparted (partition manager). Should be in **System > Admin... > Gparted or Partition Editor**

Also, when you plug in the drive, see if it turns up in **Places**. You can single-click or right-click to mount it from there.

---

### Post by mechro on 2010-01-30
> **G-ManD said:**
> 
 
sudo mount -t ext3 /dev/sdb4 /media/xyz



Ahh! I see. That applies to the blog writer's kit. It would only work on your kit by pure chance.

As I said above, see if the drive appears in Places and you shouldn't need to issue any Terminal commands.

---

### Post by G-ManD on 2010-01-30
> **mechro said:**
> Ahh! I see. That applies to the blog writer's kit. It would only work on your kit by pure chance.
 
As I said above, see if the drive appears in Places and you shouldn't need to issue any Terminal commands.
 
Cheers mechro....i will give it a bash

---

### Post by G-ManD on 2010-01-30
I probably should have mentioned that i am working with window XP as my OS. Don't know if that makes things a little more difficult. I burnt the stable version 0.4.6-1.iso of gparted as an image with Alchol 120% to a CD. changed the boot sequence in my system bios and got a blank screen during boot up. I don't have gparted loaded onto a HD. so your previous thread is present some understanding difficulty on my part.
 
some more back round on my part. I right click on my computer and went to the manage tab. where i am able to see a number of partitions on the WD drive. just that it does not recognise the drive with a letter.
 
how do i go forward from here

---

### Post by mechro on 2010-01-31
> **G-ManD said:**
> 

I downloaded the Ubuntu software...
 
In Ubuntu I was able to create a folder via the command in the terminal...



Ooh.. Err... you now say you're working from Windows XP?

What Ubuntu software did you download? Have you got a Ubuntu LiveCD?

The instructions I gave would apply to a working Ubuntu installation or a Ubuntu LiveCD i.e. from a Ubuntu desktop you could go to Places or start up the Gparted program.

---

### Post by G-ManD on 2010-02-01
My apologies Mechro...I am a complete novice and a real bozo for not explaining properly. I did indeed download ubuntu and a copy of gparted from the gparted website. In both instances i created a bootable CD. In the previous thread i actually attempted to boot with gparted CD. it was during this that i realised that you where refering to gparted in ubuntu software...
 
My operating sysytem is not Ubuntu but in fact windows XP. so as the CD suggested i can run both systems. I only chose for the excersize to run in mode where i could revert without saving changes to windows XP. in otherwords booting via the Ubuntu CD. hopefully i have managed to express myself properly this time. so this is what happened in the ubuntu application.
proceeded to Places and saw text in the pull down menu "Drive" that being my WD My book world Drive. on attempting to click on it I got the following message "Unable to scan drive for media changes. Device is not active". If I click on the Computer text i am able to see three icons. 40GB Harddisk, drive and filesystem. If i right click on Drive and select mount the following message appears "unable to mount location . Can't mount file".
I tried what you said eventually and accessed gparted through the system pull down menu. this is what i got.
 
I got a whole lot of headings Partion, file system, size, used, unused, Flags and the following information under each heading I will relay them as headings as listed above. 
1st Line Unallocated(Partion), Unallocated(File System), 23.53 MiB(Size), ---(used), ---(Unused), Blank(Flags)
2nd Line /dev/sdb1(Partion), ext3(File System), 2.80 GiB(Size), 320.41 MiB(used), 2.49 GiB(Unused), raid(Flags)
3rd Line /dev/sdb2(Partion), Linux-Swap(File System), 101.98 MiB(Size), ---(used), ---(Unused), raid(Flags)
4th Line /dev/sdb3(Partion), ext3(File System), 964.84 MiB(Size), 33.68 MiB(used), 931.16 MiB(Unused), raid(Flags)
5th Line /dev/sdb4(Partion), Yellow exclamation next to this one, unknown(File System), 461.89 GiB(Size), ---(used), ---(Unused), raid(Flags)
I was able to create a media folder and mount /dev/sdb1 to that.....it took ages to read. 
I was able to find out a little more info.....properties on the drive. 
Device Info:
Model: -                  Generic external
size:-                      465.76 GiB
Path:-                     /dev/sdb
Disk Label Type:-    msdos
Heads:-                  255
Sectors/Track:-       63
Cyclinder:-              60801
Total Sectors:-         976768065
 
I would really like to just be able to recover the data on the drive. I have information that was only stored to it and no where else. are you able to point me in the right direction
thanks for your help

---

### Post by CharlesA on 2010-02-01
If you don't have Ubuntu installed, run it off the livecd > test Ubuntu or somesuch option.

What do you get if you run "sudo fdisk -l" (no quotes) with the drive plugged in?

---

### Post by mechro on 2010-02-01
The information you quote suggests there was a Linux filesystem running on the WD drive. Does this sound correct?

Also "raid" is mentioned which suggests it was working in tandem with one or more other drives. I'm not sure that you can read data from a "raid" drive removed from its original system. Somebody else with experience of raid would have to help you with that.

---

### Post by anaconda on 2010-02-01
hmm.. The thing I dont get from your post is: does the disk work normally? Or is it partially broken?

But anyway:

You can also read ext3 disk in windows (if the disk is working OK), if you install the fs-driver 
[http://www.fs-driver.org/](http://www.fs-driver.org/)

And (in ubuntu) it seems that the partition you want to mount (where all the data is) is sdb4.. And the unknown filesystem is not a good sign.

so you can (from the live CD) eg. create a folder
sudo mkdir /mnt/sdb4
and then try to mount the partition to it by:
sudo mount /dev/sdb4 /mnt/sdb4
And with luck it will work.

If it wont, there are 2 (free) programs, that can be used for rescuing files from corrupted hard-disks
testdisk and photorec
testdisk can correct corrupted partition information, and if it wont work, then 
photorec can search files from corrupted partitions. But with it you will lose the orginal names of the files.. the contens will be ok though.

---

### Post by howefield on 2010-02-01
> **mechro said:**
> The information you quote suggests there was a Linux filesystem running on the WD drive. Does this sound correct?

It is cfs if I recall correctly. I'll dig out my manual.

---

### Post by mechro on 2010-02-01
> **howefield said:**
> It is cfs if I recall correctly. I'll dig out my manual.

I'm kinda prompting the OP to tell us why and how they have ext3/raid partitions configured on a drive when they are running windows XP. It seems to me they've acquired a drive which was part of a raid system.

---

### Post by waspbr on 2010-02-01
good luck to ya, I vowed never to use any more WD products after I lost 400GBs from my WD Mybook... it all started with a clicking sound and before I knew it the whole think was borked. 

as I said, good luck to ya.

---

### Post by G-ManD on 2010-02-01
ok hold on a second guys.......we are running to fast with things. the WD digital drive was removed from it original case due to eletric fault. I have attached as indicated in my first thread that it is plugged into a usb drive docking station. that in turn is plugged into a laptop running windows xp as operating system. i then have to use the ubuntu livecd to try and see the drive. 
 
CharlesA i have tried "sudo fdisk -|" and get
>
incidentally i did also mention in my first thread that i had visted a forum 
[http://randomlylearned.blogspot.com/2008/09/recover-data-from-my-book-world-edition.html](http://randomlylearned.blogspot.com/2008/09/recover-data-from-my-book-world-edition.html)
 
did the whole sudo gismo gwuadgie thing

---

### Post by howefield on 2010-02-01
> **mechro said:**
> I'm kinda prompting the OP to tell us why and how they have ext3/raid partitions configured on a drive when they are running windows XP. It seems to me they've acquired a drive which was part of a raid system.

The Mybookworld drives are formatted with a Linux file system. They are network drives. You create CIF shares on them and can access them from any platform, although the main supported platform is Windows.

To the OP, there is a huge amount of info here, don't know if you have had a look.

[http://mybookworld.wikidot.com/start](http://mybookworld.wikidot.com/start)

---

### Post by CharlesA on 2010-02-01
The -l is a "lowercase L" not a pipe.

That should list all the drives.

---

### Post by mechro on 2010-02-01
Oh dear, it looks like WD has some weird and wonderful way of configuring this My Book. Raid on a single drive?? Awesome - not.

Can only suggest to try searching again but mention "single drive raid".

---

### Post by mechro on 2010-02-01
> **howefield said:**
> The Mybookworld drives are formatted with a Linux file system. They are network drives. You create CIF shares on them and can access them from any platform, although the main supported platform is Windows.

To the OP, there is a huge amount of info here, don't know if you have had a look.

[http://mybookworld.wikidot.com/start](http://mybookworld.wikidot.com/start)

Thanks. I didn't realise that it was a network drive.:oops:

---

### Post by G-ManD on 2010-02-01
> **howefield said:**
> The Mybookworld drives are formatted with a Linux file system. They are network drives. You create CIF shares on them and can access them from any platform, although the main supported platform is Windows.
 
To the OP, there is a huge amount of info here, don't know if you have had a look.
 
[http://mybookworld.wikidot.com/start](http://mybookworld.wikidot.com/start)
 
 
Yes i have visited this site. that's partly how the problems started cause i could get the WD drive to mount........better still i am useless at linux

---

### Post by CharlesA on 2010-02-01
What was the problem with the original enclosure, you said it was some kind of electrical problem.

Did you get any output from running fdisk -l ?

---

