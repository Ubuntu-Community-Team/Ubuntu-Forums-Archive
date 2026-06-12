---
title: "I need help getting my Broadcom working"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Windozeuser on 2008-02-01
The forum admin moved my post - I did not post in this area.  And as far as help is concerned, I have been to a plethora of forums, all of which tell me to download ndiswrapper.  But the only place I can download to is the desktop.  Then I am told to run a bunch of commands, all of which have no idea where the software is!  When I try to download to any other directory either nothing happens (no message!) or I am told that I do not have permissions to access that folder.  All in all, it is frustrating to install a driver.  I do not have the patience to read reams of different methods of doing a simple task and then being told how this "seems to work" or "make sure you have at least the xxx kernel installed", etc.
I am not extolling the virtues of Gates' crippled system, but it is a far more friendly environment when installing new equipment.  My WLAN in windoze was installed without even a single configuration script and works well (in windoze).  So please don't flame me about where I place my posting, it was placed here by the forum bigwigs.

---

### Post by Windozeuser on 2008-02-01
Yes, I have checked the link and it still assumes an intimate knowledge of Linux.  Not much help to me.  Very little or no windoze installations require command line intervention - it all works from within th GUI.  And then only when drivers are not available.  But, again, the installation is seamless and transparent.  Sometimes a reboot is necessary, but very seldom.  If the Linux community wants to really become competitive with the M$ monopoly, then the "user-friendliness" of the Linux distros must become just as simple to install.

---

### Post by Windozeuser on 2008-02-01
My PC in this case is an HP Compaq nx7400 notebook with built-in WLAN device.  I use all the USB ports, so I really don't want to add another device as my notebook already looks like a porcupine.....

---

### Post by matthewcraig on 2008-02-01
Just pop in a PCMCIA card.  Or use a USB hub if you have a lot of devices.  No reason to work yourself into frustration, when a $30 solution is available at you nearest computer store.  Maybe HP has a different model if the internal WiFi is a mini-PCI device that can be removed.


And, just my opinion on your easy to install comment, Ubuntu is wildly easy to install - especially compared to Windows.  No hardware manufacturer's drivers, and the otherwise smooth installation will even help you do a dual boot if you want it.  When the hardware works, it works great.  When it doesn't... well, you know the rest.  But, in fact, the Linux kernel actually supports more hardware devices than any other operating system, so chances are good that it will work.  Hopefully, the Broadcom specific support may improve one day, but Broadcom's failure to embrace Linux should not be a roadblock for anyone, since it is a cheap and easily replaceable device.

ndiswrapper is non-free, binary-blob software, anyway, and it's not a long term solution.  Unless Broadcom releases the specifications or someone reverse engineers the drivers, you're going to want a more supportable device.

---

### Post by Lord Illidan on 2008-02-01
You have a problem with Broadcom. Fine, then make a thread in [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

In fact, one of the stickies there is :
[HOWTO: Broadcom 43xx based wireless cards the EASY way.]("http://ubuntuforums.org/showthread.php?t=405990")

Give as many details about your hardware as you can.
Also, this might be useful : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

Yes, you have to do some work. Yes, it isn't as easy as Windows, I agree. But I wouldn't be so quick to diss Linux since Broadcom don't release drivers for Linux in the first place, and the devs have to reverse engineer their own. If your card was made by a linux friendly company, like say, Intel, then it would need only a single click to be enabled.

---

