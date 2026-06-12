---
title: "Sabrent 802.11G PCI card runs at 802.11B speeds"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by flyfisherbryan on 2014-03-09
I installed a Sabrent 802.11G (aka Realink RT2561/RT61) PCI card in my Dell Optiplex 745, which is running Ubuntu 13.10 (dual boot with XP).  I bought this card specifically because they advertise Linux compatability and it did run right out of the box, bjt it runs at a maximum speed of 11Mb/s (often only 5),  which is 802.11B, instead of 54 Mb/s as an 802.11G should.  There are no newer drivers or firmware to install.  I do not know if my network manager is buggy, but when I click wifi settings in the context menu nothing happens.  I do not know if the problem is with the hardware or software or some configuration problem.  I did try it with ufw disabled and it still runs at 11 Mb/s or less.  Other computers on my network run as fast as 130, and this Optiplex runs at 65 with a USB wireless, but I am really hoping to get this card up to a decent speed.  Any suggestions  would be appreciated.
 

 I have read the sticky and the wiki so I have run all the commands asked for and have done my best to edite the information to include only that pertaining to my wireless situation:
 ```
$ lspci
04:00.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI

$ ifconfig
wlan2     Link encap:Ethernet  HWaddr 00:e0:12:05:05:50  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:12ff:fe05:550/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8088102 (8.0 MB)  TX bytes:844614 (844.6 KB)

$ iwconfig
wlan2     IEEE 802.11bg  ESSID:"HOME-7B42"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D3:53:7B:40   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:222  Invalid misc:8324   Missed beacon:0

$ lsmod | grep rt61pci
rt61pci                27296  0 
rt2x00pci              13111  1 rt61pci
rt2x00mmio             13395  1 rt61pci
rt2x00lib              48933  3 rt61pci,rt2x00pci,rt2x00mmio
eeprom_93cx6           13168  1 rt61pci
crc_itu_t              12627  1 rt61pci

$ dmesg | grep wlan2
[   25.929124] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   25.929604] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   28.249012] wlan2: authenticate with 00:1d:d3:53:7b:40
[   28.259988] wlan2: send auth to 00:1d:d3:53:7b:40 (try 1/3)
[   28.261296] wlan2: authenticated
[   28.264078] wlan2: associate with 00:1d:d3:53:7b:40 (try 1/3)
[   28.266071] wlan2: RX AssocResp from 00:1d:d3:53:7b:40 (capab=0x11 status=0 aid=2)
[   28.266444] wlan2: associated
[   28.266457] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  124.325435] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  249.098684] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  374.492592] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  499.057441] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  624.610373] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  749.174033] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  797.462784] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.239 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29828 PROTO=TCP SPT=443 DPT=40662 WINDOW=0 RES=0x00 RST URGP=0 
[  797.465789] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.239 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29829 PROTO=TCP SPT=443 DPT=40662 WINDOW=0 RES=0x00 RST URGP=0 
[  797.467853] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.239 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29980 PROTO=TCP SPT=443 DPT=40659 WINDOW=0 RES=0x00 RST URGP=0 
[  797.474179] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.239 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29981 PROTO=TCP SPT=443 DPT=40659 WINDOW=0 RES=0x00 RST URGP=0 
[  797.478094] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.239 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29982 PROTO=TCP SPT=443 DPT=40659 WINDOW=0 RES=0x00 RST URGP=0 
[  798.367996] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.168 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=6233 PROTO=TCP SPT=443 DPT=60541 WINDOW=0 RES=0x00 RST URGP=0 
[  798.370929] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.168 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=6234 PROTO=TCP SPT=443 DPT=60541 WINDOW=0 RES=0x00 RST URGP=0 
[  798.373787] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.168 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=6235 PROTO=TCP SPT=443 DPT=60541 WINDOW=0 RES=0x00 RST URGP=0 
[  798.379510] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.239 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=50344 PROTO=TCP SPT=443 DPT=40661 WINDOW=0 RES=0x00 RST URGP=0 
[  798.381683] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.239 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=50345 PROTO=TCP SPT=443 DPT=40661 WINDOW=0 RES=0x00 RST URGP=0 
[  874.739484] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  999.062410] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1124.248897] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1249.745081] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1374.247034] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1499.758073] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1624.249357] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1749.760709] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1874.252232] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1999.763562] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2124.255177] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2249.756540] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2374.257900] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2499.759274] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2624.260945] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2749.762219] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2874.273715] [UFW BLOCK] IN=wlan2 OUT= MAC=00:e0:12:05:05:50:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 

$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan2
       version: 00
       serial: 00:e0:12:05:05:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=3.11.0-18-generic firmware=0.8 ip=10.0.0.6 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:df9f8000-df9fffff 

$ iwlist scan
wlan2     Scan completed :
          Cell 01 - Address: 00:1D:D3:53:7B:40
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"HOME-7B42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f96156df69
                    Extra: Last beacon: 22908ms ago
                    IE: Unknown: 0009484F4D452D37423432
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503001E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880001DD3537B4010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120

$ lsb_release -d
Description:    Ubuntu 13.10

$ uname -mr
3.11.0-18-generic i686

$ sudo service networking restart
networking stop/waiting
networking start/running


```
The last command crashed my system, but I managed to get the readout anyway.  I know this is a lot of information, but I hope someone can now point me in the right direction. 
Thanks.

