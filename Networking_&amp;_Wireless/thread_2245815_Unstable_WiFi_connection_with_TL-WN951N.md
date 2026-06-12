---
title: "Unstable WiFi connection with TL-WN951N"
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by Hamburgian on 2014-09-26
I know this issue has been dealt with several times on these pages, but none of the workarounds have had any long-term noticable effect for me.

I need both lan and wlan and I have configured them as suggested in this blog:

[http://aleksz-programming.blogspot.de/2013/01/using-wifi-and-network-cable-at-same.html](http://aleksz-programming.blogspot.de/2013/01/using-wifi-and-network-cable-at-same.html)

If I don't click the  use this connection only for resouces on its network  option, then wlan is automatically disconnected.
But wlan won't work at all if this option is clicked on.

I've created the /etc/modprobe.d/ath9k.conf file with 
```
options ath9k nohwcrypt=1 
```
....adding the extra options suggested in

[http://forums.linuxmint.com/viewtopic.php?f=53&t=154774](http://forums.linuxmint.com/viewtopic.php?f=53&t=154774) have no effect whatsoever.

I've enable backports and run both  the ```
sudo apt-get update sudo apt-get dist-upgrade options
```

so the problem....at boot my WiFi runs...for about fifteen minutes or so. If I run 

 ```
sudo service network-manager restart
``` I get the same result...15 minutes of undisturbed, reliable internet. But then it dies

I'm at a loss as to what I should try next. Any ideas would be welcome.

Here's the output of my wireless script

 
```
########## wireless info START ##########

Report from: 26 Sep 2014 13:24 CEST +0200

Booted last: 26 Sep 2014 07:43 CEST +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, nomodeset, video=uvesafb:mode_option=1152x864-24,mtrr=3,scroll=ywrap, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:09.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)
	Subsystem: Qualcomm Atheros Device [168c:2093]
	Kernel driver in use: ath9k

01:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Belkin F5D5000 PCI Card/Desktop Network PCI Card [1799:5000]
	Kernel driver in use: 8139too

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:369c]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046a:0001 Cherry GmbH My3000 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe70:2787/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3715181 (3.7 MB)  TX bytes:1573036 (1.5 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.178.31  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::ea94:f6ff:fe4e:9d6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24017857 (24.0 MB)  TX bytes:58524441 (58.5 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"FRITZ!Box 7490"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'FRITZ!Box 7490' [AC5]>   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:17   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.178.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box domain

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth1  [Print Server] -------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.178.1
    DNS:             192.168.1.1

- Device: wlan0  [FRITZ!Box 7490] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Funky Doobster:  Infra, <MAC 'Funky Doobster' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    ALICE-WLAN80:    Infra, <MAC 'ALICE-WLAN80' [AC9]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Hotspot:         Infra, <MAC 'Hotspot' [AC4]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 44 WPA2
    FRITZ!Box Fon WLAN 7570 vDSL: Infra, <MAC 'FRITZ!Box Fon WLAN 7570 vDSL' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Bowman:          Infra, <MAC 'Bowman' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    HITRON-72C0:     Infra, <MAC 'HITRON-72C0' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    FRITZ!Box Fon WLAN 7570 vDSL 123: Infra, <MAC 'FRITZ!Box Fon WLAN 7570 vDSL 123' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Sportsfreund:    Infra, <MAC 'Sportsfreund' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Neuland2:        Infra, <MAC 'Neuland2' [AC1]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    *FRITZ!Box 7490: Infra, <MAC 'FRITZ!Box 7490' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2

  IPv4 Settings:
    Address:         192.168.178.31
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

    DNS:             192.168.178.1

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

no-auto-default=<MAC address>,<MAC 'eth0' [IF]>,<MAC 'eth1' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_Pocket_3020_872448
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/FRITZ!Box 7490]] (600 root)
[connection] id=FRITZ!Box 7490 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box 7490 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
	(2400 - 2483 @ 40), (N/A, 20)
	(5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
	(5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
	(5470 - 5725 @ 40), (N/A, 26), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Neuland2' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Neuland2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000025fb7507434
                    Extra: Last beacon: 1648ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Funky Doobster' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Funky Doobster"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000680f48f551
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Bowman' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Bowman"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b5029587bd
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Hotspot' [AC4]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Hotspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001848593f4d
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'FRITZ!Box 7490' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000665316
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FRITZ!Box Fon WLAN 7570 vDSL' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7570 vDSL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a7b9e03b
                    Extra: Last beacon: 140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'FRITZ!Box Fon WLAN 7570 vDSL 123' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7570 vDSL 123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004327f54
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HITRON-72C0' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HITRON-72C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e1fe93e162
                    Extra: Last beacon: 1108ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ALICE-WLAN80' [AC9]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN80"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009bba482668
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0

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
rtc

lm90
w83627ehf

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:0x0029 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[20321.677414] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20321.969353] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[20322.496307] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[20322.499806] 8139too 0000:01:0a.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[20324.071859] wlan0: authenticate with <MAC 'FRITZ!Box 7490' [AC5]>
[20324.111591] wlan0: send auth to <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20324.115936] wlan0: authenticated
[20324.120076] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20324.148980] wlan0: RX AssocResp from <MAC 'FRITZ!Box 7490' [AC5]> (capab=0x31 status=0 aid=1)
[20324.149038] wlan0: associated
[20324.149083] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20397.753127] wlan0: authenticate with <MAC 'FRITZ!Box 7490' [AC5]>
[20397.777286] wlan0: send auth to <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20397.788788] wlan0: authenticated
[20397.792047] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20398.040021] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 2/3)
[20398.144020] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 3/3)
[20398.312020] wlan0: association with <MAC 'FRITZ!Box 7490' [AC5]> timed out
[20399.625276] wlan0: authenticate with <MAC 'FRITZ!Box 7490' [AC5]>
[20399.650096] wlan0: send auth to <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20399.673976] wlan0: authenticated
[20399.676045] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20399.836886] wlan0: RX AssocResp from <MAC 'FRITZ!Box 7490' [AC5]> (capab=0x31 status=0 aid=1)
[20399.836943] wlan0: associated
[20411.753211] wlan0: authenticate with <MAC 'FRITZ!Box 7490' [AC5]>
[20411.777940] wlan0: send auth to <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20411.795813] wlan0: authenticated
[20411.800041] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20411.928032] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 2/3)
[20411.946631] wlan0: RX AssocResp from <MAC 'FRITZ!Box 7490' [AC5]> (capab=0x31 status=0 aid=1)
[20411.946686] wlan0: associated
[20421.421042] wlan0: authenticate with <MAC 'FRITZ!Box 7490' [AC5]>
[20421.445160] wlan0: send auth to <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20421.576050] wlan0: send auth to <MAC 'FRITZ!Box 7490' [AC5]> (try 2/3)
[20421.581173] wlan0: authenticated
[20421.584119] wlan0: associate with <MAC 'FRITZ!Box 7490' [AC5]> (try 1/3)
[20421.710899] wlan0: RX AssocResp from <MAC 'FRITZ!Box 7490' [AC5]> (capab=0x31 status=0 aid=1)
[20421.710967] wlan0: associated

########## wireless info END ############  

```

---

### Post by Hamburgian on 2014-09-26
deleted

---

### Post by Hamburgian on 2014-09-27
I tried disabling 802.11n as suggested in several posts.  Since there seems to be no way to disable this in the driver, I did it on the WiFi router. But this is a complete red herring, there was no improvement in stability. Since the two other laptops (one running Ubuntu 14.04) and the iMac that are using this router have no problem with 802.11n I turned this facility back on.

I live in a city, so there are plenty of other WiFis broadcasting in the immediate area, some also using the same channel as me. 
So I tried setting the network to 'manual' to lock it to one signal.

Oddly when I entered ** 255.255.255.0 ** as the subnet mask - the normal default value - I was able to connect to the router, but not to the internet or receive mails.

iwconfig

```

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MiWiFi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 34:31:C4:01:22:0D   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:172  Invalid misc:4510   Missed beacon:0

