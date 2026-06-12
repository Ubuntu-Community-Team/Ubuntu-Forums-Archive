---
title: "Broadcom BCM4312 WPA/WPA2 Enterprise under 13.04"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by Darthape on 2013-09-28
Hi, I recently installed 13.04 onto a laptop with a Broadcom BCM4312 wifi chipset. My university uses WPA/WPA2 PEAP authentication for the wifi and I can not get it to connect to the wifi regardless of what I do. I installed the b43 driver and it connects correctly to insecure networks but when I try to connect to the secure network it tells me that I have a bad password (the password is indeed correct). Any ideas?

---

### Post by varunendra on 2013-10-02
If you are sure b43 is the correct driver for your card, may I assume that you have also installed the firmware for it? If unsure, please post the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod | grep -e b43 -e wl
dmesg | grep -e b43 -e firmware
```

If you are sure about the above, please open the keyfile for your connection (its name is same as the connection name, and you need root privilege to even read it) -
```
sudo cat /etc/NetworkManager/system-connections/*<your connection's key file>*
```
This file also contains your saved security key, so **DON't post the output here** (or if you do, remove the security key part).
Is there a line that says "**system-ca-certs=true**"? If there is, open the file as root -
```
gksu gedit /etc/NetworkManager/system-connections/*<your connection key file>*
```
..change the "true" to "false", proofread, save and close the file. Then try connecting again.

---

