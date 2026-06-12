---
title: "Network Manager BLOWS!!"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-10-26
NETWORK MANAGER BLOWS!!  Ok -- I said it!!! Im over it.

---

### Post by por100pre1 on 2007-10-26
I haven't tried it yet, I'm using a desktop with an Ethernet card. Is really that bad? I like to know more about it... :-k

---

### Post by wieman01 on 2007-11-17
It does... How come nobody else has responded to this post?

But it is becoming better... almost every release.

---

### Post by kevdog on 2007-11-18
It does seem to be getting better -- like the vpn support - wish they could figure out static ip addressing and better compatibility with ra cards.

---

### Post by bretticus on 2007-11-18
I'm sure it has it annoyances, however, I doubt anyone can argue against the fact that it's not bad for being free. :)

---

### Post by tdrusk on 2007-11-18
I don't have any problems with network manager in gnome and kde.

why not post why it blows?

---

### Post by kevdog on 2007-11-18
> **tdrusk said:**
> I don't have any problems with network manager in gnome and kde.

why not post why it blows?

1. Bad support for Ra based cards
2. Not able to configure static IP addresses
3. Confusion to new users the whole Roaming Mode vs manual configurations as specified in the /etc/network/interfaces file
4. Difficult to find where network manager saves it settings
5. Frequent drops from networks (which if you connect manually will not do)
6. Frankly, very unreliable for many -- check the forums out if you don't believe me

Good Things
1. I like the interface -- very intuitive as far as icons, network presentation
2. Good icon theme (I know this can be changed but the default is good)
3. Easy to use

Just for comparison --
WICD -- seems more reliable to me -- Works in much the same way as connecting from the command line manually.
Allows for many customizable settings (although VPN is not currently supported)
Do not like icon theme
Never seems to connect on boot for me -- the daemon starts, but the entire tray.py executable -- only starts automatically about 1 out of 10 times.

---

### Post by gomadtroll on 2007-11-18
My $.02,  Gutsy Gnome,  I added a Atheros wireless card + restricted drivers/kernel. This worked from the reboot to new kernel. When I modified,  my wireless settings, manual mode, the Network manager only added ipv6 address's not the ipv4 & ipv6 that a reboot will configure. On my setup this ,ipv6 only, doesn't work. There is a difference in network configuration between whatever is being used in /etc/init.d/networking and what network manager does. POS :-)

PS,  Yes its free  but why does that mean I can't expect a working product. 

Greg

---

### Post by wieman01 on 2007-11-18
> **gomadtroll said:**
> PS,  Yes its free  but why does that mean I can't expect a working product. 
Exactly. It would be wrong to say that just because it's free, we must not expect anything. Ubuntu is a professional and - yes - commercial distribution in the sense that Canonical plan to make a living by selling their product i.e. support service. Therefore we should actually expect much more. Users should not put up with defective software because they can switch easily and leave Ubuntu for good. 

NM is a very important and critical software, and it would be a shame if people turned their backs on Ubuntu because of its deficiencies as Kevdog has pointed out.

---

### Post by kevdog on 2007-11-18
Gomadtroll

All though I feel your pain with IPv6 problems, this really isn't a network manager problem per se.  IPv6 is turned on by default with Ubuntu (but not in other distributions like Sabayon).  Your solution is to turn off or prevent the IPv6 kernel module from loading during boot.

Here are the instructions:
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

IPv6 has caused problems with a lot of users.  I've requested from the developers that they turn IPv6 off by default in Hardy, but who knows if they will do it.

---

