---
title: "Wireless on Kubuntu"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by DM was on fire! on 2010-10-21
The question's been asked quite a few times, but no responses.
Here's my dilemma.

I have Kubuntu 10.04 running on a thumb drive. Everything works great, but the wireless won't. The wireless area is completely grayed out; basically telling you REJECTED. lol
SO what can I do? I read on the KDE forums I could run killall knetworkmanager && nm-applet & and that would work, but the problem I have is wireless is my only source of internet.
It works great on PuppyLinux, so I was going to download the network-manager and go from there, but it seems there's quite a few dependencies.
So what do I do? I really wanted to try out KDE. :c

---

### Post by TBABill on 2010-10-21
Depends on your wireless device. Some require connecting to the Internet (wired) and downloading a proprietary driver, or downloading on another system and installing. I have a Broadcom card and always have to plug in once to download updates and drivers, then activate the driver. Simple to do but it does require connecting once via wire.
 
You can find out what type of device you are dealing with by opening terminal and typing: ```
lspci
```
That's LSPCI in lower case. There should be a line in the output specifically for your card. More help can come after knowing the type of card and determining if any other steps need to be taken.

---

### Post by readycarpenter on 2010-10-21
ubuntu does not ship anything proprietary, often wireless card drivers are proprietary, so as a work around and to not break their own open source policy, ubuntu has added the "hardware drivers" application, it goes online and gets the drivers.

so you need to get online via ethernet just to install the wirelesss drivers.
then goto
system> administration> hardware drivers
your wireless card should show on the list

---

### Post by DM was on fire! on 2010-10-21
It works on Ubuntu just fine. Do I still have to go through these steps all because I changed desktop environments?
I ran it just fine on Ubuntu, and I would probably have put Ubuntu on my thumb drive, but my CD was dead and would give me an I/O error about 40% though.

---

### Post by beew on 2010-10-21
I have the same problem, not just with kubuntu, but with anything KDE  (Debian KDE edition, Fedora KDE edition) but gnome works out of the box.  I have no problem connecting wirelessly on the same machines with  Ubuntu, Fedora or Debian using the gnome network manager so at least for  me it has nothing to do with whether the drivers are proprietary, it is  a KDE problem (KDE network manager problem)

You many want to try using wicd to connect instead. "Completely remove" the KDE network manager using Synaptic  and reboot, then use  a wire  connection to download and install WICD

Wicd doesn't work quite well with me, it connects on startup but then  drops the connection after 15-20 minutes and takes forever to reconnect if  at all, but it would connect again on reboot and then the same thing  happens. But this may be because I am using gnome and it may work bettrer  on KDE (I tried it just out of curiosity, gnome nm works well for me).

---

### Post by DM was on fire! on 2010-10-22
Yes, I had a similar issue with LinuxMint KDE, and LinuxMint Xcfe for that matter (which is a shame, because I love Xfce as much as I love KDE).
However, I have PuppyLinux running KDE Trinity (the previous version) and it's perfectly happy. I think someone dun goofed when they did the wireless connection for KDE4.

I read somewhere (the KDE forums I believe) that I could use network-manager-gnome, and go from there. I remember we actually do have a computer wired to ethernet now, so I will have to boot from it some time. Thank you for the help though. 

Oh. Since I didn't check back at the topic, I went ahead and ran the command TBABill gave me; although I needed lsusb rather than lspci since it's an USB object. It's recognizing it just fine.

> dm@kubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 154b:6545 PNY 
**Bus 001 Device 003: ID 5041:2235 Linksys (?) **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  

---