---

### Post by varunendra on 2014-03-10
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by flyfisherbryan on 2014-03-10
Thank you for looking at my problem.  Here are the results of the wireless script:
```

*************** info trace ***************

***** uname -a *****

Linux 2OS 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:13:28 UTC 2014 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
    Subsystem: Dell OptiPlex 745 [1028:01da]
    Kernel driver in use: tg3
04:00.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Ralink corp. EW-7108PCg/EW-7128g [1814:2561]
    Kernel driver in use: rt61pci

***** lsusb *****

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 006 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan2     IEEE 802.11bg  ESSID:"HOME-7B42"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1027  Invalid misc:48146   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan2
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan2

***** lsmod *****

rt61pci                27296  0 
rt2x00pci              13111  1 rt61pci
rt2x00mmio             13395  1 rt61pci
rt2x00lib              48933  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              517444  2 rt2x00lib,rt2x00pci
cfg80211              401762  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt61pci
crc_itu_t              12627  1 rt61pci

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan2  [HOME-7B42 1] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    *HOME-7B42:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2
    THECHOSENONE:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    HOME-48B2:       Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    xfinitywifi:     Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 47
    NETGEAR91:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA2

  IPv4 Settings:
    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan2     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"HOME-7B42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002060f4ff104
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0009484F4D452D37423432
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503001E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880001DD3537B4010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"THECHOSENONE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000114fdbe294
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000C54484543484F53454E4F4E45
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD840050F204104A0001101044000102103B000103104700100000000000001000000030469A154AB61021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110015574E44523337303028576972656C65737320415029100800020086103C000103
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ERROR: PLEASE CONTACT YOUR ISP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000657e38fd8
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001E4552524F523A20504C4541534520434F4E5441435420594F555220495350
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002060f346d2e
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030021127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002060f4c1c00
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503001E127A
                    IE: Unknown: DD07000C4303000000
          Cell 06 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR91"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011878efbcfc
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00094E4554474541523931
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010000000000000100000002CB05D89E14A102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"06B411964070"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001187ce20237
                    Extra: Last beacon: 832ms ago
                    IE: Unknown: 000C303642343131393634303730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 08 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HOME-48B2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000118783b50f6
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0009484F4D452D34384232
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010010127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880E8892CF648B010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 09 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000118783b8767
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010010127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
          Cell 10 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000118783b6fd0
                    Extra: Last beacon: 744ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010010127A
                    IE: Unknown: DD07000C4303000000
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"tom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001187d127177
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0003746F6D
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406010200000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C


***** resolv.conf *****

nameserver 127.0.1.1
search hsd1.ny.comcast.net

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF4BCBAB2D8E09C275F85E4
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8422005AAAD8B7D2F811DC4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2C5ADAF564EF1DAD569D9C3
depends:        rt2x00lib
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EB7C454417ADECB5D8A7F2A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x167a (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x1814:0x0301 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

***** dmesg *****

[   16.918586] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2561, rf: 0003, rev: 000c
[   24.412115] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   24.412664] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   24.414887] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2561s.bin'
[   24.441216] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.8
[   24.485527] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   24.486016] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   26.920934] wlan2: authenticate with <MAC address removed>
[   26.932027] wlan2: send auth to <MAC address removed> (try 1/3)
[   26.933759] wlan2: authenticated
[   26.936069] wlan2: associate with <MAC address removed> (try 1/3)
[   26.939013] wlan2: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[   26.939790] wlan2: associated
[   26.939807] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[   35.620027] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  160.967419] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  286.526397] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  324.023535] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=23.48.50.110 DST=10.0.0.6 LEN=79 TOS=0x00 PREC=0x20 TTL=59 ID=51498 DF PROTO=TCP SPT=443 DPT=45777 WINDOW=8991 RES=0x00 ACK PSH URGP=0 
[  324.490642] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=23.48.50.110 DST=10.0.0.6 LEN=79 TOS=0x00 PREC=0x20 TTL=59 ID=51500 DF PROTO=TCP SPT=443 DPT=45777 WINDOW=8991 RES=0x00 ACK PSH URGP=0 
[  325.402787] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=46680 DF PROTO=TCP SPT=443 DPT=43903 WINDOW=9149 RES=0x00 ACK PSH URGP=0 
[  325.409728] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=61934 DF PROTO=TCP SPT=443 DPT=43902 WINDOW=9213 RES=0x00 ACK PSH URGP=0 
[  325.425504] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=23.48.50.110 DST=10.0.0.6 LEN=79 TOS=0x00 PREC=0x20 TTL=59 ID=51501 DF PROTO=TCP SPT=443 DPT=45777 WINDOW=8991 RES=0x00 ACK PSH URGP=0 
[  325.724629] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=61936 DF PROTO=TCP SPT=443 DPT=43902 WINDOW=9213 RES=0x00 ACK PSH URGP=0 
[  325.788615] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=46682 DF PROTO=TCP SPT=443 DPT=43903 WINDOW=9149 RES=0x00 ACK PSH URGP=0 
[  326.051487] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=61937 DF PROTO=TCP SPT=443 DPT=43902 WINDOW=9213 RES=0x00 ACK PSH URGP=0 
[  326.180707] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=46683 DF PROTO=TCP SPT=443 DPT=43903 WINDOW=9149 RES=0x00 ACK PSH URGP=0 
[  326.501733] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=61938 DF PROTO=TCP SPT=443 DPT=43902 WINDOW=9213 RES=0x00 ACK PSH URGP=0 
[  345.873577] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=61946 DF PROTO=TCP SPT=443 DPT=43902 WINDOW=9213 RES=0x00 ACK PSH URGP=0 
[  365.547675] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=46693 DF PROTO=TCP SPT=443 DPT=43903 WINDOW=9149 RES=0x00 ACK PSH URGP=0 
[  396.282427] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=61950 DF PROTO=TCP SPT=443 DPT=43902 WINDOW=9213 RES=0x00 ACK PSH URGP=0 
[  411.090550] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  431.627425] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=184.25.109.25 DST=10.0.0.6 LEN=105 TOS=0x00 PREC=0x20 TTL=59 ID=46696 DF PROTO=TCP SPT=443 DPT=43903 WINDOW=9149 RES=0x00 ACK PSH URGP=0 
[  536.659236] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  661.228491] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  786.792557] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  911.350606] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1036.831796] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1161.353186] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1286.854449] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1411.355897] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1536.857274] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1661.358937] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1786.860373] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 1911.368962] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2036.863009] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2161.365021] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2286.873620] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2411.367436] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2536.868741] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2661.370266] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2786.871562] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2911.383327] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3036.754759] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3160.875762] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3286.377597] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3411.149392] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3536.380365] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3660.890344] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3786.382969] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3910.884167] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3921.350500] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=173.194.43.50 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29858 PROTO=TCP SPT=443 DPT=34149 WINDOW=0 RES=0x00 RST URGP=0 
[ 3925.305256] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.14 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=51294 PROTO=TCP SPT=443 DPT=52330 WINDOW=0 RES=0x00 RST URGP=0 
[ 3925.308013] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.14 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=51295 PROTO=TCP SPT=443 DPT=52330 WINDOW=0 RES=0x00 RST URGP=0 
[ 3925.310569] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.14 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=51296 PROTO=TCP SPT=443 DPT=52330 WINDOW=0 RES=0x00 RST URGP=0 
[ 3925.319119] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.1 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=38138 PROTO=TCP SPT=443 DPT=45105 WINDOW=0 RES=0x00 RST URGP=0 
[ 3925.323456] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.1 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=38139 PROTO=TCP SPT=443 DPT=45105 WINDOW=0 RES=0x00 RST URGP=0 
[ 3925.327078] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.1 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=38140 PROTO=TCP SPT=443 DPT=45105 WINDOW=0 RES=0x00 RST URGP=0 
[ 3927.312496] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.76 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=52761 PROTO=TCP SPT=443 DPT=37264 WINDOW=0 RES=0x00 RST URGP=0 
[ 3927.318117] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.76 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=52762 PROTO=TCP SPT=443 DPT=37264 WINDOW=0 RES=0x00 RST URGP=0 
[ 3927.320707] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.76 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=52760 PROTO=TCP SPT=443 DPT=37264 WINDOW=0 RES=0x00 RST URGP=0 
[ 4036.395720] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4160.887135] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4286.388488] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4410.899793] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4536.899918] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4785.894229] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4911.395612] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5035.896954] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5161.398404] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5285.900008] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5411.401278] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5535.903502] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5661.404784] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5785.911377] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 5911.418082] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6035.909416] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6161.420819] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6285.922073] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6411.423174] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6535.998386] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6661.426304] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6785.908732] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 6911.419239] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 7035.930897] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 7161.432307] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 7285.933685] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 7411.455035] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 7535.936699] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 7785.942907] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 7911.440930] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8035.942334] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8161.446140] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8285.944973] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8411.446400] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8535.947761] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8661.449626] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8785.951852] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 8911.452281] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9035.953497] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9161.456335] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9285.956354] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9411.468437] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9535.963886] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9661.462520] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9785.962398] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 9911.466336] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10035.964864] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10161.486195] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10286.787454] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10410.978806] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10412.236790] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=134.170.18.203 DST=10.0.0.6 LEN=337 TOS=0x00 PREC=0x20 TTL=115 ID=21538 DF PROTO=TCP SPT=443 DPT=40282 WINDOW=65133 RES=0x00 ACK PSH URGP=0 
[10498.072747] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.242 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=56554 PROTO=TCP SPT=443 DPT=37659 WINDOW=0 RES=0x00 RST URGP=0 
[10498.076317] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.242 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=56555 PROTO=TCP SPT=443 DPT=37659 WINDOW=0 RES=0x00 RST URGP=0 
[10498.080943] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.242 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=56556 PROTO=TCP SPT=443 DPT=37659 WINDOW=0 RES=0x00 RST URGP=0 
[10499.024542] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.79 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=49398 PROTO=TCP SPT=443 DPT=38322 WINDOW=0 RES=0x00 RST URGP=0 
[10499.027950] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.79 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=49399 PROTO=TCP SPT=443 DPT=38322 WINDOW=0 RES=0x00 RST URGP=0 
[10499.032995] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.79 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=49400 PROTO=TCP SPT=443 DPT=38322 WINDOW=0 RES=0x00 RST URGP=0 
[10500.062373] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.7 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29710 PROTO=TCP SPT=443 DPT=60505 WINDOW=0 RES=0x00 RST URGP=0 
[10500.065962] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.7 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29711 PROTO=TCP SPT=443 DPT=60505 WINDOW=0 RES=0x00 RST URGP=0 
[10500.070188] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.7 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=29712 PROTO=TCP SPT=443 DPT=60505 WINDOW=0 RES=0x00 RST URGP=0 
[10500.120523] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.245 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=51213 PROTO=TCP SPT=443 DPT=41172 WINDOW=0 RES=0x00 RST URGP=0 
[10536.470266] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10660.971605] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10786.474796] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[10910.974840] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11036.475407] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11160.976865] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11286.478547] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11410.979794] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11536.481231] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11661.062649] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11786.489593] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11910.986109] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12036.490185] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12160.991491] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12286.490341] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12410.991543] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12536.492937] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12661.006961] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12786.495844] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[12910.998106] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13036.509666] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13161.000328] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13286.512983] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13411.013117] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13536.514606] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13661.020381] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13786.517814] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[13911.019176] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14036.521167] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14161.022671] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14286.524143] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14411.025178] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14536.546630] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14661.028192] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14786.531240] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[14911.031313] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15036.532616] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15161.034130] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15286.535627] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15411.037306] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15536.539296] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15661.044730] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15786.541659] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[15911.043210] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16036.548545] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16161.049185] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16286.548091] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16411.049231] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16536.078145] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16661.552342] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16786.053762] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[16911.565296] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17036.056671] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17161.558252] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17286.709965] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17411.711361] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17536.762929] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17660.844353] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17785.905706] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[17911.007442] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18036.009032] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18161.080376] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18286.141923] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18411.143562] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18536.265015] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18661.326563] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18786.397894] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[18911.469500] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[19036.512780] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[19161.532760] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[19286.654057] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[19411.681362] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[19536.737087] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[19785.820302] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[19910.871529] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20035.923296] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20160.935142] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20286.006333] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20411.011324] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20536.029322] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20661.120742] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20786.132330] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[20911.193920] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21036.195339] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21161.266867] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21286.308367] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21411.380047] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21536.431575] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21661.482938] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21786.535071] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[21911.617350] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22036.677787] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22161.719634] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22285.800888] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22410.802264] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22535.903853] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22660.945489] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22785.947009] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[22911.008508] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23036.041042] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23161.091498] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23286.153189] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23411.154812] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23536.226206] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23661.307609] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23786.369398] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[23911.460852] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24036.542282] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24161.614012] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24286.625682] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24411.677292] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24536.708605] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24661.710926] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24786.731688] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[24910.813465] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25035.904598] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25160.906288] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25285.937900] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25410.959370] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25535.980808] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25661.022261] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25786.094690] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[25911.136193] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26036.217683] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26161.309098] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26286.351630] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26411.401908] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26536.403403] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26661.457421] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26786.578053] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[26911.650579] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27036.669676] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27161.731244] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27286.732788] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27410.774893] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27535.806339] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27660.889619] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27785.959421] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[27911.054919] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28036.122389] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28161.220204] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28286.215245] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28411.216735] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28536.288511] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28661.310317] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28786.377348] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[28911.408773] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29036.444687] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29161.526714] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29286.638099] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29411.669416] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29535.750758] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29660.753753] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29785.844230] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[29910.875807] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30035.897319] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30160.904006] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30285.935538] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30410.942123] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30535.943711] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30661.029742] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30786.136733] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30911.178305] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31036.230002] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31161.257906] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31286.332999] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31411.404765] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31536.496172] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31661.528222] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31786.549515] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31911.552241] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32036.582592] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32161.604576] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32286.625977] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32411.697428] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32535.798925] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32660.900610] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32785.932148] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32910.984408] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33035.995852] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33161.017301] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33286.028931] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33411.106935] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33536.121741] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33661.193280] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33786.305038] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[33911.336495] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34036.348145] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34161.459818] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34286.531726] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34411.552726] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34536.654412] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34661.667799] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34786.669493] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[34911.671003] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35035.761268] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35160.793027] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35285.794223] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35410.795683] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35535.857166] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35660.888784] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35785.890441] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[35910.916316] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36036.003555] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36161.085172] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36286.156789] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36411.198984] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36536.302993] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36661.352154] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36786.393879] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[36911.465575] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37036.547210] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37161.618679] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37286.680355] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37411.713998] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37535.763283] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37660.854629] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37785.906283] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[37910.927787] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38035.959410] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38160.990979] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38286.002657] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38411.024165] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38536.055795] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38663.454269] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38786.131614] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[38911.210743] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39036.212200] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39161.313813] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39286.395413] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39411.477358] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39536.523274] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39661.580360] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39786.612188] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[39911.623444] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40036.685755] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40160.777427] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40285.798771] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40410.840591] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40535.882185] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40660.926200] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40785.934828] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[40910.946552] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41035.978018] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41160.980083] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41285.991565] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41411.052995] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41536.124583] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41661.176257] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41786.187762] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[41911.299953] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42036.321141] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42161.412817] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42286.424453] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42411.426151] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42536.517730] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42661.519295] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42786.591009] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[42911.632448] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[43035.734724] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[43160.786274] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[43285.887873] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[43410.939428] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[43536.042108] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[43786.194048] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[43911.289427] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44036.307426] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44161.309067] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44286.360546] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44411.452180] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44536.453853] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44661.505416] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44786.528525] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[44911.609195] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45036.650840] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45160.742349] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45285.824035] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45410.905855] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45536.238604] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45661.088386] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45786.110181] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[45911.211710] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46036.303625] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46161.305324] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46286.386497] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46411.458451] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46536.479847] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46661.501191] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46786.563750] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[46911.655215] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47036.179074] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47161.218499] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47286.309935] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47411.351788] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47536.413000] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47661.504771] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47786.556325] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[47911.597949] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48036.659492] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48160.730855] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48285.742086] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48410.773577] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48535.804758] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48661.535971] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48786.648134] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[48911.069232] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[49036.579634] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[49161.070772] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[49286.572095] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[49411.073136] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[49536.574300] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[49786.577320] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[49910.978382] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50036.089500] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50161.580853] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50286.081784] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50411.592960] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50536.094156] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50661.595449] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50786.096710] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[50911.598165] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51036.099234] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51161.600156] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51286.101632] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51411.602947] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51536.104084] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51661.605350] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51786.112481] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[51911.607795] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52036.109248] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52161.613902] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52286.111953] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52411.613238] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52536.114643] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52661.617480] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52749.946473] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.73 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=17327 PROTO=TCP SPT=443 DPT=34201 WINDOW=0 RES=0x00 RST URGP=0 
[52749.949114] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.73 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=17329 PROTO=TCP SPT=443 DPT=34201 WINDOW=0 RES=0x00 RST URGP=0 
[52750.942062] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.230 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=12096 PROTO=TCP SPT=443 DPT=59604 WINDOW=0 RES=0x00 RST URGP=0 
[52750.977951] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.230 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=12097 PROTO=TCP SPT=443 DPT=59604 WINDOW=0 RES=0x00 RST URGP=0 
[52756.942494] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.73 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=59114 PROTO=TCP SPT=443 DPT=34199 WINDOW=0 RES=0x00 RST URGP=0 
[52756.945958] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.73 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=59115 PROTO=TCP SPT=443 DPT=34199 WINDOW=0 RES=0x00 RST URGP=0 
[52756.949229] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.73 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=59116 PROTO=TCP SPT=443 DPT=34199 WINDOW=0 RES=0x00 RST URGP=0 
[52757.944811] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.175 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=9972 PROTO=TCP SPT=443 DPT=53111 WINDOW=0 RES=0x00 RST URGP=0 
[52757.946792] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.175 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=9973 PROTO=TCP SPT=443 DPT=53111 WINDOW=0 RES=0x00 RST URGP=0 
[52757.949832] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.175 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=9974 PROTO=TCP SPT=443 DPT=53111 WINDOW=0 RES=0x00 RST URGP=0 
[52770.544143] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.240 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=52944 PROTO=TCP SPT=443 DPT=60500 WINDOW=0 RES=0x00 RST URGP=0 
[52786.363563] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[52845.006108] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.230 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=56784 PROTO=TCP SPT=443 DPT=59602 WINDOW=0 RES=0x00 RST URGP=0 
[52845.008366] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.230 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=56785 PROTO=TCP SPT=443 DPT=59602 WINDOW=0 RES=0x00 RST URGP=0 
[52845.012200] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.230 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=56786 PROTO=TCP SPT=443 DPT=59602 WINDOW=0 RES=0x00 RST URGP=0 
[52861.020614] [UFW BLOCK] IN=wlan2 OUT= MAC=<MAC address removed>:00:1d:d3:53:7b:41:08:00 SRC=74.125.226.236 DST=10.0.0.6 LEN=40 TOS=0x00 PREC=0x20 TTL=54 ID=23763 PROTO=TCP SPT=443 DPT=48389 WINDOW=0 RES=0x00 RST URGP=0 

****************** done ******************


```
Thank You!

