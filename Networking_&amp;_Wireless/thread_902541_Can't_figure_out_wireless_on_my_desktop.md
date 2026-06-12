---
title: "Can't figure out wireless on my desktop"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by jickey on 2008-08-27
Hi folks - long time computer geek, first time Ubuntu user. Well, I've played with it on a VM, but I want to use it for my primary desktop OS now, and am having just a bit of problem.

I'm running 8.04 and everything I have works fine, no problem, with one exception (well, with two, but I finally got my NTFS formatted external drive working.) My wireless connection just doesn't seem to want to work.

I have a Linksys PCI wireless card in the machine. When I run the ```
SUDO LSHW
``` in the terminal, this is the information given:

Vendor: RaLink
Product: RT2561/RT61 802.11g PCI
Logical Name: WMASTER0
Driver: RT61PCI

When I go to network tools and look at WMASTER0, it says that it does not exist.

I had it working the night I installed it (two nights) ago and have no idea what I did. One thing I'm finding is that it isn't popping up with the name of the network, I have to manually enter it (and my router is definitely broadcasting a SSID) The only thing I see that doesn't make sense is that there's no option for selecting a network security protocol of "none" (yeah, sure, I know I probably should...but I live in the middle of nowhere, and the critters don't roam around with laptops...) Can anyone advise as to what I seem to be doing wrong?

I decided to go to Ubuntu on this machine because I'm tired of my wife getting viruses on it - I put her behind firewalls, good virus protection, and Windows XP just couldn't stay clean. All she needs is the internet, a few easy games, and the occasional word processing program, so I figured it would be perfect for her. However, as much as I know about the inner workings of that lovely Microsoft OS, I'm a freakin' idiot when it comes to this. Help?

---

### Post by crazymouse on 2008-08-27
:/ This sounds like my problem exactly. I was hoping someone had responded, but after having read your post I saw there was no reply, and it made me upset. Which wireless card is it? Mine is the WMP54G, which is (supposedly) supported by Hardy off the bat. Unfortunately it feels more and more like I'm trying to configure a dummy adapter or something. I'll be waiting for a solution.

---

