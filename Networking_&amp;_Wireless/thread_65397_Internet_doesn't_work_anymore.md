---
title: "Internet doesn't work anymore?"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by OpposingForce on 2005-09-13
Ok so we moved the computers to another location in the house, and we use a wireless router now instead of a modem. Before the computers were moved the internet worked fine and fast. My internet is working on windows xp but not on ubuntu. Now when I go into System --> Networking it will not let me add a new device. The old modem is there but its greyed out/not configured. 

Ok I so I go into the help menu and it tells me the steps to add a new device. Ok so first I have to click the Add button in the connections tab. Im in the connections tab with no add or remove button in sight. I have no clue how I'm going to get this working so I need some help here please..

---

### Post by evilghost on 2005-09-13
Stupid question, but have you installed the wireless NIC yet?  You're going about the wrong way to add a new NIC.

---

### Post by mlomker on 2005-09-13
Getting wireless to work on linux can be a challenge.  What type of card did you buy?

---

### Post by evilghost on 2005-09-13
[QUOTE=mlomker]Getting wireless to work on linux can be a challenge.  What type of card did you buy?[/QUOTE]

Well true and false :)

ndiswrapper makes things a whole lot easier and I know there's a good thread on how to get it working.  I didn't have too much trouble getting my father's Belkin 802.11g PCI card working in his desktop, and the laptops are pretty easy including the HNW-110 Compaq card, the Ambicom CF->PCMCIA card, and the Cisco Aironet card.

I wouldn't say getting wireless working is a daunting task.  Of course, what's easy to me may not be to someone else, and vice-versa; hopefully we can help you out and get everything working great with your new setup.

---

### Post by mlomker on 2005-09-14
> **evilghost]Of course, what's easy to me may not be to someone else, and vice-versa said:**
> 

And I quote: [quote]I have no clue how I'm going to get this working

When that's where your starting from then it's safe to call it a *challenge*.    :-P 

I didn't say we couldn't help!  First we need to know what kind of card it is.

---

### Post by OpposingForce on 2005-09-22
D-Link AirPremier DWL-AG530 Wireless PCI Adapter

is what I have

---

### Post by OpposingForce on 2005-09-30
I gave u guys my network card can any1 help please...I cant get the breezy upgrade when it comes out if I cant connect to the net someone help please

---

### Post by OpposingForce on 2005-10-01
forget it Ill just burn breezy and install over hoary I heard it supports wireless better

---

### Post by mlomker on 2005-10-01
> D-Link AirPremier DWL-AG530 Wireless PCI Adapter
is what I have

A Google search suggests that it's an Atheros chipset, supported by the madwifi driver.

```

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo modprobe ath_pci
sudo iwconfig ath0 essid *yourAP*
sudo ifconfig ath0 up
sudo dhclient ath0

```

You'll find many references to madwifi and atheros if you search the forum.

---

