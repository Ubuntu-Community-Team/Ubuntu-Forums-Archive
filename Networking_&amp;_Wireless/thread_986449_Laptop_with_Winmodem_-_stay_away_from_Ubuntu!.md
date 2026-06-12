---
title: "Laptop with Winmodem - stay away from Ubuntu!"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by uganda on 2008-11-18
After a Windows crash 2 weeks ago, I've had enough of Windows and decided to switch to Linux/Ubuntu.  I have heard good things about it, but after over a week, I am very disillusioned and disappointed.  I have a laptop with "soft modem" and either the Linuxant HSF driver or Ubuntu seems to have killed it.  It worked 2-3 times in the beginning, enthusiastically I paid $20 for the full speed Linuxant HSF driver, but for a week now, I have tried everything including completely re-installing Ubuntu and never get a dial tone (i.e. I can't hear a dial tone or dialling out of the laptop).  The line works, I have a Windows company laptop that I can plug it into and it works just fine.

I have emailed Linuxant and even though I *paid* for their driver, the only thing they could suggest is to re-install Windows on the laptop and see whether the modem still works.  Unfortunately, re-installing Windows is not an option for me, because it is way too complicated for me to set up again.

I have posted another thread a week ago ([http://ubuntuforums.org/showthread.php?t=974924](http://ubuntuforums.org/showthread.php?t=974924)) with the details and have since done a complete re-install of Ubuntu + HSF driver + pppconfig + wvdialconf and still nothing.  Any suggestions?

As it is now, unfortunately I can only recommend to anyone with a laptop and built-in Winmodem aka "soft modem" to stay away from Linux!

---

### Post by uganda on 2008-11-30
Fwiw, I ended up buying a PCMCIA modem, which works fine - see [http://ubuntuforums.org/showthread.php?p=6282592#post6282592](http://ubuntuforums.org/showthread.php?p=6282592#post6282592)

---

### Post by AEL on 2008-12-25
No its not ubuntu fault ... the truth is LINUX are not FRIENDLY in terms of installing driver due to no vendors will support the driver for FREE....

Inorder to detect your modem ...

Install the HSFMODEM.deb

Then use the terminal to execute the sudo sh cnxtinstall.run ...

visit this site it will help u most!

[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

Good Luck ....

Even Ubuntu is not for NEWBIE ... learn the basic syntax of LINUX before using it! Windows uses MOUSE but Linux uses KEYBOARD :)

---

