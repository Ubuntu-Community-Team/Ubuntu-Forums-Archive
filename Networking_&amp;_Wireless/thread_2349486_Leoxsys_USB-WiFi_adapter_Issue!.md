---
title: "Leoxsys USB-WiFi adapter Issue!"
date: 2017-01-15
forum: Networking &amp; Wireless
---

### Post by karthik31 on 2017-01-15
Hello! I have a bought a new WiFi adapter Leoxsys rtl8188eu. 
The system detects the USB 
```
karthik@karthik:~$ lsusb
Bus 001 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
but I can't see any sign of network in my browser as well in my GUI panel regarding the adapter. I tried the methods given in this link [http://askubuntu.com/questions/301763/usb-wifi-adapter-not-working](http://askubuntu.com/questions/301763/usb-wifi-adapter-not-working)
but it isn't working.

---

### Post by jeremy31 on 2017-01-15
*Thread moved to **Networking & Wireless**.*
Please see the wireless script link in my signature and post results

---

### Post by karthik31 on 2017-01-15
It isn't working can you give me any other solution

---

### Post by ajgreeny on 2017-01-15
What isn't working? Does the script not run?

That script does not solve the problem when it's run, but produces an output to help wifi experts on this forum to suggest solutions for the problem.
Please show us the output report from the script as asked for by jeremy31.

---

### Post by karthik31 on 2017-01-15
```


########## wireless info START ##########

Report from: 15 Jan 2017 22:35 IST +0530

Booted last: 15 Jan 2017 21:04 IST +0530

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-59-generic #80~14.04.1-Ubuntu SMP Fri Jan 6 18:02:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:2212]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 001 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0 
rt2800pci              16384  0 
rt2800mmio             20480  1 rt2800pci
rt2800lib              90112  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              53248  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              733184  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              557056  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi
sparse_keymap          16384  2 hp_wmi,intel_hid

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1341068 (1.3 MB)  TX bytes:425547 (425.5 KB)

lxdbr0    Link encap:Ethernet  HWaddr <MAC 'lxdbr0' [IF2]>  
          inet addr:10.0.1.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'lxdbr0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9266 (9.2 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF3]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF3]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56923 (56.9 KB)  TX bytes:34735 (34.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

