---
title: "No wireless adapter found (on 20.04 LTS)"
date: 2020-04-28
forum: Networking &amp; Wireless
---

### Post by gnadnerb on 2020-04-28
Just bought a brand new HP 14s laptop and cannot connect to WiFi as no wireless adapter can be found. The laptop was bought and I instantly had Ubuntu installed on to it. Any help would be appreciated!

---

### Post by jeremy31 on 2020-04-28
Please post results from terminal for ```
lspci -nnk | grep -iA3 net
```

---

### Post by mcsheffrey on 2020-04-30
I'm having the same problem. I'm using a Dell Latitude E7440, with 20.04. Also have Oracle VM running Windows 10 and MacOS.  Not sure if it ever worked since I installed 20.04, but was working in 19.10.
Here's the output from lspci -nnk | grep -iA3 net

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
	DeviceName:  Onboard LAN
	Subsystem: Dell Ethernet Connection I218-LM [1028:05cb]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
--
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

---

