---
title: "Ubuntu 7.04 and Wireless MN-510"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by thompa on 2007-05-01
Hello there,
I am having problems again... While I was using 6.06, I couldn't get my printer hooked up and in doing some research came across some discussion that updates to 6.06 had somehow upset CUPS.. so, I thought that updating to the latest Ubuntu might do the trick!
Downloaded the file - which took 90 minutes on a broadband connection and then burned a CD. There seemed to be lots of advice to partition the hard drive so that the system went on one partition and files and settings on another.
Fortunately, I had kept notes and remembered which hda was which and installed on the correct one.

Again fortunately, I have another computer and can access the internet.. because nothing works and it seems many of my applications are missing! Can't even connect to the internet or our home network!

Browsing around trying to get things working - but messages keep popping up that I need an internet connection to download this or that file... hmmm I know that! 
I can't get wlan to show up in networking... but the ironic thing is the printer now works!

Shame about the rest... can anyone guide me?

By the way - although I have used the CLI, I do prefer to point and click so that I don't type anything incorrectly. I want to spend my time using applications on the computer becoming an expert on Linux.
CLI to me is a necessary evil!

---

### Post by Candace on 2007-05-05
If you're still wondering....
This is what I did from a fresh Ubuntu 7.04 install on an HP dv2000 with wireless card Broadcom 1390 WLAN. There seem to be a lot of different wireless issues with 7.04 so no guarantees, but hope these help. 

1. [http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505)

2. [http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

And my internet now works (without encryption so far). 

3. Encryption: [http://ubuntuforums.org/showthread.php?t=202834&page=40](http://ubuntuforums.org/showthread.php?t=202834&page=40)

---

### Post by thompa on 2007-05-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well the problem appears to have been caused by a badly scripted interface file is /etc/network/interfaces.

the wlan0 wasn't defined and setting it to auto enabled the wireless network... at least I think that is what I did.

Looking around the plethora of Linux sites, I came across a bug report about Samba with a recommendation tat a GUI be created to better implement networking - sounds like a great idea to me!

I still can't get over the security settings in Ubuntu which prevent me from editing a file like smb.conf! This file, once set is not usually touched again - until the next install of Ubuntu and yet it is so difficult to get at!

Security needs to be a lost more user friendly... it is worse than Vista - almost!

---

