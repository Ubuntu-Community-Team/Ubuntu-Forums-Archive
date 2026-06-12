---
title: "Linksys WMP54GS not working"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by perks on 2008-08-11
I've done many google searches and have followed many tutorials on getting my wireless internet to work but nothing has seemed to do the trick. The wireless adapter that I'm trying to use is a Linksys Wireless-G PCI Adapter w/ SpeedBooster v1 (WMP54GS). I've tried using ndiswrapper to install the drivers but nothing seems to be working. Any help is greatly appreciated! I am running the 64-bit version of Ubuntu 8.04.

Link to adapter: [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826820&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2682039789B16]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826820&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2682039789B16")

What I get when I type "lspci | grep Broadcom\ Corporation" in terminal: > 01:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


Thanks in advance!

---

### Post by Crafty Kisses on 2008-08-11
Post the following output:
```
lshw -C network
```

---

### Post by perks on 2008-08-11
*-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

---

### Post by Crafty Kisses on 2008-08-11
Sorry about this, post this output as well, ```
iwconfig
```

---

### Post by perks on 2008-08-11
lo        no wireless extensions.

eth0      no wireless extensions.

---

