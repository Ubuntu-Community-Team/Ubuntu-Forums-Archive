---
title: "Network manager"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by Finn&gt;Potatoe on 2006-11-23
Ok, I'm having real trouble installing network manager on my computer. Is there a way to install it without internet connection on Linux. My windows internet is working just fine, it's just that I can't connect to my wireless connection with Ubuntu. 

So, is there a way to get to get network manager on to a floppy for example to install it in ubuntu, or could you just install it straight from windows to ubuntu.  Please help quick, windows is driving me nuts. And sorry, I'm a nub with linux. So if you could help I'd appreciate it.

---

### Post by NetworkGuy on 2006-11-23
My experience is that Network Manager never gets your network running.  It only allows you to change profiles after the network is up and running.   From reading your post, you are having problems getting your network card to work right.

If that is true, you need to provide the community with some information to help you.  For starters, what type of network card do you have?

---

### Post by Finn&gt;Potatoe on 2006-11-23
TP-LINK 11b/g Wireless Adapter

Is that the network card? And as I said, internet works fine on windows.

I'm having troubles connecting to the network..

---

### Post by NetworkGuy on 2006-11-23
Internet works fine in Windows because you installed a driver with the card that allowed Windows to work with the card.  We are going to try to see if the driver is already installed in Linux and just need configured.

That card sounds very generic.  If the card is a PC-Card or PCI card post the results from ```
lspci
``` and ```
iwconfig
```. If the card is a USB card post the results from ```
lsusbpci
``` and ```
iwconfig
```.

---

### Post by Finn&gt;Potatoe on 2006-11-23
Ok

lo: no connectivity
wifi: no connectivity

Ath0 IEEE 802.116 Essid:" "
     mode: managed channel: 0 access point: not associated
     bit rate: 0 kb/s   TX power: 0dbm Sensitivity: 0/3
     Retry: off    Rts thr: off      fragment thr: off
     power management: off
     link quality: 0/14   signed level:-95dbm  noise level:-95dbm
     RX invalid nwid:0    RX invalid crypt: 0  RX invalid frag: 0
     TX excessive retries: 0  invalid misc: 0
     missed beacons: 0

---

### Post by NetworkGuy on 2006-11-23
You are probably going to have to use a program called NDISWRAPPER with this card.   This program allows you to use the Windows drivers with this card.  I'm looking for a good tutorial right now...

---

### Post by Finn&gt;Potatoe on 2006-11-23
Thanks, I really apprieciate your help!

---

### Post by NetworkGuy on 2006-11-23
The best tutorial I found was

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

however this is for a broadcom card instead of a Atheros card.

I don't use NdisWrapper and my experience with it is very little.  However with the help of the entire community, we should be able to get this working.  Read through the tutorial, it should work except you will have to substitute the Atheros Windows drivers for the Broadcom Windows Drivers.

---

