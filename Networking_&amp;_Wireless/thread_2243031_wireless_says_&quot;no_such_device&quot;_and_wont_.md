---
title: "wireless says &quot;no such device&quot; and wont connect (ubuntu 14.04 with Xfce DE)"
date: 2014-09-05
forum: Networking &amp; Wireless
---

### Post by pretty_whistle on 2014-09-05
I have ubuntu 14.04 with Xfce DE.

"no such WaveLAN device" (WaveLAN is the name of the wireless moniotor program, an unimportant fact I thought I'd mention) is what it says but when I reboot it detects wireless networks on the login screen, so go figure.

I had to connect a new modem and now my wireless network wont connect.  Clearly this thing didnt like me changing out the modem so now it says no such device.

I've tried:
-restarting the laptop
-deleting the network and re-entering it
-deleting the network, restarting laptop, then re-entering it
-deleting the network, powering down the laptop, powering down the modem and then restarting everything.  

All to no avail.

What can I do to fix this??

Thanks.

---

### Post by varunendra on 2014-09-06
Let's forget 'WaveLAN' (whatever that is), maybe even remove it if have doubts.

What does the Network Manager say? Does it detect available wireless networks? Tries to connect?

What does the 'sudo iwlist scan' command say? Can it detect the card and available networks?

What does the wireless_script say? [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by pretty_whistle on 2014-09-06
> **varunendra said:**
> Let's forget 'WaveLAN' (whatever that is), maybe even remove it if have doubts.

What does the Network Manager say? Does it detect available wireless networks? Tries to connect?

What does the 'lisudo iwst scan' command say? Can it detect the card and available networks?

What does the wireless_script say? [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

I dont have anything called network manager.  However, I installed "wicd network manager" and it says no wireless networks are detected.

What does the 'lisudo iwst scan' command say??  It says "command not found".

Contents of script:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

nutin 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-2328M CPU @ 2.20GHz
Memory : 3924 MB
Uptime : 07:46:04 up 15:12,  1 user,  load average: 1.18, 1.44, 1.61


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1858]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 064e:e263 Suyin Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
wl                   3999690  0 
lib80211               14040  1 wl
rt2800pci              13374  0 
rt2800mmio             16189  1 rt2800pci
rt2800lib              83150  2 rt2800pci,rt2800mmio
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  2 rt2800pci,rt2800mmio
rt2x00lib              48886  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
wmi                    18673  1 hp_wmi
mac80211              546051  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              409394  3 wl,mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
crc_ccitt              12627  1 rt2800lib


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800pci     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | rt2800pci | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Lailathedog:     Infra, <MAC C-05 Lailathedog>, Freq 2457 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2
    13thNet:         Infra, <MAC C-03 13thNet>, Freq 2417 MHz, Rate 54 Mb/s, Strength 79 WPA2
    HOME-E1B9:       Infra, <MAC C-NA HOME-E1B9 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    CenturyLink5381: Infra, <MAC C-02 CenturyLink5381>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Fools Circle:    Infra, <MAC C-07 Fools Circle>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    CenturyLink1616: Infra, <MAC C-13 CenturyLink1616>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    CenturyLink4798: Infra, <MAC C-10 CenturyLink4798>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    1375Netwerk:     Infra, <MAC C-16 1375Netwerk>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Conrad:          Infra, <MAC C-09 Conrad>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    NETGEAR36:       Infra, <MAC C-NA NETGEAR36 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HOME-A1C2:       Infra, <MAC C-01 HOME-A1C2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Fat Lee Adama Fan Club: Infra, <MAC C-NA Fat Lee Adama Fan Club 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    HP-Print-CE-Photosmart 6520: Infra, <MAC C-12 HP-Print-CE-Photosmart 6520>, Freq 2417 MHz, Rate 54 Mb/s, Strength 37 WPA2
    CenturyLink2712: Infra, <MAC C-04 CenturyLink2712>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    xfinitywifi:     Infra, <MAC C-06 xfinitywifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    Frankie4Fingers: Infra, <MAC C-NA Frankie4Fingers 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA
    HOME-460D:       Infra, <MAC C-15 HOME-460D>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    falko1958:       Infra, <MAC C-NA falko1958 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    13thNet:         Infra, <MAC C-08 13thNet>, Freq 2417 MHz, Rate 54 Mb/s, Strength 24 WPA2
    HOME-6682:       Infra, <MAC C-NA HOME-6682 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    SexySaxMan:      Infra, <MAC C-NA SexySaxMan 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    HOME-79D0:       Infra, <MAC C-NA HOME-79D0 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    xfinitywifi:     Infra, <MAC C-NA xfinitywifi 2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    HOME-7B71:       Infra, <MAC C-NA HOME-7B71 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    CenturyLink1842: Infra, <MAC C-14 CenturyLink1842>, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169     | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
    DNS:             205.171.2.25
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search PK5001Z


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.734/0.800/0.867/0.072 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.019/0.038/0.057/0.019 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 HOME-A1C2>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"HOME-A1C2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b9a69a964
                    Extra: Last beacon: 17892ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 CenturyLink5381>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink5381"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba03ff5be
                    Extra: Last beacon: 1004ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 13thNet>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"13thNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005c83a31d3
                    Extra: Last beacon: 17528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 CenturyLink2712>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink2712"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba06182cf
                    Extra: Last beacon: 688ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Lailathedog>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Lailathedog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba078f7bd
                    Extra: Last beacon: 236ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 xfinitywifi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b9a69c1fe
                    Extra: Last beacon: 17892ms ago
          Cell 07 - Address: <MAC C-07 Fools Circle>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Fools Circle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038c6972754
                    Extra: Last beacon: 372ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 13thNet>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"13thNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b9f5c8996
                    Extra: Last beacon: 944ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 Conrad>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Conrad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba0fab919
                    Extra: Last beacon: 376ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 CenturyLink4798>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink4798"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba00a4006
                    Extra: Last beacon: 1012ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b9e783b4d
                    Extra: Last beacon: 17788ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 HP-Print-CE-Photosmart 6520>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-CE-Photosmart 6520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba26d54a5
                    Extra: Last beacon: 936ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 CenturyLink1616>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink1616"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba06dd6de
                    Extra: Last beacon: 556ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 CenturyLink1842>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink1842"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b9f65b14b
                    Extra: Last beacon: 18020ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 HOME-460D>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"HOME-460D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b965d345a
                    Extra: Last beacon: 1012ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 1375Netwerk>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"1375Netwerk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba4b9d441
                    Extra: Last beacon: 692ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 DIRECT-roku-350-DBAC37>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-350-DBAC37"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba31526c1
                    Extra: Last beacon: 372ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[wl]
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[rt2800pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
firmware:       rt2860.bin
version:        2.3.0
srcversion:     AF1E5AA2D7E623CCBA9A1CD
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
version:        2.3.0
srcversion:     AA2C68A3C0E9D5BDA2B36E9
depends:        rt2800lib,rt2x00lib,rt2x00mmio

[rt2800lib]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     7A7EEDE3C2270AE56EB54F8
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     47F0A082BE7F0118126DD77
depends:        rt2x00lib,mac80211

[rt2x00mmio]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     D5F2B94A767BFCDB29314F2
depends:        rt2x00lib

[rt2x00lib]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     E9BB2D2E4429AB671216A29
depends:        mac80211,cfg80211

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[eeprom_93cx6]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        

[crc_ccitt]
filename:       /lib/modules/3.13.0-35-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/config.d/unload_modules]

[/etc/pm/config.d/unload_modules~]
SUSPEND_MODULES="$SUSPEND_MODULES rt3290sta"


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=120e49fc-e72c-4308-9f94-d572037073e4 ro quiet splash pci=nomsi vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.227610] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.227947] audit: initializing netlink socket (disabled)
[    1.823870] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   21.651667] wmi: Mapper loaded
[   21.706602] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   21.717520] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   21.754916] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.781597] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   24.838463] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.280726] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   26.333519] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   26.448667] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.449046] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20395.394967] rt2800pci 0000:02:00.0: no hotplug settings from platform
[20396.114736] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========
```

---

### Post by pretty_whistle on 2014-09-06
Wait...........

I'm going to try something first before we continue.  I'm going to restore the backup to my laptop and see if that works.  I'll post back the resutls.

---

### Post by praseodym on 2014-09-06
Why is the Broadcom-STA installed?
```

