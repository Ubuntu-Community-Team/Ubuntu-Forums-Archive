---
title: "Upgraded 14.04 to 14.10 and Wi-Fi times out authenticating (BCM4331 and RTL8188C)"
date: 2014-11-16
forum: Networking &amp; Wireless
---

### Post by Shane_Farmer on 2014-11-16
Hi All,

After upgrading my Mac Mini last night to 14.10 (from 14.04) I can no longer connect to authenticated networks. I am able to connect to unauthenticated networks and use a USB tethered phone, but connectings to my router drop out or don't connect at all. My machine has the BCM Wi-Fi card plus a USB dongle that both fail. This has been working fine while using 14.04 but broke as soon as upgrading. Does anyone have an idea what would have changed? I reinstalled the B43 firmware and it did not have any affect. I can scan for networks and the only issue seems to be with the WPA authentication.

The output from dmesg for built in (BCM4331):
```
[   18.851499] wlan0: authenticate with 28:cf:da:b0:1c:83
[   18.871219] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 1/3)
[   19.074768] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 2/3)
[   19.278714] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 3/3)
[   19.482609] wlan0: authentication with 28:cf:da:b0:1c:83 timed out
[   20.831196] wlan0: authenticate with 28:cf:da:b0:1c:83
[   20.850148] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 1/3)
[   21.053756] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 2/3)
[   21.257652] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 3/3)
[   21.461596] wlan0: authentication with 28:cf:da:b0:1c:83 timed out
[   23.317682] wlan0: authenticate with 28:cf:da:b0:1c:83
[   23.337358] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 1/3)
[   23.540928] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 2/3)
[   23.744942] wlan0: direct probe to 28:cf:da:b0:1c:83 (try 3/3)
[   23.948980] wlan0: authentication with 28:cf:da:b0:1c:83 timed out

```

The output from dmesg for USB dongle (RTL8188):
```

[10406.663590] usb 3-4: new high-speed USB device number 12 using xhci_hcd
[10406.792968] usb 3-4: New USB device found, idVendor=7392, idProduct=7811
[10406.792975] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10406.792979] usb 3-4: Product: 802.11n WLAN Adapter
[10406.792982] usb 3-4: Manufacturer: Realtek
[10406.792984] usb 3-4: SerialNumber: 00e04c000001
[10406.793692] rtl8192cu: Chip version 0x10
[10406.826472] rtl8192cu: MAC address: 80:1f:02:b6:d8:05
[10406.826477] rtl8192cu: Board Type 0
[10406.826548] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[10406.826587] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[10406.826992] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[10406.827668] rtlwifi: wireless switch is on
[10407.845146] rtl8192cu: MAC auto ON okay!
[10407.857870] rtl8192cu: Tx queue select: 0x05
[10408.204636] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[10408.404479] userif-3: sent link down event.
[10408.404484] userif-3: sent link up event.
[10409.650927] wlan1: authenticate with 28:cf:da:b0:1c:83
[10409.672056] wlan1: direct probe to 28:cf:da:b0:1c:83 (try 1/3)
[10409.873984] wlan1: send auth to 28:cf:da:b0:1c:83 (try 2/3)
[10409.877191] wlan1: authenticated
[10409.877947] wlan1: associate with 28:cf:da:b0:1c:83 (try 1/3)
[10409.903224] wlan1: RX AssocResp from 28:cf:da:b0:1c:83 (capab=0x1431 status=0 aid=3)
[10409.903315] wlan1: associated
[10409.903326] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[10410.919549] wlan1: deauthenticating from 28:cf:da:b0:1c:83 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[10410.931105] wlan1: authenticate with 28:cf:da:b0:1c:83
[10410.941896] wlan1: send auth to 28:cf:da:b0:1c:83 (try 1/3)
[10410.959879] wlan1: authenticated
[10410.961438] wlan1: associate with 28:cf:da:b0:1c:83 (try 1/3)
[10411.004482] wlan1: RX AssocResp from 28:cf:da:b0:1c:83 (capab=0x1431 status=0 aid=3)
[10411.004543] wlan1: associated
[10411.118816] userif-3: sent link down event.
[10411.118821] userif-3: sent link up event.
[10412.238252] userif-3: sent link down event.
[10412.238257] userif-3: sent link up event.
[10517.907452] wlan0: deauthenticated from 02:1a:11:fc:ca:b6 (Reason: 3=DEAUTH_LEAVING)
[10517.907826] bridge-wlan0: disabling the bridge
[10517.917203] bridge-wlan0: down
[10517.917215] bridge-wlan0: detached

```

