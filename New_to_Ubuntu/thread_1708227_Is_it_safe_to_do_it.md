---
title: "Is it safe to do it ?"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by pressko on 2011-03-16
Hi,

I have one ext4 partition with ubuntu on it and one NTFS partition with data stuff.
I want  to install Win 7 for dual boot system , but i don't want to format my NTFS part, which is full. So can i re-size ext4 part. with Gparted Live CD , [SIZE=3][B]safely ? 

[/B][SIZE=1]10x in advance :popcorn:

Best Regards ,
Pressko
[/SIZE][/SIZE]

---

### Post by Grenage on 2011-03-16
Yes, you should be ok, but remember to backup your important data - there are no guarantees.  The Windows partition will need to be a 'Primary' partition.

---

### Post by false truths on 2011-03-16
As long as you don't resize it too small to fit the data on it already, you should be fine. The question is, will the new NTFS partition have enough space to hold Windows 7?

---

### Post by matt_symes on 2011-03-16
Hi

It should be alright but i advocate always backing up your hard drive when performing this sort of operation.

Kind regards

---

### Post by hotrod6657 on 2011-03-16
You should be able to shrink your ext4 partition, as long as you have enough free space and don't try to shrink it to the point that it is too small for the amount of data you have on it.

Make sure you back up your information before messing with this at all.  Partitioning is tricky business but that should work.  as long as you have enough free space on the ext 4 partition you should be able to shrink it and make a new ntfs partition out of the unallocated space.

You may be best to try picking up a cheap 2nd hard drive and install it on that so you wouldn't have to worry about shrinking partitions.

---

### Post by pressko on 2011-03-16
Awesome , 10x for the quick response for all of you. Yeah the EXT 4 part is big enough 120 gb and it has only 14 % used space ... so i will split it 50-50% and i hope nothing will go wrong with my Ubuntu :)

---

### Post by Elfy on 2011-03-16
I've resized my / drive in the past with no ill effects. You might need to check the original and new UUID - you might get a boot problem and need to reinstall grub.

```
sudo blkid
cat [COLOR="Red"]/boot/grub/grub.cfg[/COLOR] |grep UUID
```
If you run this from the livecd you'll need to mount your install and include the whole path - eg in my case > /media/43f9cd41-c238-4798-8435-5d19a839e4db/boot/grub/grub.cfg |grep UUID

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Long time writing and I suspect you'll have answers saying backup - do it :)

---

### Post by hotrod6657 on 2011-03-16
That sounds like a plan.  Just be careful and make sure you give it time to finish, depending on what it has to move it may take a long time.  Don't get impatient and try to restart it or anything or you'll be in a world of trouble...

---

### Post by pressko on 2011-03-16
It's Done ;) 10x guys everything is fine :P I'm going to install Win 7 (puke) C Ya ;)

---

### Post by hotrod6657 on 2011-03-16
Glad it worked without any issues.

---

### Post by pressko on 2011-03-16
I'm trouble ... I cant boot ubuntu after i installed Win7  :( 
 
Even i'm presing shift while booting there is no GRUB menu , can u tell me how to fix it up step by step :(

---

### Post by hotrod6657 on 2011-03-16
You're going to have to reinstall GRUB.  Do you have a Ubuntu Live CD?  

Boot in to that and then follow the guide linked below:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I haven't needed to do that in a while, but that guide should work

Edit:

We probably should have warned you about that when you said you were installing Windows with Ubuntu already installed.  Nothing went wrong, Windows usually/always blows away GRUB when you install it on top of a system.  That's why I always install windows first on my dual boot systems.

Have no fear, that guide should get you where you need to be.

---

### Post by pressko on 2011-03-16
Yep i saw that after i posted ... sry .. :( 
I will try , but i dont have Live CD :(

---

### Post by hotrod6657 on 2011-03-16
Do you have the image still or can you redownload it from within Windows and burn it there?

Win 7 supports burning .iso images natively, just right click on the image and select "burn to disk"

Then you should be set to try the guide.

---

### Post by pressko on 2011-03-16
ok , i'm know in live CD Ubuntu...

Can u gide me cuz i'm failing to repair my grub2 :( According to the guide ... i'm Doing that : 



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8647c657

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6528    52428800   83  Linux
/dev/sda2   *        6528       13055    52428800    7  HPFS/NTFS
/dev/sda3           13055       30025   136314880    7  HPFS/NTFS
/dev/sda4           30025       30402     3023873    5  Extended
/dev/sda5           30025       30402     3023872   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1846

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ sudo mount /dev/sda1/mnt
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/dev/sda1
install_device not specified.


:(

---

### Post by matt_symes on 2011-03-16
Hi

Open a terminal from the liveCD and try this.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Kind regards

---

### Post by pressko on 2011-03-16
Sry guys ... i'm just one dump bastard  :D  

I did it when i take it slowly and think before asking dump questions :(

NOW everything is working just fine ... grub2 is here and booting both systems like charm ... 10x to all of u . 


PS: LOVE UBUNTU community <3 <3

---

### Post by hotrod6657 on 2011-03-16
> **pressko said:**
> Sry guys ... i'm just one dump bastard  :D  

I did it when i take it slowly and think before asking dump questions :(

NOW everything is working just fine ... grub2 is here and booting both systems like charm ... 10x to all of u . 


PS: LOVE UBUNTU community <3 <3

Glad everything worked for you.

I love the Ubuntu community too!  People helping people always makes me happy.

---

### Post by pressko on 2011-03-18
it's me ...again  ;) 


I have noticed that every time i boot Win7  the system time is behind with 2 hours :O I have to synchronize it and after i reboot and boot ubuntu then reboot and boot Win 7 .... system time is 2 hours behind again ... :O 

So is there any relation Ubuntu - Win 7 time ? 

PS: all settings like timezone and etc. are fine .

---

### Post by matt_symes on 2011-03-18
Hi

Set Ubuntu to use local time and not UTC.

IIRC this is what will cause that issue.

Kind regards

---

### Post by pressko on 2011-03-18
what do u mean by UTC and how to disable it ?

---

### Post by matt_symes on 2011-03-18
Hi

UTC is universal coordinated time and is *almost* synonymous on the Greenwich meridian without British daylight saving. It is based on the rotation of the earth.

Local time is, well, your local time.

I would suggest you are 2 hours behind of UTC ?

Microsoft uses Local time and Ubuntu uses UTC by default.

To change open a terminal and type

```
sudo hwclock --localtime
```

Enter your password. It will not be echoed to the screen.

I believe this is persistent between reboots but if it's not post back.

Kind regards

---

### Post by pressko on 2011-03-19
> **matt_symes said:**
> Hi

UTC is universal coordinated time and is *almost* synonymous on the Greenwich meridian without British daylight saving. It is based on the rotation of the earth.

Local time is, well, your local time.

I would suggest you are 2 hours behind of UTC ?

Microsoft uses Local time and Ubuntu uses UTC by default.

To change open a terminal and type

```
sudo hwclock --localtime
```Enter your password. It will not be echoed to the screen.



I believe this is persistent between reboots but if it's not post back.

Kind regards

i set it to hwclock to localtime but the problem still presist :(


I solved it by editing sudo gedit /etc/default/rcS 
UTC=yes to UTC=no 

now it's fine :)

---

