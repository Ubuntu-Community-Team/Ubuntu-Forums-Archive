---
title: "[SOLVED] Atheros 5007 and HAL"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by trorion on 2008-06-14
I am on 64 bit Hardy and using an ateross 5007 card.  It works on ndiswrapper but every time I boot up I have to go to
-Hardware Drivers
-Uncheck "Atheros Hardware Access Layer (HAL)
-uncheck "Support for Atheros 802.11 wireless LAN cards"
-boot up

then I have to go to hardware drivers
-Hardware Drivers
-Check "support for Atheros 802.11 wireless LAN cards"
-reboot

It's a lot of work to get a my wireless running (3 boot ups to get wireless).  Any suggestions?  Thanks!

lspci:
```

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

---

### Post by trorion on 2008-06-15
OK, the problem was that somehow the network roaming was re-loading the drivers or somehow causing a problem.  Set up manual configuration instead of roaming and it works fine now just have to manually switch to roaming if I want to roam.

---

