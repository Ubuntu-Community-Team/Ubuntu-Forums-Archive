---
title: "Getting/Installing Wireless Driver on Ubuntu..."
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Tony_SA on 2007-11-03
Hi Everyone,

I've recently downloaded Ubuntu 7.10, and installed it on another partition on my hard drive.  I'm completely new to Ubuntu so my objective at the moment is to get my wireless working.  I've got a 802.11g Wireless LAN USB Adapter and also have the CD which contains the drivers.  I have no idea how to install these drivers in Ubuntu and was hoping you guys could help me out with this.  The manual has instructions for Windows operating systems only.  The manual also states that the model of my Wireless USB stick is XG-760N.  I did a search through this forum for instructions since this problem is quite common but am a little hesitant to start punching commands into the Terminal without knowing what I'm doing.

Where do I start?  :)

Thanks for your time.

- Tony

---

### Post by DouglasAWh on 2007-11-07
Does ubuntu do anything when you plug the adapter in?

---

### Post by Lambert on 2007-11-07
> **Tony_SA said:**
> Hi Everyone,

I've recently downloaded Ubuntu 7.10, and installed it on another partition on my hard drive.  I'm completely new to Ubuntu so my objective at the moment is to get my wireless working.  I've got a 802.11g Wireless LAN USB Adapter and also have the CD which contains the drivers.  I have no idea how to install these drivers in Ubuntu and was hoping you guys could help me out with this.  The manual has instructions for Windows operating systems only.  The manual also states that the model of my Wireless USB stick is XG-760N.  I did a search through this forum for instructions since this problem is quite common but am a little hesitant to start punching commands into the Terminal without knowing what I'm doing.

Where do I start?  :)

Thanks for your time.

- Tony

The drivers on the disk are for windows only. Most manufactures don't support linux and provide drivers. They are usually community written and installed by default or other methods.

Gutsy does come with the zd1211rw driver preinstalled. You should be able to just plug your device in, driver loads, configure for connection. In ubuntu on the top right you will see an icon showing two computers, that is the nm-applet to configure network connections. Left click on that and configure.

If you're having any problems come back here and we'll help you sort through things. You can also do a forum search for zydas or zd1211 for recent threads dealing with devices using this chipset. Doesn't have to be specifi to your device as it's the chipset in the device that matters.

---