lxdbr0    no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 lxdbr0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       990     1  0 21:04 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF3]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    D-Link:          Infra, <MAC 'D-Link' [AN1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 46 WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.37
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/HUAWEI-E8231-f3ce 1]] (600 root)
[connection] id=HUAWEI-E8231-f3ce 1 | type=802-11-wireless
[802-11-wireless] ssid=HUAWEI-E8231-f3ce | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MBLAZE-MF800-BC3E]] (600 root)
[connection] id=MBLAZE-MF800-BC3E | type=802-11-wireless
[802-11-wireless] ssid=MBLAZE-MF800-BC3E | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Staff]] (600 root)
[connection] id=Staff | type=802-11-wireless
[802-11-wireless] ssid=Staff | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Connectify-theena]] (600 root)
[connection] id=Connectify-theena | type=802-11-wireless
[802-11-wireless] ssid=Connectify-theena | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CloudFox2_5A10 1]] (600 root)
[connection] id=CloudFox2_5A10 1 | type=802-11-wireless
[802-11-wireless] ssid=CloudFox2_5A10 | mac-address=<MAC 'wlan0' [IF3]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Theena_Redmi]] (600 root)
[connection] id=Theena_Redmi | type=802-11-wireless
[802-11-wireless] ssid=Theena_Redmi | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RK]] (600 root)
[connection] id=RK | type=802-11-wireless
[802-11-wireless] ssid=RK | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/smvec]] (600 root)
[connection] id=smvec | type=802-11-wireless
[802-11-wireless] ssid=smvec | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/karthikr2910]] (600 root)
[connection] id=karthikr2910 | type=802-11-wireless
[802-11-wireless] ssid=karthikr2910 | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CloudFox2_5A10]] (600 root)
[connection] id=CloudFox2_5A10 | type=802-11-wireless
[802-11-wireless] ssid=CloudFox2_5A10 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Student]] (600 root)
[connection] id=Student | type=802-11-wireless
[802-11-wireless] ssid=Student | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Sangeetha 1]] (600 root)
[connection] id=Sangeetha 1 | type=802-11-wireless
[802-11-wireless] ssid=Sangeetha | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sherlocked 1]] (600 root)
[connection] id=sherlocked 1 | type=802-11-wireless
[802-11-wireless] ssid=sherlocked | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/amirtham 1]] (600 root)
[connection] id=amirtham 1 | type=802-11-wireless
[802-11-wireless] ssid=amirtham | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Flight]] (600 root)
[connection] id=Flight | type=802-11-wireless
[802-11-wireless] ssid=Flight | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Karthik Rg]] (600 root)
[connection] id=Karthik Rg | type=802-11-wireless
[802-11-wireless] ssid=Karthik Rg | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ramamoorthy's iPhone]] (600 root)
[connection] id=Ramamoorthy's iPhone | type=802-11-wireless
[802-11-wireless] ssid=Ramamoorthy's iPhone | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vibe 5 1]] (600 root)
[connection] id=vibe 5 1 | type=802-11-wireless
[802-11-wireless] ssid=vibe 5 | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=KR_Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=karthik | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Amirtham 1]] (600 root)
[connection] id=Amirtham 1 | type=802-11-wireless
[802-11-wireless] ssid=Amirtham | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sangeetha]] (600 root)
[connection] id=Sangeetha | type=802-11-wireless
[802-11-wireless] ssid=Sangeetha | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sherlocked]] (600 root)
[connection] id=sherlocked | type=802-11-wireless
[802-11-wireless] ssid=sherlocked | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi 1]] (600 root)
[connection] id=Redmi 1 | type=802-11-wireless
[802-11-wireless] ssid=Redmi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link]] (600 root)
[connection] id=D-Link | type=802-11-wireless
[802-11-wireless] ssid=D-Link | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MotoG3 8780]] (600 root)
[connection] id=MotoG3 8780 | type=802-11-wireless
[802-11-wireless] ssid=MotoG3 8780 | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Connectify-theena 1]] (600 root)
[connection] id=Connectify-theena 1 | type=802-11-wireless
[802-11-wireless] ssid=Connectify-theena | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MotoG3 8780 1]] (600 root)
[connection] id=MotoG3 8780 1 | type=802-11-wireless
[802-11-wireless] ssid=MotoG3 8780 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/amirtham]] (600 root)
[connection] id=amirtham | type=802-11-wireless
[802-11-wireless] ssid=amirtham | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Theena_Redmi 1]] (600 root)
[connection] id=Theena_Redmi 1 | type=802-11-wireless
[802-11-wireless] ssid=Theena_Redmi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/fun]] (600 root)
[connection] id=fun | type=802-11-wireless
[802-11-wireless] ssid=fun | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=802-11-wireless
[802-11-wireless] ssid=Redmi | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RK 1]] (600 root)
[connection] id=RK 1 | type=802-11-wireless
[802-11-wireless] ssid=RK | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Student 1]] (600 root)
[connection] id=Student 1 | type=802-11-wireless
[802-11-wireless] ssid=Student | mac-address=<MAC 'wlan0' [IF3]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Amirtham]] (600 root)
[connection] id=Amirtham | type=802-11-wireless
[802-11-wireless] ssid=Amirtham | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HUAWEI-E8231-f3ce]] (600 root)
[connection] id=HUAWEI-E8231-f3ce | type=802-11-wireless
[802-11-wireless] ssid=HUAWEI-E8231-f3ce | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ramamoorthy's iPhone 1]] (600 root)
[connection] id=Ramamoorthy's iPhone 1 | type=802-11-wireless
[802-11-wireless] ssid=Ramamoorthy's iPhone | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vibe 5]] (600 root)
[connection] id=vibe 5 | type=802-11-wireless
[802-11-wireless] ssid=vibe 5 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link 1]] (600 root)
[connection] id=D-Link 1 | type=802-11-wireless
[802-11-wireless] ssid=D-Link | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

lxdbr0    no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

