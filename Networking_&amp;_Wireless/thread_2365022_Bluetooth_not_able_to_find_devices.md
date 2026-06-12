---
title: "Bluetooth not able to find devices"
date: 2017-07-01
forum: Networking &amp; Wireless
---

### Post by plopmon on 2017-07-01
I have dual-booted Windows and Ubuntu. from Ubuntu I wanted to connect my wireless Bluetooth speaker to my laptop. when I went to Bluetooth settings and add device option (the + sign thingy) it went on 'searching for devices' for almost half an hour.

do I need to install/update my Bluetooth drivers or is there a bug?

---

### Post by jeremy31 on 2017-07-01
Please open a terminal window and paste the following command and post the results
```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
```

---

### Post by plopmon on 2017-07-02
> **jeremy31 said:**
> Please open a terminal window and paste the following command and post the results
```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
```

here is the result

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	DeviceName: Realtek PCIe FE Family Controller
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1858]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	DeviceName: Atheros AR9485 802.11b/g/n WiFi Adapter
	Subsystem: Hewlett-Packard Company AR9485 Wireless Network Adapter [103c:1785]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
Bus 002 Device 005: ID 0cf3:311d Atheros Communications, Inc. 
Bus 002 Device 003: ID 05c8:0222 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1ea7:0064  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[    4.472125] usb 2-1.4: Product: Bluetooth USB Host Controller
[   18.546647] Bluetooth: Core ver 2.21
[   18.546665] Bluetooth: HCI device and connection manager initialized
[   18.546669] Bluetooth: HCI socket layer initialized
[   18.546671] Bluetooth: L2CAP socket layer initialized
[   18.546679] Bluetooth: SCO socket layer initialized
[   20.060540] usb 2-1.4: Product: Bluetooth USB Host Controller
[   31.552453] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.552454] Bluetooth: BNEP filters: protocol multicast
[   31.552458] Bluetooth: BNEP socket layer initialized
[   48.350683] Bluetooth: RFCOMM TTY layer initialized
[   48.350688] Bluetooth: RFCOMM socket layer initialized
[   48.350695] Bluetooth: RFCOMM ver 1.11

---

### Post by jeremy31 on 2017-07-02
So can you
```
bluetoothctl
power on
scan on
```

Use CTRL + d to exit from bluetoothctl

The bluetooth should work as that one is supported and there aren't any firmware errors

---

### Post by plopmon on 2017-07-02
> **jeremy31 said:**
> So can you
```
bluetoothctl
power on
scan on
```

Use CTRL + d to exit from bluetoothctl

The bluetooth should work as that one is supported and there aren't any firmware errors

THANKS!!! IT DID WORK!!!!
can you tell me what the problem was? im curious :D

---

### Post by jeremy31 on 2017-07-02
It might have just been powered down in Windows and needed to be turned on

---

### Post by plopmon on 2017-07-03
well.... problem again not solved...... when you first gave me 
```
 bluetoothctl
powe on
scan on
```
 i tested this method with my phone (Moto e3 pwer) and it paired succesfully. but when i tried to connect my bluetooth to my wireless headset named G7 then there is a probelm. at when connecting to G7 ubuntu showed it failed connecting to it. but in the top 'titlebar' thingy (im new to linux dont know the names) where bluetooth sign is present on clicking it it shows 
moto e3 power and G7. but if i go to BT settings it shows only moto e3. 

please suggest

---

### Post by jeremy31 on 2017-07-03
Try ```
pactl load-module module-bluetooth-discover
```
Then connect to the headset

---

### Post by plopmon on 2017-07-07
> **jeremy31 said:**
> Try ```
pactl load-module module-bluetooth-discover
```
Then connect to the headset

Reuslt: 

Failure: Module initialization failed

---

### Post by plopmon on 2017-07-07
> **jeremy31 said:**
> Try ```
pactl load-module module-bluetooth-discover
```
Then connect to the headset

Thanks! it dod not work by the code but just connected all by itself

---

