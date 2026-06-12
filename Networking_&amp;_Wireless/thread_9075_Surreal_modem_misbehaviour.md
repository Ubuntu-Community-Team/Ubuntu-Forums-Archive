---
title: "Surreal modem misbehaviour"
date: 2004-12-23
forum: Networking &amp; Wireless
---

### Post by jonny on 2004-12-23
First, let me say that Ubuntu is a wonderful distribution.  I've played with Knoppix, Suse, Debian and, of course, Windows and none can match Ubuntu for the simplicity, beauty and harmony of its desktop and applications.  Except, that is, for configuring modems...

My external serial modem (intel chipset) has a life of its own.  Having failed with the Computer>System configuration>networking option, I precisely followed the instructions in the Ubuntu Wiki, but when I got to the 'sudo pon' command, nothing happened.  I had no joy with Modem Lights, either.

I retried the Computer>System configuration>networking screens, and the modem sprang into life.  It also fires up whenever I turn the computer on.  That screen is the only way that I can control the modem, but It's not very friendly and I'm afraid someone might break it.

Who knows how I might get an icon or panel applet to work?  I don't know if this is relevant, but I also have a broadband connection configured (I'm setting up the PC for someone else).

---

### Post by az on 2004-12-23
Use modem lights.  It is an applet.  Look here:
[http://www.ubuntuforums.org/showthread.php?t=6319](http://www.ubuntuforums.org/showthread.php?t=6319)

---

### Post by jonny on 2004-12-23
That was quick :shock:.  I've never yet met a corporate technical services team that responds as promptly as you do!

Presumably I'm meant to enter the device as ppp0 and the lock file as /var/lock/LCK..ttyS1 (I think I'm using serial port ttyS1) on the advanced tab.  If I do that, modem lights seems to behave properly (it asks me if I want to connect / disconnect and shows the connection time), but my modem stays silent.  Here's my tail output:

[Click on modem lights to connect]
Dec 24 02:53:34 localhost pppd[4263]: pppd 2.4.2 started by jonny, uid 1000
Dec 24 02:53:35 localhost chat[4264]: abort on (BUSY)
Dec 24 02:53:35 localhost chat[4264]: abort on (NO CARRIER)
Dec 24 02:53:35 localhost chat[4264]: abort on (VOICE)
Dec 24 02:53:35 localhost chat[4264]: abort on (NO DIALTONE)
Dec 24 02:53:35 localhost chat[4264]: abort on (NO DIAL TONE)
Dec 24 02:53:35 localhost chat[4264]: abort on (NO ANSWER)
Dec 24 02:53:35 localhost chat[4264]: abort on (DELAYED)
Dec 24 02:53:35 localhost chat[4264]: send (ATZ^M)
Dec 24 02:53:35 localhost chat[4264]: expect (OK)

[long ineffectual silence, after which I click on Modem Lights with tearful frustration to disconnect]

Dec 24 02:53:53 localhost pppd[4263]: Terminating on signal 15.
Dec 24 02:53:54 localhost pppd[4263]: Exit.

That's exactly the same result I that I got when I tried using tail to explain why pon had no effect when typed at a terminal prompt.  For the record, I've also tried using gnome-ppp and Kppd on Knoppix - all with the same result.  But, somehow, Ubuntu connects me with Computer>System configuration>networking.

Could it be a permissions thing?  I can only connect with the networking panel open; when I shut it, my connection shuts down.  Another thought: could my broadband connection be confusing things?  I'm a real noob to Linux, and I really appreciate your help.

---

### Post by az on 2004-12-24
I see that your modem is sending an ATZ - expect ok, with no corresponding "got-it" and no phone number.

1-  Have you tried other ports?  (ttyS0, ttyS2)
2-  Is pppconfig properly set up?  (with the correct port and so forth?) (sudo pppconfig)
3-  No, the broadband should not prevent your modem from dialing.

---

### Post by jonny on 2004-12-24
Success!  My modem's actually on ttyS0.  I'm convinced that I successfully tried that port with no success earlier, but who cares now!

Thanks for the successful, prompt diagnosis.  Not only is ubuntu an elegant distro,I've proven that the community's very supportive, too.  I plan to spread ubuntu CDs like confetti amongst all my acquaintances  :D

---