lxdbr0    Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2x00pci]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2x00mmio]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/50-8188eu.conf]
blacklist r8188eu

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF3]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[ 4518.088484] r8169 0000:08:00.0 eth0: link down (repeated 2 times)
[ 4518.088569] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4518.211571] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4519.338244] wlan0: authenticate with <MAC 'D-Link' [AN1]>
[ 4519.343347] wlan0: send auth to <MAC 'D-Link' [AN1]> (try 1/3)
[ 4519.345555] wlan0: authenticated
[ 4519.347297] wlan0: associate with <MAC 'D-Link' [AN1]> (try 1/3)
[ 4519.356775] wlan0: RX AssocResp from <MAC 'D-Link' [AN1]> (capab=0x411 status=0 aid=6)
[ 4519.356835] wlan0: associated
[ 4519.356874] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4519.668183] r8169 0000:08:00.0 eth0: link up
[ 4519.668193] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4533.115141] r8169 0000:08:00.0 eth0: link down
[ 4534.654793] r8169 0000:08:00.0 eth0: link up
[ 4537.360395] wlan0: deauthenticating from <MAC 'D-Link' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

 
```

This is the result. What should I do next?

---

### Post by jeremy31 on 2017-01-15
What is the result of ```
locate 8188eu.ko
```

---

### Post by karthik31 on 2017-01-15
```

karthik@karthik:~$ locate 8188eu.ko
/lib/modules/4.2.0-27-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.2.0-42-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-34-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-36-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-38-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-42-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-45-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-53-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-57-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
/lib/modules/4.4.0-59-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko



```
This one

---

### Post by jeremy31 on 2017-01-15
Something happened as it never installed the driver, so we can reinstall
```
sudo apt-get install git build-essential dkms linux-headers-generic
git clone https://github.com/lwfinger/rtl8188eu.git
sudo dkms add ./rtl8188eu
sudo dkms build 8188eu/1.0
sudo dkms install 8188eu/1.0
```

Reboot

---

### Post by karthik31 on 2017-01-15
Did it and now the report is: ```


########## wireless info START ##########

Report from: 15 Jan 2017 23:58 IST +0530

Booted last: 15 Jan 2017 23:56 IST +0530

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-59-generic #80~14.04.1-Ubuntu SMP Fri Jan 6 18:02:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:2212]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 001 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800pci              16384  0 
rt2800mmio             20480  1 rt2800pci
rt2800lib              90112  2 rt2800pci,rt2800mmio
hp_wmi                 16384  0 
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              53248  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              733184  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              557056  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi
sparse_keymap          16384  2 hp_wmi,intel_hid

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218794 (218.7 KB)  TX bytes:108237 (108.2 KB)

lxdbr0    Link encap:Ethernet  HWaddr <MAC 'lxdbr0' [IF2]>  
          inet addr:10.0.1.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'lxdbr0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7923 (7.9 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF3]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF3]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1098 (1.0 KB)  TX bytes:7437 (7.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

