---
title: "Looking for wifi driver"
date: 2016-01-09
forum: Networking &amp; Wireless
---

### Post by jacatone on 2016-01-09
I'm using Ubuntu 14 with a Dell Latitude D620 64-bit. I'm looking for the Broadcom built in wifi driver. My information for it is below. Thanks

jacatone@D620:~$ lspci -nn -d 14e4:
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by kurt18947 on 2016-01-09
Have you looked in the Networking & Wireless forum? Maybe ask the mods to move your thread, you'll likely get better responses there.

---

### Post by cariboo on 2016-01-09
If you can't connect at all from your Ubuntu install, please run the following command:

```
sudo lshw -C network > network.txt
```

This will create a file called network.txt in your home directory, copy it to where you can find it in your Windows install, and paste it into your next post.

From the quick bit of research I did, eth0 will only work if WiFi is disconnected turned off and wlan0 will only qork if eth0 is inactive.

---

### Post by jacatone on 2016-01-10
I'm using Ubuntu 14 with a Dell Latitude D620 64-bit. I'm looking for the Broadcom built in wifi driver. My information for it is below. Thanks

jacatone@D620:~$ lspci -nn -d 14e4:
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by Bucky Ball on 2016-01-10
Plug in an ethernet cable, do an update, reboot. If the card is still not working, check Additional Drivers. You should find a driver there offered for the card. What do you see?

Either way, please provide the output of:

```
sudo lshw -C network
```

---

### Post by Hadaka on 2016-01-10
Hi, From a working wired connection please open a terminal ctrl/alt/t 
then copy and paste one line at a time..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by howefield on 2016-01-10
Moved to the "*Networking & Wireless*" forum.

Edit : and duplicate threads merged.

---