sudo modprobe -rfv wl rt2800pci
sudo modprobe -v rt2800pci
sudo apt-get remove --purge bcmwl-kernel-source
```

---

### Post by pretty_whistle on 2014-09-06
> **praseodym said:**
> Why is the Broadcom-STA installed?
```

sudo modprobe -rfv wl rt2800pci
sudo modprobe -v rt2800pci
sudo apt-get remove --purge bcmwl-kernel-source
```

Isnt that going to remove it?  

It worked ok before I changed out the modem so it should work now.  I dont see how that's the problem.   Unless......... is it a wireless driver problem?? Maybe the older driver wont pick up the new modem?

---

### Post by pretty_whistle on 2014-09-06
Well.....

I restored my backup but it failed.  It's still a problem.  :(

---

### Post by praseodym on 2014-09-06
Obviously, you do not have a Broadcom device, so removing it should not be the problem. Despite that: 2 drivers could cause problems

---

### Post by pretty_whistle on 2014-09-06
> **praseodym said:**
> Obviously, you do not have a Broadcom device, so removing it should not be the problem. Despite that: 2 drivers could cause problems

I ran the commands you gave and restarted the computer.  Darn problem is still there.  :(

---

### Post by varunendra on 2014-09-06
> **pretty_whistle said:**
> I dont have anything called network manager.  However, I installed "wicd network manager" and it says no wireless networks are detected.

What does the '**[COLOR="#FF0000"]lisudo iwst[/COLOR]** scan' command say??  It says "command not found".
I don't think I typed those weird words as commands, must be a copy-paste error on your part, even in the quote above. Please check my first post again - it is "iwlist", and you shouldn't need to be told what "sudo" means. ;) The result is not needed now though, as the script report already includes it.

Oh, and the report cries out loud that you do have a thing called Network Manager installed -
> **pretty_whistle said:**
> ```
nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | rt2800pci | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

