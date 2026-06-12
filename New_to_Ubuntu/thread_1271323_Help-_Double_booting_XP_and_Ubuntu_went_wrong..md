---
title: "Help- Double booting XP and Ubuntu went wrong."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by ubuntnoob512 on 2009-09-20
**[COLOR=Red]Please help[/COLOR]. Windows XP wont boot after installing Ubuntu.**


I have a very special computer. Here is it's lifestory. Ok so, i bought it off of ebay as a 2.2gz Core 2 Duo (pretty fast), a 512 NVIDIA graphics card that i was told was relly good, It has a 15.4 inch screen (laptop), Mainly MSI brand whitebox, 111 gb HD, 4 gb of ram, and Windows XP 64 bit (one of the worst operating systems ever. My computer would freze and i would have to restart often.

The computer with powercord, drivers, and actuall win XP 64 bit disk was about $325. Yes, a great deal.

From there I installed Vista 32 bit, vista 64 bit, windows home 32 bit, and finally windows pro 32 bit.

I just recently have put Ubuntu 8.04 on my Xp 32 bit computer. I Partitioned the drive already so i had 5 GB for Testing operating systems like Ubuntu and in the future i want to try snow leopard, Google chrome, other versions of linix, and windows 7. 

In the Ubuntu set up, it would only let me put windows and Ubuntu on the same partion so i currently have a blank 5 GB partion.

Well the who point of this posting:

when i turn on my computer, it goes to the screen that lets me choose between the 2 operating systems.

If i click in Linix, it boots just fine and i am using linix as I am posting this question.

If i click on Windows Xp pro, i get the same blue screen that says something like:
If this is the first time you have seen this screen, restart your computer

If you have seen this screen before, uninstall all newly installed programs.

The only newly installed program is Ubuntu.

So, What do i do. I know a lot about computers but this is my first time using linix. I am not quite sure what to do. If you have read this whole thing and answered i thank you.
                                                      

                                     I forgot to say, I am 14, bad at spelling and i have the Actual Ubuntu disk. ( i burned it)

               

 Linix is on the same partion as windows. And believe me, Windows 64 bit has thrown lots of hissy fits so i got him deleted.

when I open Partion Editor it has something like this:

Partition _     File System            ____Mount Point___           Label _         Size____             Used __     Unused _Flags 
  /dev/sda1     ntfs_____________            /media/disk_________                 104.41GB_70GB_34.41GB__boot
/dev/sda3      extended _______________________________2.5GB_____       ---____          ----        
/dev/sda5      ext3               / ________________________________                                 2.33GB ___    2.11GB_  228MB   
/dev/sda6     linix-swap ____________________________172.54MB___  ----____         ----      
/dev/sda2     ntfs__________________________                                   Test Drive_4.88GB ___    ---- ____---    

ya

so please help, i need it. And talk in english because I am only 14 and new to linix.

---

### Post by erilidon on 2009-09-20
That's called the Windows BSOD (Blue Screen of Death). It sounds to me like your windows installation has become corrupt. If you still have the install disks you can try to reinstall it or even run a recovery.

If you are worried about any files that may be stored in windows, ubuntu should be able to access that hard drive.

---

### Post by ubuntnoob512 on 2009-09-20
Yes i have already gotten to that drive and i can get all i had on there again easily. And yes i do have the blue screen of death. I don't have the installation disks. I got Win XP 32 from my cousin. I have win7 from off of the pirate bay. Should i try to put that on. I have a DVD burner on this computer, just no dvds.

Ohh wait, i am chatting with that cousin, he is going to sent me a link to a download of win 32 bit and i can burn a cd.

that works.

---

### Post by kambrik on 2009-09-21
Did you install windows first or Ubuntu first?  Because you may have corrupted the windows boot loader. 

