---
title: "Dell Optiplex 755 + Ralink rt2870 usb adapter = Won't build, won't connect"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by newtonchris2 on 2016-04-13
Hi,

  I've spent so many hours now trying to figure out the solution to a problem before having to bug anyone else about it.  Unfortunately, similar issues have been resolved in ways that don't apply to me.  

I have a dell optiplex 755.  It does not, by default, have wireless capability.  I bought a wireless adapter so I may connect to my wireless router.  It's a ralink rt2870 usb wireless card. 

  I am stuck on the build.  When I get inside the file I type..

$ sudo make

 ..  after much data output to the screen I eventually see two errors..  and still no internet access.  

Is there anyone familiar with this issue that might be able to help me?

- Chris

---

### Post by HermanAB on 2016-04-14
Unless you have a very old system, you don't need to build or install the driver - it should already be there:
[https://forums.linuxmint.com/viewtopic.php?t=191243](https://forums.linuxmint.com/viewtopic.php?t=191243)

---

### Post by newtonchris2 on 2016-04-14
Thank you, Herman.  It sounds like I'm not using the correct terminology then.  If the driver is already available for me then I can't figure out why I'm not connecting to the internet.  I had windows 7 running before installing Ubuntu.  The same usb wireless card worked just fine on windows 7.  Since deleting windows and installing Ubuntu I cannot get online.  

I know I'm doing something wrong, but being that I'm so new to ubuntu I don't even know where to begin to fix the issue.  

Stressed and desperate,
-Chris

---

### Post by Geoffrey_Arndt on 2016-04-14
Chris . . . . no need to be stressed.    It does take some experience to build wireless drivers.   For example, do you know if you have the requisite software installed on Ubuntu to allow you to do the build in the first place?   Then, when you build a driver like this and basically, start running a modified kernel, what happens when the kernel gets updated?

So, while I have successfully built realtek wireless drivers - - it's just not worth the hassle.   So, I opted to buy (from Amazon - - about $10) a couple proven usb-wireless adapters that are "plug & play".

Took about 2 minutes for the Ultra 150 b/g/n nano dongle to find and connect to my wireless gateway.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by Geoffrey_Arndt on 2016-04-14
One other really important detail - - just what version of Ubuntu are you running?   If you're still on 12.04 . . . . just updating will most likely cause your wireless device to function.

---

### Post by howefield on 2016-04-15
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by newtonchris2 on 2016-04-17
I have Ubuntu 14.04 LTS

---

### Post by newtonchris2 on 2016-04-17
> **Geoffrey_Arndt said:**
> Chris . . . . no need to be stressed.    It does take some experience to build wireless drivers.   For example, do you know if you have the requisite software installed on Ubuntu to allow you to do the build in the first place?   Then, when you build a driver like this and basically, start running a modified kernel, what happens when the kernel gets updated?

So, while I have successfully built realtek wireless drivers - - it's just not worth the hassle.   So, I opted to buy (from Amazon - - about $10) a couple proven usb-wireless adapters that are "plug & play".

Took about 2 minutes for the Ultra 150 b/g/n nano dongle to find and connect to my wireless gateway.

[http://www.pandawireless.com/](http://www.pandawireless.com/)


Thank you for the follow-up.  The ralink rt2870 device that I have is plug&play(as far as I know), but it seems outdated.  After continued research I'm finding that the driver for this device is referencing handles in the 2.4.x kernel that have since been renamed in later kernel versions.   My kernel is now a 4.2.something.   I found a patch written in 2008, but when I run the patch..

"$ patch -p1 [patchname].patch"

 ..nothing comes of it.  I just see the cursor return itself to the line below; there is no output and there is no confirmation.  I have to end up killing it (after 10 minutes) just to get back to my command line.

The problems I am running into at time of "sudo make"..

A..  There are many "assignment from incompatible pointer type" errors.
B..  There are many "warning: unused variable"  errors.

This brings me to my next question.  

1..  _*Am I running the patch command correctly?*_  If so, then I need to figure out why I'm not getting a response from the terminal when I am entering said command.  Note:  the patch is located within the same home directory as the driver file.  Also, I've searched about other driver versions that were said to have been already installed(native) in the ubuntu OS(ie, drivers for rt2800, etc.), but doing a driver lookup comes back with zero drivers listed.

If I could just get my hands on a recent driver/patch then maybe all of my problems will be solved.  Furthermore, I am not also able to connect the computer to a hard line(which may be a related issue), so there is no chance I'll be able to install any drivers from the machine's terminal screen.  I have to computer-hop the data from my windows notebook to my ubuntu desktop via a usb storage drive.

I'm on at least 10+ hours of searching for a solution to this.   Oh ubuntu, you better end up being as good as they say..

- Chris

---

