---
title: "ASUS laptop with Ralink RT5390 not working properly"
date: 2015-05-04
forum: Networking &amp; Wireless
---

### Post by antonio42 on 2015-05-04
Hi! I am new to all this open source lifestyle and i have a problem that i can't fix.

I have tried and installed Linux Mint 17.1, Ubuntu 14.04.02 LTS and Xubuntu 14.04.02 (currently installed and running Xub) and i seem to have the same problem in all distros.

Wifi is not working properly, i get less signal comparing it to Win8 and it is pretty intermitent. My extensive investigation all over Google seems to be a common issue with the rt2800pci driver and the device RT5390 from Ralink and you are better off installing the propietary drivers. Problem is the drivers are for a pretty old kernel version.

I've followed various approaches like this one: [https://github.com/agerwick/RT28XX-RT539X-Linux-driver](https://github.com/agerwick/RT28XX-RT539X-Linux-driver) or this one [http://www.ptrxyz.de/?p=161](http://www.ptrxyz.de/?p=161) (Currently did the first one and don't know how to reverse it, everytime i tried something i would reinstall OS completely...)

So far, i've tried it in the 3 distros i mentioned and i get higher signal, but when i try to browse the net i get a Kernel Panic in Mint, and a black screen in Ubuntu and Xubuntu and nothing else to be done just hold the power button.

I ran the Wireless-info script... I need a hand please, just a noob in this new world of Linux.

By the way, i am using a USB TP-LINK (RT2870/RT3070 Wireless Adapter) to post this and it also has less signal compared to Win8, but at least works because if i try to browse with the rt5390 i'll get a black screen... :(