mark@mark-ubu64:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:db:d0:be:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:30:bd:70:27:87  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe70:2787/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25716 (25.7 KB)  TX bytes:88752 (88.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:576897 (576.8 KB)  TX bytes:576897 (576.8 KB)

wlan0     Link encap:Ethernet  HWaddr e8:94:f6:4e:9d:6b  
          inet addr:192.168.178.31  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::ea94:f6ff:fe4e:9d6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:206793 errors:0 dropped:11 overruns:0 frame:0
          TX packets:123615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:300148024 (300.1 MB)  TX bytes:11941267 (11.9 MB)

```

While entering the ip addresses **24** appears in the subnet mask box. If you leave it at **24** it seems to work....and as you can see I've managed to download a whole 300 MB without the WiFi resetting...a new world record for ath9K.

I still have IPv6 set to ignored, as suggested in most of the posts, and I have no idea how to enter manual settings for this.

Isn't this a bit worrying? IPv6 is the *new* internet. Shouldn't Ubuntu be able to handle new?

---

### Post by Hamburgian on 2014-09-28
Well, yesterday was just a flash in the pan. Today I'm back to wlan disconnecting every five minutes.
A couple things that I've noticed that perhaps the wisest out there can help with.

1. I've set my wireless card to manual connect. I thought this should set it to connect only to my WiFi router, and only to the ip address that my WiFi router has registered to my PC. But after the connection fails I've noticed that I sometimes have to select a **hidden WiFi network**?? where I am asked for my psk, even though it's sitting there in the network-Manager settings, but at other times my WiFi service is listed. How can that be, if I've told Network-Manager I only want to connect to a certain ip address and all the information is there?

Is there something running in the background that is interfering with Network-Manager? I looked at /var/log/syslog and noticed that avahi-daemon seems to be actively messing things up (if I've read this correctly!) Here is a record of a half hour

```

Sep 28 18:06:39 mark-ubu64 kernel: [ 4910.841242] wlan0: authenticate with 34:31:c4:01:22:0d
Sep 28 18:06:39 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Sep 28 18:06:39 mark-ubu64 kernel: [ 4910.866605] wlan0: send auth to 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:06:39 mark-ubu64 kernel: [ 4910.976030] wlan0: send auth to 34:31:c4:01:22:0d (try 2/3)
Sep 28 18:06:39 mark-ubu64 wpa_supplicant[1001]: wlan0: Trying to associate with 34:31:c4:01:22:0d (SSID='MiWiFi' freq=2412 MHz)
Sep 28 18:06:39 mark-ubu64 kernel: [ 4910.987474] wlan0: authenticated
Sep 28 18:06:39 mark-ubu64 kernel: [ 4910.988049] wlan0: associate with 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:06:39 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 28 18:06:39 mark-ubu64 kernel: [ 4911.292042] wlan0: associate with 34:31:c4:01:22:0d (try 2/3)
Sep 28 18:06:39 mark-ubu64 kernel: [ 4911.400040] wlan0: associate with 34:31:c4:01:22:0d (try 3/3)
Sep 28 18:06:39 mark-ubu64 kernel: [ 4911.664134] wlan0: association with 34:31:c4:01:22:0d timed out
Sep 28 18:06:39 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: associating -> disconnected
Sep 28 18:06:39 mark-ubu64 NetworkManager[910]: keyfile: ipv4.address1: address 192.168.178.31/24 gateway 192.168.178.1
Sep 28 18:06:40 mark-ubu64 wpa_supplicant[1001]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 28 18:06:39 mark-ubu64 NetworkManager[910]: keyfile: ipv4.address1: address 192.168.178.31/24 gateway 192.168.178.1
Sep 28 18:06:40 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 28 18:06:41 mark-ubu64 wpa_supplicant[1001]: wlan0: SME: Trying to authenticate with 34:31:c4:01:22:0d (SSID='MiWiFi' freq=2412 MHz)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.488373] wlan0: authenticate with 34:31:c4:01:22:0d
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.516338] wlan0: send auth to 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 28 18:06:41 mark-ubu64 wpa_supplicant[1001]: wlan0: Trying to associate with 34:31:c4:01:22:0d (SSID='MiWiFi' freq=2412 MHz)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.524311] wlan0: authenticated
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.529363] wlan0: associate with 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:06:41 mark-ubu64 wpa_supplicant[1001]: wlan0: Associated with 34:31:c4:01:22:0d
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.552388] wlan0: RX AssocResp from 34:31:c4:01:22:0d (capab=0x31 status=0 aid=1)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.552460] wlan0: associated
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.552570] cfg80211: Calling CRDA for country: DE
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.557909] cfg80211: Regulatory domain changed to country: DE
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.557915] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.557918] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.557920] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.557922] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.557924] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
Sep 28 18:06:41 mark-ubu64 kernel: [ 4913.557926] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Sep 28 18:06:41 mark-ubu64 wpa_supplicant[1001]: wlan0: WPA: Key negotiation completed with 34:31:c4:01:22:0d [PTK=CCMP GTK=CCMP]
Sep 28 18:06:41 mark-ubu64 wpa_supplicant[1001]: wlan0: CTRL-EVENT-CONNECTED - Connection to 34:31:c4:01:22:0d completed [id=0 id_str=]
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MiWiFi'.
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 28 18:06:41 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) successful, device activated.
Sep 28 18:06:42 mark-ubu64 ntpd[10765]: ntpd exiting on signal 15
Sep 28 18:06:56 mark-ubu64 ntpdate[10880]: adjust time server 178.23.121.164 offset -0.001326 sec
Sep 28 18:06:56 mark-ubu64 ntpd[11025]: ntpd 4.2.6p5@1.2349-o Wed Oct  9 19:08:06 UTC 2013 (1)
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: proto: precision = 0.840 usec
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen and drop on 1 v6wildcard :: UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen normally on 2 lo 127.0.0.1 UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen normally on 3 eth1 192.168.1.102 UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen normally on 4 wlan0 192.168.178.31 UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen normally on 5 lo ::1 UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen normally on 6 wlan0 fe80::ea94:f6ff:fe4e:9d6b UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listen normally on 7 eth1 fe80::230:bdff:fe70:2787 UDP 123
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: peers refreshed
Sep 28 18:06:56 mark-ubu64 ntpd[11026]: Listening on routing socket on fd #24 for interface updates
Sep 28 18:07:31 mark-ubu64 wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=34:31:c4:01:22:0d reason=4 locally_generated=1
Sep 28 18:07:31 mark-ubu64 NetworkManager[910]: <warn> Connection disconnected (reason -4)
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.640246] cfg80211: Calling CRDA to update world regulatory domain
Sep 28 18:07:31 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: completed -> disconnected
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.654733] cfg80211: World regulatory domain updated:
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.654739] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.654742] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.654744] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.654746] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.654748] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 18:07:31 mark-ubu64 kernel: [ 4963.654750] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 18:07:31 mark-ubu64 wpa_supplicant[1001]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 28 18:07:31 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 28 18:07:47 mark-ubu64 NetworkManager[910]: <warn> (wlan0): link timed out.
Sep 28 18:07:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: activated -> failed (reason 'SSID not found') [100 120 53]
Sep 28 18:07:47 mark-ubu64 NetworkManager[910]: <warn> Activation (wlan0) failed for connection 'MiWiFi'
Sep 28 18:07:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 28 18:07:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep 28 18:07:47 mark-ubu64 dbus[748]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 28 18:07:47 mark-ubu64 kernel: [ 4979.034015] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 28 18:07:47 mark-ubu64 avahi-daemon[880]: Withdrawing address record for fe80::ea94:f6ff:fe4e:9d6b on wlan0.
Sep 28 18:07:47 mark-ubu64 avahi-daemon[880]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::ea94:f6ff:fe4e:9d6b.
Sep 28 18:07:47 mark-ubu64 avahi-daemon[880]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 28 18:07:47 mark-ubu64 avahi-daemon[880]: Withdrawing address record for 192.168.178.31 on wlan0.
Sep 28 18:07:47 mark-ubu64 avahi-daemon[880]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.178.31.
Sep 28 18:07:47 mark-ubu64 avahi-daemon[880]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 28 18:07:47 mark-ubu64 NetworkManager[910]: <info> Writing DNS information to /sbin/resolvconf
Sep 28 18:06:01 mark-ubu64 dnsmasq[1172]: using nameserver 192.168.178.1#53
Sep 28 18:07:47 mark-ubu64 dnsmasq[1172]: setting upstream servers from DBus
Sep 28 18:07:47 mark-ubu64 dnsmasq[1172]: using nameserver 192.168.178.1#53
Sep 28 18:07:47 mark-ubu64 dnsmasq[1172]: using nameserver 192.168.1.1#53
Sep 28 18:07:47 mark-ubu64 dbus[748]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 28 18:07:47 mark-ubu64 NetworkManager[910]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 28 18:07:48 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: scanning -> inactive
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: Deleting interface #6 wlan0, fe80::ea94:f6ff:fe4e:9d6b#123, interface stats: received=0, sent=0, dropped=0, active_time=48 secs
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: Deleting interface #4 wlan0, 192.168.178.31#123, interface stats: received=6, sent=10, dropped=0, active_time=48 secs
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: 78.46.107.140 interface 192.168.178.31 -> (none)
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: 5.9.39.5 interface 192.168.178.31 -> (none)
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: 144.76.114.171 interface 192.168.178.31 -> (none)
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: 62.116.130.3 interface 192.168.178.31 -> (none)
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: 192.168.178.1 interface 192.168.178.31 -> (none)
Sep 28 18:07:50 mark-ubu64 ntpd[11026]: peers refreshed
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Auto-activating connection 'MiWiFi'.
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) starting connection 'MiWiFi'
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless): access point 'MiWiFi' has security, but secrets are required.
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless): connection 'MiWiFi' has security, and secrets exist.  No new secrets needed.
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Config: added 'ssid' value 'MiWiFi'
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Config: added 'scan_ssid' value '1'
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Config: added 'bssid' value '34:31:c4:01:22:0d'
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Config: added 'psk' value '<omitted>'
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> Config: set interface ap_scan to 1
Sep 28 18:07:50 mark-ubu64 wpa_supplicant[1001]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Sep 28 18:07:51 mark-ubu64 wpa_supplicant[1001]: wlan0: SME: Trying to authenticate with 34:31:c4:01:22:0d (SSID='MiWiFi' freq=2412 MHz)
Sep 28 18:07:51 mark-ubu64 kernel: [ 4982.859617] wlan0: authenticate with 34:31:c4:01:22:0d
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Sep 28 18:07:51 mark-ubu64 kernel: [ 4982.881504] wlan0: direct probe to 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:07:51 mark-ubu64 kernel: [ 4983.084020] wlan0: direct probe to 34:31:c4:01:22:0d (try 2/3)
Sep 28 18:07:51 mark-ubu64 kernel: [ 4983.288056] wlan0: direct probe to 34:31:c4:01:22:0d (try 3/3)
Sep 28 18:07:51 mark-ubu64 kernel: [ 4983.492030] wlan0: authentication with 34:31:c4:01:22:0d timed out
Sep 28 18:07:51 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 28 18:07:52 mark-ubu64 wpa_supplicant[1001]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 28 18:07:52 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 28 18:08:16 mark-ubu64 NetworkManager[910]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Sep 28 18:08:16 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep 28 18:08:16 mark-ubu64 NetworkManager[910]: <warn> Activation (wlan0) failed for connection 'MiWiFi'
Sep 28 18:08:16 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 28 18:08:16 mark-ubu64 NetworkManager[910]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep 28 18:08:16 mark-ubu64 NetworkManager[910]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 28 18:08:16 mark-ubu64 NetworkManager[910]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 28 18:08:17 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: scanning -> inactive
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Auto-activating connection 'MiWiFi'.
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) starting connection 'MiWiFi'
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless): access point 'MiWiFi' has security, but secrets are required.
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless): connection 'MiWiFi' has security, and secrets exist.  No new secrets needed.
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Config: added 'ssid' value 'MiWiFi'
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Config: added 'scan_ssid' value '1'
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Config: added 'bssid' value '34:31:c4:01:22:0d'
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Config: added 'psk' value '<omitted>'
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> Config: set interface ap_scan to 1
Sep 28 18:08:19 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep 28 18:08:36 mark-ubu64 wpa_supplicant[1001]: message repeated 9 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Sep 28 18:08:37 mark-ubu64 wpa_supplicant[1001]: wlan0: SME: Trying to authenticate with 34:31:c4:01:22:0d (SSID='MiWiFi' freq=2412 MHz)
Sep 28 18:08:37 mark-ubu64 kernel: [ 5029.239351] wlan0: authenticate with 34:31:c4:01:22:0d
Sep 28 18:08:37 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 28 18:08:37 mark-ubu64 kernel: [ 5029.265674] wlan0: direct probe to 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:08:37 mark-ubu64 kernel: [ 5029.468022] wlan0: direct probe to 34:31:c4:01:22:0d (try 2/3)
Sep 28 18:08:37 mark-ubu64 kernel: [ 5029.672029] wlan0: direct probe to 34:31:c4:01:22:0d (try 3/3)
Sep 28 18:08:38 mark-ubu64 kernel: [ 5029.876020] wlan0: authentication with 34:31:c4:01:22:0d timed out
Sep 28 18:08:38 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 28 18:08:39 mark-ubu64 wpa_supplicant[1001]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 28 18:08:39 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 28 18:08:44 mark-ubu64 NetworkManager[910]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Sep 28 18:08:44 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep 28 18:08:44 mark-ubu64 NetworkManager[910]: <warn> Activation (wlan0) failed for connection 'MiWiFi'
Sep 28 18:08:44 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 28 18:08:44 mark-ubu64 NetworkManager[910]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep 28 18:08:44 mark-ubu64 NetworkManager[910]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 28 18:08:44 mark-ubu64 NetworkManager[910]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 28 18:08:45 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: scanning -> inactive
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Auto-activating connection 'MiWiFi'.
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) starting connection 'MiWiFi'
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless): access point 'MiWiFi' has security, but secrets are required.
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless): connection 'MiWiFi' has security, and secrets exist.  No new secrets needed.
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Config: added 'ssid' value 'MiWiFi'
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Config: added 'scan_ssid' value '1'
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Config: added 'bssid' value '34:31:c4:01:22:0d'
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Config: added 'psk' value '<omitted>'
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> Config: set interface ap_scan to 1
Sep 28 18:08:47 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep 28 18:08:53 mark-ubu64 wpa_supplicant[1001]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Sep 28 18:08:53 mark-ubu64 wpa_supplicant[1001]: wlan0: SME: Trying to authenticate with 34:31:c4:01:22:0d (SSID='MiWiFi' freq=2412 MHz)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.652788] wlan0: authenticate with 34:31:c4:01:22:0d
Sep 28 18:08:53 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.677198] wlan0: send auth to 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:08:53 mark-ubu64 wpa_supplicant[1001]: wlan0: Trying to associate with 34:31:c4:01:22:0d (SSID='MiWiFi' freq=2412 MHz)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.686716] wlan0: authenticated
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.689344] wlan0: associate with 34:31:c4:01:22:0d (try 1/3)
Sep 28 18:08:53 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 28 18:08:53 mark-ubu64 wpa_supplicant[1001]: wlan0: Associated with 34:31:c4:01:22:0d
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.722110] wlan0: RX AssocResp from 34:31:c4:01:22:0d (capab=0x31 status=0 aid=1)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.722183] wlan0: associated
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.722246] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.722399] cfg80211: Calling CRDA for country: DE
Sep 28 18:08:53 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.731358] cfg80211: Regulatory domain changed to country: DE
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.731364] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.731367] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.731369] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.731371] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.731373] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
Sep 28 18:08:53 mark-ubu64 kernel: [ 5045.731375] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Sep 28 18:08:54 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Sep 28 18:08:55 mark-ubu64 avahi-daemon[880]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::ea94:f6ff:fe4e:9d6b.
Sep 28 18:08:55 mark-ubu64 avahi-daemon[880]: New relevant interface wlan0.IPv6 for mDNS.
Sep 28 18:08:55 mark-ubu64 avahi-daemon[880]: Registering new address record for fe80::ea94:f6ff:fe4e:9d6b on wlan0.*.
Sep 28 18:08:57 mark-ubu64 ntpd[11026]: Listen normally on 8 wlan0 fe80::ea94:f6ff:fe4e:9d6b UDP 123
Sep 28 18:08:57 mark-ubu64 ntpd[11026]: peers refreshed
Sep 28 18:08:57 mark-ubu64 ntpd[11026]: new interface(s) found: waking up resolver
Sep 28 18:08:57 mark-ubu64 wpa_supplicant[1001]: wlan0: WPA: Key negotiation completed with 34:31:c4:01:22:0d [PTK=CCMP GTK=CCMP]
Sep 28 18:08:57 mark-ubu64 wpa_supplicant[1001]: wlan0: CTRL-EVENT-CONNECTED - Connection to 34:31:c4:01:22:0d completed [id=0 id_str=]
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MiWiFi'.
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 28 18:08:57 mark-ubu64 avahi-daemon[880]: Withdrawing address record for fe80::ea94:f6ff:fe4e:9d6b on wlan0.
Sep 28 18:08:57 mark-ubu64 avahi-daemon[880]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::ea94:f6ff:fe4e:9d6b.
Sep 28 18:08:57 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 28 18:08:57 mark-ubu64 avahi-daemon[880]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 28 18:08:57 mark-ubu64 avahi-daemon[880]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.178.31.
Sep 28 18:08:57 mark-ubu64 avahi-daemon[880]: New relevant interface wlan0.IPv4 for mDNS.
Sep 28 18:08:57 mark-ubu64 avahi-daemon[880]: Registering new address record for 192.168.178.31 on wlan0.IPv4.
Sep 28 18:08:58 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 28 18:08:58 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 28 18:08:58 mark-ubu64 NetworkManager[910]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 28 18:08:59 mark-ubu64 NetworkManager[910]: <info> Policy set 'MiWiFi' (wlan0) as default for IPv4 routing and DNS.
Sep 28 18:08:59 mark-ubu64 NetworkManager[910]: <info> Writing DNS information to /sbin/resolvconf
Sep 28 18:08:59 mark-ubu64 dnsmasq[1172]: setting upstream servers from DBus
Sep 28 18:08:59 mark-ubu64 dnsmasq[1172]: using nameserver 192.168.1.1#53
Sep 28 18:08:59 mark-ubu64 dnsmasq[1172]: using nameserver 192.168.178.1#53
Sep 28 18:08:59 mark-ubu64 avahi-daemon[880]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::ea94:f6ff:fe4e:9d6b.
Sep 28 18:08:59 mark-ubu64 avahi-daemon[880]: New relevant interface wlan0.IPv6 for mDNS.
Sep 28 18:08:59 mark-ubu64 avahi-daemon[880]: Registering new address record for fe80::ea94:f6ff:fe4e:9d6b on wlan0.*.
Sep 28 18:08:59 mark-ubu64 NetworkManager[910]: <info> Activation (wlan0) successful, device activated.
Sep 28 18:08:59 mark-ubu64 dbus[748]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 28 18:08:59 mark-ubu64 dbus[748]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