Do you have the windows recovery console installed?
If so you may be able to fix your windows and lose the linux then reinstall linux.  Look at this: [http://www.compuhowto.com/linux/removing-ubuntu-and-grub/]("http://www.compuhowto.com/linux/removing-ubuntu-and-grub/")

If you do not have the recovery console installed I would suggest losing the linux and do a fresh install of windows then reload linux. Or vise-versa

---

### Post by LewRockwell on 2009-09-21
we've heard of people having trouble with the pirated stuff

we're just wondering how anyone could verify the integrity of pirateware

Surely it would be fairly easy to slip a key-logger and password stealer into some pirateware

.

---

### Post by oldfred on 2009-09-21
If you have only 2.5GB for Ubuntu you let the system install without enlarging the partition. It will boot but your first update will fail as you do not have enough space. You need at least 8-10GB as a minimum for Ubuntu. You need to shrink the windows partition and use the slider to make more room for Ubuntu.
With 4GB of ram you do not need much swap for normal day to day use but 172.5mb is too small. If you ever want to hibernate you probable need 3 to 4GB to be safe. When you hibernate everything in memory must be written to swap. If your are running the 32 bit version only about 3.2GB is used anyway.

---

### Post by gizmobay on 2009-09-21
> In the Ubuntu set up, it would only let me put windows and Ubuntu on the same partion so i currently have a blank 5 GB partion.

I wonder if he overwrote the windows OS?

---

### Post by SuaSwe on 2009-09-21
> 
I wonder if he overwrote the windows OS?


I think ubuntunoob512 may have installed Ubuntu on the same partition as Windows without defragging very, very carefully first, which will cause part of the drive (and obviously potentially part of the system structure) to become corrupted.

> 
Did you install windows first or Ubuntu first? Because you may have corrupted the windows boot loader.


Unless I'm totally off with the fairies: Ubuntu's GRUB overwrites the Windows boot loader anyway - in fact that's really the idea - as GRUB recognises Windows whereas Windows' boot loader does not recognise Ubuntu. :)

To be truthful, having lived through a great deal of dual-boot nightmares helping friends with similar issues, my suggestion would be to back up your data, wipe the drive and partition it using a Windows installation CD (I've personally found this to be easier than using GParted) leaving at least 10GB for Ubuntu and probably more like 20GB to Windows XP. I do believe you can then format the rest of the space as NTFS - which you can do using Windows' Disk Manager - and use as storage, as this file system type will be accessible via either OS.

Or forget all about dual-booting and just go with Ubuntu - as far as I'm concerned, that's the best and easiest option of the lot. :D

---

### Post by Zoot7 on 2009-09-21
@ubuntnoob512
Have you by any chance got the error code of the BSOD? Also does it boot in safe mode? Your best bet is probably to perform a repair install. Guide here:
**[http://michaelstevenstech.com/XPrepairinstall.htm]("http://michaelstevenstech.com/XPrepairinstall.htm")**
And then re-install Grub to the MBR as specified here:
**[http://ubuntuforums.org/showpost.php?p=117829&postcount=2]("http://ubuntuforums.org/showpost.php?p=117829&postcount=2")**
> **SuaSwe said:**
> Or forget all about dual-booting and just go with Ubuntu - as far as I'm concerned, that's the best and easiest option of the lot. :D
Agreed. ;)

---

### Post by Random-penguin on 2009-09-21
"I got Win XP 32 from my cousin. I have win7 from off of the pirate bay"


Not a good idea using these as they almost certainly include malware..... Try just using Ubuntu for now and see how you get on.... You'll certainly learn some new skills, which could be really useful for any career or hobby (I note you're 14).

If you need windows for some program then check whether it is supported under wine or check out the Linux equivalents available.

If you really need windows a legal copy is the best way to keep the nasties out!!!

---

### Post by ubuntnoob512 on 2009-09-21
Thanks all, yes windows came first.

No, i don't think my version of win 32 has a virus or whatever. (my cousin used it, i scanned it with AVG, i read the comments, and it was the correct size.)

I tryed doing win 32 in save mode and all the options.

I dont have any data I need to back up. (I can access it though)

look for my newer one.

i have a newer post.

---

### Post by ubuntnoob512 on 2009-09-21
Found my new tread:

[http://ubuntuforums.org/showthread.php?t=1272186](http://ubuntuforums.org/showthread.php?t=1272186)

---

### Post by Darkwing-Duck on 2009-09-23
This might help in fixing GRUB and the MBR (Master Boot Record)

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