Wireless info output when both wifi adapters are present
```


########## wireless info START ##########

Report from: 16 Nov 2014 13:50 PST -0800

Booted last: 16 Nov 2014 10:56 PST -0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:07:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

\boot\vmlinuz-3.16.0-24-generic, ro, initrd=boot\initrd.img-3.16.0-24-generic

##### desktop ###########################

Ubuntu Studio

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)
    Subsystem: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:010e]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 005: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 008: ID 05ac:828a Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 003 Device 003: ID 0925:3881 Lakeview Research Saleae Logic
Bus 003 Device 010: ID 05ac:9226 Apple, Inc. LED Cinema Display
Bus 003 Device 009: ID 05ac:8508 Apple, Inc. iSight in LED Cinema Display
Bus 003 Device 008: ID 05ac:1105 Apple, Inc. Audio in LED Cinema Display
Bus 003 Device 007: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 006: ID 046d:c245 Logitech, Inc. G400 Optical Mouse
Bus 003 Device 002: ID 05ac:9126 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              67670  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                64237  2 rtl_usb,rtl8192cu
rtl8192c_common        53170  1 rtl8192cu
b43                   400218  0 
mac80211              660592  4 b43,rtl_usb,rtlwifi,rtl8192cu
cfg80211              510218  3 b43,mac80211,rtlwifi
ssb                    62366  1 b43
bcma                   52443  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF]>  
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:172.16.57.1  Bcast:172.16.57.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.176.1  Bcast:172.16.176.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.43.108  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::2acf:e9ff:fe01:85e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13325855 (13.3 MB)  TX bytes:3536851 (3.5 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:10.1.10.20  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:feb6:d805/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1840 (1.8 KB)  TX bytes:10354 (10.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

vmnet1    no wireless extensions.

docker0   no wireless extensions.

vmnet8    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Mobile Wombat clear"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Mobile Wombat clear' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:196  Invalid misc:5490   Missed beacon:0

wlan1     IEEE 802.11bgn  ESSID:"wombat"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'wombat' [AC5]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 wlan0
10.1.10.0       0.0.0.0         255.255.255.0   U     9      0        0 wlan1
172.16.57.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.176.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.43.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search wp.comcast.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan1  [wombat (dongle)] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-96D2:       Infra, <MAC 'HOME-96D2' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    Jackson:         Infra, <MAC 'Jackson' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    HOME-C847:       Infra, <MAC 'HOME-C847' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    James Franco:    Infra, <MAC 'James Franco' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    SF Smash:        Infra, <MAC 'SF Smash' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    onlyifyouhaveto: Infra, <MAC '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    HOME-6592:       Infra, <MAC 'HOME-6592' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Karyn:           Infra, <MAC 'Karyn' [AC15]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    JulietLynne's Network: Infra, <MAC 'JulietLynne's Network' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Mobile Wombat clear: Infra, <MAC 'Mobile Wombat clear' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    *wombat:         Infra, <MAC 'wombat' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 WPA2
    SUCETTE:         Infra, <MAC 'SUCETTE' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2

  IPv4 Settings:
    Address:         10.1.10.20
    Prefix:          24 (255.255.255.0)
    Gateway:         10.1.10.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: wlan0  [Mobile Wombat clear] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Jackson:         Infra, <MAC 'Jackson' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    HOME-96D2:       Infra, <MAC 'HOME-96D2' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    James Franco:    Infra, <MAC 'James Franco' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA2
    SUCETTE:         Infra, <MAC 'SUCETTE' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    Nation:          Infra, <MAC 'SUCETTE' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    HOME-6592:       Infra, <MAC 'HOME-6592' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    HOME-4142:       Infra, <MAC 'HOME-4142' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    admin:           Infra, <MAC 'HOME-4142' [AN25]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    xfinitywifi:     Infra, <MAC 'admin' [AN26]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    JulietLynne's Network: Infra, <MAC 'JulietLynne's Network' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HOME-1B38:       Infra, <MAC 'HOME-1B38' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Tread Lightlier: Infra, <MAC 'Tread Lightlier' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Nation:          Infra, <MAC 'Nation' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    wombat:          Infra, <MAC 'wombat' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA2
    monolith2.4:     Infra, <MAC 'wombat' [AN32]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    *Mobile Wombat clear: Infra, <MAC 'Mobile Wombat clear' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85
    sfhome:          Infra, <MAC 'sfhome' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    NETGEAR99:       Infra, <MAC 'sfhome' [AN35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    EP:              Infra, <MAC 'NETGEAR99' [AN36]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    SF Smash:        Infra, <MAC 'SF Smash' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA
    Monkey:          Infra, <MAC 'Monkey' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    HOME-5652:       Infra, <MAC 'Monkey' [AN39]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2

  IPv4 Settings:
    Address:         192.168.43.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1

    DNS:             192.168.43.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

[[/etc/NetworkManager/system-connections/Mobile Wombat]] (600 root)
[connection] id=Mobile Wombat | type=802-11-wireless
[802-11-wireless] ssid=Mobile Wombat | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/wombat 1]] (600 root)
[connection] id=wombat (dongle) | type=802-11-wireless
[802-11-wireless] ssid=wombat | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wombat]] (600 root)
[connection] id=wombat | type=802-11-wireless
[802-11-wireless] ssid=wombat | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Mobile Wombat clear]] (600 root)
[connection] id=Mobile Wombat clear | type=802-11-wireless
[802-11-wireless] ssid=Mobile Wombat clear | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

vmnet1    no frequency information.

docker0   no frequency information.

vmnet8    no frequency information.

lo        no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

wlan1     11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      7   APs on   Frequency:2.412 GHz (Channel 1)
      18   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      15   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Mobile Wombat clear' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:off
                    ESSID:"Mobile Wombat clear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000004e8037
                    Extra: Last beacon: 244ms ago
          Cell 02 - Address: <MAC 'DADDYLONGLEGS' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"DADDYLONGLEGS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001002318199
                    Extra: Last beacon: 5436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME-C847' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"HOME-C847"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002afa06c189
                    Extra: Last beacon: 5004ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Jackson' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Jackson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157c251c183
                    Extra: Last beacon: 132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'wombat' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"wombat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000030edfa3a3
                    Extra: Last beacon: 216ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HOME-1B38' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"HOME-1B38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a33dd1c173
                    Extra: Last beacon: 488ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'HOME-4142' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HOME-4142"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013ed2e58152
                    Extra: Last beacon: 276ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC '' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013ed2e71b4a
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Tread Lightlier' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Tread Lightlier"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007cc11d92d8
                    Extra: Last beacon: 2316ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a33dd35b68
                    Extra: Last beacon: 384ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a33dd682c6
                    Extra: Last beacon: 176ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'xfinitywifi' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013ed2e40361
                    Extra: Last beacon: 376ms ago
          Cell 13 - Address: <MAC 'sfhome' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"sfhome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000119926448bf
                    Extra: Last beacon: 184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Monkey' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Monkey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157c149b301
                    Extra: Last beacon: 304ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Karyn' [AC15]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Karyn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016aa1e3183
                    Extra: Last beacon: 2264ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Nation' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Nation"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bff6a18e
                    Extra: Last beacon: 1024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'James Franco' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"James Franco"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bf704799
                    Extra: Last beacon: 604ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'HOME-6592' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"HOME-6592"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bcb12158
                    Extra: Last beacon: 588ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC '' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bcaaebd3
                    Extra: Last beacon: 996ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'xfinitywifi' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bcaaf36d
                    Extra: Last beacon: 996ms ago
          Cell 21 - Address: <MAC 'SUCETTE' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"SUCETTE"
           docker0   Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

         Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b567b2cf1c
                    Extra: Last beacon: 568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'HOME-C847' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"HOME-C847"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002af978ac65
                    Extra: Last beacon: 1636ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002afa536265
                    Extra: Last beacon: 1732ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME-96D2' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"HOME-96D2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013fac9f172
                    Extra: Last beacon: 1700ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'wombat' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"wombat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000030eeef940
                    Extra: Last beacon: 124ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Mobile Wombat clear' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"Mobile Wombat clear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002f47034b
                    Extra: Last beacon: 248ms ago
          Cell 06 - Address: <MAC '' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013ed301ab5a
                    Extra: Last beacon: 184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Jackson' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Jackson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157c26ac84f
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Karyn' [AC15]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Karyn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016a962b183
                    Extra: Last beacon: 16304ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'James Franco' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"James Franco"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bea6b837
                    Extra: Last beacon: 15568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'HOME-6592' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HOME-6592"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bcd46527
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bbe79bd3
                    Extra: Last beacon: 15548ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'xfinitywifi' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bcd494fc
                    Extra: Last beacon: 20ms ago
          Cell 13 - Address: <MAC 'JulietLynne's Network' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"JulietLynne's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000157bf209678
                    Extra: Last beacon: 16160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s
                    Mode:Master
                    Extra:tsf=000000a09fe43143
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'SF Smash' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"SF Smash"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s
                    Mode:Master
                    Extra:tsf=000000a09ef9df6b
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"onlyifyouhaveto"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s
                    Mode:Master
                    Extra:tsf=000000a09ef9d578
                    Extra: Last beacon: 15380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC '' [AC17]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013fac9fbcb
                    Extra: Last beacon: 1700ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'SUCETTE' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SUCETTE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b566e91328
                    Extra: Last beacon: 15544ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'xfinitywifi' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013faceb344
                    Extra: Last beacon: 1388ms ago
          Cell 20 - Address: <MAC 'xfinitywifi' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013ed2f6e66d
                    Extra: Last beacon: 888ms ago
          Cell 21 - Address: <MAC 'HOME-4142' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HOME-4142"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013ed301a161
                    Extra: Last beacon: 184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     7D4E6934194D7838D498CA2
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     085B283910CF6CA0B4CAE2C
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A279C50E29ED7F277EAF738
depends:        
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         RafaÅ‚ MiÅ‚ecki
author:         GÃ¡bor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     3CEE8C37D02010CA66D9311
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.16.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D5DBE66E4CC44B010DB516
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     2055C3093DA2EE9DEB5572C
depends:        
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:88:40:D1:7B:DF:90:2E:17:1E:23:B4:BB:C2:72:8E:B6:94:C7:0A
sig_hashalgo:   sha512

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1686 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[ 9471.014269] wlan0: authentication with <MAC 'wombat' [AC5]> timed out
[ 9482.229962] wlan0: authenticate with <MAC 'wombat' [AC5]>
[ 9482.248906] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 1/3)
[ 9482.452408] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 2/3)
[ 9482.656300] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 3/3)
[ 9482.860195] wlan0: authentication with <MAC 'wombat' [AC5]> timed out
[ 9498.391496] wlan0: authenticate with <MAC 'wombat' [AC5]>
[ 9498.391749] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 1/3)
[ 9498.592130] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 2/3)
[ 9498.796023] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 3/3)
[ 9498.999916] wlan0: authentication with <MAC 'wombat' [AC5]> timed out
[ 9510.223291] wlan0: authenticate with <MAC 'wombat' [AC5]>
[ 9510.242536] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 1/3)
[ 9510.446047] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 2/3)
[ 9510.649941] wlan0: direct probe to <MAC 'wombat' [AC5]> (try 3/3)
[ 9510.853836] wlan0: authentication with <MAC 'wombat' [AC5]> timed out
[ 9544.194130] wlan0: authenticate with <MAC address>
[ 9544.213115] wlan0: send auth to <MAC address> (try 1/3)
[ 9544.416604] wlan0: send auth to <MAC address> (try 2/3)
[ 9544.620517] wlan0: send auth to <MAC address> (try 3/3)
[ 9544.824411] wlan0: authentication with <MAC address> timed out
[ 9556.040296] wlan0: authenticate with <MAC address>
[ 9556.059037] wlan0: direct probe to <MAC address> (try 1/3)
[ 9556.262581] wlan0: direct probe to <MAC address> (try 2/3)
[ 9556.466447] wlan0: direct probe to <MAC address> (try 3/3)
[ 9556.670337] wlan0: authentication with <MAC address> timed out
[ 9574.003730] wlan0: authenticate with <MAC address>
[ 9574.004009] wlan0: direct probe to <MAC address> (try 1/3)
[ 9574.205345] wlan0: direct probe to <MAC address> (try 2/3)
[ 9574.409240] wlan0: direct probe to <MAC address> (try 3/3)
[ 9574.613135] wlan0: authentication with <MAC address> timed out
[ 9608.422953] wlan0: authenticate with <MAC address>
[ 9608.423527] wlan0: send auth to <MAC address> (try 1/3)
[ 9608.623694] wlan0: send auth to <MAC address> (try 2/3)
[ 9608.827588] wlan0: send auth to <MAC address> (try 3/3)
[ 9609.031486] wlan0: authentication with <MAC address> timed out
[ 9620.239084] wlan0: authenticate with <MAC address>
[ 9620.258119] wlan0: direct probe to <MAC address> (try 1/3)
[ 9620.461620] wlan0: direct probe to <MAC address> (try 2/3)
[ 9620.665514] wlan0: direct probe to <MAC address> (try 3/3)
[ 9620.869408] wlan0: authentication with <MAC address> timed out
[ 9638.912319] wlan0: authenticate with <MAC 'Mobile Wombat clear' [AC1]>
[ 9638.912607] wlan0: send auth to <MAC 'Mobile Wombat clear' [AC1]> (try 1/3)
[ 9638.920487] wlan0: authenticated
[ 9638.924167] wlan0: associate with <MAC 'Mobile Wombat clear' [AC1]> (try 1/3)
[ 9639.128047] wlan0: associate with <MAC 'Mobile Wombat clear' [AC1]> (try 2/3)
[ 9639.133037] wlan0: RX AssocResp from <MAC 'Mobile Wombat clear' [AC1]> (capab=0x401 status=0 aid=1)
[ 9639.133397] wlan0: associated
[ 9639.133436] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9639.134042] bridge-wlan0: device is wireless, enabling SMAC
[ 9639.134046] bridge-wlan0: up
[ 9639.134050] bridge-wlan0: attached
[ 9639.164149] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'Mobile Wombat clear' [AC1]>
[10406.793692] rtl8192cu: Chip version 0x10
[10406.826472] rtl8192cu: MAC address: <MAC 'wlan1' [IF]>
[10406.826477] rtl8192cu: Board Type 0
[10406.826548] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[10406.826587] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[10406.826992] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[10406.827668] rtlwifi: wireless switch is on
[10407.845146] rtl8192cu: MAC auto ON okay!
[10407.857870] rtl8192cu: Tx queue select: 0x05
[10408.204636] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[10409.650927] wlan1: authenticate with <MAC 'wombat' [AC5]>
[10409.672056] wlan1: direct probe to <MAC 'wombat' [AC5]> (try 1/3)
[10409.873984] wlan1: send auth to <MAC 'wombat' [AC5]> (try 2/3)
[10409.877191] wlan1: authenticated
[10409.877947] wlan1: associate with <MAC 'wombat' [AC5]> (try 1/3)
[10409.903224] wlan1: RX AssocResp from <MAC 'wombat' [AC5]> (capab=0x1431 status=0 aid=3)
[10409.903315] wlan1: associated
[10409.903326] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[10410.919549] wlan1: deauthenticating from <MAC 'wombat' [AC5]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[10410.931105] wlan1: authenticate with <MAC 'wombat' [AC5]>
[10410.941896] wlan1: send auth to <MAC 'wombat' [AC5]> (try 1/3)
[10410.959879] wlan1: authenticated
[10410.961438] wlan1: associate with <MAC 'wombat' [AC5]> (try 1/3)
[10411.004482] wlan1: RX AssocResp from <MAC 'wombat' [AC5]> (capab=0x1431 status=0 aid=3)
[10411.004543] wlan1: associated

########## wireless info END ############

```

Cheers,
- Shane

---