```

and my avahi-deamon.conf settings
```

# This file is part of avahi.
#
# avahi is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2 of the
# License, or (at your option) any later version.
#
# avahi is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public
# License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with avahi; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

# See avahi-daemon.conf(5) for more information on this configuration
# file!

[server]
#host-name=foo
#domain-name=local
#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=yes
#allow-interfaces=eth0
#deny-interfaces=eth1
#check-response-ttl=no
#use-iff-running=no
#enable-dbus=yes
#disallow-other-stacks=no
#allow-point-to-point=no
#cache-entries-max=4096
#clients-max=4096
#objects-per-client-max=1024
#entries-per-entry-group-max=32
ratelimit-interval-usec=1000000
ratelimit-burst=1000

[wide-area]
enable-wide-area=yes

[publish]
#disable-publishing=no
#disable-user-service-publishing=no
#add-service-cookie=no
#publish-addresses=yes
#publish-hinfo=yes
#publish-workstation=yes
#publish-domain=yes
#publish-dns-servers=192.168.50.1, 192.168.50.2
#publish-resolv-conf-dns-servers=yes
#publish-aaaa-on-ipv4=yes
#publish-a-on-ipv6=no

[reflector]
#enable-reflector=no
#reflect-ipv=no

[rlimits]
#rlimit-as=
rlimit-core=0
rlimit-data=4194304
rlimit-fsize=0
rlimit-nofile=768
rlimit-stack=4194304
rlimit-nproc=3