....

NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
```
Surprise, huh? :p

I wonder if wicd and nm could be fighting with each other, unless you properly disabled it (recommended is to completely uninstall one if using the other). I recommend purging wicd and using nm again (if not already) for now. It is usually easier to keep things simplified and at defaults while troubleshooting a problem, unless what you changed is proven to be the/a problem itself.

> **pretty_whistle said:**
> It worked ok before I changed out the modem so it should work now.  I dont see how that's the problem.
Well.. everything lives before it dies. Having a driver like "wl" installed needlessly IS a problem, let's see if it was removed properly.. Please purge wicd, and run the script again to post a fresh report showing current status.

And which of the listed APs is the one you are trying to connect to? Do you have admin access to it?
Additionally, could you give us a link to the user manual of your new modem/AP?

---

### Post by pretty_whistle on 2014-09-06
> **varunendra said:**
> I don't think I typed those weird words as commands, must be a copy-paste error on your part, even in the quote above. Please check my first post again - it is "iwlist", and you shouldn't need to be told what "sudo" means. ;) The result is not needed now though, as the script report already includes it.

Oh, and the report cries out loud that you do have a thing called Network Manager installed -

Surprise, huh? :p

I wonder if wicd and nm could be fighting with each other, unless you properly disabled it (recommended is to completely uninstall one if using the other). I recommend purging wicd and using nm again (if not already) for now. It is usually easier to keep things simplified and at defaults while troubleshooting a problem, unless what you changed is proven to be the/a problem itself.


Well.. everything lives before it dies. Having a driver like "wl" installed needlessly IS a problem, let's see if it was removed properly.. Please purge wicd, and run the script again to post a fresh report showing current status.

And which of the listed APs is the one you are trying to connect to? Do you have admin access to it?
Additionally, could you give us a link to the user manual of your new modem/AP?

I installed wicd to help with this problem so the problem was there before I installed it.  Also I ran the script before wicd was installed so it didn't affect the output of the script.

I do have admin access to my modem and the modem I have is this one:

[http://www.zyxel.com/us/en/products_services/pk5001z.shtml?t=p](http://www.zyxel.com/us/en/products_services/pk5001z.shtml?t=p)

I couldnt find a manual for it but there's a PDF for it if that helps:

[http://www.zyxel.com/us/en/uploads/images/ds_PK5001Z.pdf](http://www.zyxel.com/us/en/uploads/images/ds_PK5001Z.pdf)

---

### Post by pretty_whistle on 2014-09-06
Which AP am I trying to connect to?  It's a hidden network that's not listed.

I have another laptop with windows on it and the wireless network works there.  :o  And I'm using wired on the laptop with the problem.  :o

---

### Post by varunendra on 2014-09-06
> **pretty_whistle said:**
> I installed wicd to help with this problem so the problem was there before I installed it.  Also I ran the script before wicd was installed so it didn't affect the output of the script.
Noticed any positive change with WICD? I guess not. If so, how about reverting back to NM (while 'purging' WICD completely) so we have to deal with things that we understand better?

I don't hate WICD, neither do I have any 'affair' going on with NM; it's just that the symptoms so far don't give any hint that the problem can be even remotely caused due to NM. If it becomes suspicious at any stage of troubleshooting, switching between WICD and NM is just a matter of two commands, half a minute.

> **pretty_whistle said:**
> Which AP am I trying to connect to?  It's a hidden network that's not listed.
Not related to the problem, but hiding the AP could be just a minor hindrance in troubleshooting, and _totally pointless_ from security point of view, I once tried to explain why (not very authoritative, but so far I have seen no arguments to the contrary) : [http://ubuntuforums.org/showpost.php?p=13100605](http://ubuntuforums.org/showpost.php?p=13100605)

By the way, the only ONE hidden SSID that appears in the report (yes it does!) has a very weak signal (Cell 11, signal strength 28/70). So either it is not your AP, or something wrong with the card/antenna/driver (oh, but the rt2800pci driver seems to work well as per some other recent threads).

> I have another laptop with windows on it and the wireless network works there.  :o  And I'm using wired on the laptop with the problem.  :o
[s]Okay, so that probably rules out something being wrong with the antenna. Not much help beyond that.[/s]
**EDIT:** Oops! Missed the "another laptop" part. Totally unhelpful then.

Please show the current report (preferably, with NM reinstalled, and other suggested changes applied).

---

### Post by pretty_whistle on 2014-09-07
How do I use the terminal to purge wicd?  I'm only familiar with the software center.

---

### Post by varunendra on 2014-09-07
Simply -
```
sudo apt-get purge wicd wicd-gtk
```

This page should be quite interesting and useful for you if you wish or need to switch between NM and WICD again : [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by pretty_whistle on 2014-09-07
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

nutin 3.13.0-34-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-2328M CPU @ 2.20GHz
Memory : 3924 MB
Uptime : 09:46:27 up 23:55,  2 users,  load average: 1.31, 1.45, 1.48


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1858]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 064e:e263 Suyin Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
rt2800pci              13374  0 
rt2800mmio             16189  1 rt2800pci
rt2800lib              83150  2 rt2800pci,rt2800mmio
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  2 rt2800pci,rt2800mmio
rt2x00lib              48886  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              546051  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              409394  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
wmi                    18673  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800pci     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | rt2800pci | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Lailathedog:     Infra, <MAC C-05 Lailathedog>, Freq 2457 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    13thNet:         Infra, <MAC C-06 13thNet>, Freq 2417 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Fools Circle:    Infra, <MAC C-04 Fools Circle>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    CenturyLink5381: Infra, <MAC C-01 CenturyLink5381>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    HOME-A1C2:       Infra, <MAC C-03 HOME-A1C2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    xfinitywifi:     Infra, <MAC C-NA xfinitywifi 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    Fat Lee Adama Fan Club: Infra, <MAC C-07 Fat Lee Adama Fan Club>, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    CenturyLink1616: Infra, <MAC C-02 CenturyLink1616>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    DIRECT-roku-350-DBAC37: Infra, <MAC C-11 DIRECT-roku-350-DBAC37>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Conrad:          Infra, <MAC C-12 Conrad>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    1375Netwerk:     Infra, <MAC C-13 1375Netwerk>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    HP-Print-CE-Photosmart 6520: Infra, <MAC C-09 HP-Print-CE-Photosmart 6520>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HOME-460D:       Infra, <MAC C-NA HOME-460D 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    CenturyLink1842: Infra, <MAC C-10 CenturyLink1842>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    CenturyLink4798: Infra, <MAC C-08 CenturyLink4798>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    NETGEAR36:       Infra, <MAC C-NA NETGEAR36 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    CenturyLink2712: Infra, <MAC C-NA CenturyLink2712 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    HOME-E1B9:       Infra, <MAC C-NA HOME-E1B9 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    13thNet:         Infra, <MAC C-NA 13thNet 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA2
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169     | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
    DNS:             205.171.2.25
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

BonAire              : ssid=BonAire | mac-address=<MAC ID removed> | ipv4=auto | ipv6=auto 
CenturyLink2712      : ssid=CenturyLink2712 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
H5c8a4fWr 1          : ssid=H5c8a4fWr | ipv4=auto | ipv6=auto 
HOME-5952            : ssid=HOME-5952 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search PK5001Z


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.594/0.644/0.694/0.050 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.036/0.040/0.045/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 CenturyLink5381>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink5381"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000516e57b492
                    Extra: Last beacon: 8496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 CenturyLink1616>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink1616"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000516e7b44f9
                    Extra: Last beacon: 8496ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 HOME-A1C2>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"HOME-A1C2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000516611b45f
                    Extra: Last beacon: 8944ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Fools Circle>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Fools Circle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004e9527f99f
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Lailathedog>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Lailathedog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000516f0c03bd
                    Extra: Last beacon: 92ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 13thNet>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"13thNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b97d5107a
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 Fat Lee Adama Fan Club>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Fat Lee Adama Fan Club"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005171e8c047
                    Extra: Last beacon: 92ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 CenturyLink4798>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink4798"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000516e27a1fa
                    Extra: Last beacon: 9536ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 HP-Print-CE-Photosmart 6520>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-CE-Photosmart 6520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051710638bf
                    Extra: Last beacon: 1056ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 CenturyLink1842>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink1842"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000516f026176
                    Extra: Last beacon: 604ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 DIRECT-roku-350-DBAC37>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-350-DBAC37"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051712c8d93
                    Extra: Last beacon: 8496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Conrad>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Conrad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000516f0857c9
                    Extra: Last beacon: 8496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 1375Netwerk>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"1375Netwerk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051767d1a41
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[rt2800pci]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
firmware:       rt2860.bin
version:        2.3.0
srcversion:     D876F002AA85529257D61EB
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
version:        2.3.0
srcversion:     F196893F5F72140CA847345
depends:        rt2800lib,rt2x00lib,rt2x00mmio

[rt2800lib]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00pci]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211

[rt2x00mmio]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib

[rt2x00lib]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     CC69EE39E7D673974A21C0A
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[eeprom_93cx6]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        

[crc_ccitt]
filename:       /lib/modules/3.13.0-34-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/config.d/unload_modules]

[/etc/pm/config.d/unload_modules~]
SUSPEND_MODULES="$SUSPEND_MODULES rt3290sta"


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=120e49fc-e72c-4308-9f94-d572037073e4 ro quiet splash pci=nomsi vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.222718] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.223068] audit: initializing netlink socket (disabled)
[    1.822085] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   13.250092] wmi: Mapper loaded
[   14.785608] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   14.793889] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   21.374596] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.865411] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   26.016524] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   26.129933] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.130275] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[43965.193644] rt2800pci 0000:02:00.0: no hotplug settings from platform
[43968.021642] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[45558.750903] rt2800pci 0000:02:00.0: no hotplug settings from platform
[45561.512066] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========
```
Here it is.

