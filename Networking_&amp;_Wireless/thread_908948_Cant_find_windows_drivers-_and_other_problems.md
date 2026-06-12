---
title: "Cant find windows drivers- and other problems"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by acmariner99 on 2008-09-03
Hey all. I have ndiswrapper but I have no idea where my wireless driver files are. I looked in system32 but found no wireless .inf files required by ndiswrapper. Where can I download the needed .inf files for a Broadcom Corp card? My wireless is also noted as UNCLAIMED when I run lshw. How do I fix this. I also do not have a wireless option in my network manager. I have to use windows until I get wireless capability, so any help would be appreciated.

---

### Post by acmariner99 on 2008-09-03
My wireless card is a Brodcom 802.11b/g wlan

---

### Post by cdtech on 2008-09-03
You don't see your card with:
sudo lshw -C network

---

### Post by cdtech on 2008-09-03
I would also suggest uninstalling the ndiswrapper and installing the:
sudo apt-get install b43-fwcutter
Since the b43 now works with the broadcom card (4311)

---