```


Can anyone out there point me in the right direction please?

---

### Post by Hamburgian on 2014-10-20
So, I've been banging my head against this brick wall for nigh on two months, and I'm giving up. 
For a while I thought it might have been a problem with the BIOS settings..perhaps IRQ seetings. I had noticed that every time the wifi dropped off my video became sluggish, but I've invested in a couple of powerline boxes and there has been no effect on video performance when the wifi cuts out since using them (I still have the wifi card installed and would very much like to get it working reliably)

In the case that this might be the problem here's a schematic of my motherboard - an MSI K9N neo V3. [https://www.dropbox.com/s/65xsztrsev...20pci.gif?dl=0](https://www.dropbox.com/s/65xsztrsev...20pci.gif?dl=0)
I read in this post [http://forums.speedguide.net/showthread.php?231970-How-do-I-change-the-IRQ-of-my-network-card](http://forums.speedguide.net/showthread.php?231970-How-do-I-change-the-IRQ-of-my-network-card) that network cards should be in the 2nd of the 4 PCI slots, but I only have three and a PCIE x16 slot above - where my monsterously large video card is, and I can't fit anything in the slot below.


A couple of remarks that may give some clues to anyone who has a deeper knowledge of bugs in wifi drivers.
I have two ubuntu installations. The one I use most is a fresh 64 bit install (from sept 2014) wireless script here.
```
/0/3                        memory      RAM memory 
/0/1                        bridge      MCP65 LPC Bridge 
/0/1.1                      bus         MCP65 SMBus 
/0/1.2                      memory      RAM memory 
/0/2                        bus         MCP65 USB 1.1 OHCI Controller 
/0/2.1                      bus         MCP65 USB 2.0 EHCI Controller 
/0/7                        multimedia  MCP65 High Definition Audio 
/0/8                        bridge      MCP65 PCI bridge 
/0/8/9          wlan0       network     AR922X Wireless Network Adapter 
/0/9                        storage     MCP65 IDE 
/0/a                        storage     MCP65 AHCI Controller 
/0/b                        bridge      MCP65 PCI Express bridge 
/0/c                        bridge      MCP65 PCI Express bridge 
/0/c/0          eth0        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
/0/d                        bridge      MCP65 PCI Express bridge 
/0/d/0                      display     NV40 [GeForce 6800 GT/GTO/Ultra] 
/0/e                        bridge      MCP65 PCI Express bridge 
/0/100                      bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
/0/101                      bridge      K8 [Athlon64/Opteron] Address Map 
/0/102                      bridge      K8 [Athlon64/Opteron] DRAM Controller 
/0/103                      bridge      K8 [Athlon64/Opteron] Miscellaneous Control 
/0/5            scsi0       storage     
/0/5/0.0.0      /dev/cdrom  disk        DVD-ROM DDU1615 
/0/6            scsi4       storage     
/0/6/0.0.0      /dev/sda    disk        1TB WDC WD10EALX-009 
/0/6/0.0.0/1    /dev/sda1   volume      48GiB EXT4 volume 
/0/6/0.0.0/2    /dev/sda2   volume      371GiB Extended partition 
/0/6/0.0.0/2/5  /dev/sda5   volume      9006MiB Linux swap / Solaris partition 
/0/6/0.0.0/2/6  /dev/sda6   volume      362GiB Linux filesystem partition 
/0/6/0.0.0/3    /dev/sda3   volume      44GiB EXT4 volume 
/0/6/0.0.0/4    /dev/sda4   volume      466GiB EXT4 volume 
/0/f            scsi5       storage     
/0/f/0.0.0      /dev/sr1    disk        DVDRAM GH24NSB0 
Linux mark-ubu64 3.13.0-38-generic #65-Ubuntu SMP Thu Oct 9 11:36:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 
[    0.000000] No AGP bridge found 
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780] 
[    0.000000] No NUMA configuration found 
[    0.000000] No AGP bridge found 
[    0.188735] ACPI: No dock devices found. 
[    0.204641] Found 1 acpi root devices 
[    0.204775] usbcore: registered new interface driver usbfs 
[    0.204775] usbcore: registered new interface driver hub 
[    0.204775] usbcore: registered new device driver usb 
[    0.214121] Switched to clocksource hpet 
[    0.239974] pnp: PnP ACPI: found 13 devices 
[    0.325220] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.325267] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.325322] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.325378] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.325437] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.325500] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.325567] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    1.134382] Console: switching to colour frame buffer device 128x48 
[    1.212134] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002 
[    1.212137] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    1.212140] usb usb1: Product: EHCI Host Controller 
[    1.212143] usb usb1: Manufacturer: Linux 3.13.0-38-generic ehci_hcd 
[    1.212146] usb usb1: SerialNumber: 0000:00:02.1 
[    1.212329] hub 1-0:1.0: USB hub found 
[    1.270068] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001 
[    1.270072] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    1.270075] usb usb2: Product: OHCI PCI host controller 
[    1.270078] usb usb2: Manufacturer: Linux 3.13.0-38-generic ohci_hcd 
[    1.270081] usb usb2: SerialNumber: 0000:00:02.0 
[    1.270245] hub 2-0:1.0: USB hub found 
[    1.270660] i8042: PNP: No PS/2 controller found. Probing ports directly. 
[    1.276382] Loaded X.509 cert 'Magrathea: Glacier signing key: 2adeedea6cba0b95a6222240711f49c87207bbf6' 
[    1.287736] IMA: No TPM chip found, activating TPM-bypass! 
[    1.288694] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (2 cpu cores) (version 2.20.00) 
[    1.288703] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.390235] r8169 0000:03:00.0 eth0: RTL8168b/8111b at 0xffffc90000636000, 00:19:db:d0:be:f3, XID 18000000 IRQ 45 
[    1.390239] r8169 0000:03:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko] 
[    1.580046] usb 1-4: new high-speed USB device number 3 using ehci-pci 
[    1.713290] usb 1-4: New USB device found, idVendor=05e3, idProduct=0608 
[    1.713295] usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0 
[    1.713298] usb 1-4: Product: USB2.0 Hub 
[    1.713752] hub 1-4:1.0: USB hub found 
[    2.016040] usb 2-3: new low-speed USB device number 2 using ohci-pci 
[    2.229048] usb 2-3: New USB device found, idVendor=046a, idProduct=0001 
[    2.229054] usb 2-3: New USB device strings: Mfr=1, Product=0, SerialNumber=0 
[    2.229057] usb 2-3: Manufacturer: Cherry GmbH 
[    2.247360] usbcore: registered new interface driver usbhid 
[    2.247364] usbhid: USB HID core driver 
[    2.250028] input: Cherry GmbH as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input5 
[    2.250169] hid-generic 0003:046A:0001.0001: input,hidraw0: USB HID v1.11 Keyboard [Cherry GmbH] on usb-0000:00:02.0-3/input0 
[    2.304304] usb 1-4.1: new low-speed USB device number 4 using ehci-pci 
[    2.400413] usb 1-4.1: New USB device found, idVendor=093a, idProduct=2510 
[    2.400417] usb 1-4.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
[    2.400419] usb 1-4.1: Product: USB Optical Mouse 
[    2.400422] usb 1-4.1: Manufacturer: PixArt 
[    2.404112] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4.1/1-4.1:1.0/input/input6 
[    2.404263] hid-generic 0003:093A:2510.0002: input,hidraw1: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:02.1-4.1/input0 
[    4.020065] uvesafb: probe of uvesafb.0 failed with error -5 
[   15.842096] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   16.571201] lp: driver loaded but no devices found 
[   16.985097] w83627ehf: Found W83627DHG chip at 0xa10 
[   17.028760] cfg80211: Calling CRDA to update world regulatory domain 
[   18.082630] cfg80211: World regulatory domain updated: 
[   18.082637] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   18.082639] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.082642] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.082644] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   18.082646] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.082648] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.979172] ath: EEPROM regdomain: 0x809c 
[   18.979178] ath: EEPROM indicates we should expect a country code 
[   18.979180] ath: doing EEPROM country->regdmn map search 
[   18.979182] ath: country maps to regdmn code: 0x52 
[   18.979184] ath: Country alpha2 being used: CN 
[   18.979185] ath: Regpair used: 0x52 
[   19.055533] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht' 
[   19.056132] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xffffc90010aa0000, irq=18 
[   19.056363] cfg80211: Calling CRDA for country: CN 
[   19.084966] cfg80211: Regulatory domain changed to country: CN 
[   19.084972] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   19.084975] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   19.084977] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm) 
[   19.084979] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm) 
[   19.084981] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm) 
[   19.084983] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm) 
[   19.351782] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro 
[   20.740184] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input14 
[   20.740346] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input13 
[   20.740484] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input12 
[   20.740561] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input11 
[   20.740629] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input10 
[   20.740696] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input9 
[   20.740764] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input8 
[   20.740840] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input7 
[   25.349138] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   25.352727] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   25.381305] r8169 0000:03:00.0 eth0: link down 
[   25.381320] r8169 0000:03:00.0 eth0: link down 
[   25.381402] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   25.381918] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   27.044604] wlan0: authenticate with 34:31:c4:01:22:0d 
[   27.069326] wlan0: direct probe to 34:31:c4:01:22:0d (try 1/3) 
[   27.165899] r8169 0000:03:00.0 eth0: link up 
[   27.165912] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[   27.276057] wlan0: send auth to 34:31:c4:01:22:0d (try 2/3) 
[   27.285180] wlan0: authenticated 
[   27.288037] wlan0: associate with 34:31:c4:01:22:0d (try 1/3) 
[   27.313074] wlan0: RX AssocResp from 34:31:c4:01:22:0d (capab=0x31 status=0 aid=1) 
[   27.313119] wlan0: associated 
[   27.313152] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   27.313227] cfg80211: Calling CRDA for country: DE 
[   27.317949] cfg80211: Regulatory domain changed to country: DE 
[   27.317955] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   27.317957] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   27.317960] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   27.317962] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   27.317964] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm) 
[   27.317966] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm) 
[   27.402164] wlan0: deauthenticating from 34:31:c4:01:22:0d by local choice (reason=2) 
[   27.412941] cfg80211: Calling CRDA to update world regulatory domain 
[   27.415938] wlan0: authenticate with 34:31:c4:01:22:0d 
[   27.436449] wlan0: send auth to 34:31:c4:01:22:0d (try 1/3) 
[   27.436741] cfg80211: World regulatory domain updated: 
[   27.436744] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   27.436747] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   27.436750] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   27.436752] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   27.436755] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   27.436758] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   28.408654] wlan0: authenticated 
[   28.644895] wlan0: associate with 34:31:c4:01:22:0d (try 1/3) 
[   28.667693] wlan0: RX AssocResp from 34:31:c4:01:22:0d (capab=0x31 status=0 aid=1) 
[   28.667765] wlan0: associated 
[   28.667874] cfg80211: Calling CRDA for country: DE 
[   28.677250] cfg80211: Regulatory domain changed to country: DE 
[   28.677256] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   28.677258] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   28.677260] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   28.677262] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   28.677264] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm) 
[   28.677266] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm) 
[   51.393342] vboxdrv: Found 2 processor cores. 
[   51.653258] vboxpci: IOMMU not found (not registered) 
[  385.251661] type=1400 audit(1413711175.456:69): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home64/mark/.config/libaccounts-glib/accounts.db" pid=3922 comm="mission-control" requested_mask="rw" denied_mask="rw" fsuid=1000 ouid=1000 
[  385.251828] type=1400 audit(1413711175.456:70): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home64/mark/.config/libaccounts-glib/accounts.db" pid=3922 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000 
[  385.303182] type=1400 audit(1413711175.508:71): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home64/mark/.config/dconf/user" pid=3922 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000 
[  385.492615] type=1400 audit(1413711175.700:72): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home64/mark/.local/share/telepathy/mission-control/accounts.cfg" pid=3922 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000 
[  395.868723] cfg80211: Calling CRDA to update world regulatory domain 
[  395.877744] cfg80211: World regulatory domain updated: 
[  395.877752] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[  395.877755] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  395.877758] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  395.877760] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[  395.877763] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  395.877765] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  396.769304] wlan0: authenticate with 34:31:c4:01:22:0d 
[  396.793513] wlan0: send auth to 34:31:c4:01:22:0d (try 1/3) 
[  396.802622] wlan0: authenticated 
[  396.804057] wlan0: associate with 34:31:c4:01:22:0d (try 1/3) 
[  396.896459] wlan0: RX AssocResp from 34:31:c4:01:22:0d (capab=0x31 status=0 aid=1) 
[  396.896554] wlan0: associated 
[  396.896641] cfg80211: Calling CRDA for country: DE 
[  396.904229] cfg80211: Regulatory domain changed to country: DE 
[  396.904236] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[  396.904239] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[  396.904241] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[  396.904244] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[  396.904247] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm) 
[  396.904249] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm) 
[  401.844277] cfg80211: Calling CRDA to update world regulatory domain 
[  401.863662] cfg80211: World regulatory domain updated: 
[  401.863674] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[  401.863680] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  401.863685] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  401.863690] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[  401.863695] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  401.863699] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  402.729655] wlan0: authenticate with 34:31:c4:01:22:0d 
[  402.753727] wlan0: send auth to 34:31:c4:01:22:0d (try 1/3) 
[  402.800993] wlan0: authenticated 
[  402.804059] wlan0: associate with 34:31:c4:01:22:0d (try 1/3) 
[  402.915592] wlan0: associate with 34:31:c4:01:22:0d (try 2/3) 
[  403.015917] wlan0: associate with 34:31:c4:01:22:0d (try 3/3) 
[  403.068936] wlan0: association with 34:31:c4:01:22:0d timed out 
[  417.243131] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  448.876546] wlan0: authenticate with 34:31:c4:01:22:0d 
[  448.897958] wlan0: send auth to 34:31:c4:01:22:0d (try 1/3) 
[  448.902854] wlan0: authenticated 
[  448.904039] wlan0: associate with 34:31:c4:01:22:0d (try 1/3) 
[  448.934426] wlan0: RX AssocResp from 34:31:c4:01:22:0d (capab=0x31 status=0 aid=1) 
[  448.934480] wlan0: associated 
[  448.934521] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[  448.934631] cfg80211: Calling CRDA for country: DE 
[  448.944076] cfg80211: Regulatory domain changed to country: DE 
[  448.944083] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[  448.944086] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[  448.944088] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[  448.944090] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[  448.944092] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm) 
[  448.944094] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm) 
	Release Date: 11/20/2007 
		Serial services are supported (int 14h) 
	Manufacturer: MSI 
	Product Name: MS-7369 
	Serial Number: To Be Filled By O.E.M. 
	Manufacturer: MSI 
	Product Name: MS-7369 
	Serial Number: To be filled by O.E.M. 
	Manufacturer: To Be Filled By O.E.M. 
	Serial Number: To Be Filled By O.E.M. 
	Manufacturer: AMD              
	Serial Number: To Be Filled By O.E.M. 
	Port Type: Serial Port 16550A Compatible 
	Manufacturer: Manufacturer0 
	Serial Number: SerNum0 
	Manufacturer: Manufacturer1 
	Serial Number: SerNum1 
	Manufacturer: Manufacturer2 
	Serial Number: SerNum2 
	Manufacturer: Manufacturer3 
	Serial Number: SerNum3 
