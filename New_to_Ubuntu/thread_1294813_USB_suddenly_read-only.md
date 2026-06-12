---
title: "USB suddenly read-only?"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by 2roombas on 2009-10-18
The 2 gb Kingston Data traveler usb-stick that I've been using the past few days has suddenly become read-only and I cannot delete any files from it to add more.  What happened?  It was woking just fine for a few days?!

Yes, I searched this before asking here, but I'm too new with all of this because I really found nothing that made sense to me as a fix.

Does anyome know how happened, and is there an easy fix?

---

### Post by ikt on 2009-10-18
Does it give an error message or anything?

---

### Post by t0p on 2009-10-18
This has happened to me a few times.  One time, it was due to the filesystem becoming corrupted (Linux will often mount damaged filesystems read-only, to prevent further damage). I reformated it and all was fine.  One time the usb stick was damaged, so I took it back where I bought it from for a refund.  One time I put the stick aside for a week or so, then I tried it again and it worked okay.

The first 2 options aren't so good for you if there are irreplaceable files on the stick.  The last one is obviously the most attractive, but there's no guarantee that the stick will start working again.

---

### Post by 2roombas on 2009-10-18
Yes.  After I plug it in I used to see "Kingston" in my Places, but now only "2.0 GB Media."

After opening that folder I see the files I'm trying to delete off of there, but after Edit>SSelect All then Delete, A pop up...
[B]
Cannot move fike to the trash, do you want to delete immieediatly?[/B]

I click "delete all" because this pop-up seems to occur on every file noq.  After I click "delete a;;" I see...
[B]
Error while deleting:  [/B]There was an error getting informatiom about the files in the folder "main."

Then when I click the "Show more details", I see this...
[INDENT]Error stating file '/media/disk/pool/main/f': Input/output error[/INDENT]

---

### Post by 2roombas on 2009-10-18
> **t0p said:**
> This has happened to me a few times.  One time, it was due to the filesystem becoming corrupted (Linux will often mount damaged filesystems read-only, to prevent further damage). I reformated it and all was fine.  One time the usb stick was damaged, so I took it back where I bought it from for a refund.  One time I put the stick aside for a week or so, then I tried it again and it worked okay.

The first 2 options aren't so good for you if there are irreplaceable files on the stick.  The last one is obviously the most attractive, but there's no guarantee that the stick will start working again.

Actually this stick is brand new, I just bought it and have only used it a few times now.  It was fine up until last night I when downloaded the 9.10 beta to it... and now it won't remove those files.  How do I reformat?  I have nothing but those files on there.  I have all my personal stuff kept on an 8 gb sandisk.

---

### Post by picpak on 2009-10-18
This happened to me with a flashdrive a while back. I ended up having to reformat it under Windows to get it to work again. If anyone knows how to reformat a USB drive under Ubuntu, please let me know.

---

### Post by Sir Jasper on 2009-10-18
Hi,

If there is nothing on it that you need then use Gparted (also described as Partition Editor) and reformat the stick (having unmounted it first).

Click the drop down box in the top right hand corner to choose your stick and after you have chosen the file system you want click on the green apply icon.

My regards

---

### Post by 2roombas on 2009-10-18
> **picpak said:**
> This happened to me with a flashdrive a while back. I ended up having to reformat it under Windows to get it to work again. If anyone knows how to reformat a USB drive under Ubuntu, please let me know.

All 3 of my computers have Ubuntu on them, no more windows to use, so yes, can someone lease explain how to reformat a usb?  Hopefully kind of easy too? :P  

I have searched but most answers ar 2+ years old, using terminal.  Is there nothing more current, easier?

---

### Post by Sir Jasper on 2009-10-18
Do as suggested in reply #7.

---

### Post by BikeHelmet on 2009-10-18
> **picpak said:**
> This happened to me with a flashdrive a while back. I ended up having to reformat it under Windows to get it to work again. If anyone knows how to reformat a USB drive under Ubuntu, please let me know.
Reply #7 might work.

If you don't have the Gnome Partition Editor installed, grab it from Add/Remove.

I had a stupid OSX machine corrupt a Kodak camera's SD card. Best guess as to why? I think it wanted to stick a .trashes folder at the start of the card, and the camera didn't like that.

Ubuntu wasn't able to fix the issue by formatting. After an hour of farting around with it in OSX/Ubuntu, I had to use an old Win2k computer to format it. Solved in 30 seconds. :mad:

---

### Post by 2roombas on 2009-10-18
[QUOTE=Sir Jasper;8126339]Hi,

If there is nothing on it that you need then use Gparted (also described as Partition Editor) and reformat the stick (having unmounted it first).

