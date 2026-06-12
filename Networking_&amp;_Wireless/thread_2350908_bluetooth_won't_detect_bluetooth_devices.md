---
title: "bluetooth won't detect bluetooth devices"
date: 2017-01-28
forum: Networking &amp; Wireless
---

### Post by shanelo7a on 2017-01-28
Hi,
this is my first using UBUNTU, I got it installed and updated the software and drivers and got my WiFi to work but now I am facing a problem with my bluetooth won't detect any devices, I tried different devices and none of them got detected by my pc
I tried this 
```

lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'

```

and got this 
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:80dd]
    Kernel driver in use: r8169
    Kernel modules: r8169
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Kernel driver in use: wl
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 003: ID 064e:930a Suyin Corp. 
Bus 001 Device 002: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 60:6D:C7:D2:31:16  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING INQUIRY 
    RX bytes:1586 acl:0 sco:0 events:163 errors:0
    TX bytes:3180 acl:0 sco:0 commands:147 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'ahmed-HP-ENVY-Notebook'
    Class: 0x0c010c
    Service Classes: Rendering, Capturing
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)

[   25.505159] Bluetooth: Core ver 2.21
[   25.505174] Bluetooth: HCI device and connection manager initialized
[   25.505177] Bluetooth: HCI socket layer initialized
[   25.505180] Bluetooth: L2CAP socket layer initialized
[   25.505186] Bluetooth: SCO socket layer initialized
[   27.690002] Bluetooth: hci0 command 0x1001 tx timeout
[   35.685804] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[   35.690659] Bluetooth: hci0: BCM: chip id 70
[   35.706660] Bluetooth: hci0: BCM43142A
[   35.706664] Bluetooth: hci0: BCM (001.001.011) build 0000
[   39.447314] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   39.447318] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   41.449720] Bluetooth: hci0 command 0x1003 tx timeout
[   42.728532] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.728534] Bluetooth: BNEP filters: protocol multicast
[   42.728538] Bluetooth: BNEP socket layer initialized
[ 1627.027487] Bluetooth: hci0: BCM: chip id 70
[ 1627.043477] Bluetooth: hci0: BCM43142A
[ 1627.043481] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 1627.043497] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 1627.043499] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 1629.048936] Bluetooth: hci0 command 0x1003 tx timeout
[ 1629.140331] Bluetooth: RFCOMM TTY layer initialized
[ 1629.140338] Bluetooth: RFCOMM socket layer initialized
[ 1629.140343] Bluetooth: RFCOMM ver 1.11

```


```

sudo service bluetooth status

```

and I got this 

```

Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Not enough free handles
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Not enough free handles
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Current Time Service co
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: gatt-time-server: Input
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Not enough free handles
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Not enough free handles
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Sap driver initializati
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: sap-server: Operation n
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Endpoint registered: se
Jan 28 21:38:20 ahmed-HP-ENVY-Notebook bluetoothd[1168]: Endpoint registered: se
lines 1-19/19 (END)


```
where do I go from there ?

---

### Post by wildmanne39 on 2017-01-28
*Thread moved to **Networking & Wireless for better support**.*

---

### Post by jeremy31 on 2017-01-29
You should see Pilot6's [answer](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu)

Search the Window's inf file for 216d as that is your bluetooth device from your lsusb results to find [RAMUSB216D.CopyList] and there should be a .hex file name listed.  Then convert the .hex file using the hex2hcd to name it BCM.hcd and then copy into /lib/firmware/brcm/

Reboot and it should work better

---