eth0      no wireless extensions. 

lo        no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:"MiWiFi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 34:31:C4:01:22:0D   
          Bit Rate=19.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:26  Invalid misc:2938   Missed beacon:0 

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; } 
options ath9k nohwcrypt=1 
# which ath5k cannot recover. To prevent this condition, stop 
blacklist ath_pci 
blacklist eth1394 
# replaced by p54pci 
blacklist prism54 
# replaced by b43 and ssb. 
blacklist bcm43xx 
blacklist uart6850 
blacklist twl4030_wdt 
# /etc/modprobe.d/iwlwifi.conf 
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the 
# microcode file installed on the system.  When removing iwlwifi, first 
# remove the iwl?vm module and then iwlwifi. 
remove iwlwifi \ 
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \ 
&& /sbin/modprobe -r mac80211 
[main] 
NetworkingEnabled=true 
WirelessEnabled=true 
WWANEnabled=true 
WimaxEnabled=true 
> hal.1: read hal dataprocess 7006: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282. 
This is normally a bug in some application using the D-Bus library. 
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files 
28: PCI 109.0: 0282 WLAN controller                             
  [Created at pci.318] 
  Unique ID: y9sn.fgU_neq4Gf1 
  Parent ID: RE4e.L5YND3qIlx3 
  SysFS ID: /devices/pci0000:00/0000:00:08.0/0000:01:09.0 
  SysFS BusID: 0000:01:09.0 
  Hardware Class: network 
  Model: "Atheros AR922X Wireless Network Adapter" 
  Vendor: pci 0x168c "Atheros Communications Inc." 
  Device: pci 0x0029 "AR922X Wireless Network Adapter" 
  SubVendor: pci 0x168c "Atheros Communications Inc." 
  SubDevice: pci 0x2093 
  Revision: 0x01 
  Driver: "ath9k" 
  Driver Modules: "ath9k", "ath9k" 
  Device File: wlan0 
  Features: WLAN 
  Memory Range: 0xfbef0000-0xfbefffff (rw,non-prefetchable) 
  IRQ: 18 (73971 events) 
  HW Address: e8:94:f6:4e:9d:6b 
  Link detected: yes 
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP 
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap 
  Module Alias: "pci:v0000168Cd00000029sv0000168Csd00002093bc02sc80i00" 
  Driver Info #0: 
    Driver Status: ath9k is active 
    Driver Activation Cmd: "modprobe ath9k" 
  Config Status: cfg=new, avail=yes, need=no, active=unknown 
  Attached to: #17 (PCI bridge) 

29: PCI 300.0: 0200 Ethernet controller 
  [Created at pci.318] 
  Unique ID: rBUF.CmmM0KavH6B 
  Parent ID: lgGW.fF85GV9wF2C 
  SysFS ID: /devices/pci0000:00/0000:00:0c.0/0000:03:00.0 
  SysFS BusID: 0000:03:00.0 
  Hardware Class: network 
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller" 
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd." 
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller" 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd." 
  SubDevice: pci 0x369c 
  Revision: 0x01 
  Driver: "r8169" 
  Driver Modules: "r8169" 
  Device File: eth0 
  I/O Ports: 0xe800-0xe8ff (rw) 
  Memory Range: 0xfbfff000-0xfbffffff (rw,non-prefetchable) 
  Memory Range: 0xfbfc0000-0xfbfdffff (ro,non-prefetchable,disabled) 
  IRQ: 45 (1071 events) 
  HW Address: 00:19:db:d0:be:f3 
  Link detected: yes 
  Module Alias: "pci:v000010ECd00008168sv00001462sd0000369Cbc02sc00i00" 
  Driver Info #0: 
    Driver Status: r8169 is active 
    Driver Activation Cmd: "modprobe r8169" 
  Config Status: cfg=new, avail=yes, need=no, active=unknown 
  Attached to: #25 (PCI bridge) 
root       922  0.0  0.1 346560  6408 ?        Ssl  11:26   0:01 NetworkManager 
root       990  0.0  0.0  30608  2692 ?        Ss   11:26   0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant 
nobody    1261  0.0  0.0  36696  1508 ?        S    11:26   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d 
root      4403  0.0  0.0  10232  3668 ?        S    11:33   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-wlan0.pid -lf /var/lib/NetworkManager/dhclient-dca3d901-f15f-4852-a9d0-2f48626cfc5a-wlan0.lease -cf /var/lib/NetworkManager/dhclient-wlan0.conf wlan0 
mark      7020  0.0  0.0  15116   920 pts/10   R+   12:10   0:00 egrep --color=auto wpa|icd|etwork 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface 
0.0.0.0         192.168.178.1   0.0.0.0         UG        0 0          0 wlan0 
192.168.178.0   0.0.0.0         255.255.255.0   U         0 0          0 wlan0 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1 
search fritz.box 
total 213712 
786433 drwxr-xr-x  3 root root     4096 Okt 19 11:22 . 
     2 drwxr-xr-x 25 root root     4096 Okt 19 11:20 .. 
788438 -rw-r--r--  1 root root  1158016 Mai  3 02:30 abi-3.13.0-24-generic 
793289 -rw-r--r--  1 root root  1162712 Aug 13 18:45 abi-3.13.0-34-generic 
786437 -rw-r--r--  1 root root  1163858 Aug 15 04:56 abi-3.13.0-35-generic 
792759 -rw-r--r--  1 root root  1163858 Sep  4 00:24 abi-3.13.0-36-generic 
792901 -rw-r--r--  1 root root  1164489 Sep 23 00:24 abi-3.13.0-37-generic 
793192 -rw-r--r--  1 root root  1164489 Okt  9 14:33 abi-3.13.0-38-generic 
788437 -rw-r--r--  1 root root   165510 Mai  3 02:30 config-3.13.0-24-generic 
793288 -rw-r--r--  1 root root   165611 Aug 13 18:45 config-3.13.0-34-generic 
786435 -rw-r--r--  1 root root   165652 Aug 15 04:56 config-3.13.0-35-generic 
792786 -rw-r--r--  1 root root   165671 Sep  4 00:24 config-3.13.0-36-generic 
792903 -rw-r--r--  1 root root   165712 Sep 23 00:24 config-3.13.0-37-generic 
793190 -rw-r--r--  1 root root   165712 Okt  9 14:33 config-3.13.0-38-generic 
786434 drwxr-xr-x  6 root root     4096 Okt 19 11:22 grub 
792050 -rw-r--r--  1 root root 19101280 Sep  4 13:55 initrd.img-3.13.0-24-generic 
806234 -rw-r--r--  1 root root 27190788 Sep  9 14:19 initrd.img-3.13.0-34-generic 
801448 -rw-r--r--  1 root root 27202236 Sep 11 16:54 initrd.img-3.13.0-35-generic 
788011 -rw-r--r--  1 root root 27216123 Okt  3 09:35 initrd.img-3.13.0-36-generic 
792907 -rw-r--r--  1 root root 27214968 Okt  3 10:25 initrd.img-3.13.0-37-generic 
787319 -rw-r--r--  1 root root 27218738 Okt 19 11:22 initrd.img-3.13.0-38-generic 
786438 -rw-r--r--  1 root root   176500 Mär 12  2014 memtest86+.bin 
786439 -rw-r--r--  1 root root   178176 Mär 12  2014 memtest86+.elf 
786440 -rw-r--r--  1 root root   178680 Mär 12  2014 memtest86+_multiboot.bin 
788439 -rw-------  1 root root  3372643 Mai  3 02:30 System.map-3.13.0-24-generic 
793290 -rw-------  1 root root  3381262 Aug 13 18:45 System.map-3.13.0-34-generic 
788440 -rw-------  1 root root  3386444 Aug 15 04:56 System.map-3.13.0-35-generic 
792785 -rw-------  1 root root  3386479 Sep  4 00:24 System.map-3.13.0-36-generic 
792904 -rw-------  1 root root  3386945 Sep 23 00:24 System.map-3.13.0-37-generic 
793191 -rw-------  1 root root  3386936 Okt  9 14:33 System.map-3.13.0-38-generic 
788436 -rw-------  1 root root  5776416 Mai  3 02:30 vmlinuz-3.13.0-24-generic 
793291 -rw-------  1 root root  5797728 Aug 13 18:45 vmlinuz-3.13.0-34-generic 
786436 -rw-------  1 root root  5806368 Aug 15 04:56 vmlinuz-3.13.0-35-generic 
792787 -rw-------  1 root root  5806848 Sep  4 00:24 vmlinuz-3.13.0-36-generic 
792902 -rw-------  1 root root  5808832 Sep 23 00:24 vmlinuz-3.13.0-37-generic 
793186 -rw-------  1 root root  5808736 Okt  9 14:33 vmlinuz-3.13.0-38-generic 
Support status summary of 'mark-ubu64': 