---

### Post by varunendra on 2014-03-10
Have you purposefully enabled UFW (Ubuntu FireWall)? Have you configured it properly? As you can see, there is a whole river of blocked packets as per dmesg.

If you are not sure, I'd suggest to disable it -
```
sudo ufw disable
```

Apart from this, your router is currently using the dreaded WPA/WPA2 mixed mode with TKIP. Please change it to pure WPA2-AES (CCMP). No mixed mode, no TKIP!
Reboot the router after saving any changes.

If this doesn't help, additionally try this in Ubuntu -
```
echo "options rt61pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt61pci.conf
```
This will create a .conf file that will shift the packet encryption from hardware to software. To let this change take effect, either reboot or manually reload the driver -
```
sudo modprobe -rv rt61pci
sudo modprobe -v rt61pci
```

Then retry to connect and check -
```
iwconfig
```
Is the connection speed better now? Practical transfer speeds?

---

### Post by flyfisherbryan on 2014-03-10
I did everything you said and I still have the problem.  Even though I had said in my original post I had tried it with ufw disabled, I tried it again.  I thought that the default configuration of ufw was good for an average user so that is what I am using.  I changed my router's security settings and ran the other command you sent, yet still:

```
$ iwconfig
wlan2     IEEE 802.11bg  ESSID:"HOME-7B42"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1D:D3:53:7B:40   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:107  Invalid misc:7656   Missed beacon:0


```
If you can think of anything else, I will try it.  If not, I will contact the manufactyrer and let you know what they say.

