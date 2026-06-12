---
title: "Wireless connection unstable on 14.04.2"
date: 2015-04-21
forum: Networking &amp; Wireless
---

### Post by bob_smith3 on 2015-04-21
Hi all, 
I am brand new to Linux and Ubuntu. I installed it yesterday, and throughout, I have noticed the wi-fi connection lasts for about 10 minutes after boot. Then, it suddenly goes down. Turning off the wireless connection and turning it back on does not solve the problem. The only solution is to shut down and reboot the system. After reboot, the wi-fi will last for another 10 minutes or so. I have tried using a wired connection, and everything runs very smoothly, as expected. So I assume it's an issue with the drivers? If so, how can I fix this? All input will be greatly appreciated!
Sincerely,
Bob Smith

---

### Post by Vladlenin5000 on 2015-04-21
Hi and welcome.

> **bob_smith3 said:**
> So I assume it's an issue with the drivers?

Good assumption.
It's a question better suited for Networking & Wireless. Please read and follow instructions in [Before posting in Networking and Wireless]("http://ubuntuforums.org/showthread.php?t=370108") , a sticky in the aforementioned section.

---

### Post by bob_smith3 on 2015-04-21
I had the same thread in that section, and it was seen as a duplicate, and was therefore closed.

---

### Post by Vladlenin5000 on 2015-04-21
When I said better suited it didn't follow you had to open another one. Instead you should have reported yourself and asked to be moved (I just did, no need for you to do it again).

---

### Post by lisati on 2015-04-21
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2015-04-22
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Also Vladlenin5000 gave you the link with the script in it.
Thanks

---

### Post by bob_smith3 on 2015-04-22
Hi:
Thank you for your prompt replies. So I upgraded from Ubuntu   14.04.2 to 14.10, and the wi-fi issues seems to have been partially  solved. It's still not permanent, but I can at least turn off the wifi  and turn it back on and the problem is resolved. Anyways, attached is the "wireless-info.tar.gz" file:



[ATTACH]261463[/ATTACH]

