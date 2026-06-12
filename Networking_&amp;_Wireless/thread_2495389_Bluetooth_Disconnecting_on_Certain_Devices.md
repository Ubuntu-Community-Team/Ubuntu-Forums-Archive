---
title: "Bluetooth Disconnecting on Certain Devices"
date: 2024-02-17
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2024-02-17
I have an odd problem that may or may not be a new issue. I have a pair of BT headphones that work just fine. I have tried connected other devices, though, and the devices will pair; connect for a second or two; and then disconnect. The ONLY way I get them to reconnect (even for just a second) is to remove it from the paired list and let it reestablish a pair. Once it's disconnected, I cannot even toggle the connection on and off. 

I have had issues with a bluetooth turntable in the past, but I eventually got that one working. I don't remember how, though.  

The most recent device I am trying to pair is a barcode scanner - a socketMobile model CHS 7Qi. 

Another issue I've noticed is that - sometimes - if I turn on bluetooth, the builtin wi-fi will stop working until I turn bluetooth back off. That is not always the case, though. Sometimes it works fine / Sometimes it doesn't. I don't mean that the wi-fi is disconnected or anything like that. I just cannot browse ANYTHING on the internet while bluetooth is active when this happens. The connection eventually times out.

I am running Ubuntu 22.04 (fully updated) on a Dell Latitude e7450. 

Any thing else you need, I'd be happy to provide. I would really appreciate any help with this.

---

### Post by rebeltaz on 2024-02-24
bump?

---

### Post by jeremy31 on 2024-02-24
Post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; sudo dmesg|egrep -i 'blue|firm'
```

---

### Post by rebeltaz on 2024-02-24
laptop:~$ lspci -nnk | grep -iA3 net; lsusb; sudo dmesg|egrep -i 'blue|firm'
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-LM [8086:15a2] (rev 03)
	DeviceName:  Onboard LAN
	Subsystem: Dell Ethernet Connection (3) I218-LM [1028:062e]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
--
02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5410]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
Bus 001 Device 003: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
Bus 001 Device 002: ID 8087:8001 Intel Corp. Integrated Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 012: ID 05a4:9862 Ortek Technology, Inc. Targus Number Keypad (Composite Device)
Bus 002 Device 013: ID 047d:1022 Kensington Orbit Optical
Bus 002 Device 011: ID 05a4:9837 Ortek Technology, Inc. Targus Number Keypad
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