Thanks for the help,   Bryan

---

### Post by varunendra on 2014-03-10
All the manufacturers have one exactly same thing to say - "We don't support Linux" ;)

And the default setting of almost all specialized firewalls is to block 'Everything', unless selectively allowed by the user. If you don't know how to configure UFW, keep it disabled. Ubuntu or any Linux distro is secure enough without added firewall rules for most people. You really need it only when you are using it for remote access or as a server and have opened some extra ports for those purposes. (I'm not an expert of software firewalls in Ubuntu, but I do know this much).

Please try -
```
sudo iwconfig wlan2 rate 48M
```
Does it stick? The other supported bit rates (higher than 11M) are : 18M, 24M, 36M, 54M which you can try instead of 48M.

If it does not accept the forced speed, or becomes worse with them, please post a fresh report of wireless script, plus the output of -
```
grep [[:alnum:]] /sys/module/rt61pci/parameters/*
```

---

### Post by flyfisherbryan on 2014-03-10
> All the manufacturers have one exactly same thing to say - "We don't support Linux" :wink:
In this cae that is simply _not_ true.  The manufacturer of this card lists Linux in it's adverts,has Linux drivers on it's web site, and has the word Linux on the box the card came in!  They can't say that.

Trying to force a speed change changed what the display said, but then I had no connection.  I re-started the computer and the setting reverted to 11.