lxdbr0    no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 lxdbr0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       973     1  0 23:56 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF3]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    D-Link:          Infra, <MAC 'D-Link' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 40 WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.37
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/HUAWEI-E8231-f3ce 1]] (600 root)
[connection] id=HUAWEI-E8231-f3ce 1 | type=802-11-wireless
[802-11-wireless] ssid=HUAWEI-E8231-f3ce | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MBLAZE-MF800-BC3E]] (600 root)
[connection] id=MBLAZE-MF800-BC3E | type=802-11-wireless
[802-11-wireless] ssid=MBLAZE-MF800-BC3E | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Staff]] (600 root)
[connection] id=Staff | type=802-11-wireless
[802-11-wireless] ssid=Staff | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Connectify-theena]] (600 root)
[connection] id=Connectify-theena | type=802-11-wireless
[802-11-wireless] ssid=Connectify-theena | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CloudFox2_5A10 1]] (600 root)
[connection] id=CloudFox2_5A10 1 | type=802-11-wireless
[802-11-wireless] ssid=CloudFox2_5A10 | mac-address=<MAC 'wlan0' [IF3]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Theena_Redmi]] (600 root)
[connection] id=Theena_Redmi | type=802-11-wireless
[802-11-wireless] ssid=Theena_Redmi | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RK]] (600 root)
[connection] id=RK | type=802-11-wireless
[802-11-wireless] ssid=RK | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/smvec]] (600 root)
[connection] id=smvec | type=802-11-wireless
[802-11-wireless] ssid=smvec | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/karthikr2910]] (600 root)
[connection] id=karthikr2910 | type=802-11-wireless
[802-11-wireless] ssid=karthikr2910 | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CloudFox2_5A10]] (600 root)
[connection] id=CloudFox2_5A10 | type=802-11-wireless
[802-11-wireless] ssid=CloudFox2_5A10 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Student]] (600 root)
[connection] id=Student | type=802-11-wireless
[802-11-wireless] ssid=Student | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Sangeetha 1]] (600 root)
[connection] id=Sangeetha 1 | type=802-11-wireless
[802-11-wireless] ssid=Sangeetha | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sherlocked 1]] (600 root)
[connection] id=sherlocked 1 | type=802-11-wireless
[802-11-wireless] ssid=sherlocked | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/amirtham 1]] (600 root)
[connection] id=amirtham 1 | type=802-11-wireless
[802-11-wireless] ssid=amirtham | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Flight]] (600 root)
[connection] id=Flight | type=802-11-wireless
[802-11-wireless] ssid=Flight | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Karthik Rg]] (600 root)
[connection] id=Karthik Rg | type=802-11-wireless
[802-11-wireless] ssid=Karthik Rg | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ramamoorthy's iPhone]] (600 root)
[connection] id=Ramamoorthy's iPhone | type=802-11-wireless
[802-11-wireless] ssid=Ramamoorthy's iPhone | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vibe 5 1]] (600 root)
[connection] id=vibe 5 1 | type=802-11-wireless
[802-11-wireless] ssid=vibe 5 | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=KR_Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=karthik | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Amirtham 1]] (600 root)
[connection] id=Amirtham 1 | type=802-11-wireless
[802-11-wireless] ssid=Amirtham | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sangeetha]] (600 root)
[connection] id=Sangeetha | type=802-11-wireless
[802-11-wireless] ssid=Sangeetha | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sherlocked]] (600 root)
[connection] id=sherlocked | type=802-11-wireless
[802-11-wireless] ssid=sherlocked | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi 1]] (600 root)
[connection] id=Redmi 1 | type=802-11-wireless
[802-11-wireless] ssid=Redmi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link]] (600 root)
[connection] id=D-Link | type=802-11-wireless
[802-11-wireless] ssid=D-Link | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MotoG3 8780]] (600 root)
[connection] id=MotoG3 8780 | type=802-11-wireless
[802-11-wireless] ssid=MotoG3 8780 | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Connectify-theena 1]] (600 root)
[connection] id=Connectify-theena 1 | type=802-11-wireless
[802-11-wireless] ssid=Connectify-theena | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MotoG3 8780 1]] (600 root)
[connection] id=MotoG3 8780 1 | type=802-11-wireless
[802-11-wireless] ssid=MotoG3 8780 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/amirtham]] (600 root)
[connection] id=amirtham | type=802-11-wireless
[802-11-wireless] ssid=amirtham | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Theena_Redmi 1]] (600 root)
[connection] id=Theena_Redmi 1 | type=802-11-wireless
[802-11-wireless] ssid=Theena_Redmi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/fun]] (600 root)
[connection] id=fun | type=802-11-wireless
[802-11-wireless] ssid=fun | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=802-11-wireless
[802-11-wireless] ssid=Redmi | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RK 1]] (600 root)
[connection] id=RK 1 | type=802-11-wireless
[802-11-wireless] ssid=RK | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Student 1]] (600 root)
[connection] id=Student 1 | type=802-11-wireless
[802-11-wireless] ssid=Student | mac-address=<MAC 'wlan0' [IF3]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Amirtham]] (600 root)
[connection] id=Amirtham | type=802-11-wireless
[802-11-wireless] ssid=Amirtham | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HUAWEI-E8231-f3ce]] (600 root)
[connection] id=HUAWEI-E8231-f3ce | type=802-11-wireless
[802-11-wireless] ssid=HUAWEI-E8231-f3ce | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ramamoorthy's iPhone 1]] (600 root)
[connection] id=Ramamoorthy's iPhone 1 | type=802-11-wireless
[802-11-wireless] ssid=Ramamoorthy's iPhone | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vibe 5]] (600 root)
[connection] id=vibe 5 | type=802-11-wireless
[802-11-wireless] ssid=vibe 5 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link 1]] (600 root)
[connection] id=D-Link 1 | type=802-11-wireless
[802-11-wireless] ssid=D-Link | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

