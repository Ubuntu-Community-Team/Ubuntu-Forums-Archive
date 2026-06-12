---
title: "ubuntu 13.10 - wifi slow - iwl3945"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by martin48 on 2014-02-03
Hi. My name is martin and i have some problems with my ubuntu 13.10. My notebook is a Dell XPS m1530, with intel 3945ABG wifi card.
This problem appears a few days ago, i do not know if it began after an apt-get upgrade of any package.

The connection works intermittently slow. I can reproduce the problem when i want by suspending and resuming ubuntu.
Now, i need to reset Wifi connection to obtain full speed. 
If i use a wired connection i have no problems. In dual boot with windows 7, i have no problems with wifi.

Here you are some screenshots so you can see the difference.

[ATTACH=CONFIG]250056[/ATTACH]

[ATTACH=CONFIG]250057[/ATTACH]


uname -mr
```
3.8.0-27-generic i686
```

lspci
```

pepe@pepe:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G84M [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

lsusb
```
pepe@pepe:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

ifconfig
```
pepe@pepe:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:5c:51:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3662814 (3.6 MB)  TX bytes:1153781 (1.1 MB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:546447 (546.4 KB)  TX bytes:546447 (546.4 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1c:6c:7c:41:2c  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe7c:418c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:274595416 (274.5 MB)  TX bytes:25927009 (25.9 MB)

```

iwconfig
```
pepe@pepe:~$ iwconfig 
wlan0     IEEE 802.11abg  ESSID:"pepito"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:29:23:BC:32:2C   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:5410   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.

```

lshw
```
pepe@pepe:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:5c:51:23
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:7c:41:8c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.8.0-27-generic firmware=15.32.2.9 ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f1eff000-f1efffff

```

lsmod
```

pepe@pepe:/etc$ lsmod | grep "iwl*"
iwl3945                63619  0 
iwlegacy               87575  1 iwl3945
mac80211              526519  2 iwl3945,iwlegacy
cfg80211              436177  3 iwl3945,iwlegacy,mac80211

```

dmesg
```
pepe@pepe:/etc$ dmesg | grep iwl*
[   30.685230] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   30.685235] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   30.740691] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   30.740697] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   30.740851] iwl3945 0000:0b:00.0: irq 46 for MSI/MSI-X
[   30.757182] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   34.598142] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   39.742199] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   39.742203] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 9630.241061] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 9630.241065] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[13484.169418] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[13484.169424] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[14751.712045] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[14751.712050] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[15289.947063] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[15289.947067] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[15347.883761] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[15347.883765] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[15652.885471] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[15652.885477] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[16541.248407] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[16541.248411] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[18035.585123] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[18035.585127] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[18146.264061] iwl3945 0000:0b:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[18146.264065] iwl3945 0000:0b:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP

```

> sudo iwlist wlan0 scan
[ATTACH]250059[/ATTACH]




Thanks,

---

### Post by martin48 on 2014-02-03
I had tried several changes without lucky:
1- change script /usr/lib/pm-utils/power.d/wireless
2- create file ath9k.conf
3- disable ipv6 in /etc/sysctl.conf

---

### Post by martin48 on 2014-02-04
any help?

---

### Post by kurt18947 on 2014-02-05
No expert here but perhaps this is a clue:

> The connection works intermittently slow. I can reproduce the problem when i want by suspending and resuming ubuntu.
Now, i need to reset Wifi connection to obtain full speed.

There have been issues in the past with wifi devices not disconnecting properly before a machine goes into suspend.  Because the device did not disconnect properly, it cannot reconnect properly.  If you manually disconnect then reconnect, your device works.  Here is a thread from 2012.  I detailed what has worked for me with another adapter in the past:

[http://ubuntuforums.org/showthread.php?t=2072509&highlight=suspend](http://ubuntuforums.org/showthread.php?t=2072509&highlight=suspend).  Post #5 but in your case substitute "iwl3945" for "r8712u".  I make no assurances this fix will help you but I doubt there'd be any harm and if it doesn't help, simply delete the file.  I have a machine with the iwl 3945 card installed but have blacklisted it preferring a faster USB device.

---

