---
title: "Network Manager with Intel 3945ABG No Wireless Option"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by SendDerek on 2006-10-16
I know that this has been beaten to death, but I'm really having a hard time getting my wireless to work in my fresh Ubuntu 6.06 installation.

I've read through about 10 articles/wiki's/how-to's/ect... to try and find an answer but I havn't found anything that really helps me.

Okay, so here's what's up:

First, I tried with the Network Monitor.
[LIST][*]Only the eth0 (wired) is listed[*]When I type in eth1 manually, it states that the wireless media is disconnected[*]When I hit "Configure" it will lead me to the network settings, and the wireless device is listed and activated[*]I select "Wireless Connection" and hit "Properties" and I can choose from a list of network names (including mine)[*]So, I choose mine, and type in the password but it's never listed in the Network Monitor
[/LIST]

So, okay... Network Monitor isn't the best I hear, so I download and install Network Manager v0.6.2.  Excellent.  I have the applet loading on startup and it will connect to my wired device quickly, but still not wireless option of any sort.  It just says "Wired Network" when I click on the applet.

I've gotten all the updates available for this program and for Ubuntu as of 20 minutes ago and still no help.  I've restarted the system with no help either.

I'm familiar with KNetwork Manager from my recent Kubuntu trial and remembered that my wireless worked perfectly when I had that program.  So, I installed that and tried it out... nothing.  Wireless is "Enabled" and there are no wireless devices to be seen.

I've checked my /etc/network/interfaces file and found this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Micha
wireless-key s:********

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

I don't think that looks bad or unusual.  Maybe it is, but I'm new to ubuntu (my first day!). 

So, in short (maybe):
[LIST]
[*]Network Settings recognized that I have a wireless device as eth1.
[*]Network Monitor, Network Manager, KNetwork Manager don't see it. (Network Monitor sees it, but says it's disconnected).
[*]I have all updates.
[*]It worked once in Kubuntu, before I reformatted it with Ubuntu.
[*]Me: ](*,)
[/LIST]

I know this is a lot to read and ask for, but could somebody help shed some light down on this for me and maybe help me get it working again?

BTW: I have a Sony Vaio VGN-FE550G with the Intel 3945ABG Network Card.

---

### Post by SendDerek on 2006-10-16
Ummm... so, yeah.  I went to bed last night, woke up this morning and all is well.  

I love computers.  They're smarter than I am.

---

