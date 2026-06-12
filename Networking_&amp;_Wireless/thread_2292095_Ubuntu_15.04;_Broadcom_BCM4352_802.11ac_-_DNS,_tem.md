---
title: "Ubuntu 15.04; Broadcom BCM4352 802.11ac - DNS, temporary failure name resolution"
date: 2015-08-25
forum: Networking &amp; Wireless
---

### Post by narcoticfresh on 2015-08-25
Hi guys..

So after 15+ years of happy Linuxing, I'm stuck at a mysterious problem. It's annoying and strange and I would appreciate some help..

First off, my wireless info is here: [http://paste.ubuntu.com/12190930/](http://paste.ubuntu.com/12190930/)
I'm by no means sure it's a driver issue..

[B]Situation
[/B]After years using LTS releases, I decided using vivid (15.04) on my new Dell XPS 13z 2015 Edition. A nice laptop. And as Dell is a Linux supporter and also ships a Developer Edition using Ubuntu, I figured it's compatible hardware. And indeed, mostly it is.

Wireless works fine for the most part, I'm using the correct driver according to [chilli555's Broadcom Sticky Post]("http://ubuntuforums.org/showthread.php?t=2214110") (as should be visible in wireless-info.txt) - this is all stock installed; I didn't reconfigure anything. This package got installed by Ubuntu and the wl kernel module is active.

See this

```
dn@host:~$ lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

dn@host:~$ sudo dpkg -s bcmwl-kernel-source
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 7850
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>

```

**The problem**
So what is my problem if networking works mostly..?
Well, that's where the mystery starts... ;-)

At some point, and sporadically, DNS lookups seem to stop working. Tools like wget, dig, curl and so on all show "temporary failure in name resolution". A simple reconnect to the Wifi network solves the problem until it happens the next time. This is veeery annoying to say the least.

To be clear: When DNS lookups fail, I'm still connected. I'm having my IP and all. IP based access (no DNS necessary) works.

What I tried so far:
[LIST]
[*]Turn off the local dnsmasq in NetworkManager and let it write the DHCP provided DNS servers in /etc/resolv.conf directly - didn't help
[*]Currently, my DHCP server (at home; not the one I provided here in wireless-info.txt) serves up the Google Public DNS Servers. I changed that to my ISP ones - it doesn't seem to matter which DNS servers I use, the error still happens.
[*]Entering the DNS servers into the NetworkManager connection instead of receiving it from the router - didn't help
[/LIST]

**Guesses**
So naturally, I'm puzzled by this problem. If the connection wouldn't work at all or disconnect sometimes, it would be easier and could be a driver issue. But this DNS resolve problem is really strange.

Somehow it seems to happen when I do something with Vagrant and VirtualBox - both tools I for work. Does anybody have the comparable issues? I realize that especially VirtualBox fiddles around with networking - but both tools don't use "su" privileges, how on earth could they somehow "disable" DNS lookups?!

I'm dual booting with Windows on this laptop - needless to say all works fine there and this issue never comes up.. So this shows to me it cannot be a signal issue or networking issue caused by the network. Also we have a lot of different devices on the network (be it phones, tablets, other PCs), none of them have any issues at all. 

**Help?**
So I realize this is a strange problem, hard to help for in a forum like that. But maybe somebody can point me to the right direction, to a related issue, to something that can help me? ;-)


***UPDATE***
I could not reproduce the issue using the "vagrant up" command. I halted my vagrant box and up'ed it again, it didn't reproduce the issue. Issuing this commands does stuff with VirtualBox (as it's my Vagrant provider), so at the moment it doesn't seem to be an issue with those things.

I'm somehow thinking it's a signal issue. It seems when I have strong signal, the issue doesn't occur, but I have no proof for that idea. And it seems odd to me - how could have lower signal (it's never "low", always above 50%) could have an impact on name resolution only? Seems not possible to me..

---

### Post by ezekiel123 on 2015-10-16
I am having the exact same issue on the same Laptop, except I am using Linux Mint. Let me know if you can somehow resolve that.

It's worth noting that this does not happen in every Wifi. My home network works just fine, several others (work, coffeeshop, ...) are practically unusable.

---

