---
title: "TEW-421PC Problems"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by austinderrick2 on 2008-01-29
I'm installing the TEW-421PC (Version C1.1R)

I used ndiswrapper to install the drivers. The card shows up and all, but I can not find any wireless networks. (Even though I am about 15 feet from my router)

Here is my /etc/network/interfaces file:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interfaces
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```


Also:

```

$ ndiswrapper -l
net8185 : driver installed device (10EC:8185) present (alternate driver: r8180)

```

Any ideas?

---

### Post by TekBudda on 2008-02-14
I am having this same problem on a IBM ThinkPad A21e, running Unbuntu 7.10 (Alternate ISO).  I can connect to the wireless network using a wireless device on another laptop so I know the network is there.

Initially the card was detected & seemed to be doling all teh right stuff without the need for me to be installing anything.  I did notice the last time I booted up that it didn't seem to be recognizing the card this time.  I also found that the laptop would freeze when I tried to change  any options forcing a reboot.

I haven't tried installing the ndiswrapper yet as Unbuntu seems to detect the card fine.  I would like to figure this out soon as I am thinking of picking up a matching USB WiFi NIC...and possibly PCI cards to match & make the whole network wirless.

---

### Post by ubunyou on 2008-02-16
I have been having trouble with that card since installing ubuntu.
Some notes:
-I had to use ndiswrapper, I could see the wireless networks with the rtl8185 driver using 

```
  
> iwlist wlan0 scan

```
but the signal strength was always reported to by zero
  
-The XP drivers from the TEW-421PC CD didn't work, the Win2000 drivers did

-Using Gutsy Gibbon and torrenting over wireless caused system crashes. The crashes 
stopped after upgrading to Hardy Heron (Ubuntu dev. kernel)

-Even with the kernel upgrade the wireless connectivity fails after 30min-1hour. At this point if I unload and then load ndiswrapper I regain connectivity (for another 30-45 minutes)

```
  
>ifdown wlan0
>modprobe -r ndiswrapper
>modprobe ndiswrapper

```

Help and suggestions would be greatly appreciated as this is a frustrating issue.
OR, recommendations of a more Linux friendly USB or PCI wireless device would be great.

---

### Post by ubunyou on 2008-03-04
I eventually solved all my problems with this card.
What I did was take it out of my computer and smash it into little pieces, and then I went to the store and bought a Linksys WMP54G (version 3 or greater - mine was v4.1) and it works flawlessly with Ubuntu 8.04 - and from what I hear 7.10.
Trust me man not worth the headache ... smashy smashy, totally worth it.
A more general note - check out this site before buying hardware - now i know ...
[http://www.linux-drivers.org/](http://www.linux-drivers.org/)

---

