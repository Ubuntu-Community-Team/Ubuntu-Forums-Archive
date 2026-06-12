---
title: "Can't connect to internet - HP Probook 650 G1"
date: 2017-03-25
forum: Networking &amp; Wireless
---

### Post by llamacorn on 2017-03-25
Hi, I just installed Ubuntu 16.04.2 as a dual boot with Windows 10 on my laptop. I can't connect to wired or wireless networks. I've scanned many threads, but can't find a solution


heston@heston-HP-ProBook-650-G1:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
heston@heston-HP-ProBook-650-G1:~$ lspci -nnk | grep -iA3 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 04)
	Subsystem: Hewlett-Packard Company Ethernet Connection I217-V [103c:1993]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 04)
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
	DeviceName: WLAN
	Subsystem: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:05e2]
	Kernel driver in use: bcma-pci-bridge
heston@heston-HP-ProBook-650-G1:~$

---

### Post by chili555 on 2017-03-25
Please check here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by jeremy31 on 2017-03-25
Can you copy the results from terminal for ```
rfkill list
```
```
lspci -nnk | grep -iA3 net
```

welcome to the forums

---

### Post by llamacorn on 2017-03-25
Hi, I have added a screenshot above

---

### Post by jeremy31 on 2017-03-25
Screenshot didn't get posted

---

### Post by llamacorn on 2017-03-25
My apologies, please find plain text above

---

### Post by chili555 on 2017-03-25
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
DeviceName: WLAN
Subsystem: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:05e2]We have a new sticky for you: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by llamacorn on 2017-03-26
> **chili555 said:**
> We have a new sticky for you: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

I can't connect to the internet at all, I did see the sticky, but I couldn't use it. If I could only get the LAN to work then I could use the sticky.

---

### Post by chili555 on 2017-03-26
You can find the driver and its dependency on the install media. Here is a guide: [http://askubuntu.com/questions/835475/this-device-is-not-working-wifi-issues/835493#835493](http://askubuntu.com/questions/835475/this-device-is-not-working-wifi-issues/835493#835493)

As well, I'd love to see what is going wrong with the ethernet. Please run and post:```
dmesg | grep e100
```

---

### Post by llamacorn on 2017-03-26
[ATTACH=CONFIG]274311[/ATTACH]

Hi above is the screenshot. I did try install the intel drivers myself when LAN wasn't working, so I might have messed that up

---

### Post by chili555 on 2017-03-26
The screenshot says that your ethernet interface enp0s25 is up and has negotiated 100 Mbps, full duplex. It sounds suspiciously like it's actually working. Please plug in the ethernet cable and tell us if there is any indication that it is recognized in Network Manager; specifically, do you see anything listed related to ethernet when you click the Network Manager icon? [https://myn900.files.wordpress.com/2010/08/1.png](https://myn900.files.wordpress.com/2010/08/1.png)

What does this tell us after the cable is connected?```
dmesg | grep enp
```

---

### Post by llamacorn on 2017-03-26
My ethernet has miraculously started working. I don't know what fixed it. Now it's just for the wireless. Thanks for all your help. Much appreciated.

---

