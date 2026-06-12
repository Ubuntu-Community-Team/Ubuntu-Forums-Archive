---
title: "Wifi is visible but cannot be connected to"
date: 2016-01-01
forum: Networking &amp; Wireless
---

### Post by psychic2 on 2016-01-01
I run 15.10 and have a TP-link WN881ND, which should be supported under ATH9K. The card pretends to be able to connect to the home wifi (about 5yd away with a wall in between) but is a dirty liar and cannot be trusted.

Attempting to connect to the wifi (verizon fios, unless my eyes deceive me) will result in the computer trying to connect and then giving up. It will then ask for the password again and repeat the process.

When fed the wrong password, it will throw a bitch fit and split the connection in two in settings, neither of which has a password. When these networks are deleted, the computer will be "unable to find the network" but will continue to display the network in the list of available networks. I don't think this is actually important to say, except to point out that [B]Yes. I am using. The correct. Password.
[/B]
I have no access to a wired network without significant stress and frustration and a major invasion of my landlord's privacy. If I did have access to a wired network, I would not be posting this, as I honestly would prefer the wired over the wireless. I do have access to the internet via my laptop and can download and transfer files if I need to.

Thanks much

---

### Post by jeremy31 on 2016-01-01
Can you change the wifi encryption settings on the FIOS?  It probably has WEP and/or TKIP enabled and that causes headaches for many wireless cards in Linux

[https://www.verizon.com/support/residential/internet/fiosinternet/networking/setup/security/125521.htm](https://www.verizon.com/support/residential/internet/fiosinternet/networking/setup/security/125521.htm) click on "change to WPA2" under the correct device

---

### Post by psychic2 on 2016-01-01
It is under my landlord who is away on vacation until tomorrow (so I can't get in), but I doubt that's the issue. It's definitely WPA2. I looked at the router.

---

### Post by psychic2 on 2016-01-02
SOLVED
O
L
V
E
D

The issue was with the Gigabyte  motherboard. Enabling IOMMU disabled the USB3.0 ports (which is  annoying) but at least I have Wi-Fi now. Hopefully a fix for this issue  will come soon.

---

### Post by Helven Ink on 2016-01-04
Has anyone found a better fix for this problem? I have a gigabyte MB (970A-ds3p) and the TP-Link WN881nd wifi card, and I can't connect to the router in Ubuntu. It just keeps asking me for my PW. The card works just fine in Windows though, which is how I'm asking this question in the first place.
I'm going to try enabling IOMMU, as is suggested in this thread, but I'm not eager to lose USB 3.0. (I guess... I don't really understand what IOMMU is and wikipedia isn't helping me to understand it.) 

Any improved solutions to this problem would be greatly appreciated.

               Jon

---