For your convenience, here's the contents of wireless-info.tar.gz
```


########## wireless info START ##########

Report from: 22 Apr 2015 07:11 EDT -0400

Booted last: 22 Apr 2015 06:48 EDT -0400

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-34-generic #47-Ubuntu SMP Fri Apr 10 18:02:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 5986:055d Acer, Inc 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0781:5581 SanDisk Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
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

rtl8723be              84972  0 
btcoexist              50429  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26674  1 rtl8723be
rtlwifi                64237  2 rtl_pci,rtl8723be
mac80211              660592  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              510218  2 mac80211,rtlwifi
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop

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
          inet addr:192.168.2.26  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c238:96ff:fe14:e241/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24049928 (24.0 MB)  TX bytes:2866144 (2.8 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Bell320"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Bell320' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management: off
          Link Quality=70/70  Signal level=4 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### NetworkManager info ###############

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

- Device: wlan0  [Bell320] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    EMSBA:           Infra, <MAC 'EMSBA' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BELL856:         Infra, <MAC 'BELL856' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BELL200:         Infra, <MAC 'BELL200' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BELL955:         Infra, <MAC 'BELL955' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2
    DANNYD:          Infra, <MAC 'DANNYD' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    BELL052:         Infra, <MAC 'BELL052' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    FYAU:            Infra, <MAC 'FYAU' [AC7]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Salah11:         Infra, <MAC 'Salah11' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    Bell408:         Infra, <MAC 'Bell408' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    MyHouse:         Infra, <MAC 'MyHouse' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WEP
    FYAU-guest:      Infra, <MAC 'FYAU-guest' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 40
    *Bell320:        Infra, <MAC 'Bell320' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 36 WPA2
    BELL098:         Infra, <MAC 'BELL098' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BELL598:         Infra, <MAC 'BELL598' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    SHAW-53724C-Guest: Infra, <MAC 'SHAW-53724C-Guest' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    Linksys00379:    Infra, <MAC 'Linksys00379' [AN16]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BELL901:         Infra, <MAC 'BELL901' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    somnium:         Infra, <MAC 'somnium' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.26
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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

[[/etc/NetworkManager/system-connections/Bell320]] (600 root)
[connection] id=Bell320 | type=802-11-wireless
[802-11-wireless] ssid=Bell320 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

country CA: DFS-UNSET
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      6   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Bell320' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"Bell320"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000125e5db48c
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FYAU-guest' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"FYAU-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005d8e2f99dc
                    Extra: Last beacon: 1168ms ago
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000858b049c4b
                    Extra: Last beacon: 7864ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'BELL098' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=4 dBm  
                    Encryption key:on
                    ESSID:"BELL098"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004bc7404a36
                    Extra: Last beacon: 4392ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BELL200' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"BELL200"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008587d7c41c
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Bell408' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"Bell408"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000125e5dca51
                    Extra: Last beacon: 16ms ago
          Cell 07 - Address: <MAC 'FYAU' [AC7]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"FYAU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005d8e2f7ae1
                    Extra: Last beacon: 4392ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'MyHouse' [AC8]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MyHouse"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000858e017ad9
                    Extra: Last beacon: 4392ms ago
          Cell 09 - Address: <MAC 'BELL955' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"BELL955"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000058fa7c418
                    Extra: Last beacon: 4392ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000858cc1e18a
                    Extra: Last beacon: 4776ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Salah11' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Salah11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000858cc1e876
                    Extra: Last beacon: 4772ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'BELL856' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"BELL856"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000504df26180
                    Extra: Last beacon: 4460ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'somnium' [AC13]>
                    Channel:1lo        Interface doesn't support scanning.

1
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"somnium"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008587ff213d
                    Extra: Last beacon: 4436ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'EMSBA' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"EMSBA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008580e40d2d
                    Extra: Last beacon: 4392ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        72:0F:95:EA:B0:EA:3A:33:B3:BE:DE:E1:EE:3A:E7:88:F5:1C:AE:26
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
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        72:0F:95:EA:B0:EA:3A:33:B3:BE:DE:E1:EE:3A:E7:88:F5:1C:AE:26
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        72:0F:95:EA:B0:EA:3A:33:B3:BE:DE:E1:EE:3A:E7:88:F5:1C:AE:26
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        72:0F:95:EA:B0:EA:3A:33:B3:BE:DE:E1:EE:3A:E7:88:F5:1C:AE:26
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5410C94462FA26A0A3F256C
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        72:0F:95:EA:B0:EA:3A:33:B3:BE:DE:E1:EE:3A:E7:88:F5:1C:AE:26
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        72:0F:95:EA:B0:EA:3A:33:B3:BE:DE:E1:EE:3A:E7:88:F5:1C:AE:26
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

[   22.974535] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.257032] wlan0: authenticate with <MAC 'Bell320' [AC1]>
[   24.267204] wlan0: direct probe to <MAC 'Bell320' [AC1]> (try 1/3)
[   24.471227] wlan0: send auth to <MAC 'Bell320' [AC1]> (try 2/3)
[   24.472763] wlan0: authenticated
[   24.475231] wlan0: associate with <MAC 'Bell320' [AC1]> (try 1/3)
[   24.478926] wlan0: RX AssocResp from <MAC 'Bell320' [AC1]> (capab=0xc11 status=0 aid=2)
[   24.479066] wlan0: associated
[   24.479084] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  329.049487] wlan0: AP <MAC 'Bell320' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[  643.258687] wlan0: deauthenticating from <MAC 'Bell320' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  654.618967] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  655.538852] wlan0: authenticate with <MAC 'Bell320' [AC1]>
[  655.549082] wlan0: send auth to <MAC 'Bell320' [AC1]> (try 1/3)
[  655.551999] wlan0: authenticated
[  655.554074] wlan0: associate with <MAC 'Bell320' [AC1]> (try 1/3)
[  655.557804] wlan0: RX AssocResp from <MAC 'Bell320' [AC1]> (capab=0xc11 status=0 aid=2)
[  655.557948] wlan0: associated
[  655.557996] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-04-22
Please do:
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
does that help?
Thanks

---

### Post by bob_smith3 on 2015-05-19
I totally forgot about this thread. So basically, I just ended up upgrading from the 14.04.2LTS version to the 14.10 version. Solved the wifi issues. Thanks

---

### Post by Avirup_Das on 2015-09-29
Hi bob_smith3,

Can you please confirm if the signal strength have improved in 14.10 version of ubuntu as well?

For me, I am using 14.04, and although the Wi-Fi is working somehow, the signal strength is very weak.

Wi-Fi interface: RTL8723BE

---

