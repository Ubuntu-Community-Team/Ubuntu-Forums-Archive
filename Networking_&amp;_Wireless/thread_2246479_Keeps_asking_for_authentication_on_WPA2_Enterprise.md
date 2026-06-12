---
title: "Keeps asking for authentication on WPA2 Enterprise networks(Possible chipset problem)"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by bart-westheim on 2014-10-01
I have a problem with WPA Enterprise-networks, specifically Eduroam (a global network thinghy for universities). When I configure the network and try to connect it keeps coming back to the authentication screen, like I entered a wrong password or something. Now I know this is not the case, and the info works on any other computer/laptop.

Now I've read that there are some Ubuntu-issues with my chipset, the Intel Centrino Wireless N-2230, and I was wondering how I could fix this? I am quite new to Linux so I have no clue what to do, and of course, IT can't help either.

Cheers!

*Edit* Solved, it was an issue with the certificate.

---

### Post by davit2 on 2014-10-01
What about your wireless signal, is it good?

---

### Post by bart-westheim on 2014-10-01
```
########## wireless info START ##########


Report from: 01 Oct 2014 09:58 CEST +0200


Booted last: 27 Sep 2014 08:17 CEST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
    Kernel driver in use: iwlwifi


0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5000]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 05ca:1823 Ricoh Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3192784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3494807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3001114952 (3.0 GB)  TX bytes:2107816020 (2.1 GB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.43.100  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::6236:ddff:fef2:5756/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1841090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1366746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2264502676 (2.2 GB)  TX bytes:175919838 (175.9 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"XT1032 8350"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'XT1032 8350' [AC5]>   
          Bit Rate=43.3 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:90   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 wlan0
192.168.43.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


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
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         off


- Device: wlan0  [XT1032 8350] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           43 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    eduroam:         Infra, <MAC 'eduroam' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2 Enterprise
    wiretap:         Infra, <MAC 'wiretap' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    UMguest:         Infra, <MAC 'UMguest' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74
    eduroam:         Infra, <MAC 'eduroam' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    UMnet:           Infra, <MAC 'UMnet' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    UMguest:         Infra, <MAC 'UMguest' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42
    UMnet:           Infra, <MAC 'UMnet' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    EuMediaNet-ICT:  Infra, <MAC 'EuMediaNet-ICT' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    UMguest:         Infra, <MAC 'UMguest' [AC9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    UMnet:           Infra, <MAC 'UMnet' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    UMguest:         Infra, <MAC 'UMguest' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    UMnet:           Infra, <MAC 'UMnet' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA2 Enterprise
    ADSL-internet:   Infra, <MAC 'ADSL-internet' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    eduroam:         Infra, <MAC 'eduroam' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    UMnet:           Infra, <MAC 'UMnet' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    UMnet:           Infra, <MAC 'UMnet' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    UMguest:         Infra, <MAC 'UMguest' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    UMnet:           Infra, <MAC 'UMnet' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    *XT1032 8350:    Infra, <MAC 'XT1032 8350' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 76 WPA2


  IPv4 Settings:
    Address:         192.168.43.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1


    DNS:             192.168.43.1


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[802-1x] ca-cert=/etc/ssl/certs/COMODO_Certification_Authority.pem
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/UMnet]] (600 root)
[ipv6] method=auto
[connection] id=UMnet | type=802-11-wireless
[802-11-wireless] ssid=UMnet | mac-address=<MAC 'wlan0' [IF]>
[802-1x] ca-cert=/etc/ssl/certs/COMODO_Certification_Authority.pem
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/XT1032 8350]] (600 root)
[connection] id=XT1032 8350 | type=802-11-wireless
[802-11-wireless] ssid=XT1032 8350 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SETUP]] (600 root)
[connection] id=SETUP | type=802-11-wireless
[802-11-wireless] ssid=SETUP | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/eduroam~]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[802-1x] ca-cert=/etc/ssl/certs/COMODO_Certification_Authority.pem
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Ziggo42134]] (600 root)
[connection] id=Ziggo42134 | type=802-11-wireless
[802-11-wireless] ssid=Ziggo42134 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/wiretap]] (600 root)
[connection] id=wiretap | type=802-11-wireless
[802-11-wireless] ssid=wiretap | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UMnet~]] (600 root)
[ipv6] method=auto
[connection] id=UMnet | type=802-11-wireless
[802-11-wireless] ssid=UMnet | mac-address=<MAC 'wlan0' [IF]>
[802-1x] ca-cert=/etc/ssl/certs/COMODO_Certification_Authority.pem
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Ninjas_in_de_tuin]] (600 root)
[connection] id=Ninjas_in_de_tuin | type=802-11-wireless
[802-11-wireless] ssid=Ninjas_in_de_tuin | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Goudvissen en RD4-vuilnismannen]] (600 root)
[connection] id=Goudvissen en RD4-vuilnismannen | type=802-11-wireless
[802-11-wireless] ssid=Goudvissen en RD4-vuilnismannen | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Amsterdam (based on set time zone)


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'wiretap' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"wiretap"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002cd6f96d389
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UMguest' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"UMguest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001185f6a238
                    Extra: Last beacon: 48ms ago
          Cell 03 - Address: <MAC 'UMnet' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"UMnet"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b239a2904a
                    Extra: Last beacon: 29752ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'UMnet' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"UMnet"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a7c5c2b069
                    Extra: Last beacon: 540ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'XT1032 8350' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"XT1032 8350"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000029ec156
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'eduroam' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001185f63f3a
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'UMnet' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"UMnet"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001185f700bb
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'eduroam' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010af869aa6
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'UMguest' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"UMguest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b23b679e39
                    Extra: Last beacon: 48ms ago
          Cell 10 - Address: <MAC 'UMnet' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UMnet"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010af875c27
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC 'UMguest' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"UMguest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010af86fdad
                    Extra: Last beacon: 48ms ago
          Cell 12 - Address: <MAC 'UMnet' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UMnet"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b23bb66aff
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'EuMediaNet-ICT' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"EuMediaNet-ICT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001c8134c4fae
                    Extra: Last beacon: 156ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
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


[iwlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


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


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[101675.924644] wlan0: deauthenticating from <MAC 'UMnet' [AC7]> by local choice (reason=3)
[101722.670164] wlan0: authenticate with <MAC 'UMnet' [AC7]>
[101722.671694] wlan0: send auth to <MAC 'UMnet' [AC7]> (try 1/3)
[101722.673092] wlan0: authenticated
[101722.676680] wlan0: associate with <MAC 'UMnet' [AC7]> (try 1/3)
[101722.784838] wlan0: associate with <MAC 'UMnet' [AC7]> (try 2/3)
[101722.789292] wlan0: RX AssocResp from <MAC 'UMnet' [AC7]> (capab=0x411 status=0 aid=9)
[101722.793199] wlan0: associated
[101724.832026] wlan0: deauthenticating from <MAC 'UMnet' [AC7]> by local choice (reason=3)
[101779.745834] wlan0: authenticate with <MAC 'UMnet' [AC7]>
[101779.749104] wlan0: send auth to <MAC 'UMnet' [AC7]> (try 1/3)
[101779.751582] wlan0: authenticated
[101779.753882] wlan0: associate with <MAC 'UMnet' [AC7]> (try 1/3)
[101779.758657] wlan0: RX AssocResp from <MAC 'UMnet' [AC7]> (capab=0x411 status=0 aid=9)
[101779.762171] wlan0: associated
[101781.793175] wlan0: deauthenticating from <MAC 'UMnet' [AC7]> by local choice (reason=3)
[101804.474956] wlan0: authenticate with <MAC 'UMnet' [AC7]>
[101804.477422] wlan0: send auth to <MAC 'UMnet' [AC7]> (try 1/3)
[101804.479926] wlan0: authenticated
[101804.482135] wlan0: associate with <MAC 'UMnet' [AC7]> (try 1/3)
[101804.509393] wlan0: RX AssocResp from <MAC 'UMnet' [AC7]> (capab=0x411 status=0 aid=9)
[101804.512642] wlan0: associated
[101804.579209] wlan0: deauthenticating from <MAC 'UMnet' [AC7]> by local choice (reason=3)
[102098.543371] wlan0: Selected IBSS BSSID <MAC address> based on configured SSID
[102098.557926] iwlwifi 0000:03:00.0: Unable to find TIM Element in beacon (repeated 2 times)
[102128.594726] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[102133.374729] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[102133.382345] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[102133.453260] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[103052.373623] wlan0: authenticate with <MAC 'XT1032 8350' [AC5]>
[103052.379872] wlan0: send auth to <MAC 'XT1032 8350' [AC5]> (try 1/3)
[103052.383267] wlan0: authenticated
[103052.387421] wlan0: associate with <MAC 'XT1032 8350' [AC5]> (try 1/3)
[103052.401614] wlan0: RX AssocResp from <MAC 'XT1032 8350' [AC5]> (capab=0x431 status=0 aid=1)
[103052.404082] wlan0: associated
[103052.404125] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```
wifi script