Here are the new wireless script results:
```

*************** info trace ***************

***** uname -a *****

Linux 2OS 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:13:28 UTC 2014 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
    Subsystem: Dell OptiPlex 745 [1028:01da]
    Kernel driver in use: tg3
04:00.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Ralink corp. EW-7108PCg/EW-7128g [1814:2561]
    Kernel driver in use: rt61pci

***** lsusb *****

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 006 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan2     IEEE 802.11bg  ESSID:"HOME-7B42"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC address removed>   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:116  Invalid misc:3634   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan2
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan2

***** lsmod *****

rt61pci                27296  0 
rt2x00pci              13111  1 rt61pci
rt2x00mmio             13395  1 rt61pci
rt2x00lib              48933  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              517444  2 rt2x00lib,rt2x00pci
cfg80211              401762  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt61pci
crc_itu_t              12627  1 rt61pci

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan2  [HOME-7B42 1] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NETGEAR91:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 57 WPA2
    THECHOSENONE:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    ERROR: PLEASE CONTACT YOUR ISP: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    HOME-48B2:       Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    xfinitywifi:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100
    xfinitywifi:     Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 37
    *HOME-7B42:      Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 82 WPA2
    06B411964070:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP

  IPv4 Settings:
    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan2     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"HOME-7B42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000189f0eebb
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0009484F4D452D37423432
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030016127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880001DD3537B4010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000189ed5af1
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030016127A
                    IE: Unknown: DD07000C4303000000
          Cell 03 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000189d9f6bd
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030016127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ERROR: PLEASE CONTACT YOUR ISP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000115730f71
                    Extra: Last beacon: 14852ms ago
                    IE: Unknown: 001E4552524F523A20504C4541534520434F4E5441435420594F555220495350
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"THECHOSENONE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013dd77aef5
                    Extra: Last beacon: 1716ms ago
                    IE: Unknown: 000C54484543484F53454E4F4E45
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD840050F204104A0001101044000102103B000103104700100000000000001000000030469A154AB61021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110015574E44523337303028576972656C65737320415029100800020086103C000103
          Cell 06 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR91"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011b076eebe5
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00094E4554474541523931
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010000000000000100000002CB05D89E14A102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
          Cell 07 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HOME-48B2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011b06b96270
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 0009484F4D452D34384232
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010010127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880E8892CF648B010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 08 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011b06b991ee
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010010127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
          Cell 09 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s


***** resolv.conf *****

nameserver 127.0.1.1
search hsd1.ny.comcast.net

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF4BCBAB2D8E09C275F85E4
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8422005AAAD8B7D2F811DC4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2C5ADAF564EF1DAD569D9C3
depends:        rt2x00lib
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EB7C454417ADECB5D8A7F2A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x167a (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x1814:0x0301 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

***** dmesg *****

[   17.001286] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2561, rf: 0003, rev: 000c
[   24.284267] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   24.284875] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   24.287269] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2561s.bin'
[   24.338681] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.8
[   24.381439] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   24.381947] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   26.708788] wlan2: authenticate with <MAC address removed>
[   26.729423] wlan2: send auth to <MAC address removed> (try 1/3)
[   26.731594] wlan2: authenticated
[   26.732059] wlan2: associate with <MAC address removed> (try 1/3)
[   26.736760] wlan2: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   26.737108] wlan2: associated
[   26.737123] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready

****************** done ******************


``` 

