---
title: "Wifi unstable on lenovo y50-70 ubuntu 14.04 rtl8723be"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by apwb-d on 2015-01-28
Hi.

The Wifi on my Lenovo Y50-70 was unstable. 

I tried ```
sudo iw reg set IN
 sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
``` from [http://ubuntuforums.org/showthread.php?t=2259037&p=13198699#post13198699](http://ubuntuforums.org/showthread.php?t=2259037&p=13198699#post13198699). 
Now the wireless connection only establishes 5 minutes after startup. That means 5 Minutes waiting. Is there comething I could try? 

```

########## wireless info START ##########

Report from: 28 Jan 2015 17:20 CET +0100

Booted last: 28 Jan 2015 17:10 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 5986:055e Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630669  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
ideapad_laptop         18216  0 
mxm_wmi                13021  1 nouveau
sparse_keymap          13948  1 ideapad_laptop
wmi                    19177  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f276:1cff:fe5a:ba7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:558148 (558.1 KB)  TX bytes:138541 (138.5 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e33:7aff:fe1b:3959/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3930 (3.9 KB)  TX bytes:10708 (10.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Shalom"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'Shalom' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-6 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### nm-tool ###########################

** (process:2889): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: connected (global)

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.134
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: wlan0  [Shalom] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ToCaNetz:        Infra, <MAC 'ToCaNetz' [AC7]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    WLAN-63F256:     Infra, <MAC 'WLAN-63F256' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    o2-WLAN91:       Infra, <MAC 'o2-WLAN91' [AC6]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA2
    ap-goh-n:        Infra, <MAC 'ap-goh-n' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    EasyBox-D9E250:  Infra, <MAC 'EasyBox-D9E250' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 28 WPA WPA2
    Halligallil:     Infra, <MAC 'Halligallil' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    FRITZ!Box 7330 SL: Infra, <MAC 'FRITZ!Box 7330 SL' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    www.fbn-dd.de/GOH2: Infra, <MAC 'www.fbn-dd.de/GOH2' [AN8]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 100 WPA2 Enterprise
    WLAN-4D5252:     Infra, <MAC 'WLAN-4D5252' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    ap-goh-c:        Infra, <MAC 'ap-goh-c' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
    FRITZ!Box 7362 SL: Infra, <MAC 'FRITZ!Box 7362 SL' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    www.fbn-dd.de/EAP: Infra, <MAC 'www.fbn-dd.de/EAP' [AN12]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 70 WPA2 Enterprise
    Mitulsky-Gastnetz-2.4G: Infra, <MAC 'Mitulsky-Gastnetz-2.4G' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Mitulsky-Heimnetz-2.4G: Infra, <MAC 'Mitulsky-Heimnetz-2.4G' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    www.fbn-dd.de/GOH3: Infra, <MAC 'www.fbn-dd.de/GOH3' [AN15]>, Freq 2417 MHz, Rate 11 Mb/s, Strength 6 WPA2 Enterprise
    www.fbn-dd.de/EAP: Infra, <MAC 'www.fbn-dd.de/EAP' [AN16]>, Freq 2417 MHz, Rate 11 Mb/s, Strength 54 WPA2 Enterprise
    www.fbn-dd.de/BUR3: Infra, <MAC 'www.fbn-dd.de/BUR3' [AN17]>, Freq 2432 MHz, Rate 11 Mb/s, Strength 100 WPA2 Enterprise
    www.fbn-dd.de/EAP: Infra, <MAC 'www.fbn-dd.de/EAP' [AN18]>, Freq 2432 MHz, Rate 11 Mb/s, Strength 57 WPA2 Enterprise
    www.fbn-dd.de/WPA: Infra, <MAC 'www.fbn-dd.de/WPA' [AN19]>, Freq 2432 MHz, Rate 11 Mb/s, Strength 50 WPA WPA2
    *Shalom:         Infra, <MAC 'Shalom' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA2
    WLAN-80D000:     Infra, <MAC 'WLAN-80D000' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2

  IPv4 Settings:
    Address:         192.168.0.110
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/Xperia Z1 Compact_9e47]] (600 root)
[connection] id=Xperia Z1 Compact_9e47 | type=802-11-wireless
[802-11-wireless] ssid=Xperia Z1 Compact_9e47 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Shalom]] (600 root)
[connection] id=Shalom | type=802-11-wireless
[802-11-wireless] ssid=Shalom | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!B]] (600 root)
[connection] id=FRITZ!B | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!B | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ap-goh-n]] (600 root)
[connection] id=ap-goh-n | type=802-11-wireless
[802-11-wireless] ssid=ap-goh-n | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Shalom 1]] (600 root)
[connection] id=Shalom 1 | type=802-11-wireless | permissions=user:guest-pFQCxW:;
[802-11-wireless] ssid=Shalom | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

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
          Current Frequency:2.452 GHz (Channel 9)

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      4   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Shalom' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Shalom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005d3242715
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ap-goh-n' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ap-goh-n"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001a8cc7627177
                    Extra: Last beacon: 140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FRITZ!Box 7362 SL' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-14 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7362 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000026232a40cba
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Halligallil' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:on
                    ESSID:"Halligallil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000105ec1fbed
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ap-goh-c' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"ap-goh-c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a72ae5801b3
                    Extra: Last beacon: 8ms ago
          Cell 06 - Address: <MAC 'o2-WLAN91' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN91"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006e494d148
                    Extra: Last beacon: 232ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 07 - Address: <MAC 'ToCaNetz' [AC7]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ToCaNetz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125ff7a712
                    Extra: Last beacon: 3476ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'WLAN-63F256' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WLAN-63F256"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000285c753d7b1
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'EasyBox-D9E250' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-D9E250"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000065f3bba893
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'WLAN-4D5252' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:on
                    ESSID:"WLAN-4D5252"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d968f1147f
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Mitulsky-Heimnetz-2.4G' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Mitulsky-Heimnetz-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a212eb360
                    Extra: Last beacon: 2124ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Mitulsky-Gastnetz-2.4G' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Mitulsky-Gastnetz-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a212ebcf5
                    Extra: Last beacon: 2120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'FRITZ!Box 7330 SL' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7330 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017bc9c5308c
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC '\00' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000013be5789e66
                    Extra: Last beacon: 708ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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
options iwlwifi 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   23.569013] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   25.341133] wlan0: authenticate with <MAC 'Shalom' [AC1]>
[   25.360778] wlan0: send auth to <MAC 'Shalom' [AC1]> (try 1/3)
[   25.364085] wlan0: authenticated
[   25.364491] wlan0: associate with <MAC 'Shalom' [AC1]> (try 1/3)
[   25.384193] wlan0: RX AssocResp from <MAC 'Shalom' [AC1]> (capab=0x31 status=0 aid=2)
[   25.384345] wlan0: associated
[   25.384351] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.411477] wlan0: deauthenticating from <MAC 'Shalom' [AC1]> by local choice (reason=2)
[   25.432856] wlan0: authenticate with <MAC 'Shalom' [AC1]>
[   25.432930] wlan0: send auth to <MAC 'Shalom' [AC1]> (try 1/3)
[   26.375852] wlan0: send auth to <MAC 'Shalom' [AC1]> (try 2/3)
[   26.477763] wlan0: send auth to <MAC 'Shalom' [AC1]> (try 3/3)
[   26.581833] wlan0: authentication with <MAC 'Shalom' [AC1]> timed out
[   50.913154] wlan0: authenticate with <MAC address>
[   50.922931] wlan0: send auth to <MAC address> (try 1/3)
[   51.024733] wlan0: send auth to <MAC address> (try 2/3)
[   51.128857] wlan0: send auth to <MAC address> (try 3/3)
[   51.232923] wlan0: authentication with <MAC address> timed out
[   52.170468] wlan0: authenticate with <MAC 'Shalom' [AC1]>
[   52.180202] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 1/3)
[   52.382186] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 2/3)
[   52.586421] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 3/3)
[   52.790639] wlan0: authentication with <MAC 'Shalom' [AC1]> timed out
[   78.113413] wlan0: authenticate with <MAC address>
[   78.113486] wlan0: send auth to <MAC address> (try 1/3)
[   78.214552] wlan0: send auth to <MAC address> (try 2/3)
[   78.318710] wlan0: send auth to <MAC address> (try 3/3)
[   78.422830] wlan0: authentication with <MAC address> timed out
[   88.470172] wlan0: authenticate with <MAC 'Shalom' [AC1]>
[   88.470259] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 1/3)
[   88.674102] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 2/3)
[   88.878278] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 3/3)
[   89.082489] wlan0: authentication with <MAC 'Shalom' [AC1]> timed out
[  106.145004] wlan0: authenticate with <MAC address>
[  106.145081] wlan0: send auth to <MAC address> (try 1/3)
[  106.245346] wlan0: send auth to <MAC address> (try 2/3)
[  106.349468] wlan0: send auth to <MAC address> (try 3/3)
[  106.453574] wlan0: authentication with <MAC address> timed out
[  116.505414] wlan0: authenticate with <MAC 'Shalom' [AC1]>
[  116.505562] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 1/3)
[  116.708831] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 2/3)
[  116.913204] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 3/3)
[  117.117484] wlan0: authentication with <MAC 'Shalom' [AC1]> timed out
[  134.201387] wlan0: authenticate with <MAC 'Shalom' [AC1]>
[  134.201478] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 1/3)
[  134.405153] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 2/3)
[  134.609446] wlan0: direct probe to <MAC 'Shalom' [AC1]> (try 3/3)
[  134.813765] wlan0: authentication with <MAC 'Shalom' [AC1]> timed out
[  460.555144] wlan0: authenticate with <MAC 'Shalom' [AC1]>
[  460.564615] wlan0: send auth to <MAC 'Shalom' [AC1]> (try 1/3)
[  460.568356] wlan0: authenticated
[  460.570249] wlan0: associate with <MAC 'Shalom' [AC1]> (try 1/3)
[  460.590103] wlan0: RX AssocResp from <MAC 'Shalom' [AC1]> (capab=0x31 status=0 aid=2)
[  460.590301] wlan0: associated

########## wireless info END ############


```

---

### Post by Pilot6 on 2015-01-28
You need to intall new driver.

sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install
sudo reboot

---

### Post by ben136 on 2015-01-28
I also have a Lenovo Y50-70 and am having wifi problems with Ubuntu. However, I don't think I have a rtl8723 wireless card (I have an Intel one instead). I've attached my wireless-script output. Any ideas?

---

### Post by Rahmengo on 2015-01-30
Hi there. I have a Lenovo G50-70 laptop with a RTL8723BE Wi-Fi card and Bluetooth.
I too have problems with my internet connection dropping out and Bluetooth no being bale to discover devices nor be discovered.
What's up with this card?
I have been a Linux user since 2008 and this is the first time ever I have had a problem with hardware on a laptop.
I have spent hours, no make that days so far searching the Internet for an answer with no luck.

I guess I will keep trying and report back if I find a solution... Until then....

---

### Post by jeremy31 on 2015-01-30
> **Rahmengo said:**
> Hi there. I have a Lenovo G50-70 laptop with a RTL8723BE Wi-Fi card and Bluetooth.
I too have problems with my internet connection dropping out and Bluetooth no being bale to discover devices nor be discovered.
What's up with this card?
I have been a Linux user since 2008 and this is the first time ever I have had a problem with hardware on a laptop.
I have spent hours, no make that days so far searching the Internet for an answer with no luck.

I guess I will keep trying and report back if I find a solution... Until then....

Have you tried Pilot6's fix?

The bluetooth on that card may never work, Larry Finger said he would start working on it again once he was done redoing the rtl wifi code.  The last change to the bluetooth was 3 months ago [https://github.com/lwfinger/rtl8723au_bt/tree/new/Linux_BT_USB_2.11.20140423_8723BE](https://github.com/lwfinger/rtl8723au_bt/tree/new/Linux_BT_USB_2.11.20140423_8723BE)

---

### Post by Rahmengo on 2015-01-31
Thanks Jeremy31,
I will try it later tonight...
I am not too sure of the second line in Pilot6's post, namely;
[B]git clone
[/B]What does that mean?
(Although I have used Linux for some years, I have** never** had to run anything like this, so this is completely new to me)
The rest I understand and will give it a crack by mysef.
thanks in advance

---

### Post by jeremy31 on 2015-01-31
> **Rahmengo said:**
> Thanks Jeremy31,
I will try it later tonight...
I am not too sure of the second line in Pilot6's post, namely;
[B]git clone
[/B]What does that mean?
(Although I have used Linux for some years, I have** never** had to run anything like this, so this is completely new to me)
The rest I understand and will give it a crack by mysef.
thanks in advance

git clone plus the website location downloads from a github source.  This one is legit as it belongs to the kernel developer in charge of maintaining the rtl wifi code

---

### Post by Rahmengo on 2015-02-01
OK. Thanks jeremy31!
After all these years, this is my first time on a Linux forum - I tend to work things out mysef. However, this time around, I feel like a total newbie!! :oops:

I'll keep you posted on my progress. Thanks again for your prompt replies and your effort in replying.

---

### Post by Rahmengo on 2015-02-01
Hi to jeremy31:

I have been busy but will attend to this "bug" in the coming days and will update you soon.
I have a new Lenovo G50-70 laptop that came with Windoze 8.1 pre-installed (with Realtek RTL8723BE card). I have multi-booted it with Ubuntu 14.04 **and** Mint 17.1 Cinamon.
As  Mint is my production OS I will try the solution above on the Ubuntu OS  and report back. If it works I will then attempt on the Mint OS as  well.
Thanks in advance for your help...

---

### Post by erivera6 on 2015-02-06
So far so good with Pilot6's fix. (Wifi was losing its ipv4 ip) Thanks!
Lenovo G50-45
AMD A6-6310
UEFI BIOS
4 GB RAM
1 TB HDD
Linux Mint 17.1 (Rebecca) MATE 1.8.1
Kernel 3.13.0-37 generic
wifi : Realtek RTL8723BE

---

### Post by Rahmengo on 2015-02-10
Hi Jeremy31 - apologies for not replying sooner, but my work week has been hectic and weekend busier and I finally have some time to myself to tinker with this problem....

As mentioned above, my Lenovo G50-70 laptop is having connectivity issues with WiFi dropping out. I have done some further research and have noticed you responded on another thread on the same topic, found on this [thread]("http://askubuntu.com/questions/583177/wifi-network-drop-on-lenovo-g50-70") and this [thread]("http://askubuntu.com/questions/580551/wireless-wifi-network-is-not-working-on-ubuntu-12-04-lenovo-z50-70/580578#580578"), with the following code:

   [FONT=courier new][COLOR=#0000FF][SIZE=2]sudo apt-get install linux-headers-generic build-essential
[/SIZE][/COLOR][/FONT][FONT=courier new][COLOR=#0000FF][SIZE=2]wget -N -t 5 -T 10 [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz)[/SIZE][/COLOR][/FONT][FONT=courier new][COLOR=#0000FF][SIZE=2]
tar -xf backports-3.18.1-1.tar.xz[/SIZE][/COLOR][/FONT][FONT=courier new][COLOR=#0000FF][SIZE=2]
cd ~/backports-3.18.1-1
[/SIZE][/COLOR][/FONT][FONT=courier new][COLOR=#0000FF][SIZE=2]make defconfig-rtlwifi
[/SIZE][/COLOR][/FONT][FONT=courier new][COLOR=#0000FF][SIZE=2]make
[/SIZE][/COLOR][/FONT][SIZE=2][COLOR=#0000ff][FONT=courier new]sudo make install
[/FONT][/COLOR]
[/SIZE][FONT=arial]Then reboot.

My question is, shall I use Pilot6's solution quoted earlier on this thread or the solution you provided in the other threads (copied above)?

My laptop came orignally with Windows 8.1 preinstalled which I have then multi-booted to run Ubuntu 14.04 and Mint 17.1 (both 64 bit). I am running 3.13.0-32-generic kernel. Wireless works fine on Windows 8.1 but drops out on both Ubuntu and Mint.
The output of the wireless script is attached.
Any help is appreciated before I pull the tigger on one of the solutions :-)

[/FONT]

---

### Post by jeremy31 on 2015-02-10
You could probably use either one and not notice any difference although the link from Pilot6 should be the latest version

---

### Post by Rahmengo on 2015-02-10
Wow - that was quick! :-)
Thanks for the response.

I'll give the Pilot6 solution a go and see how it works. I'll report back once I've tested the wireless.
Thank you.

---

### Post by Rahmengo on 2015-02-15
I have followed Pilot6's solution as shown on page 1 of this thread and it appears to have worked!
No WiFi dropout over 2 hours of browsing.
The Pilot6's solution was performed on a Lenovo G50-70 laptop with the RTL8723BE WiFi card, running Ubuntu 14,04 (64 bit) with 3.13.0-32-generic kernel.

I will continue to monitor the WiFi performance and report back in a week's time.

If all holds up, I will also perform the solution on the Linux MInt 17.1 (64 bit) operating system which is also on the same (muti-booted) laptop.

Many thanks to you all, especially Pilot6 (for the solution), jeremy31 (for always responding) and to others for their input.):P

---

### Post by Rahmengo on 2015-02-20
Hi there!
Just reporting back to inform forum readers that Pilot6's soultion on page 1 of this thread has worked beautifully for a whole week without any wifi dropouts on my Lenovo G50-70 laptop, RTL8723BE card, Ubuntu 14.04 (64 bit) and kernel 3.13.0-32-generic.

I will also now perform the same solution this weekend on the same (multi-booted) laptop on the Mint 17.1 (64 bit) operating system and report back.

Until then....

---

### Post by Rahmengo on 2015-03-01
Just reporting back that Pilot6's solution on page 1 of this thread was also implemented onto my Lenovo G50-70 laptop under Linux MInt 17.1 (64 bit) and all is working well (with the exception of Bluetooth).
I'll head over to the Linux MInt forum and provide fedback there.

Once again, thanks to all involved!!

---

### Post by SteinarSS on 2015-03-17
Pilot6's solution also worked for me for some weeks, but a couple of days ago the problem with the wi-fi dropping out just reappeared. I did nothing that I knw of, but maybe some update screwed things up? Has anyone experienced the same problem again? I have a Lenovo G50-45.

---

### Post by Rahmengo on 2015-04-07
Hi SteinaeSS!
I must say my connection has been working flawlessly. I use both Ubuntu 14.04 and Linux Mint 17.1 (both 64 bit) on the same multi-booted machine (Lenovo G50-70) and no problems since my post above.
I must admit though - I mainly use Linux Mint as my OS of choice. But I did use Ubuntu 14.04 the other day and it was working fine.

---

### Post by jeremy31 on 2015-04-07
> **SteinarSS said:**
> Pilot6's solution also worked for me for some weeks, but a couple of days ago the problem with the wi-fi dropping out just reappeared. I did nothing that I knw of, but maybe some update screwed things up? Has anyone experienced the same problem again? I have a Lenovo G50-45.

The update may have installed a new kernel, so
```
cd rtlwifi_new
make clean
make
sudo make install
```
reboot

---

### Post by Rahmengo on 2015-04-07
Thanks jeremy31! Always quick to reply with concise details and instructions.
I'll keep that tip in my back pocket for when I need it.

You sir are highly regarded :-)

---

### Post by arnaudlecam on 2015-05-01
I had the same problem with :
- 3.19.0-15-generic linux kernel on Xubuntu 15.04 Vivid
- Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
Your trick seems to work perfectly for me
Thank you Pilot6 !

---

### Post by serdar132 on 2015-05-29
I have had the same problem, and have it resolved with the indications you have given. Thank you very much.

HOWEVER after the update it has gone back to the begining and I have the same issues all around. Are we going to go through this everytime we update?

Thanks

---

### Post by morebodi on 2015-06-20
Pilot's solution worked perfectly well on my lenovo G50-70

---

### Post by Pilot6 on 2015-06-21
> **serdar132 said:**
> I have had the same problem, and have it resolved with the indications you have given. Thank you very much.

HOWEVER after the update it has gone back to the begining and I have the same issues all around. Are we going to go through this everytime we update?

Thanks

Install the driver from my ppa. It will stay after kernel upgrades.

---

### Post by maurette on 2015-07-09
> **Pilot6 said:**
> Install the driver from my ppa. It will stay after kernel upgrades.

How could I install the driver from your PPA Pilot6?  thanks in advance

---

### Post by umberto4 on 2015-08-02
> **maurette said:**
> How could I install the driver from your PPA Pilot6?  thanks in advance

Hi, the ppa page should be this: [https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi). Inside you can find instructions for installation.

---

### Post by e270889o on 2015-08-24
> **Pilot6 said:**
> Install the driver from my ppa. It will stay after kernel upgrades.


Thanks Pilot6.

Can you explain the diferente files in your ppa?

I think we should install** rtlwifi-new-dkms** but, what are the other things? I can see a [COLOR=#333333][FONT=Ubuntu] **rtl8723au-bt-dkms**

Thanks[/FONT][/COLOR]

---

### Post by terry42 on 2015-11-20
Thank you so much Pilot6!

I am a total linux newbie - no idea what I'm doing at the moment - and I just installed Ubuntu 14.04 over my Windows 10, because I didn't know how to create partitians, and the wifi went on the blink. I have a Lenovo G50 and I had already tried Linux Mint and it wouldn't find my wifi card at all, so this was another attempt at Linux. Anyway, to cut a boring story short, this worked like a charm! So thank you again!

---

### Post by epdiamantopoulos on 2016-01-23
Just to report that[ ]("http://ubuntuforums.org/showthread.php?t=2262957&p=13217592#post13217592")[[URL="http://ubuntuforums.org/showthread.php?t=2262957&p=13217592#post13217592"]**[COLOR=#000000]Pilot6[/COLOR]**]("http://ubuntuforums.org/member.php?u=1514892")[/URL]['s solution]("http://ubuntuforums.org/showthread.php?t=2262957&p=13217592#post13217592") works great.

---