You have 2439 packages (78.3%) supported until Mai 2019 (5y) 
You have 161 packages (5.2%) supported until Februar 2015 (9m) 
You have 16 packages (0.5%) supported until Juli 2015 (9m) 
You have 272 packages (8.7%) supported until Mai 2017 (3y) 

You have 4 packages (0.1%) that can not/no-longer be downloaded 
You have 223 packages (7.2%) that are unsupported 

Run with --show-unsupported, --show-supported or --show-all to see more details 
Module                  Size  Used by 
joydev                 17381  0 
nfnetlink_queue        22329  1 
nfnetlink              14606  2 nfnetlink_queue 
nf_conntrack_ipv4      15012  3 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4 
xt_tcpudp              12884  8 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter 
xt_iprange             12783  0 
xt_conntrack           12760  3 
nf_conntrack           96976  2 xt_conntrack,nf_conntrack_ipv4 
ipt_REJECT             12541  1 
xt_mark                12563  6 
xt_NFQUEUE             12776  3 
x_tables               34059  8 xt_iprange,xt_mark,ip_tables,xt_tcpudp,xt_NFQUEUE,xt_conntrack,iptable_filter,ipt_REJECT 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               409815  3 vboxnetadp,vboxnetflt,vboxpci 
ctr                    13049  3 
ccm                    17773  3 
rfcomm                 69160  4 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm 
binfmt_misc            17468  1 
arc4                   12608  2 
snd_hda_codec_realtek    65580  1 
nvidia              11334886  40 
snd_hda_intel          56451  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13602  1 snd_hda_codec 
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_rawmidi            30144  1 snd_seq_midi 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi 
ath9k_hw              453856  2 ath9k_common,ath9k 
kvm_amd                59987  0 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi 
snd_timer              29482  2 snd_pcm,snd_seq 
kvm                   451552  1 kvm_amd 
mac80211              630653  1 ath9k 
snd                    69322  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi 
ppdev                  17671  0 
soundcore              12680  1 snd 
cfg80211              484040  3 ath,ath9k,mac80211 
w83627ehf              42987  0 
hwmon_vid              12783  1 w83627ehf 
edac_core              62291  0 
serio_raw              13462  0 
edac_mce_amd           22617  0 
k8temp                 12978  0 
lm90                   20490  0 
i2c_nforce2            13221  0 
parport_pc             32701  1 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc 
mac_hid                13205  0 
uvesafb                28686  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid 
pata_acpi              13038  0 
psmouse               106678  0 
r8169                  67581  0 
mii                    13934  1 r8169 
floppy                 69418  0 
ahci                   25819  4 
libahci                32716  1 ahci 
pata_amd               18225  0 

```

I also have a 32 bit installation. This has been updated/upgraded using LTS releases from an original Gutsy install. The wifi is much more stable here, once even started on resume after a suspend!!!! But it's slow - as is the wifi on 64 bit, when I can get it working. The 32 bit also has Gnome, Lubuntu & Kubuntu desktops installed along with Ubuntu. I can't think why that would improve the Wifi - the kernel being the same - but perhaps there's a good reason for the 32 bit being more stable. Before anyone suggests that I stick with the 32 bit install - I can't install any 64 bit programs, e.g. windows 7, in virtual box & using 64 bit installation on a 64 bit machine is supposed to be more efficient, isn't it?

Here's the wireless script output
```
Package hwinfo is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 

E: Package 'hwinfo' has no installation candidate 
  *-network               
       description: Wireless interface 
       product: AR922X Wireless Network Adapter 
       vendor: Qualcomm Atheros 
       physical id: a 
       bus info: pci@0000:01:0a.0 
       logical name: wlan0 
       version: 01 
       serial: e8:94:f6:4e:9d:6b 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-36-generic firmware=N/A ip=192.168.178.31 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:18 memory:fbef0000-fbefffff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth2 
       version: 01 
       serial: 00:19:db:d0:be:f3 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:45 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbfc0000-fbfdffff 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
lo        Interface doesn't support scanning. 

eth2      Interface doesn't support scanning. 

                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    ESSID:"MiWiFi" 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    ESSID:"Willy.tel IO" 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    ESSID:"WILLY.TEL-89H4294Y" 
auto lo 
iface lo inet loopback 

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=14.04 
DISTRIB_CODENAME=trusty 
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS" 
01:0a.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01) 
	Subsystem: Qualcomm Atheros Device [168c:2093] 
	Kernel driver in use: ath9k 
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01) 
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:369c] 
	Kernel driver in use: r8169 
Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 002: ID 046a:0001 Cherry GmbH My3000 Keyboard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  
H/W path        Device      Class       Description 
=================================================== 
                            system      MS-7369 (To Be Filled By O.E.M.) 
/0                          bus         MS-7369 
/0/0                        memory      64KiB BIOS 
/0/4                        processor   AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ 
/0/4/5                      memory      128KiB L1 cache 
/0/4/6                      memory      512KiB L2 cache 
/0/2d                       memory      4GiB System Memory 
/0/2d/0                     memory      1GiB DIMM DDR2 Synchronous 
/0/2d/1                     memory      1GiB DIMM DDR2 Synchronous 
/0/2d/2                     memory      1GiB DIMM DDR2 Synchronous 
/0/2d/3                     memory      1GiB DIMM DDR2 Synchronous 
/0/3                        processor   
/0/3/0                      memory      128KiB L1 cache 
/0/3/1                      memory      512KiB L2 cache 
/0/5                        memory      RAM memory 
/0/1                        bridge      MCP65 LPC Bridge 
/0/1.1                      bus         MCP65 SMBus 
/0/1.2                      memory      RAM memory 
/0/2                        bus         MCP65 USB 1.1 OHCI Controller 
/0/2.1                      bus         MCP65 USB 2.0 EHCI Controller 
/0/7                        multimedia  MCP65 High Definition Audio 
/0/8                        bridge      MCP65 PCI bridge 
/0/8/a          wlan0       network     AR922X Wireless Network Adapter 
/0/9                        storage     MCP65 IDE 
/0/a                        storage     MCP65 AHCI Controller 
/0/b                        bridge      MCP65 PCI Express bridge 
/0/c                        bridge      MCP65 PCI Express bridge 
/0/c/0          eth2        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
/0/d                        bridge      MCP65 PCI Express bridge 
/0/d/0                      display     NV40 [GeForce 6800 GT/GTO/Ultra] 
/0/e                        bridge      MCP65 PCI Express bridge 
/0/100                      bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
/0/101                      bridge      K8 [Athlon64/Opteron] Address Map 
/0/102                      bridge      K8 [Athlon64/Opteron] DRAM Controller 
/0/103                      bridge      K8 [Athlon64/Opteron] Miscellaneous Control 
/0/6            scsi0       storage     
/0/6/0.0.0      /dev/cdrom  disk        DVD-ROM DDU1615 
/0/f            scsi4       storage     
/0/f/0.0.0      /dev/sda    disk        1TB WDC WD10EALX-009 
/0/f/0.0.0/1    /dev/sda1   volume      48GiB EXT4 volume 
/0/f/0.0.0/2    /dev/sda2   volume      371GiB Extended partition 
/0/f/0.0.0/2/5  /dev/sda5   volume      9006MiB Linux swap / Solaris partition 
/0/f/0.0.0/2/6  /dev/sda6   volume      362GiB Linux filesystem partition 
/0/f/0.0.0/3    /dev/sda3   volume      44GiB EXT4 volume 
/0/f/0.0.0/4    /dev/sda4   volume      466GiB EXT4 volume 
/0/10           scsi5       storage     
/0/10/0.0.0     /dev/sr1    disk        DVDRAM GH24NSB0 
Linux mark-ubu 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 athlon i686 GNU/Linux 
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780] 
[    0.163756] ACPI: No dock devices found. 
[    0.178163] Found 1 acpi root devices 
[    0.178293] usbcore: registered new interface driver usbfs 
[    0.178293] usbcore: registered new interface driver hub 
[    0.178293] usbcore: registered new device driver usb 
[    0.181020] Switched to clocksource hpet 
[    0.190675] pnp: PnP ACPI: found 13 devices 
[    0.304471] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.304519] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.304575] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.304632] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.304693] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.304757] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.304826] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    1.012082] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002 
[    1.012085] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    1.012087] usb usb1: Product: EHCI Host Controller 
[    1.012090] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd 
[    1.012093] usb usb1: SerialNumber: 0000:00:02.1 
[    1.012203] hub 1-0:1.0: USB hub found 
[    1.070041] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001 
[    1.070044] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    1.070047] usb usb2: Product: OHCI PCI host controller 
[    1.070049] usb usb2: Manufacturer: Linux 3.13.0-36-generic ohci_hcd 
[    1.070052] usb usb2: SerialNumber: 0000:00:02.0 
[    1.070152] hub 2-0:1.0: USB hub found 
[    1.070480] i8042: PNP: No PS/2 controller found. Probing ports directly. 
[    1.078737] Loaded X.509 cert 'Magrathea: Glacier signing key: ff9ada11b855516a7298659d4e3fbb76c54ad330' 
[    1.093364] IMA: No TPM chip found, activating TPM-bypass! 
[    1.093934] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (2 cpu cores) (version 2.20.00) 
[    1.093941] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.327420] isapnp: No Plug & Play device found 
[    1.381224] usb 1-4: new high-speed USB device number 3 using ehci-pci 
[    1.410289] r8169 0000:03:00.0 eth0: RTL8168b/8111b at 0xf8410000, 00:19:db:d0:be:f3, XID 18000000 IRQ 45 
[    1.410292] r8169 0000:03:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko] 
[    1.513235] usb 1-4: New USB device found, idVendor=05e3, idProduct=0608 
[    1.513241] usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0 
[    1.513245] usb 1-4: Product: USB2.0 Hub 
[    1.513645] hub 1-4:1.0: USB hub found 
[    1.816049] usb 2-2: new low-speed USB device number 2 using ohci-pci 
[    2.029041] usb 2-2: New USB device found, idVendor=046a, idProduct=0001 
[    2.029047] usb 2-2: New USB device strings: Mfr=1, Product=0, SerialNumber=0 
[    2.029050] usb 2-2: Manufacturer: Cherry GmbH 
[    2.057525] usbcore: registered new interface driver usbhid 
[    2.057529] usbhid: USB HID core driver 
[    2.062942] input: Cherry GmbH as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input5 
[    2.063060] hid-generic 0003:046A:0001.0001: input,hidraw0: USB HID v1.11 Keyboard [Cherry GmbH] on usb-0000:00:02.0-2/input0 
[    2.104244] usb 1-4.1: new low-speed USB device number 4 using ehci-pci 
[    2.200112] usb 1-4.1: New USB device found, idVendor=093a, idProduct=2510 
[    2.200117] usb 1-4.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
[    2.200121] usb 1-4.1: Product: USB Optical Mouse 
[    2.200123] usb 1-4.1: Manufacturer: PixArt 
[    2.203369] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4.1/1-4.1:1.0/input/input6 
[    2.203516] hid-generic 0003:093A:2510.0002: input,hidraw1: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:02.1-4.1/input0 
[    3.502221] Console: switching to colour frame buffer device 160x64 
[   16.241667] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   16.894747] lp: driver loaded but no devices found 
[   16.920186] systemd-udevd[342]: renamed network interface eth0 to eth2 
[   17.000300] cfg80211: Calling CRDA to update world regulatory domain 
[   18.422623] cfg80211: World regulatory domain updated: 
[   18.422629] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   18.422632] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.422634] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.422637] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   18.422639] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.422641] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   18.961695] ath: EEPROM regdomain: 0x809c 
[   18.961700] ath: EEPROM indicates we should expect a country code 
[   18.961702] ath: doing EEPROM country->regdmn map search 
[   18.961704] ath: country maps to regdmn code: 0x52 
[   18.961706] ath: Country alpha2 being used: CN 
[   18.961708] ath: Regpair used: 0x52 
[   19.037324] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht' 
[   19.037940] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xf9d60000, irq=18 
[   19.038875] cfg80211: Calling CRDA for country: CN 
[   19.041208] w83627ehf: Found W83627DHG chip at 0xa10 
[   19.103397] cfg80211: Regulatory domain changed to country: CN 
[   19.103403] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   19.103406] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   19.103408] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm) 
[   19.103410] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm) 
[   19.103412] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm) 
[   19.103414] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm) 
[   20.511439] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro 
[   20.968161] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input14 
[   20.968278] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input13 
[   20.968355] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input12 
[   20.968432] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input11 
[   20.968510] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input10 
[   20.968586] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input9 
[   20.968655] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input8 
[   20.968732] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input7 
[   24.831854] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   24.837761] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   24.861317] r8169 0000:03:00.0 eth2: link down 
[   24.861333] r8169 0000:03:00.0 eth2: link down 
[   24.861385] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready 
[   24.862348] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready 
[   26.564180] wlan0: authenticate with 34:31:c4:01:22:0d 
[   26.582471] wlan0: direct probe to 34:31:c4:01:22:0d (try 1/3) 
[   26.784021] wlan0: direct probe to 34:31:c4:01:22:0d (try 2/3) 
[   26.988023] wlan0: direct probe to 34:31:c4:01:22:0d (try 3/3) 
[   27.192051] wlan0: authentication with 34:31:c4:01:22:0d timed out 
[   27.264431] wlan0: authenticate with 34:31:c4:01:22:0d 
[   27.283061] wlan0: direct probe to 34:31:c4:01:22:0d (try 1/3) 
[   27.484024] wlan0: direct probe to 34:31:c4:01:22:0d (try 2/3) 
[   27.688019] wlan0: send auth to 34:31:c4:01:22:0d (try 3/3) 
[   27.692941] wlan0: authenticated 
[   27.696030] wlan0: associate with 34:31:c4:01:22:0d (try 1/3) 
[   27.734133] wlan0: RX AssocResp from 34:31:c4:01:22:0d (capab=0x31 status=0 aid=1) 
[   27.734186] wlan0: associated 
[   27.734219] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   27.734291] cfg80211: Calling CRDA for country: DE 
[   27.738455] cfg80211: Regulatory domain changed to country: DE 
[   27.738460] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   27.738463] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   27.738465] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   27.738467] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm) 
[   27.738469] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm) 
[   27.738471] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm) 
[   60.738953] vboxdrv: Found 2 processor cores. 
[   60.861468] vboxpci: IOMMU not found (not registered) 
[   78.930857] type=1400 audit(1412416700.160:72): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home32/mark/.config/libaccounts-glib/accounts.db" pid=3423 comm="mission-control" requested_mask="rw" denied_mask="rw" fsuid=1000 ouid=1000 
[   78.930994] type=1400 audit(1412416700.160:73): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home32/mark/.config/libaccounts-glib/accounts.db" pid=3423 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000 
[   78.935595] type=1400 audit(1412416700.164:74): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home32/mark/.config/dconf/user" pid=3423 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000 
[   79.209830] type=1400 audit(1412416700.440:75): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home32/mark/.local/share/telepathy/mission-control/accounts.cfg" pid=3423 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000 
[   79.224499] type=1400 audit(1412416700.456:76): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/media/WORK/home32/mark/.cache/.mc_connections" pid=3423 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000 
	Release Date: 11/20/2007 
		Serial services are supported (int 14h) 
	Manufacturer: MSI 
	Product Name: MS-7369 
	Serial Number: To Be Filled By O.E.M. 
	Manufacturer: MSI 
	Product Name: MS-7369 
	Serial Number: To be filled by O.E.M. 
	Manufacturer: To Be Filled By O.E.M. 
	Serial Number: To Be Filled By O.E.M. 
	Manufacturer: AMD              
	Serial Number: To Be Filled By O.E.M. 
	Port Type: Serial Port 16550A Compatible 
	Manufacturer: Manufacturer0 
	Serial Number: SerNum0 
	Manufacturer: Manufacturer1 
	Serial Number: SerNum1 
	Manufacturer: Manufacturer2 
	Serial Number: SerNum2 
	Manufacturer: Manufacturer3 
	Serial Number: SerNum3 