And the result of the new line you gave me:

```
grep [[:alnum:]] /sys/module/rt61pci/parameters/*
Y

```

Thanks for spending so much time on my problem.

---

### Post by chili555 on 2014-03-10
> The manufacturer of this card lists Linux in it's adverts,has Linux drivers on it's web site, and has the word Linux on the box the card came in! **They can't say that.**I'll wager that they can and they do. Varun and I await your report.

Is the 2.4 GHz band in your N-capable router set to use channel width of 20 MHz, 40 MHz or mixed? You may find that 20 MHz only works better. [http://www5.pcmag.com/media/images/349131-channel-width.jpg?thumb=y](http://www5.pcmag.com/media/images/349131-channel-width.jpg?thumb=y)

I didn't want to step on Varun's toes, but when I read, "They can't say that," I was powerless to stop myself!

---

### Post by varunendra on 2014-03-10
Glad to know you found a vendor who explicitly supports Linux and even advertises it. Hope they keep up with the support. :)

Onto the problem - two neighboring access-points with same signal strength (are they yours?) are also using the same channel which you have changed to - channel 2. This may cause mutual interference causing problems.

I suggest you change to channel 1 or 11, save and reboot the router. If this doesn't improve the speed, try a newer, backported driver as suggested in this post : [http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696](http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696)

