---
title: "ASUS GL702ZC: Bluetooth not detected or working"
date: 2018-05-17
forum: Networking &amp; Wireless
---

### Post by Welly Wu on 2018-05-17
I own a new ASUS ROG STRIX GL702ZC gaming notebook PC and I installed Ubuntu 18.04.0 64 bit LTS GNU/Linux bare metal using the clean installation method. There are no other desktop operating systems installed on it other than Ubuntu.

```
wellywu@GL702ZC:~$ sudo lshw -C network; lsb_release -a; uname -a; sudo rfkill list
[sudo] password for wellywu: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: enp6s0
       version: 10
       serial: 18:31:bf:18:bc:df
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:64 ioport:e000(size=256) memory:fe604000-fe604fff memory:fe600000-fe603fff
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 00
       serial: 80:c5:f2:11:9b:8f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8822be driverversion=4.15.0-21-generic firmware=N/A ip=192.168.1.64 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:74 ioport:d000(size=256) memory:fe500000-fe50ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
Linux GL702ZC 4.15.0-21-generic #22-Ubuntu SMP Tue May 1 13:26:51 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
wellywu@GL702ZC:~$
```

802.11 dual-band AC Wi-Fi works, but Bluetooth 4.1 is not detected and it does not work. I need help troubleshooting it or learning more information about it to get it to work.

```
wellywu@GL702ZC:~$ sudo hcitool dev
Devices:
wellywu@GL702ZC:~$ sudo service bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: active (running) since Thu 2018-05-17 15:33:26 EDT; 1h 42min ago
     Docs: man:bluetoothd(8)
 Main PID: 2846 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;2846 /usr/lib/bluetooth/bluetoothd

May 17 15:33:26 GL702ZC systemd[1]: Starting Bluetooth service...
May 17 15:33:26 GL702ZC bluetoothd[2846]: Bluetooth daemon 5.48
May 17 15:33:26 GL702ZC systemd[1]: Started Bluetooth service.
May 17 15:33:26 GL702ZC bluetoothd[2846]: Starting SDP server
May 17 15:33:26 GL702ZC bluetoothd[2846]: Bluetooth management interface 1.14 in

wellywu@GL702ZC:~$ sudo hciconfig
hci0:    Type: Primary  Bus: USB
    BD Address: 80:C5:F2:11:9B:8E  ACL MTU: 820:8  SCO MTU: 255:16
    DOWN 
    RX bytes:601 acl:0 sco:0 events:32 errors:0
    TX bytes:375 acl:0 sco:0 commands:32 errors:0

wellywu@GL702ZC:~$ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
wellywu@GL702ZC:~$
```

If someone can assist me, then I will be grateful. In the meantime, I am going to be patient and watch this thread of mine.

---