wlan0     IEEE 802.11bgn  ESSID:"MiWiFi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 34:31:C4:01:22:0D   
          Bit Rate=26 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:25  Invalid misc:1817   Missed beacon:0 

lo        no wireless extensions. 

eth2      no wireless extensions. 

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; } 
options ath9k nohwcrypt=1 
# which ath5k cannot recover. To prevent this condition, stop 
blacklist ath_pci 
blacklist eth1394 
# replaced by p54pci 
blacklist prism54 
# replaced by b43 and ssb. 
blacklist bcm43xx 
blacklist uart6850 
blacklist twl4030_wdt 
# /etc/modprobe.d/iwlwifi.conf 
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the 
# microcode file installed on the system.  When removing iwlwifi, first 
# remove the iwl?vm module and then iwlwifi. 
remove iwlwifi \ 
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \ 
&& /sbin/modprobe -r mac80211 

[main] 
NetworkingEnabled=true 
WirelessEnabled=true 
WWANEnabled=true 
WimaxEnabled=true 
sudo: hwinfo: command not found 
root       999  0.0  0.1  53276  5908 ?        Ssl  11:57   0:01 NetworkManager 
root      1166  0.0  0.0   6916  2392 ?        Ss   11:57   0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant 
root      1246  0.0  0.0   5520  3048 ?        S    11:57   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-wlan0.pid -lf /var/lib/NetworkManager/dhclient-41da7d5c-791e-4a4f-a0ba-9f3fb1f6f2d8-wlan0.lease -cf /var/lib/NetworkManager/dhclient-wlan0.conf wlan0 
nobody    1310  0.0  0.0   5556  1396 ?        S    11:57   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d 
mark     16712  0.0  0.0   4440   772 pts/2    S+   12:57   0:00 egrep --color=auto wpa|icd|etwork 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface 
0.0.0.0         192.168.178.1   0.0.0.0         UG        0 0          0 wlan0 
192.168.178.0   0.0.0.0         255.255.255.0   U         0 0          0 wlan0 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1 
search fritz.box 
total 319444 
652801 drwxr-xr-x  3 root root    12288 Oct  4 12:15 . 
     2 drwxr-xr-x 23 root root     4096 Sep 30 09:41 .. 