If it installed smoothly, test it and let me know if there is any positive difference. There is an even newer backports package (as you can notice yourself on the download page), but the drivers that I have tested so far from this version have all performed better than those in 3.11 (your current version). So try this one first. We can try the latest one as our 'Last shot'.

**EDIT:**
Oops! My master is here. :D
Sorry doc, at 1 KB/s speed (yeah!!) it takes multiple refreshes plus some dancing around the laptop before a post gets through.. I'm only 15 min late it seems :P

---

### Post by flyfisherbryan on 2014-03-10
No go.  It still doesn't work correctly.  How do I install newer driver?  Same commands with version numbers changed?

---

### Post by varunendra on 2014-03-10
Please confirm everything you confirmed/tried so far from what was suggested in the two posts above yours, just so that we can be specific.

A detailed feedback of all the options attempted/kept/discarded is VERY important and useful for us to keep ourselves up-to-date on what works and what doesn't.

So please share with us everything you have tried from the above suggestions, as well as something else that maybe significant but not mentioned here so far. Thanks! :)

---

### Post by flyfisherbryan on 2014-03-11
I have tried everything above in the order they appear, and tested after each.  Manually changing the speed changed the display in Terminal to 48, but the GUI still said 11 and the speed did not change.  I installed this card because my[SIZE=2] Netgear Wireless USB Micro WNA1000M[/SIZE] was unreliable.  Although it ran at 65Mb/s it would often drop the connection (5-10 times a day).  In desperation I put this back in and after all the things we did to the router (and maybe the drivers?) it is now running at 135 Mb/s and has not dropped the connection yet!  Perhaps I am going back to this.  I will call the manufacturer tomorrow and see what they have to say.  Still if you have any other suggaestions I will try them, if only to solve the issue so we know the answer.  Thanks again!

---

### Post by flyfisherbryan on 2014-03-16
When I got a chance, I installed this card on a Windows machine and had the same problem.  It is a hardware problem and I will be returning the card.  But it has been 4 or 5 days and my Netgear[SIZE=2] Wireless USB Micro WNA1000M[/SIZE] is working perfectly.  Speed has doubled and I have not lost the connection once!  So all the changes I made were not in vain.  I assume this was with the changes I made to my router security settings, but I am not sure.  So... Thanks for all your help, sorry I did not try to test the hardware first, but I am happy my connection is working better than ever!

---

