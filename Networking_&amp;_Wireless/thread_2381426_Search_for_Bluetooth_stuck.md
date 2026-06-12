---
title: "Search for Bluetooth stuck"
date: 2017-12-31
forum: Networking &amp; Wireless
---

### Post by Vaclav Vasek on 2017-12-31
I have installed Bluetooth dongle on Ubuntu OS 16/04 LST 
The "search" for Bluetooth devices ( Bluetooth speaker, RPi 3 ) gets stuck - no devices found. 

Here is some terminal output 

os64@os64-desktop:~$ lsusb
Bus 002 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bc2:2322 Seagate RSS LLC 
Bus 001 Device 010: ID 0a48:3239 I/O Interconnect Multimedia Card Reader
Bus 001 Device 007: ID 1307:0310 Transcend Information, Inc. SD/MicroSD CardReader [hama]
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 011: ID 047f:0ca1 Plantronics, Inc. USB DSP v4 Audio Interface
Bus 001 Device 009: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 001 Device 024: ID 0457:0163 Silicon Integrated Systems Corp. SiS163U 802.11 Wireless LAN Adapter
Bus 001 Device 004: ID 2001:f103 D-Link Corp. DUB-H7 7-port USB 2.0 hub
Bus 001 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
os64@os64-desktop:~$ sudo /etc/init.d/bluetooth status
[sudo] password for os64: 
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2017-12-31 09:29:28 CST; 13min ago
     Docs: man:bluetoothd(8)
 Main PID: 1011 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1011 /usr/lib/bluetooth/bluetoothd

Dec 31 09:29:30 os64-desktop bluetoothd[1011]: Not enough free handles to re...e
Dec 31 09:29:30 os64-desktop bluetoothd[1011]: Not enough free handles to re...e
Dec 31 09:29:30 os64-desktop bluetoothd[1011]: Current Time Service could no...d
Dec 31 09:29:30 os64-desktop bluetoothd[1011]: gatt-time-server: Input/outpu...)
Dec 31 09:29:30 os64-desktop bluetoothd[1011]: Not enough free handles to re...e
Dec 31 09:29:30 os64-desktop bluetoothd[1011]: Not enough free handles to re...e
Dec 31 09:29:30 os64-desktop bluetoothd[1011]: Sap driver initialization failed.
Dec 31 09:29:30 os64-desktop bluetoothd[1011]: sap-server: Operation not per...)
Dec 31 09:29:50 os64-desktop bluetoothd[1011]: Endpoint registered: sender=:...e
Dec 31 09:29:50 os64-desktop bluetoothd[1011]: Endpoint registered: sender=:...k
Hint: Some lines were ellipsized, use -l to show in full.
os64@os64-desktop:~$ 

os64@os64-desktop:~$ hcitool scan
Scanning ...
os64@os64-desktop:~$ hcitool scan
Scanning ...
os64@os64-desktop:~$ 

So - what is wrong here ? Which tool is not getting the devices?

**OR - do in need more generic Bluetooth dongle - I have "radio" .**

---