```



########## wireless info START ##########

Report from: 04 May 2015 01:24 CDT -0500

Booted last: 04 May 2015 01:04 CDT -0500

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-36-generic #48~14.04.1-Ubuntu SMP Wed Apr 15 13:11:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2860

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b404 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              27189  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              652718  3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              12707  1 rt2800lib
cfg80211              494362  2 mac80211,rt2x00lib
asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rt5390sta            1452202  1 
wmi                    19193  1 asus_wmi
video                  20128  2 i915,asus_wmi

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

ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF]>  
          inet6 addr: fe80::5635:30ff:fe6a:7eea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6235888 (6.2 MB)  TX bytes:11857 (11.8 KB)
          Interrupt:17 

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea94:f6ff:fe13:19b9/64 Scope:Link
          inet6 addr: fd34:cdbe:70a7:7500:c13c:2c26:5278:4024/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53751 (53.7 KB)  TX bytes:20647 (20.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=76/100  Signal level:-63 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bgn  ESSID:"Guaifai"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Guaifai' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.huawei.net

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1  [Guaifai 2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    INFINITUM4m9g:   Infra, <MAC 'INFINITUM4m9g' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    INFINITUMDEFEF8: Infra, <MAC 'INFINITUMDEFEF8' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Fam.Matabuena:   Infra, <MAC 'Fam.Matabuena' [AC4]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    INFINITUM1ABF35: Infra, <MAC 'INFINITUM1ABF35' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    bdd14e:          Infra, <MAC 'bdd14e' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    INFINITUMA17B32: Infra, <MAC 'INFINITUMA17B32' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    INFINITUM581213: Infra, <MAC 'INFINITUM581213' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    INFINITUM0520:   Infra, <MAC 'INFINITUM0520' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WEP
    INFINITUM7728:   Infra, <MAC 'INFINITUM7728' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP
    *Guaifai:        Infra, <MAC 'Guaifai' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 71 WPA2

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             208.67.222.222
    DNS:             208.67.220.220

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

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'ra0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    INFINITUM4m9g:   Infra, <MAC 'INFINITUM4m9g' [AC2]>, Freq 2412 MHz, Rate 2 Mb/s, Strength 59 WPA WPA2
    Fam.Matabuena:   Infra, <MAC 'Fam.Matabuena' [AC4]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    INFINITUMDEFEF8: Infra, <MAC 'INFINITUMDEFEF8' [AC3]>, Freq 2437 MHz, Rate 2 Mb/s, Strength 39 WPA WPA2
    INFINITUM0520:   Infra, <MAC 'INFINITUM0520' [AC7]>, Freq 2412 MHz, Rate 0 Mb/s, Strength 35 WEP
    Guaifai:         Infra, <MAC 'Guaifai' [AC1]>, Freq 2412 MHz, Rate 14 Mb/s, Strength 100 WPA2
    INFINITUM581213: Infra, <MAC 'INFINITUM581213' [AC9]>, Freq 2462 MHz, Rate 2 Mb/s, Strength 32 WPA WPA2
    AXTEL_0188D4:    Infra, <MAC 'AXTEL_0188D4' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    INFINITUM1ABF35: Infra, <MAC 'INFINITUM1ABF35' [AC6]>, Freq 2462 MHz, Rate 2 Mb/s, Strength 39 WPA WPA2
    bdd14e:          Infra, <MAC 'bdd14e' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA

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

[[/etc/NetworkManager/system-connections/Guaifai 2]] (600 root)
[connection] id=Guaifai 2 | type=802-11-wireless
[802-11-wireless] ssid=Guaifai
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Guaifai 1]] (600 root)
[connection] id=Guaifai 1 | type=802-11-wireless
[802-11-wireless] ssid=Guaifai | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Guaifai]] (600 root)
[connection] id=Guaifai | type=802-11-wireless
[802-11-wireless] ssid=Guaifai | mac-address=<MAC 'ra0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Mexico_City (based on set time zone)

country MX:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 23), DFS
    (5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

ra0       14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: <MAC 'Guaifai' [AC1]>
                    Protocol:802.11b/g/n
                    ESSID:"Guaifai"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/100  Signal level=-67 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'INFINITUM4m9g' [AC2]>
                    Protocol:802.11b/g/n
                    ESSID:"INFINITUM4m9g"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/100  Signal level=-69 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'INFINITUMDEFEF8' [AC3]>
                    Protocol:802.11b/g/n
                    ESSID:"INFINITUMDEFEF8"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/100  Signal level=-69 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Fam.Matabuena' [AC4]>
                    Protocol:802.11b/g/n
                    ESSID:"Fam.Matabuena"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'AXTEL_0188D4' [AC5]>
                    Protocol:802.11b/g/n
                    ESSID:"AXTEL_0188D4"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
  lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Device or resource busy

        Cell 06 - Address: <MAC 'INFINITUM1ABF35' [AC6]>
                    Protocol:802.11b/g/n
                    ESSID:"INFINITUM1ABF35"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/100  Signal level=-83 dBm  Noise level=-78 dBm
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'INFINITUM0520' [AC7]>
                    Protocol:802.11b/g
                    ESSID:"INFINITUM0520"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 08 - Address: <MAC 'bdd14e' [AC8]>
                    Protocol:802.11b/g
                    ESSID:"bdd14e"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/100  Signal level=-79 dBm  Noise level=-74 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'INFINITUM581213' [AC9]>
                    Protocol:802.11b/g/n
                    ESSID:"INFINITUM581213"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AA4336C224E35E523F23134
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     21417B97E30FD4E6E469E1F
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     EDDCA794C9E4C3981037918
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     71EFA3CA86D02D0528C49EE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     05170C37AC7B7A82211E896
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[rt5390sta]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.6.0.0
srcversion:     95F69F45628F41F1E10506E
depends:        
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

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

rt5390sta

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
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x5390 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'ra0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[ 1187.918634] wlan1: deauthenticating from <MAC 'Guaifai' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1193.775566] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[ 1200.304535] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[ 1200.319581] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0005 detected
[ 1200.361587] systemd-udevd[2659]: renamed network interface wlan0 to wlan1
[ 1200.363304] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 1200.363339] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 1200.594126] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1201.871957] wlan1: authenticate with <MAC 'Guaifai' [AC1]>
[ 1201.897095] wlan1: send auth to <MAC 'Guaifai' [AC1]> (try 1/3)
[ 1201.898208] wlan1: authenticated
[ 1201.900936] wlan1: associate with <MAC 'Guaifai' [AC1]> (try 1/3)
[ 1201.902977] wlan1: RX AssocResp from <MAC 'Guaifai' [AC1]> (capab=0x431 status=0 aid=1)
[ 1201.907488] wlan1: associated
[ 1201.907521] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1202.595027] IPv6: wlan1: IPv6 duplicate address fe80::ea94:f6ff:fe13:19b9 detected!
[ 1218.009914] IPv6: wlan1: IPv6 duplicate address fd34:cdbe:70a7:7500:ea94:f6ff:fe13:19b9 detected!
[ 1218.620301] IPv6: wlan1: IPv6 duplicate address fd34:cdbe:70a7:7500:c13c:2c26:5278:4024 detected!
[ 1218.924880] IPv6: wlan1: IPv6 duplicate address fd34:cdbe:70a7:7500:21da:980e:19e0:f8d1 detected!
[ 1219.390867] IPv6: wlan1: IPv6 duplicate address fd34:cdbe:70a7:7500:6cca:ff50:da3d:ee92 detected!

########## wireless info END ############




```

---

### Post by antonio42 on 2015-05-04
Sorry for double post, but i think this will be better to point it apart. My search on the forums has been pretty extensive. I already configured the router to use only WPA2-AES, no TKIP. Configured in Channel 1 or 11 for my tests, currently on 11. This was pointed on this thread: [http://ubuntuforums.org/showthread.php?t=2204194](http://ubuntuforums.org/showthread.php?t=2204194)

Also installed Xubuntu as it seemed like the solution for that other guy, but at least not for me, i do get better signal but not like in Win8.

Using WifiAnalyzer from my Android devices i get around -50dBm for my SSID "Guaifai", also get around that in Win8 using INSSIDER

---

