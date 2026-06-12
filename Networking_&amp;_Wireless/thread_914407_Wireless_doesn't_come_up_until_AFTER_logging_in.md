---
title: "Wireless doesn't come up until AFTER logging in?"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by eckz59 on 2008-09-08
Hi all,

I am using Hardy Heron and I bought a D-Link WDA-1320 wireless NIC to go into my mother's Everex gPC. It runs great - Ubuntu notices it when I first start up the computer, and Network-Manager lets me enter the wireless security details just fine.

However, I noticed that if you turn on the computer and just let it boot, the wireless interface (ath0 in my situation) does not have a network connection (until somebody logs in). Why is this? I want to be able to SSH to the computer without having to have logged on locally first.

Is there a way to get ath0 to connect to my wireless network and get an IP during boot-up, without the need to log in?

---

### Post by slakkie on 2008-09-08
> **eckz59 said:**
> Hi all,

I am using Hardy Heron and I bought a D-Link WDA-1320 wireless NIC to go into my mother's Everex gPC. It runs great - Ubuntu notices it when I first start up the computer, and Network-Manager lets me enter the wireless security details just fine.

However, I noticed that if you turn on the computer and just let it boot, the wireless interface (ath0 in my situation) does not have a network connection (until somebody logs in). Why is this? I want to be able to SSH to the computer without having to have logged on locally first.

Is there a way to get ath0 to connect to my wireless network and get an IP during boot-up, without the need to log in?

That is because you rely on a network manager which is dependent on your GUI. Which is a bad thing IYAM. This could be solved if those network managers would write their configuration into /etc/network/interfaces, but most of them (if not all) don't do this. 

You need to configure your interface via /etc/network/interfaces, this will then be started when your computer boots. I haven't used the HOWTO myself, but you could use this one: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) .

I myself use the following setup:
[http://ubuntuforums.org/showthread.php?t=124153](http://ubuntuforums.org/showthread.php?t=124153)

This has several benefits which to me are huge:
1) Networking is setup via init.d and not via a GUI login
2) Able to switch GUI's without the need to reconfigure my networks

---

### Post by eckz59 on 2008-09-09
Hi slakkie,

Thanks, your suggestion led me to find [**_this_**]("http://ubuntuforums.org/showthread.php?t=12045"). It now works correctly! This is what my /etc/network/interfaces file looks like (for anyone else who wants to know):

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
wireless-essid <my network id>
wireless-key <my 26-digit WEP key>
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1


---

### Post by slakkie on 2008-09-09
Yw :)

---