---

### Post by varunendra on 2014-09-07
The dmesg log shows no attempts to connect to any AP. Is the AP's SSID still hidden? Did you try to connect to it?

I see no hidden SSIDs in the scan results this time. If you set it to advertise its SSID now, is it listed in either the nm-tool or 'iwlist scan' parts? Which one?

I do see a connection profile ("BonAire") that is set to use a wireless device that currently does not exist in the system. If that is the one you are trying to connect to, please delete that saved profile from NM, and let it create one automatically when you scan and try to connect to it again.

**PS:**
The "/etc/pm/config.d/unload_modules" file is needless now. You can (probably 'should') delete it now -
```
sudo rm /etc/pm/config.d/unload_module*
```

---

### Post by pretty_whistle on 2014-09-07
> **varunendra said:**
> The dmesg log shows no attempts to connect to any AP. Is the AP's SSID still hidden? Did you try to connect to it?

I see no hidden SSIDs in the scan results this time. If you set it to advertise its SSID now, is it listed in either the nm-tool or 'iwlist scan' parts? Which one?

I do see a connection profile ("BonAire") that is set to use a wireless device that currently does not exist in the system. If that is the one you are trying to connect to, please delete that saved profile from NM, and let it create one automatically when you scan and try to connect to it again.

**PS:**
The "/etc/pm/config.d/unload_modules" file is needless now. You can (probably 'should') delete it now -
```
sudo rm /etc/pm/config.d/unload_module*
```

BonAire is from a few years ago when I went on vacation so I deleted it.

The one I want is still hidden, it is r H5c8a4fWr but it's not in the list for some reason.  It's listed in my "network connections" window however.

You said, "...If that is the one you are trying to connect to, please delete that  saved profile from NM, and let it create one automatically when you scan  and try to connect to it again.".  Shall I do this with H5c8a4fWr listed in the "network connections" window even though it's not BonAire?  I'm going to try that.......delete it and let it scan networks available and *then* put it in there.  I didnt let it scan before so maybe it never got a chance to find it in the first place........

---

### Post by pretty_whistle on 2014-09-07
I tried it.  It failed.

---

### Post by pretty_whistle on 2014-09-08
I had an idea and tried it.  It worked.  :)

I thought if it's going to act like a annoyance maybe making the SSID public instead of hidden may enable it to pick up the network.  It did!  Why that made a difference I dont know.

Technically I dont like my SSID broadcasted but the chance of someone war driving and trying to hack my network are slim so I can rest easy despite it.  :)

Thanks for your help though.  :)

I'll mark this as solved.

---

