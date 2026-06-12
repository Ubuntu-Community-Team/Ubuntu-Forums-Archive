---
title: "Ubuntu 14.04.2 LTS + Native r8188eu driver = Poor reception and regular disconnects"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by nmparmar on 2015-02-27
Hi,

Recently installed Ubuntu 14.04 in VMware, and am seeing really poor connectivity with the native driver for the RealTek 802.11N Wireless. Straight out of the box,the NIC refuses to connect. Error message was as below: Reason 1 is an unknown disconnect as I understand. 

```

Feb 24 17:37:44 ubuntu wpa_supplicant[1316]: wlan1: CTRL-EVENT-DISCONNECTED bssid=3c:ce:73:6c:cb:b0 reason=1 locally_generated=1
Feb 24 17:37:44 ubuntu kernel: [ 4296.694291] cfg80211: World regulatory domain updated:
Feb 24 17:37:44 ubuntu kernel: [ 4296.694294] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 24 17:37:44 ubuntu kernel: [ 4296.694296] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 24 17:37:44 ubuntu kernel: [ 4296.694297] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 24 17:37:44 ubuntu kernel: [ 4296.694298] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 24 17:37:44 ubuntu kernel: [ 4296.694299] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 24 17:37:44 ubuntu kernel: [ 4296.694301] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 24 17:37:44 ubuntu wpa_supplicant[1316]: wlan1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Internet" auth_failures=2 duration=20
Feb 24 17:37:44 ubuntu NetworkManager[869]: <info> (wlan1): supplicant interface state: 4-way handshake -> group handshake
Feb 24 17:37:44 ubuntu NetworkManager[869]: <warn> Connection disconnected (reason -1)
Feb 24 17:37:44 ubuntu NetworkManager[869]: <info> (wlan1): supplicant interface state: group handshake -> disconnected
Feb 24 17:37:44 ubuntu NetworkManager[869]: <warn> Connection disconnected (reason -1)


```

After performing the 'sudo apt-get update, and sudo apt-get dist-upgrade', I am actually able to maintain a connection for a few minutes now. I still see really poor reception, however, and regular disconnects. The disconnects dont seem to log any messages, but it's as if the wifi connection is seen as really weak. 

Unfortunately, if i run windows 7 with the same NIC, my connection is solid and quite strong, which suggests the problem is with the Ubuntu native driver. 

 Ubuntu rarely shows the signal as stronger than 1 bar. 

As per the sticky, I've run the wireless_script, the output of which is attached below. 


Would welcome any suggestions on improving the quality of this connection. 

Thanks

---

### Post by nmparmar on 2015-02-27
On a related note, windows sees the device as Realtek RTL8188ETV Wireless LAN 802.11n USB 2.0 Network Adapter.

Also, below extracted contents of the wireless-info.txt with SSID's sanitised. 