---

### Post by bart-westheim on 2014-10-01
Yes the strength of the connection isn't the issue. I am encountering this issue in two different universities spread out over at least 7 different buildings. The strength of the signal has no influence whatsoever on this problem.

---

### Post by davit2 on 2014-10-01
install the latest updates in order to get new kernel 3.16

---

### Post by bart-westheim on 2014-10-01
> **davit2 said:**
> install the latest updates in order to get new kernel 3.16
Any way to do this without internet? (no way to connect the laptop in question to the internet)

*edit* And also, why would this work? Is this a known issue with my kernel?

---

### Post by davit2 on 2014-10-01
use Ethernet (LAN) connection

---

### Post by bart-westheim on 2014-10-01
> **davit2 said:**
> use Ethernet (LAN) connection
Well no ****. If that was a possibility, do you really think I would be asking?

---

### Post by bart-westheim on 2014-10-01
Well, my doubts are confirmed. I went to a coffee shop for their wifi, installed that kernel, and it had no effect whatsoever.

---

### Post by davit2 on 2014-10-01
what type of encryption are you using? would you try another, and you what is kernel version now?

---

### Post by davit2 on 2014-10-01
try without password

---

### Post by bart-westheim on 2014-10-01
> **davit2 said:**
> what type of encryption are you using? would you try another, and you what is kernel version now?
As mentioned in my first post, its a (global!)university network, called eduroam, and secured with WPA2 Enterprise. It is now 3.16. Obviously I cannot change the encryption of a global institute.

---

### Post by bart-westheim on 2014-10-01
> **davit2 said:**
> try without password
I appreciate the fact that you're trying, but you're not helping at all. Please read my opening post again. It is on a network not under my own administration and I cannot change anything about it.

---

### Post by bart-westheim on 2014-10-01
Fixed it eventually. Problem with the certificate.

---

### Post by bart-westheim on 2014-10-01
I am now connecting without the certificate. Can this do any harm?

---

### Post by Marc_Tremblay on 2014-10-24
Hello,

I am having the same problem at our school board where we are converting all our old laptops to Ubuntu. If I install anything newer that ubuntu 12.04 I am unable to connect to our WIFI network and it keeps looping asking for the users credentials.

We use WPA2 enterprise, no certificate, and PEAP

Were youable to resolve your issue?

---

