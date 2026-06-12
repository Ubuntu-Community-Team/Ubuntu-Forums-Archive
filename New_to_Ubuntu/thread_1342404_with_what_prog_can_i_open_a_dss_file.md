---
title: "with what prog can i open a dss file?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by ni ni on 2009-11-30
Hi all,

what program can i use to open a dss (digital Speech Standard) file??

Thanks :KS:KS:KS

---

### Post by howefield on 2009-11-30
Try this thread for a solution..

[http://ubuntuforums.org/showthread.php?t=134649](http://ubuntuforums.org/showthread.php?t=134649)

---

### Post by ni ni on 2009-11-30
oh thanks so much but that person used wine, and i don't have wine because i don't have windows; only linux.

---

### Post by Geoff918 on 2009-11-30
Here's some information:

[http://gitorious.org/linux-omap-dss2/linux/blobs/b42d4809ea05009fff30bf64135ddba7ddf31427/Documentation/arm/OMAP/DSS](http://gitorious.org/linux-omap-dss2/linux/blobs/b42d4809ea05009fff30bf64135ddba7ddf31427/Documentation/arm/OMAP/DSS)

Here's a post I found from:

Mr Tibbs: location: 

[http://www.linuxquestions.org/questions/linux-software-2/can-i-install-olympus-dss-player-under-wine-in-linux-523993/](http://www.linuxquestions.org/questions/linux-software-2/can-i-install-olympus-dss-player-under-wine-in-linux-523993/)


We have several DSS players here running under Linux/Wine.  But you have several options:

1. ExpressScribe is a free windows program that works very well under wine. There is a DSS extension available on their site that allows it to play DSS files as well. Our secretaries use this player for transcription under Linux with serial port foot pedals.

2. Olympus's DSS Player Lite works "out of the box" even if you simply copy it from a Windows installation. (No need to run the installer on Wine.)

3. Olympus's DSS Player 2002 (I haven't tried others yet) install and works "out of the box" on my Suse 10.1 system. It did not work when I tried it last year on my Suse 9.x version with a much older version of wine.

Now for the devices issue. It is unlikely you will not get the DS-330 working under wine since it doesn't have a Linux USB driver but the DS-3000 and DS-4000 series should work because they connect like a removable drive.

EDIT:

I got the DS-4000 (and DS-2300) working with Wine. I did not attempt to get the USB driver working though. I setup a script to automatically copy DSS files from the Dictaphone when it is automounted. I also re-directed the Message Tray in the Olympus software to the DSS Player to allow my users to delete files right off of the device. Functionally, this works very much like it does in Windows. Some of the hardware specific features like transfering ID info to the device still don't work but that isn't much of an issue.

For the DS-330's I used VMWare Player with Win98 (lite). Because I am using Suse 10.2, I needed to re-compile the kernel to enable USB support but once installed, it works flawlessly.

---

### Post by howefield on 2009-11-30
You don't need windows to use wine.

Wine simply allows you to run certain windows programs in linux. It is great for some programs which are supported. Certainly not a panacea for all windows programs however.

I'll see if I can find a native linux program which can open your dss files.

---

### Post by howefield on 2009-11-30
[http://www.nch.com.au/scribe/linux.html](http://www.nch.com.au/scribe/linux.html)


A native linux version.

---

### Post by ni ni on 2009-12-03
thanks to everyone for helping me. i installed dsslite player from the olympus website in wine like in the post recommended by howefield and it worked perfectly!

p.s. - i can't believe i thought you needed a dual boot, or whatever to use WINE.  I'm so dim!

---

