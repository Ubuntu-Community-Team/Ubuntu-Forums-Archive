---
title: "wifi adapter no longer recognized after upgrade to Bionic Beaver (HP EliteBook 8760w)"
date: 2018-11-09
forum: Networking &amp; Wireless
---

### Post by ivors on 2018-11-09
After responding to "A new version of ubuntu is available" from unity desktop on 17 to 18.4 Bionic Beaver, the wifi adapter is no longer recognized

Pasetbin [http://paste.ubuntu.com/p/wcmYQN4ZSB/](http://paste.ubuntu.com/p/wcmYQN4ZSB/)

The display adapter wasnt also but I managed to fix that by searching these forums.

---

### Post by ivors on 2018-11-09
lspci shows:
25:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)

---

### Post by ivors on 2018-11-09
....and lshw gives
*-network UNCLAIMED
       description: Network controller
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:25:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d2200000-d2201fff

---

### Post by jeremy31 on 2018-11-09
Try ```
sudo apt install --reinstall linux-modules-extra-$(uname -r)
```
Reboot

---

### Post by ivors on 2018-11-12
> **jeremy31 said:**
> Try ```
sudo apt install --reinstall linux-modules-extra-$(uname -r)
```
Reboot


Worked at treat, also fixed the SD card reader, thankyou!

---

