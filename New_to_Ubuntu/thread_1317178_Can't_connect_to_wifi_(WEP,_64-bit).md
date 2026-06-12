---
title: "Can't connect to wifi (WEP, 64-bit)"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by jparrot99 on 2009-11-06
As I just posted, I have an old laptop I'm trying to get working, but I am struggling. I've tried searching the forums, I am just getting more confused!

I am new to linux. I am trying to install Ubuntu 9.10. It's a bit slow, that is in my other post.

Sony Vaio, PCG-972M, 496 MHz, AMD Duron Processor, 128 MB RAM
Harddrive 3.3GB, using 1.9GB (as reported within Ubuntu by "Disk Usage Analyser")

PCMCIA card: Belkin F5D7010
Wifi: WEP, 64-bit, key index: 1  (I can't change this)
No ethernet port

I can't connect to the internet. I've clicked on the Network icon at the top of the screen. It can see my wifi. I entered:
Security: WEP 40/128-bit key
Key: (as working on my other XP machine)

But it doesn't connect. It just comes up with the dialog again a few minutes later.

What do I do next? Any help appreciated!
   Jose

---

### Post by yvan232002 on 2009-11-06
Hello,
I am also using XP and Ubuntu. I have the same settings as yiu describe. Sometimes the router stops working when using both systems. Usually it works again after power off / on again on the router.

---

### Post by jparrot99 on 2009-11-08
Thanks I'll try that. I haven't ever managed to connect yet, so I didn't think it was a problem with the router, but with Ubuntu, but happy to try anything!

---

### Post by jparrot99 on 2009-11-08
OK, I tried rebooting everything, to no avail.

Anyone any ideas how I can get any further with trying to connect over wifi? What should be my next step? 

PCMCIA card: Belkin F5D7010
Wifi: WEP, 64-bit, key index: 1

It just keeps asking for key again and again.

At the moment I don't have any other option than to give up with Ubuntu.

Jose

---

### Post by Rayve on 2009-11-08
I'm running 9.04, and netbook remix on my netbook, so this is only a thought, but:

Have you tried right clicking on the network icon at the top, then choosing "Edit Connections"?  From there, you should be able to click the "Wireless" tab, see your wireless connection, and be sure that "Enable for all users" is checked.

ETA: I use WPA2 security, myself.  I've been told WEP isn't the most secure, as others mention below.

---

### Post by Hobgoblin on 2009-11-08
Disable security on the router and see if you can connect.

If you can then try a different security, WEP isn't very secure anyway.

---

### Post by keplerspeed on 2009-11-08
Try the ubuntu hardy heron LTS release 8.04. Some people are experiencing issues with WEP and karmic, including me on a eeePC. If you dont want to use 8.04 give 9.04 a try, Jaunty Jackalope.

It appears that you wireless card is detected and working fine. Can you connect to any other networks? Double check the WEP key too.

---