```

########## wireless info START ##########

Report from: 27 Feb 2015 10:43 GMT +0000

Booted last: 27 Feb 2015 10:40 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #75-Ubuntu SMP Tue Feb 10 15:24:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, find_preseed=/preseed.cfg, auto, noprompt, priority=critical, locale=en_US, quiet

##### desktop ###########################

Ubuntu

##### lspci #############################

02:01.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
    Subsystem: VMware PRO/1000 MT Single Port Adapter [15ad:0750]
    Kernel driver in use: e1000

##### lsusb #############################

Bus 001 Device 002: ID 0bda:0179 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0 
r8188eu               814658  0 

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

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.250.1.247  Bcast:10.250.15.255  Mask:255.255.240.0
          inet6 addr: fe80::2e0:4cff:fe81:8564/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:175 overruns:0 frame:0
          TX packets:127 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32298 (32.2 KB)  TX bytes:19422 (19.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Internet"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Internet' [AC1]>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=7/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.250.0.1      0.0.0.0         UG    0      0        0 wlan0
10.250.0.0      0.0.0.0         255.255.240.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Internet 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8188eu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    VisitorInternet: Infra, <MAC 'AAAAAA' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    ipad:            Infra, <MAC 'DDDDDD' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    C17H21NO4:       Infra, <MAC 'EEEEEE' [AC6]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 0 WPA
    ipad:            Infra, <MAC 'DDDDDD' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Perrier Guest:   Infra, <MAC 'BBBBBB' [AC7]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 0 WPA2
    Perrier:         Infra, <MAC 'CCCCCC' [AC8]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 0 WPA2
    Internet:        Infra, <MAC 'Internet' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2
    VisitorInternet: Infra, <MAC 'AAAAAA' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    ipad:            Infra, <MAC 'DDDDDD' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    VisitorInternet: Infra, <MAC 'AAAAAA' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    linksys-n:       Infra, <MAC 'FFFFFF' [AC19]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 0
    EVOLDN_NODE:     Infra, <MAC 'GGGGGG' [AN12]>, Freq 2437 MHz, Rate 44 Mb/s, Strength 0 WPA2
    Internet:        Infra, <MAC 'Internet' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    *Internet:       Infra, <MAC 'Internet' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    stochastics:     Infra, <MAC 'HHHHHH' [AN15]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2 Enterprise
    AV_TYPE_B_7:     Infra, <MAC 'JJJJJJ' [AN16]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 0

  IPv4 Settings:
    Address:         10.250.1.247
    Prefix:          20 (255.255.240.0)
    Gateway:         10.250.0.1

    DNS:             194.72.6.57
    DNS:             194.73.82.242
    DNS:             8.8.8.8

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
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
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Internet 1]] (600 root)
[connection] id=Internet | type=802-11-wireless
[802-11-wireless] ssid=Internet | bssid=<MAC 'Internet' [AC1]> | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Internet 1-e678b4ff-829f-49ca-8420-1620594bd9f4]] (600 root)
[connection] id=Internet 1 | type=802-11-wireless
[802-11-wireless] ssid=Internet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

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

      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      7   APs on   Frequency:2.437 GHz (Channel 6)
      6   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Internet' [AC1]>
                    ESSID:"Internet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac023c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=2/100  
          Cell 02 - Address: <MAC 'ipad' [AC2]>
                    ESSID:"ipad"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac023c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 03 - Address: <MAC '' [AC3]>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac023c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 04 - Address: <MAC 'VisitorInternet' [AC4]>
                    ESSID:"VisitorInternet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac023c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac023c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 06 - Address: <MAC 'C17H21NO4' [AC6]>
                    ESSID:"C17H21NO4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 07 - Address: <MAC 'Perrier Guest' [AC7]>
                    ESSID:"Perrier Guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 08 - Address: <MAC 'Perrier' [AC8]>
                    ESSID:"Perrier"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 09 - Address: <MAC 'ipad' [AC9]>
                    ESSID:"ipad"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 10 - Address: <MAC '' [AC10]>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 11 - Address: <MAC 'VisitorInternet' [AC11]>
                    ESSID:"VisitorInternet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 12 - Address: <MAC 'Internet' [AC12]>
                    ESSID:"Internet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 13 - Address: <MAC '' [AC13]>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 14 - Address: <MAC '' [AC14]>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 15 - Address: <MAC 'Internet' [AC15]>
                    ESSID:"Internet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 16 - Address: <MAC '' [AC16]>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 17 - Address: <MAC 'VisitorInternet' [AC17]>
                    ESSID:"VisitorInternet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 18 - Address: <MAC 'ipad' [AC18]>
                    ESSID:"ipad"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd180050f20101000050f20201000050f20201000050f2022800
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30140100000fac020100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 19 - Address: <MAC 'linksys-n' [AC19]>
                    ESSID:"linksys-n"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality:0  Signal level:0  Noise level:0

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        03:38:57:53:7C:DE:7B:D5:4C:0B:E6:29:0C:13:EF:AD:5B:06:8C:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8188eu]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     3E7C2595787C9010733B049
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        03:38:57:53:7C:DE:7B:D5:4C:0B:E6:29:0C:13:EF:AD:5B:06:8C:DC
sig_hashalgo:   sha512
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

##### /etc/modules ######################

lp
rtc

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   16.815951] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[   20.337797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   25.070388] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