Click the drop down box in the top right hand corner to choose your stick and after you have chosen the file system you want click on the green apply icon.

And where is this green apply icon??

UPDATE:  Never mind. I see thst I have to install the gparted packages.  I'm doing that now.

---

### Post by 2roombas on 2009-10-18
I open the Partition Editor and the only options in the upper right pulldown are...

/dev/sda (25.95 GiB)
/dev/sdb (1.85 GiB)

Screen when choosing the sdb... a green apply?!

---

### Post by Sir Jasper on 2009-10-18
Hi,

You are almost there, but you need to unmount the flash drive first.

Then you have to choose the format you want before it can be applied.

My regards

---

### Post by Sir Jasper on 2009-10-18
Hi,

If you still have a problem understanding use the help button, google or come back for clarification.

My regards

---

### Post by 2roombas on 2009-10-18
OK... silly question here, sorry (but thank you too because I'm learning :)), you say to unmount first... um, how do I do that?  All I have done is plug it in ths far.  I only bought these usb drives a few weeks ago to get rid of my CD's that were messing up, and that ppl said were going the way vinyl records did,  so I'm pretty new to them right now

---

### Post by Sir Jasper on 2009-10-18
Hi,

If your stick does not show on your screen then find it in the Places menu.

Right click on it and choose unmount.

Now load Gparted and do what you did before.

Now click the drive icon on the left and choose your format.

Finally, click on the green tick item near the top.

Exit from Gparted. Remount the stick and see if you can copy to it.

My regards

Added:

It is always wise to unmount your stick before you unplug it.

---

### Post by 2roombas on 2009-10-18
I just went to places>2.0 GB Media...Unmount Volume.  Opened Partition Editor... now what do I do?

---

### Post by 2roombas on 2009-10-18
> **Sir Jasper said:**
> Hi,

If your stick does not show on your screen then find it in the Places menu.

Right click on it and choose unmount.

Now load Gparted and do what you did before.

Now click the drive icon on the left and choose your format.

Finally, click on the green tick item near the top.

Exit from Gparted. Remount the stick and see if you can copy to it.

My regards

Added:

It is always wise to unmount your stick before you unplug it.


What do I choose?  Options are:

ext2
ext3
ext4
ft16
fat32
linux-swap
reiserfs

---

### Post by Sir Jasper on 2009-10-18
Hi,

Choose FAT 32 as it was that or Ext 3.

Good luck. I am off line now.

My regards

---

### Post by 2roombas on 2009-10-18
Cool.:) Thank you... the problem is solved... and I just learned something new!   I'm lovng this ubunu!\\:D/

---

### Post by picpak on 2009-10-19
> **Sir Jasper said:**
> Hi,

If there is nothing on it that you need then use Gparted (also described as Partition Editor) and reformat the stick (having unmounted it first).

Click the drop down box in the top right hand corner to choose your stick and after you have chosen the file system you want click on the green apply icon.

My regards

Hmm, I never thought of it that way before. That'll work wonders. Thanks!

---

### Post by pgar23 on 2009-10-19
> **picpak said:**
> This happened to me with a flashdrive a while back. I ended up having to reformat it under Windows to get it to work again. If anyone knows how to reformat a USB drive under Ubuntu, please let me know.

Here is a website that easily breaksdown how to format a USB drive.
[http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)

---

### Post by super kim on 2009-10-19
i had this problem,

something to do with the mount... i fixed it by un-mounting then mounting the drive several times [http://ubuntuforums.org/showthread.php?t=1286449](http://ubuntuforums.org/showthread.php?t=1286449)

---

### Post by pgar23 on 2009-10-19
You wont even have to download any of those programs, you can format your USB drive from the termianl.
STEP BY STEP INSTRUCTIONS;
1. Applications > Accessories > Termianl
2. sudo mkfs.ext3 /dev/sda1 (In this example I used /dv/sda1, the /dev stand for /devices and the /sda1 is the slot where the usb drive should be located, it may be different for you)
[COLOR=#FF0000]Caution:[/COLOR] Careful while entering device/partition name; wrong name can wipe out entire hard disk!!!

---

### Post by Goveynetcom on 2009-10-19
I have had this problem many a time with my 4GB flash drive and my PSP in USB mode. But I didn't reformat them I just unmounted the targeted device(without removing it) then I removed it and put it back. Then it gave me full access again. Also, did you accidentally change your privileges so that you can't modify files in that folder?

---

### Post by jakan on 2009-10-26
> **Goveynetcom said:**
> ..I just unmounted the targeted device(without removing it) then I removed it and put it back. Then it gave me full access again

This just worked for me, thank you!

---

