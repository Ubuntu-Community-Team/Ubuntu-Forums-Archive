---
title: "Need some help getting wireless working on Dell Inspiron B130"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by obiwaynekenobi on 2007-06-23
I'm sure this has already been posted, but I'm running into some trouble and despite googling for several hours, I'm still stuck on this.  I'm dual-booting Ubuntu 7.0.4 with Windows XP Pro and can't seem to get my wireless card working.  According to the Windows Device Manager it's a **Dell Wireless 1470 Dual-Band WLAN Mini-PCI Card**, but according to lshw -C network it's a **BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver**.  I've installed the closest set of drivers that I could find for it (in my case this was bcmwl5a.inf and the associated .sys file).  ndiswrapper says that the driver was installed correctly, but I'm not seeing wlan0 in either ifconfig or iwconfig.  

I've also installed the alternate driver bcm43xx.  The Windows Wireless Drivers GUI displays "Hardware present: No" and when I try to install the driver it tells me "Driver **driver** is already installed."  I've tried removing the driver with *sudo ndiswrapper -r bcmwl5a* and installing it via the GUI instead of the terminal; It works (i.e. doesn't cough up an error message) but still displays Hardware present: No.  I've read that it's supposed to copy both bcmwl5a.inf and bcmwl5.sys to the /etc/ndiswrapper folder, but all it shows is bcmwl5a when I type ndiswrapper -l.  If I manually copy bcmwl5.sys to the directory, it displays "invalid driver file!" for its listing.

Any other suggestions?  Many thanks in advance for the help.

---

### Post by obiwaynekenobi on 2007-06-23
EDIT EDIT:  That was short-lived.  The connection died for some reason and now it won't show up again.  If I set it to Manual Configuration and enter my network name and passkey (I'm using WEP), nothing happens.  The network manager display doesn't change to the bars like it did at first, and it just reads "Manual network configuration", and no connection.  If I set my Wireless to "Roaming mode" in Network Settings and then disable/enable networking, it shows a list of wireless connections (blank) and when I go to connect to other wireless network, I enter the network name and WEP key, and it just displays empty bars that reads "Wireless connection to <network> (0%)" and nothing happens, it doesn't connect at all but doesn't kick me back an error anything, either.  

I'm not sure why it's not picking up on the connection.  Help!

---

