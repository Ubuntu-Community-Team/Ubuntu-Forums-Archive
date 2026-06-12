---
title: "USB drive ejecting prematurely. Any one else have this?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by powel212 on 2009-08-31
I have 2 computers with different hardware configurations both running Jaunty. If I try to transfer large groups of small files to an external drive then the drive will halfway through the transfer eject the disk. I have tested with external drive and USB flash drive. It leads me to think it may be in the software. The individual files are small but in total are over 1 Gig. 

Anyone else experience this?

Am I missing something?

Powel

---

### Post by schwascore on 2009-09-05
There's a joke here somewhere...

(Sorry, I don't have any info that will help.)

---

### Post by rogerp1 on 2009-09-06
Yes I have had this. I am having a lot of trouble with USB...havent found any answers yet.

If I plug in my Freecom dvb-t usb dongle it works for a bit and then crashes and I lose anything thats connected to USB.

USB drives work for a bit and then disconnect. I have to reboot to get then to work again

---

### Post by javadubb on 2009-10-24
I have this problem too, and it's making me furious. My USB flash drive will eject after a short period of time automatically, and when I am copying files I get a "Input/Output Error." I really need help on this.  ](*,)

---

### Post by NCLI on 2009-10-24
Karmic will be here in a few days, and handles disks in a totally different way. Submit a bug if it still happens in Karmic.

---

### Post by javadubb on 2009-11-08
This is making me very angry, I can't transfer any of my photos, music or videos to my second computer without my USB flash drive automatically unmounting. It will typically start to copy a few files and then unmount randomly. The drive works fine on other computers... had the problem in jaunty, and i'm in karmic and I still have it. I REALLY NEED HELP please i am a beginner.:cry:

---

### Post by ace007 on 2009-11-08
It has to do with ubuntu's drivers and the specific hardware in your computer. I have no problem with my USB drives, but my SD card reader repeatedly unmounts and remounts, usually mid-file copy. 

I dont have a solution but the proper drivers should help. (No clue how to do this.)

---

### Post by PGScooter on 2009-11-08
Can't you disable automatic mounting/unmounting?

Have you tried copying using nautilus/thunar/cp/rsync/ ?

---

### Post by anewguy on 2009-11-08
> **schwascore said:**
> There's a joke here somewhere...

(Sorry, I don't have any info that will help.)

I didn't know they actually made viagra for PC's!

Dave :)

---

### Post by ricardo.gloe on 2009-11-09
Could just be a hardware problem. Had similar problems a while back, turned out the usb connections to the mb were a bit loose.

---

### Post by javadubb on 2009-11-10
Aaah, I'm not exactly sure what to do. I have always tried to copy files by dragging and dropping in Gnome (Nautilus I think right?), and I just installed the program rsync and tried copying a few videos from my USB flash drive to my computer and rsync froze up, then my USB drive unmounted. :( --Sometimes when I plug my usb drive back into the computer, It won't mount. The computer recognizes it but i get a funky message when I try to open the icon that appears. On the other hand, sometimes when the drive unexpectedly unmounts, I plug it back in and it works. It seems as though there is a period of time I need to wait for it to work again. I don't know what "cp" is and I have no idea how to enable/disable automatic mounting/unmounting. Does anybody suggest I do something that could eliminate some probable causes of this problem? 


Thanks for the help.

---

### Post by javadubb on 2009-11-15
After searching for a long time on google i found that this problem could possibly be related to something called "ehci_hcd." I am not sure really but the thread can be found at [http://ubuntuforums.org/showthread.php?t=1214003](http://ubuntuforums.org/showthread.php?t=1214003).

I really wish I could figure this out!!!

---

### Post by javadubb on 2009-11-28
!!!!!!! My usb storage devices will (typically) work if i boot up my computer with them plugged in! Only problem is the transfer rates are around 3.2 MB/s :(


so, maybe for those of you who try this the same thing will happen?

---

### Post by tgalati4 on 2009-11-28
Premature ejection could be caused by extra sensitivity of the USB controller.  Unfortunately, there are no pills for this, but there are some creams that are effective.

Seriously, it sounds like your USB controller has gone tits up.  It works at USB 1.1 speeds but not 2.0 speeds.  The resets occur when the chip heats up (as during a large file transfer, then ejects).

Post the output of the following:

dmesg | tail 

(plug in your usb device)

dmesg | tail -20

(Perform a repeating operation until premature ejection.)

dmesg | tail -30

---

