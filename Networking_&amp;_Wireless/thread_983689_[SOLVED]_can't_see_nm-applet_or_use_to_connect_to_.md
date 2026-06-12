---
title: "[SOLVED] can't see nm-applet or use to connect to anywhere but at a single location"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by allankyoto on 2008-11-15
Here's the situation.

Ubuntu 8.10 installed via Wubi (through Vista) on my Dell 1525 Laptop at my workplace.

Everything works fine. Can detect various wireless networks at the office...can join them easily. No problem

I took the laptop home and now the NM-applet has disappeared from the system tray although when I check with system-monitor it seems to be running. 

I add the network manager icon to the taskbar but that does not allow me to see those wireless connection bars. It does not give me any option to enable or disable wireless like it does when I am at work. 

I had enough with fooling with the wireless and plugged it in via ethernet connection but that also will not work. 

I rebooted the system into Vista and both the ethernet and wireless connected fine at home. 

Any thoughts? Suggestions? Please don't leave me stuck on Vista at home! ;)

---

### Post by Marcus Derekus on 2008-11-16
What wireless card do you have?

---

### Post by allankyoto on 2008-11-16
I'm not sure why it would matter which card I have since the card works fine in connecting to any of the 3 or 4 networks available at my office when in Ubuntu and only will not work when trying to connect to my home wireless network (or wired network for that matter)

My guess is there is something screwy with Network Manager but I'm not software savvy enough to know what that is. 

For the record  the wireless card is a built in Intel Corp Pro/Wireless 3945abg and the wired is the Marvell Technology 88e8040 PCI-E Fast Ethernet Controller (rev12)

That info was gotten from a check with lspci.

---

### Post by xadder on 2008-11-16
Did you try the solution I just posted (thread before yours), editing /etc/network/interfaces and removing everything without "lo"?

---

### Post by allankyoto on 2008-11-16
As you suggested at the bottom of this thread...[http://ubuntuforums.org/showthread.php?t=981247](http://ubuntuforums.org/showthread.php?t=981247)

I did a 

sudo edit /etc/network/interfaces

and removed all lines except those including lo.
Now I just have:

auto lo
iface lo inet loopback

After rebooting I was able to detect my wireless networks as usual with network manager which was back in its usual place in the system tray. 

Thanks a bunch for this!

---

### Post by xadder on 2008-11-16
Hi allankyoto,

Glad to be of help! I wasn't the first to find this solution, but I can't remember where I found that idea. There were so many posts on wireless problems which all involved a lot more work than simply editing "interfaces". I'm curious if there is some disadvantage to this though. I started a new thread 

[http://ubuntuforums.org/showthread.php?t=983801]("http://ubuntuforums.org/showthread.php?t=983801")

("simple wireless solutions") so maybe somebody will explain - I know too little about networking. For now I'm just happy it works!

---

### Post by xadder on 2008-11-16
Hi allankyoto,

Maybe you should flag this thread as [SOLVED]? It would be nice to see some wireless problems posts with this flag, as people seem to be writing in new posts with exactly the same problem, without reading about this solution at least?

I wasted so much time trying to get my wireless working,that it is frustrating to see people unaware of a possible solution.

---

