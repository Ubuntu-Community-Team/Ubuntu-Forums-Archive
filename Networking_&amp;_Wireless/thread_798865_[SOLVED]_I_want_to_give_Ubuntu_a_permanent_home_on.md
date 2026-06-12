---
title: "[SOLVED] I want to give Ubuntu a permanent home on my Compaq F756NR laptop"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by braveerudite on 2008-05-18
Hi everyone

I bought a [Compaq F756NR]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01297714&lc=en&cc=us&dlc=en&product=3646836&rule=9564&lang=en") laptop and installed Ubuntu 8.04 Hardy Heron (64-bit) no dual partition for Windows or nothing, just a pure Ubuntu laptop.  I need you guys help to get the wireless on my laptop working.

After installation I notice that by default Ubuntu installed the proprietary wireless drivers for my laptop. They are listed as follow:

Atheros Hardware Access Layer (HAL)

Support for Atheros 802.11 wireless LAN cards.


I believe these are the proper drivers for my laptop wireless because before I erase the windows Vista factory installation from my laptop I looked under divide manager and I saw Atheros for wireless.

I love Ubuntu for some many reasons that I can't  list them all. But I notice getting the wireless working in any Linux distribution is a pain for everyone.  Knowing this I still went and bought my self a new laptop just to able to take the fun of Ubuntu everywhere I go.

Drivers seem to be already install by default but there are no tools to pick the signal in range I want to connect to.  I have WPA2 Personal security on my home wireless network and it works great with my Nintendo Wii and my laptop (Before I erase it to install Ubuntu) So with that I know that my wireless network is set up properly and my laptop wireless hardware is working properly.

Ones I get wireless working on my laptop I'll be in Ubuntu mobile heaven.

Thank you all for your time

---

### Post by Mr A Mouse on 2008-05-18
Hi, brave! Do you know what specific model of Atheros wireless card you have? 

For me (working with an Atheros AR5007), [this howto]("http://ubuntuforums.org/showthread.php?p=4829026") turned the trick.

---

### Post by braveerudite on 2008-05-18
> **Mr A Mouse said:**
> Hi, brave! Do you know what specific model of Atheros wireless card you have? 

For me (working with an Atheros AR5007), [this howto]("http://ubuntuforums.org/showthread.php?p=4829026") turned the trick.


Thank you for you reply.  That is a good question. Is there a tool or a terminal command I can type that would show me the specific Atheros model I have on my laptop?

---

### Post by Mr A Mouse on 2008-05-18
The easiest way I know of is to type:

```
lspci
```

into a terminal. This will give you information on all your pci devices--for me, the wireless is the last on the list.

---

### Post by braveerudite on 2008-05-18
> **Mr A Mouse said:**
> The easiest way I know of is to type:

```
lspci
```

into a terminal. This will give you information on all your pci devices--for me, the wireless is the last on the list.

Mine seems to be the last one on the list also and is listed as follow.

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

I checked out the link you gave me and I found there information about something call ["Wicd"]("http://wicd.sourceforge.net/") which is suppose to handle my network connections (LAN or Wireless) in an easy way.  I follow the instructions for installing Wicd on Ubuntu and it removed network-manager, which is the default GNOME network manager and cause loss of network connection temporarily. My wire connection works but no luck with getting wireless to work.  Do I need to install anything else to get Wicd to work? or can it be that I don't have the proper drivers install?

---

### Post by braveerudite on 2008-05-18
I'm looking for a way to figure out if my wireless card is either eth0, eth1 or wlan0, wlan1 ...ect

I was looking on Synaptic an application that could tell me so but after installing they are nowhere to be found in Gnome menu.  Still hate installing something then not showing up in the gnome menu.

Can some one help me id my wireless card eth0 or wla0 or whatever number it is.  I need this to configure wicd.

---

### Post by Mr A Mouse on 2008-05-18
Give this a shot: [http://ubuntuforums.org/showthread.php?t=743299](http://ubuntuforums.org/showthread.php?t=743299)

If that doesn't work, there is another way, but let's try that one first.

---

### Post by Mr A Mouse on 2008-05-18
When your card is recognized, it will be ath0--ethX is a wired ethernet card, and I believe wifi0 is a software interface to the wireless card (which the system can't work with yet).

---

### Post by braveerudite on 2008-05-18
> **Mr A Mouse said:**
> Hi, brave! Do you know what specific model of Atheros wireless card you have? 

For me (working with an Atheros AR5007), [this howto]("http://ubuntuforums.org/showthread.php?p=4829026") turned the trick.

I follow the howto step by step but can't go further because I'm gettign an error.

```
rambo@Ubuntu64:~$ tar xvf ar5007eg-*.tar.gz
ar5007eg-64-0.2/
ar5007eg-64-0.2/ar5007eg/
ar5007eg-64-0.2/ar5007eg/net5211.inf
ar5007eg-64-0.2/ar5007eg/net5211.cat
ar5007eg-64-0.2/ar5007eg/ar5211.sys
ar5007eg-64-0.2/README
rambo@Ubuntu64:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rambo@Ubuntu64:~$ 

```

I looked in the forums for anyone else having the same problem while trying this guide and found one guy that did but got it working but didn't post a guide in how.

---

### Post by braveerudite on 2008-06-03
Has anyone got Ubuntu 64 8.04 wireless to work in a Compaq F756NR laptop?

---

### Post by braveerudite on 2008-06-08
Finally my prayers were answer... w00t

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

