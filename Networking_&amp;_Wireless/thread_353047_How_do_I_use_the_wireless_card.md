---
title: "How do I use the wireless card?"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by arbasel on 2007-02-04
I am very new to linux.

I have an old Toshiba Satellite (PS275A-4K986) on which I have installed Ubuntu 6.10.

The device manager indicates that it can see the PCMCIA Wifi card. However in the network settings all that is displayed is the Modem and under the network tools all I can see is the Looback Interface.

Where do I go from here and how do I do it.

---

### Post by gradedcheese on 2007-02-04
Most likely, the card needs a driver or some further configuration that didn't ship out of the box.  First, you need to find out exactly what the card is (or rather the chipset).  Open a terminal and run:

lspci

And post the output here.  The line you're interested in starts with 'Ethernet controller'.

---

### Post by chili555 on 2007-02-04
If it's a wireless card, I think it may show up as *Network* Controller. You might get a bit more useful information with lspci -vv. (...minus vee vee for those of us with trifocals!)

Once you have identified it, you can search this forum for posts on how to set it up.

Good luck!

---

### Post by arbasel on 2007-02-05
Using lspci I get 02:00.0 Ethernet controler: Atheros Communications, Inc AR5212 802.11abg NEC (rev 01)

with -vv I can add the following:
subsystem: Atheros Communications, Inc. Unkniwn device 1051
Control: I/O- Mem- Busmaster- SecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-

---

### Post by chili555 on 2007-02-05
The AR5212 chipset works with madwifi. It is included in linux-restricted-modules, which you can install via synaptic. Make sure you get the module that matches your running kernel. uname -r in my case, for example, gives 2.6.17-10-generic, so I'd have to be sure that was the module I installed.

Then you should be able to configure your card the usual way: System -> Administration -> Networking.

---

### Post by arbasel on 2007-02-05
Thanks for that, but as I'm new to linux, I'm not sure where to start; what is a "linux-restricted-modules," and what is "synaptic" and how do I use it?

If I installed using the Ubuntu ISO that I downloaded, can I use this disk to install the above?

---

### Post by chili555 on 2007-02-05
Open up a terminal and type in sudo synaptic. If it is already there, as I suspect it is, it will start up. You can search for linux-restricted-modules. Right click it, mark for installation and Apply.

[http://packages.ubuntu.com/edgy/misc/linux-restricted-modules-2.6.17-10-386](http://packages.ubuntu.com/edgy/misc/linux-restricted-modules-2.6.17-10-386)

---

### Post by arbasel on 2007-02-05
k... got it to see the card.... 

I'm using WPA-PSK on my router ... where to I configure this in ubuntu. I've put the SSID and what it calls the network password but couldn't see where to setup the encryption. Also what command can I use to see where the connection is failing i.e. what log file can I look at?

---

### Post by arbasel on 2007-02-05
Some more info.

When I go to Network Tools I now see 3 Network devices
1) lo
2) Unknown Interface (wifi0)
3) Unknown Interface (ath0)

When I look at wifi0 there is some interface stats but no protocol or IP address

For ath0 there is no interface stats but there protocol is IPv6 and the IP address is something I've never seen before.

---

### Post by gradedcheese on 2007-02-06
ath0 is your actual network interface, wifi0 is probably virtual interface for management.  so, assuming that you've now installed the driver (ie: madwifi), you can configure ath0 to join your network.  lo is a 'loopback interface' used for some internal things, you can ignore that.

If you are willing to do a little work, you can get things set up (and with WPA) by following these instructions:

 [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

I hope that helps.

---

