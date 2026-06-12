---
title: "Networking for guests"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by sheol on 2007-08-07
Since linux doesn't have a networking group, how do I allow any user to connect to networks on my computer without the need for super user privleges?

ifstate seems to be one file, but what else needs to be done?

---

### Post by dougfractal on 2007-08-07
so what happens when a user uses nautilus > go >  network > connect to server   ?

there's a guide here
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking)

---

### Post by sheol on 2007-08-09
I'm not sure you follow my post.
*I* know how to get my computer talking to the network when I am using it.  I want a guest to be able to connect to the internet, without other privileges.

Is this something the network manager does? Because I'm still using iwconfig and dhclient (both of which need to be run as su).  The network managers never seem to work right for me.

---

### Post by dougfractal on 2007-08-09
> I'm not sure you follow my post. sorry I thought you were trying to mount a networked drive.


"iwconfig and dhclient" don't work at boot up? You need to activate them every reboot?

If this is case then it can be fixed, unfortuantly I have got my laptop with me, so I'll help from memory 8-[

its something todo with /etc/network/interfaces

 /etc/network/interfaces ? (WiFi WEP) [http://ubuntuforums.org/showthread.php?t=12045](http://ubuntuforums.org/showthread.php?t=12045)

---

### Post by sheol on 2007-08-10
Well nI suppose I should explain everything regarding my networking.

I have an lenovo X61s laptop with an integrated Atheros wireless card.

My network managers have never worked.  (In fact my network managers have never worked for wireless for anyone so far as I have personally experienced).  That's no big deal I'm quite comfortable in the command line or in the guts of my computer.

When I was using Feisty interfaces just seemed to not do much and so I had to manually connect.  After upgrading to Gutsy it actually was creating a bogus dhclient
see [https://bugs.launchpad.net/ubuntu/+bug/130715]("https://bugs.launchpad.net/ubuntu/+bug/130715")

So I indeed always connect from the command line.  With mot programs it I could simply add the user to the group for which the program belongs, but dhclient calls something else which requires root privleges.  So dhclient always has to be run with sudo.

---

### Post by dougfractal on 2007-08-12
Can you add this to /etc/network/interfaces and it should connect at boot
> iface ath0 inet dhcp
wireless-essid XXXXXXXXXX
wireless-key XXXXXXXXXXXXXXXXXXX
wireless-channel XX

---------------------------------------------------------

> dhclient always has to be run with sudo add guest to the /etc/sudoers
you must use** sudo visudo**
> guest ALL=(ALL) dhclient


If it doesn't work can you return post
> iwconfig
lspci -vvnn | grep -i "network"

---

