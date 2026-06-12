---
title: "WiFi is not available on HP Pavillion 15t under Ubuntu 16.04"
date: 2017-01-02
forum: Networking &amp; Wireless
---

### Post by martincooney on 2017-01-02
Have not been able to find anything on the Intel Dual BandWireless-AC 3168 802.11 ac 1x1 WiFi + BT 4.0 Combo Adapter

Device is not shown on the menu bar. Any suggestions would be greatly appreciated. I grow tired of dragging my laptop around with an ethernet cable permanently attached.

---

### Post by Hadaka on 2017-01-03
Hi please open a terminal ctrl/alt/t then Copy and paste
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux-firmware_1.161_all.deb
```
boot and test wireless
thaqnks.

---

### Post by martincooney on 2017-01-03
Thank you for your fast response. Unfortunately, still no wifi. Here is the updated wireless information file.

---

### Post by Hadaka on 2017-01-03
Hi, please open a terminal...then copy and paste..
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
then do..
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean
```
BOOT and test wireless
thanks.

---

### Post by martincooney on 2017-01-03
Still no wifi. Attached are the newest wireless-info.

Thanks
Martin

---

### Post by ppnman on 2017-01-03
You need linux-firmware-nonfree because your wifi card Is nonfree
Download from here: [https://launchpad.net/ubuntu/xenial/amd64/linux-firmware-nonfree/1.16](https://launchpad.net/ubuntu/xenial/amd64/linux-firmware-nonfree/1.16)
And then, reboot.

---

### Post by chili555 on 2017-01-03
> **ppnman said:**
> You need linux-firmware-nonfree because your wifi card is Ralink AND Ralink Is nonfree
Download from here: [https://launchpad.net/ubuntu/xenial/amd64/linux-firmware-nonfree/1.16](https://launchpad.net/ubuntu/xenial/amd64/linux-firmware-nonfree/1.16)
Or just : sido apt install linux-firmware-nonfree 
And then, reboot.His wireless card is clearly an Intel:> 05:00.0 Network controller [0280]: Intel Corporation Device [8086:24fb] (rev 10)
	DeviceName: Intel Dual BandWireless-AC 3168 802.11 ac 1x1 WiFi + BT 4.0 Combo Adapter
	Subsystem: Intel Corporation Device [8086:2110]
This suggestion will be ineffective.

---

### Post by praseodym on 2017-01-03
Unfortunately: Wrong. Its Intel:
```

05:00.0 Network controller [0280]: Intel Corporation Device [8086:24fb] (rev 10)
	DeviceName: Intel Dual BandWireless-AC 3168 802.11 ac 1x1 WiFi + BT 4.0 Combo Adapter
	Subsystem: Intel Corporation Device [8086:2110]
```

Check the bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1627114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1627114)

You need kernel 4.8

---

### Post by jeremy31 on 2017-01-03
And to install the 4.8 kernel in Ubuntu 16.04
```
sudo apt-get install linux-generic-hwe-16.04-edge
```

Reboot and it should work with Hadaka's firmware suggestion

---

### Post by martincooney on 2017-01-03
Success!!! It is so nice to be able to roll up that long umbilical that was connecting my laptop to my network. I kept worrying that someone would trip and break their neck on that blue cable. What a relief to be wireless again.

I do not know how to express my extreme gratitude to all that helped by contributing to this thread. jeremy31, your suggestion to update the kernel to 4.8 coupled with Hadaka's firmware update solved my problem. You guys are AWESOME. I wish I could contribute to this forum, but my knowledge about Linix is very basic. I guess my contribution will have to be my sincere thanks.

Unfortunately, I do not know how to close this thread.

---

### Post by Hadaka on 2017-01-04
Glad to see you are up and running !
Thank you for taking the time to comment
and mark your thread solved.

---