652809 -rw-r--r--  1 root root   652718 Feb 14  2012 abi-2.6.32-39-generic 
687289 -rw-r--r--  1 root root   656085 Feb 14  2012 abi-2.6.32-39-generic-pae 
690713 -rw-r--r--  1 root root   656137 Mar  6  2012 abi-2.6.32-40-generic-pae 
676579 -rw-r--r--  1 root root   656323 Mar 29  2012 abi-2.6.32-41-generic-pae 
653240 -rw-r--r--  1 root root  1166929 Aug 13 18:58 abi-3.13.0-34-generic 
653750 -rw-r--r--  1 root root  1168075 Aug 15 05:09 abi-3.13.0-35-generic 
653098 -rw-r--r--  1 root root  1168075 Sep  4 00:36 abi-3.13.0-36-generic 
653061 -rw-r--r--  1 root root   800195 Apr 11  2012 abi-3.2.0-23-generic-pae 
653097 -rw-r--r--  1 root root   804930 Feb 19  2014 abi-3.2.0-60-generic-pae 
653121 -rw-r--r--  1 root root   804930 May  3 00:34 abi-3.2.0-61-generic-pae 
653173 -rw-r--r--  1 root root   805098 May 16 02:28 abi-3.2.0-63-generic-pae 
653178 -rw-r--r--  1 root root   805098 Jun  5 01:20 abi-3.2.0-64-generic-pae 
653187 -rw-r--r--  1 root root   805098 Jul  5 00:05 abi-3.2.0-65-generic-pae 
653107 -rw-r--r--  1 root root   805150 Jul 15 21:05 abi-3.2.0-67-generic-pae 
652807 -rw-r--r--  1 root root   116014 Feb 14  2012 config-2.6.32-39-generic 
687288 -rw-r--r--  1 root root   116469 Feb 14  2012 config-2.6.32-39-generic-pae 
690712 -rw-r--r--  1 root root   116469 Mar  6  2012 config-2.6.32-40-generic-pae 
676578 -rw-r--r--  1 root root   116469 Mar 29  2012 config-2.6.32-41-generic-pae 
653230 -rw-r--r--  1 root root   169732 Aug 13 18:58 config-3.13.0-34-generic 
653280 -rw-r--r--  1 root root   169722 Aug 15 05:09 config-3.13.0-35-generic 
653093 -rw-r--r--  1 root root   169741 Sep  4 00:36 config-3.13.0-36-generic 
653062 -rw-r--r--  1 root root   147226 Apr 11  2012 config-3.2.0-23-generic-pae 
653096 -rw-r--r--  1 root root   147559 Feb 19  2014 config-3.2.0-60-generic-pae 
653124 -rw-r--r--  1 root root   147559 May  3 00:34 config-3.2.0-61-generic-pae 
653172 -rw-r--r--  1 root root   147587 May 16 02:28 config-3.2.0-63-generic-pae 
653169 -rw-r--r--  1 root root   147587 Jun  5 01:20 config-3.2.0-64-generic-pae 
653186 -rw-r--r--  1 root root   147587 Jul  5 00:05 config-3.2.0-65-generic-pae 
653183 -rw-r--r--  1 root root   147588 Jul 15 21:05 config-3.2.0-67-generic-pae 
652804 drwxr-xr-x  6 root root    12288 Oct  3 07:55 grub 
653049 -rw-r--r--  1 root root  8003738 Feb 18  2012 initrd.img-2.6.32-39-generic 
683626 -rw-r--r--  1 root root  7958967 Mar  9  2012 initrd.img-2.6.32-39-generic-pae 
686322 -rw-r--r--  1 root root 12553998 Mar 23  2012 initrd.img-2.6.32-40-generic-pae 
675821 -rw-r--r--  1 root root 12555377 Apr 12  2012 initrd.img-2.6.32-41-generic-pae 
653094 -rw-r--r--  1 root root 18810645 Aug 18 09:39 initrd.img-3.13.0-34-generic 
653074 -rw-r--r--  1 root root 26465500 Sep 11 22:27 initrd.img-3.13.0-35-generic 
653101 -rw-r--r--  1 root root 26472647 Oct  4 12:15 initrd.img-3.13.0-36-generic 
653066 -rw-r--r--  1 root root 14141843 Apr 20 20:55 initrd.img-3.2.0-23-generic-pae 
653099 -rw-r--r--  1 root root 14209302 Apr 20 20:58 initrd.img-3.2.0-60-generic-pae 
653117 -rw-r--r--  1 root root 14208863 May 25 17:40 initrd.img-3.2.0-61-generic-pae 
653175 -rw-r--r--  1 root root 14209232 May 27 08:15 initrd.img-3.2.0-63-generic-pae 
653180 -rw-r--r--  1 root root 14209417 Jun  6 08:21 initrd.img-3.2.0-64-generic-pae 
653106 -rw-r--r--  1 root root 14193178 Jul  6 13:26 initrd.img-3.2.0-65-generic-pae 
653271 -rw-r--r--  1 root root 14069308 Aug 15 12:37 initrd.img-3.2.0-67-generic-pae 
653252 -rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin 
653254 -rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf 
653250 -rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin 
652810 -rw-r--r--  1 root root  1693223 Feb 14  2012 System.map-2.6.32-39-generic 
687290 -rw-r--r--  1 root root  1734310 Feb 14  2012 System.map-2.6.32-39-generic-pae 
690714 -rw-r--r--  1 root root  1734549 Mar  6  2012 System.map-2.6.32-40-generic-pae 
676580 -rw-r--r--  1 root root  1735263 Mar 29  2012 System.map-2.6.32-41-generic-pae 
653236 -rw-------  1 root root  2693057 Aug 13 18:58 System.map-3.13.0-34-generic 
653758 -rw-------  1 root root  2697306 Aug 15 05:09 System.map-3.13.0-35-generic 
653048 -rw-------  1 root root  2697363 Sep  4 00:36 System.map-3.13.0-36-generic 
653060 -rw-------  1 root root  2313006 Apr 11  2012 System.map-3.2.0-23-generic-pae 
653095 -rw-------  1 root root  2321933 Feb 19  2014 System.map-3.2.0-60-generic-pae 
653122 -rw-------  1 root root  2321933 May  3 00:34 System.map-3.2.0-61-generic-pae 
653108 -rw-------  1 root root  2322710 May 16 02:28 System.map-3.2.0-63-generic-pae 
653177 -rw-------  1 root root  2323570 Jun  5 01:20 System.map-3.2.0-64-generic-pae 
653188 -rw-------  1 root root  2323677 Jul  5 00:05 System.map-3.2.0-65-generic-pae 
653190 -rw-------  1 root root  2323784 Jul 15 21:05 System.map-3.2.0-67-generic-pae 
652997 -rw-r--r--  1 root root     1196 Feb 14  2012 vmcoreinfo-2.6.32-39-generic 
687291 -rw-r--r--  1 root root     1200 Feb 14  2012 vmcoreinfo-2.6.32-39-generic-pae 
690715 -rw-r--r--  1 root root     1200 Mar  6  2012 vmcoreinfo-2.6.32-40-generic-pae 
676581 -rw-r--r--  1 root root     1200 Mar 29  2012 vmcoreinfo-2.6.32-41-generic-pae 
652806 -rw-r--r--  1 root root  4048992 Feb 14  2012 vmlinuz-2.6.32-39-generic 
687287 -rw-r--r--  1 root root  4181888 Feb 14  2012 vmlinuz-2.6.32-39-generic-pae 
690711 -rw-r--r--  1 root root  4181984 Mar  6  2012 vmlinuz-2.6.32-40-generic-pae 
676577 -rw-r--r--  1 root root  4182592 Mar 29  2012 vmlinuz-2.6.32-41-generic-pae 
653242 -rw-------  1 root root  5820592 Aug 13 18:58 vmlinuz-3.13.0-34-generic 
653771 -rw-------  1 root root  5826864 Aug 15 05:09 vmlinuz-3.13.0-35-generic 
653078 -rw-------  1 root root  5826768 Sep  4 00:36 vmlinuz-3.13.0-36-generic 
653065 -rw-r--r--  1 root root  5015840 Apr 23  2012 vmlinuz-3.2.0-23-generic-pae 
653064 -rw-------  1 root root  5032480 Feb 19  2014 vmlinuz-3.2.0-60-generic-pae 
653125 -rw-------  1 root root  5031904 May  3 00:34 vmlinuz-3.2.0-61-generic-pae 
653174 -rw-------  1 root root  5034176 May 16 02:28 vmlinuz-3.2.0-63-generic-pae 
653179 -rw-------  1 root root  5036352 Jun  5 01:20 vmlinuz-3.2.0-64-generic-pae 
653185 -rw-------  1 root root  5036576 Jul  5 00:05 vmlinuz-3.2.0-65-generic-pae 
653184 -rw-------  1 root root  5037728 Jul 15 21:05 vmlinuz-3.2.0-67-generic-pae 
Support status summary of 'mark-ubu': 

You have 150 packages (4.9%) supported until February 2015 (9m) 
You have 12 packages (0.4%) supported until July 2015 (9m) 
You have 266 packages (8.6%) supported until May 2017 (3y) 
You have 2296 packages (74.3%) supported until May 2019 (5y) 

You have 121 packages (3.9%) that can not/no longer be downloaded 
You have 244 packages (7.9%) that are unsupported 

Run with --show-unsupported, --show-supported or --show-all to see more details 
Module                  Size  Used by 
nfnetlink_queue        17823  0 
nfnetlink              14214  1 nfnetlink_queue 
nf_conntrack_ipv4      14492  0 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4 
xt_tcpudp              12756  0 
iptable_filter         12706  0 
ip_tables              17987  1 iptable_filter 
xt_iprange             12679  0 
xt_conntrack           12664  0 
nf_conntrack           83685  2 xt_conntrack,nf_conntrack_ipv4 
ipt_REJECT             12485  0 
xt_mark                12499  0 
xt_NFQUEUE             12672  0 
x_tables               22067  8 xt_iprange,xt_mark,ip_tables,xt_tcpudp,xt_NFQUEUE,xt_conntrack,iptable_filter,ipt_REJECT 
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               299807  3 vboxnetadp,vboxnetflt,vboxpci 
ctr                    12905  3 
ccm                    17496  3 
rfcomm                 53664  4 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm 
binfmt_misc            13140  1 
w83627ehf              33635  0 
arc4                   12536  2 
snd_hda_codec_realtek    55163  1 
hwmon_vid              12687  1 w83627ehf 
lm90                   19770  0 
ppdev                  17391  0 
nvidia              10304642  40 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13272  1 snd_hda_codec 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_rawmidi            25135  1 snd_seq_midi 
ath9k                 144602  0 
ath9k_common           13359  1 ath9k 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi 
ath9k_hw              438205  2 ath9k_common,ath9k 
snd_timer              28584  2 snd_pcm,snd_seq 
kvm_amd                50537  0 
kvm                   388084  1 kvm_amd 
ath                    23922  3 ath9k_common,ath9k,ath9k_hw 
k8temp                 12842  0 
mac80211              546051  1 ath9k 
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi 
serio_raw              13230  0 
cfg80211              409394  3 ath,ath9k,mac80211 
soundcore              12600  1 snd 
parport_pc             31981  1 
lp                     13299  0 
i2c_nforce2            13037  0 
parport                40836  3 lp,ppdev,parport_pc 
mac_hid                13037  0 
uvesafb                27862  1 
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid 
pata_acpi              12886  0 
psmouse                91329  0 
r8169                  61562  0 
mii                    13654  1 r8169 
ahci                   25579  4 
floppy                 55416  0 
pata_amd               13761  0 
libahci                27214  1 ahci

```

A couple of other observations
There's no problem with the wifi signal. I ran for two days using a TP-Link TL-MR3020 (a kind of all in one repeater, receiver, hotspot box) plugged into my ethernet and it ran without interuption and reasonably fast.

There's no problem with the ath9k driver. I have an ASUS X55A laptop with built in Wifi. I've never experienced any cut-out, or drop-off, on this amchine. Of course, it's never been running for more than 3 or 4 hours at a time, but to get 3 or 4 hours stable Wifi on my desktop would be a miracle!

I wasn't able to get any wifi using a live CD - but that may have something to do with NVIDEA incompatibility - the live Cd takes about 20 minutes to load in any case.

So, that leaves some kind of software/hardware incompatibility. Plug and play Wifi seems to be a lottery. I'd hazard a guess that around 70% of Ubuntu users put there own machines together in one form or another, and the WN951N is one of the top 10 wifi network cards on the market. As someone who has been happily using ubuntu for the last 7 years, it's come as a bit of a shock that there is no 'fix' for this. This is the first time I've really had to post anything on the forums, there's always been someone who's had the problem and there's usually been another someone who knows how to fix said problem. I've spend 7 weeks trawling through these posts and have yet to read anyone whose found a solution. For anyone who is searching I'd recommend checking the links suggested by Kirk Schnabel in this post [http://ubuntuforums.org/showthread.php?t=2017181](http://ubuntuforums.org/showthread.php?t=2017181) If you can't fix it with the info you find there, you're probably wasting your time.

For any developers working on this problem, I'm leaving the Wifi card in for now and will gladly be your guinea pig - wifi has an advantage with windows sharing that I'd like to be able to use.

---

### Post by Hamburgian on 2014-10-20
deleted

---

### Post by Hamburgian on 2014-10-20
deleted

---

