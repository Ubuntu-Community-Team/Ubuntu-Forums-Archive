---
title: "Wake on Lan ? HP 625 wireless"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by Niemil on 2014-02-09
I've an laptop that's an [B]HP 625
[/B]On this computer I have currently dual boot. Ubuntu 13.10 and Windows 7.

I usually run Windows 7 (because of softwares I use frequently the past months), but I don't mind running Ubuntu 13.10.

The goal with wake on lan is that I wanna be able to turn on my computer and control it via my phone (Xperia acro S, android OS) and possible other computers as well.
I'm thinking of using TeamViewer or similar software.

This because I want to be able to control my downloadings, files and much more while I'm away. 
I've a extern harddrive connected with my laptop all the time where I've lots of stuffs, and it would just be great to have access all time to my laptop.


I don't want to need have the computer on all the time.
So I really want this wake on lan. Any suggestion how to do?

I read something about changing in BIOS, I been rarely in BIOS and I ain't sure which option it may be if it exists for HP 625?


Thanks in advance.

---

### Post by praseodym on 2014-02-09
Check in your BIOS the settings somewhere in "Wake on LAN" or "Power on PCI/PCIE Devices". Also check
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by Niemil on 2014-02-10
Yes, I found it I think. It already had the default setting as this, and I guess that's correct? It's some own BIOS that my HP 625 computer has. It's not like other computers I've been using where it's often blue background with white text or so. This HP BIOS I could use the mousepointer even.

Here is screenshot of it:
[http://i62.tinypic.com/msyo9i.jpg](http://i62.tinypic.com/msyo9i.jpg)

BEFORE PROCEEDING!
I need to know, is it impossible to do Wake on Lan with Wireless internet?

Fact is I got wireless, and I think I wanna stay with it. I don't wanna draw a cable all over the house or anything like it.
I googled earlier and some guides I read it said it has to be wired network, that wireless not working? :(

---

### Post by praseodym on 2014-02-10
You could check these:

[http://wireless.kernel.org/en/users/Documentation/WoWLAN](http://wireless.kernel.org/en/users/Documentation/WoWLAN)
[http://ubuntuforums.org/showthread.php?t=1978288&p=12288765#post12288765](http://ubuntuforums.org/showthread.php?t=1978288&p=12288765#post12288765)

But I don&#8217;t think it makes sense because the wireless card needs current all the time for it.

---

