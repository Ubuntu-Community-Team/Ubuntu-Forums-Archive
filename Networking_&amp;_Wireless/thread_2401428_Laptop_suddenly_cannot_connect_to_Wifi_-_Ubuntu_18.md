---
title: "Laptop suddenly cannot connect to Wifi - Ubuntu 18.04"
date: 2018-09-18
forum: Networking &amp; Wireless
---

### Post by Tigarq on 2018-09-18
[COLOR=#242729][FONT=Arial]Hi guys and gals, 

The issue is that my laptop suddenly stopped connecting to the wifi, the very same network that it used to connect to before. The network is still seen and recognized by the network manager but it displays "activation of network connection failed." My android phone still connects, so does my flatmate's windows laptop.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I used the lspci and rfkill commands in the terminal. Here are the outputs[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Lspci command:[/FONT][/COLOR]

```
01:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
Subsystem: Intel Corporation Wireless 8260 [8086:9010]
Kernel driver in use: iwlwifi
Kernel modules: iwlwifi
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Samsung Electronics Co Ltd RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [144d:c136]
    Kernel driver in use: r8169
    Kernel modules: r8169
```
[COLOR=#242729][FONT=Arial]
And the rfkill command:[/FONT][/COLOR]

```
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```[COLOR=#242729][FONT=Arial]
I would really appreciate your help on this one! Any ideas what might have gone wrong?[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-09-18
See the wireless script link in my signature and post results

---

### Post by Autodave on 2018-09-18
Another simple thing to try:


  	 	 	 	   This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by Tigarq on 2018-09-18
It created a wireless-info.txt file. Here's the result - [https://paste.ubuntu.com/p/RmT6pMGm26/](https://paste.ubuntu.com/p/RmT6pMGm26/)

---

### Post by jeremy31 on 2018-09-19
See if it improves after ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by Tigarq on 2018-09-19
It didn't improve, "activation of network connection" keeps popping up. Any other ideas what I can do about it, Jeremy?

---