lxdbr0    no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

lxdbr0    Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.457 GHz (Channel 10)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'D-Link' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"D-Link"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007125b45187
                    Extra: Last beacon: 13012ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2x00pci]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2x00mmio]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/50-8188eu.conf]
blacklist r8188eu

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF3]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[   36.923284] r8169 0000:08:00.0 eth0: link up
[   36.923294] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.626301] wlan0: authenticate with <MAC 'D-Link' [AC1]>
[   64.641967] wlan0: send auth to <MAC 'D-Link' [AC1]> (try 1/3)
[   64.643380] wlan0: authenticated
[   64.645863] wlan0: associate with <MAC 'D-Link' [AC1]> (try 1/3)
[   64.654811] wlan0: RX AssocResp from <MAC 'D-Link' [AC1]> (capab=0x411 status=0 aid=1)
[   64.654878] wlan0: associated
[   64.654921] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   68.394831] wlan0: deauthenticating from <MAC 'D-Link' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############



```
What next?

---

### Post by jeremy31 on 2017-01-15
What happens when you ```
sudo modprobe -v 8188eu
```

---

### Post by karthik31 on 2017-01-15
```
karthik@karthik:~$ sudo modprobe -v 8188eu
insmod /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/8188eu.ko 
modprobe: ERROR: could not insert '8188eu': Required key not available


```
am getting this error.

---

### Post by jeremy31 on 2017-01-15
Go into the BIOS settings and disable secure boot

---

### Post by karthik31 on 2017-01-15
Yeah. It works fine. Thank you so much Mr. Jeremy :) . Besides, what about the secure boot, should it be still disabled? Or enabled?

---

### Post by jeremy31 on 2017-01-15
I needs to be disabled for it to load the wireless module

---

### Post by karthik31 on 2017-01-15
Will it bring any problems?

---

### Post by jeremy31 on 2017-01-15
It shouldn't cause any issues and there are a lot of computers using Ubuntu without the Secure boot option

---

### Post by ajgreeny on 2017-01-15
> **karthik31 said:**
> Will it bring any problems?
It certainly shouldn't cause any difficulties.

Secure boot is a Microsoft "lock" to stop the loading of anything that does not have a security key issued by Microsoft only, as far as I'm aware.
Disabling secure boot has nothing to do with Linux and will not affect Windows either, if you have it.

---

### Post by karthik31 on 2017-01-15
Thanks for the info

---

### Post by karthik31 on 2017-02-04
Jeremy unfortunately the problem started again after update. When I run ```
karthik@karthik:~$ sudo modprobe -v 8188eu
insmod /lib/modules/4.4.0-62-generic/updates/dkms/8188eu.ko 
modprobe: ERROR: could not insert '8188eu': Exec format error
 
```
What to do know?

---

### Post by jeremy31 on 2017-02-04
It is likely an issue with the dkms.conf file but it can be fixed

```
sudo -H gedit /var/lib/dkms/8188eu/1.0/build/dkms.conf
```

Scroll down to ```
MAKE="'make' all"
```
Replace it with
```
MAKE="'make' all KVER=${kernelver}"
```
Save, exit gedit, and
```
sudo dkms remove 8188eu/1.0 -k $(uname -r)
```
```
sudo dkms install 8188eu/1.0
```
Then reboot and see if it works

The problem was likely the result of dkms building the new module using the older kernel header files and that seems to be fixed by changing the MAKE line in the dkms.conf file

---

### Post by karthik31 on 2017-02-04
It is all done Jeremy thank you its working now.

---

### Post by jeremy31 on 2017-02-05
If you want it to work for the next kernel update
```
sudo -H gedit /usr/src/8188eu-1.0/dkms.conf
```

Make the same changes there

---

