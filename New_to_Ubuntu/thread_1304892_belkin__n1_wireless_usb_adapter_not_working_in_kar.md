---
title: "belkin  n1 wireless usb adapter not working in karmic"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by akiratheoni on 2009-10-29
just installed karmic koala today. my belkin n1 wireless usb adapter is not working. i can detect wireless networks, but not connect to any of them.

it was working fine with jaunty but now it's not working. any help? thanks. i read something about using an older kernel but i don't know which version to use out of the ones listed on this webpage: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by akiratheoni on 2009-10-29
Bump, would be nice to see if I'm the only one who is getting this problem or if there is a solution to this. Thanks!

---

### Post by crazedwombats on 2009-10-29
I'm having the same issue using a D link USB adapter. Can locate networks but not connect to them? Just curious how is your network secured? I'm using WPA2.

---

### Post by akiratheoni on 2009-10-29
Yeah, I can locate all the networks but not connect to them. I'm using the Arizona State University wireless connection so there's no encryption on the network.

---

### Post by crazedwombats on 2009-10-29
I was just able to get mine to work. I changed my routers settings from AES+TKIP to just AES and everything magically worked. Good luck!

---

### Post by akiratheoni on 2009-10-29
Dang, I don't have a router so I can't do that! Oh well. I think I'm going to get my ethernet jack fixed so I can just do a wireless connection instead.

---

### Post by hebein on 2009-10-30
Hi, I am facing the same problem with Belkin N10117 v 1011 de USB-Stick.
Can see all networks, but connection is not established (WEP 64bit).
The stick seems to be assigned an IP-adress as I can see on the router, so there must be a problem on the Ubuntu side. 
Did you get your stick to work as 802.11N? I only got 54 Mbps.

regards,
gunther:popcorn:

---

### Post by wiz812 on 2009-10-30
Same problem with my azure wave-NU221. jaunty ran it fresh out of the box, no question at all. karmic justs seems to flirt with the network for a bit befor eventually bottling out. Could do with a nudge in the right direction soon or i'll be going back to XP cap in hand and that is so not cool.

---

### Post by akiratheoni on 2009-10-30
Bump, it seems that a lot of people are getting an identical problem with different wireless cards... I hope there's a fix out there. I'm currently on Vista which I don't want to be.

---

### Post by ricardisimo on 2009-10-31
D-Link DWA-140 USB wireless adapter on my machine. Worked flawlessly before Karmic. In fact, I had to investigate how to blacklist the internal PCI-Express wireless, so that the USB would be the default. Now all I can do is stare at really strong networks, and not join any of them.

Has anyone filed a bug report on this yet?

---

### Post by ricardisimo on 2009-10-31
There are at least two pertinent bugs:

One claims that those of us with the rt2870-based USBs simply need to blacklist rt2800 - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323)

The other seems to suggest that it is a kernel issue, resolved (for the time being) by booting from an earlier linux-image if possible - [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/436043](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/436043)

These are at least starting points. Let us know if any of these work for you.

---

### Post by ricardisimo on 2009-10-31
The three-step blacklisting and module addition solution in [that first bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323") solved my problem completely. Although it does take the connection a long moment to get going, it's zing-zap-zip right now. Good luck.

---

### Post by akiratheoni on 2009-10-31
Hey guys I'm bumping this to confirm that ricardismo's link worked for me and I now have Internet. It appears that Ubuntu is loading two modules that conflict with each other so you need to blacklist one of them. Here's the solution that I used, which was in the bug report posted in the post above me.

> 

Same issue with Belkin F5D8053v4 Wireless USB Dongle.

Symptoms of issue: Cannot detect access points. (no internet/network)

Fixed with:

Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.

Internets is now working perfectly.


---

### Post by wiz812 on 2009-11-03
Yes that worked for me too many thanks indeed!

Now its just down to the wierd green box that keeps appearing in the top right hand corner!;)

---

### Post by jastonas on 2009-11-13
> **akiratheoni said:**
> just installed karmic koala today. my belkin n1 wireless usb adapter is not working. i can detect wireless networks, but not connect to any of them.
[/url]

Working out of the box??
Mine is not recognised at all?? Could it be because I have 64bit?

---

### Post by SuperEngineer on 2009-12-27
Hi there
I reprted the following a while back but no real progress yet....
        492990                    [USB wireless adaptor (AW-NU221) recognises connection but will not connect in 9.10 - all ok in 9.04]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492990")

For what it's worth I also tried several other lastest distro relesases (live CDs rather than installed) and found that Kubuntu & Mint suffered the same way (no surprise as they're both Karmic variants). OpenSUSE (gnome & kde) bot failed the same way, Fedora ditto.  The only latest distro that didn't suffer from this bug was Mandriva.

Does anyone know if the "three step resolution" works if you can see the network but not connect to it???
Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.

Thanks.

---

### Post by ricardisimo on 2010-01-13
I wanted to add something here. I don't know what sort of upgrade took place recently, but the wireless is working pretty flawlessly right now. I've done nothing other than regular upgrades since finding that 3-step fix in Launchpad. There is no more delay or lag in my connection. I mean, there are better days and worse, but that's on the router end now, and not my machine.

---

### Post by Wolfie Lee on 2010-01-27
Nevermind

---

