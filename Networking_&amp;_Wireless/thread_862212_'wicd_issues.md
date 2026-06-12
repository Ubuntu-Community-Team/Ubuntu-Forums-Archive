---
title: "'wicd issues"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by arnicainthemembrane on 2008-07-17
When I quit using Network Manager for favor of wicd, my computer(IBM Thinkpad T40 running Hardy) stopped using the PCI wireless card I usually use for internet connectivity. Also, wicd has a curious tendency to seize up during "obtaining IP address". It then won't quit until I force quit, whereupon it won't start up again, and I have to restart the computer. This happens rather frequently. Any advice appreciated.

---

### Post by imdano on 2008-07-17
I'd recommend upgrading to the [1.5.0 release candidate](www.wicd.net/lastest) and see if you still experience the same problems.  If you do, I can work you through troubleshooting them.

---

### Post by damis648 on 2008-07-17
Also try the new Network Manager .7 which has a thread floating around somewhere... you might like it.

---

### Post by arnicainthemembrane on 2008-07-17
I have downloaded wicd "extras" and we'll see how it works. What remains is the computer's inability to make use of the PCI internet card, an issue I didn't have when I was (mistakenly) running wicd with network Manager. How can I know what hardware Ubuntu is using, and then how can I get wicd to use it?

---

### Post by imdano on 2008-07-17
> **arnicainthemembrane said:**
> I have downloaded wicd "extras" and we'll see how it works.Not sure what you mean by "extras"...What did you download exactly?
> What remains is the computer's inability to make use of the PCI internet card, an issue I didn't have when I was (mistakenly) running wicd with network Manager. How can I know what hardware Ubuntu is using, and then how can I get wicd to use it?You can get a lit of the networking hardware with ```
sudo lshw -C network
```Sometimes people run into problems where uninstall NetworkManager hides their wireless card.  I think it's because of NM edits /etc/networks/interfaces when it gets uninstalled, and sometimes the wireless card ends up not getting put "up" when the computer starts.  If you remember the normal name of your wireless interface (it will probably show up in the results of lshw) you can run ```
sudo ifconfig <wireless interface> up
```And it might come back.

---

### Post by arnicainthemembrane on 2008-07-17
This is what Lshw gave me:  


*-network:0 DISABLED    
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth2
       version: 03
       serial: 00:1a:6b:67:2d:4c
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:79:65:10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.5.132 latency=64 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
  *-network UNCLAIMED
       description: Network controller
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64

Now, what does Unclaimed mean? How can I claim it, and what do i call it in order to claim it?

---

### Post by imdano on 2008-07-17
Unclaimed means there is no driver associated with it.  Search for forums for rt2500 for info on how to install the correct driver.  Though to be honest, you're probably better off using the Intel card...Ralink cards are notoriously buggy and hard to get working.

---

### Post by arnicainthemembrane on 2008-07-17
thanks for the advice, I'll see what I can do... odd, because it was working fine with NM...

---

### Post by imdano on 2008-07-17
Did you do a kernel upgrade or anything like that around the time you uninstalled NM?  Installing wicd and uninstalling NM don't touch your drivers at all, so I'm not sure what happened there.

---

### Post by arnicainthemembrane on 2008-07-18
Well, I reinstalled the driver and now the computer is recognizing the card. So it seems to have been fixed.  The issue with wicd is resolved as well, as it appears to be connecting and not requiring a restart. I'm not an advanced enough troubleshooter to figure out why it does what it does, what drivers are installed, etc, and, quite frankly, it's a bit of a chore to figure out these things in ubuntu.

---

