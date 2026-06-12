---
title: "wifi doesn't work, always disconnected"
date: 2014-07-20
forum: Networking &amp; Wireless
---

### Post by lizpy66 on 2014-07-20
anytime I turn my laptop on from a shutdown or anything, it always says the network is disconnected, I get no option to use my wi fi. It used to do this occasionally in the past which could be fixed with a simpe restart but for the last week it does everytime on start up and the only way for me to fix it is with "sudo lshw -C network" though I think it worked with "sudo rfkill unblock all" once, can't remember. I'm on ubuntu 14.04, don't know my wirelass card on my laptop. I'm a bit of a noob to ubuntu though sorry.

Thanks in advance

---

### Post by varunendra on 2014-07-20
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Toz on 2014-07-20
*Moved to Networking & Wireless.*

---

### Post by lizpy66 on 2014-07-21
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

larry-HP-Pavilion-g6-Notebook-PC 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : AMD A4-4300M APU with Radeon(tm) HD Graphics
Memory : 3355 MB
Uptime : 08:08:19 up  1:05,  1 user,  load average: 2.44, 2.35, 2.32


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
    Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Brayden2006"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: C4:3D:C7:53:7C:84   
          Bit Rate=57.8 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:145  Invalid misc:7392   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626557  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): 
cfg80211      (2): 
mac80211      (5): 
wmi           (2): 


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o========o==============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
======================o=============o========o==============o=========o===========o==============o===========
 eth0                 | Wired       | r8169  | unavailable  | no      |           |              | 84:34:97:87:43:90
----------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0  [Brayden2006] | 802.11 WiFi | ath9k  | connected    | yes     | 43 Mb/s   | WEP/WPA/WPA2 | 20:16:D8:0A:6B:25

    bedlam:          Infra, E0:3F:49:ED:5B:28, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Alhamba:         Infra, 00:1C:10:2B:FC:58, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    Rusty:           Infra, 00:22:75:B2:66:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *Brayden2006:    Infra, C4:3D:C7:53:7C:84, Freq 2452 MHz, Rate 54 Mb/s, Strength 62 WPA2
    LamNet2:         Infra, 20:AA:4B:68:44:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    hpsetup:         Ad-Hoc, 96:E6:E8:A5:76:A1, Freq 2457 MHz, Rate 11 Mb/s, Strength 30
    randyandshellyhall: Infra, E0:91:F5:E6:2E:84, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    GLOCK21:         Infra, E8:89:2C:38:4C:30, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    MineNotYours:    Infra, EC:1A:59:83:52:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    myqwest7621:     Infra, CC:5D:4E:83:67:0D, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    HOME-448F:       Infra, CC:35:40:CE:44:8F, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    HOME-6F42:       Infra, 5C:57:1A:EA:6F:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    CenturyLink1600: Infra, 2A:28:5D:30:C9:2C, Freq 2442 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    HOME-F011:       Infra, 8C:04:FF:B4:F0:11, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    TheFamilies:     Infra, 00:26:F2:DD:2A:12, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    HOME-F582:       Infra, 44:32:C8:2D:F5:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    haines:          Infra, 00:1C:10:07:23:9A, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WEP

    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.661/1.883/3.106/1.223 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.026/0.030/0.034/0.004 ms


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

          Current Frequency:2.452 GHz (Channel 9)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

```

---

### Post by lizpy66 on 2014-07-21
is that what you needed? I should state I'm on UEFI system and its now working or at least it did once so far though i suspect it will turn off again

---

### Post by varunendra on 2014-07-21
Did you supply your login password when asked by the script?

It seems the script crashed midway while scanning the available networks, so the report is incomplete.

Please also post the outputs of -
```
id
```this time.

---

### Post by lizpy66 on 2014-07-21
yes I did. anyway to fix it?
```

uid=1000(larry) gid=1000(larry) groups=1000(larry),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)

```

---

### Post by varunendra on 2014-07-21
What is the output of -
```
ls -l /sys/module/ath9k/parameters
```
??

I don't know if it is a bug in the script itself or some issue in scanning that caused it to break at that point. Try manually scanning the network and see if you get any errors -
```
sudo iwlist scan
```

This shouldn't be related to the problem you are having, but the error messages, if any, may give us clues on what is wrong. Currently I am suspecting some permission issues somewhere. The output of the "id" command is fine, so it maybe something else on which the permissions are not as they should be.

---

### Post by lizpy66 on 2014-07-21
heres the results of the first one, also may I state the button for wifi doesn't work either not sure if that matters or not.
```

total 0
-r--r--r-- 1 root root 4096 Jul 21 08:04 blink
-r--r--r-- 1 root root 4096 Jul 21 08:04 bt_ant_diversity
-r--r--r-- 1 root root 4096 Jul 21 08:04 btcoex_enable
-r--r--r-- 1 root root 4096 Jul 21 08:04 nohwcrypt
-r--r--r-- 1 root root 4096 Jul 21 08:04 ps_enable

```

here's the results for the 2nd
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C4:3D:C7:53:7C:84
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Brayden2006"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000286113ee08
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 000B4272617964656E32303036
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B000103104700106A0326E9AF1A966EAF81E640167E1E541021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180205F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409080400000000000000000000000000000000000000
          Cell 02 - Address: E8:89:2C:38:4C:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"GLOCK21"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000105383f12d4
                    Extra: Last beacon: 2300ms ago
                    IE: Unknown: 0007474C4F434B3231
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
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
                    IE: Unknown: 0B05020062127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880E8892C384C3010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 03 - Address: 44:32:C8:2D:F5:82
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HOME-F582"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000040b77afc30
                    Extra: Last beacon: 2612ms ago
                    IE: Unknown: 0009484F4D452D46353832
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B0001031047001065250772DB647B725F6BAC88565707C61021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: E2:89:2C:38:4C:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010538440bc1
                    Extra: Last beacon: 2296ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020074127A
                    IE: Unknown: DD07000C4303000000
          Cell 05 - Address: 88:F7:C7:66:4D:E7
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HOME-4DE7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000411e729e20
                    Extra: Last beacon: 2328ms ago
                    IE: Unknown: 0009484F4D452D34444537
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B00010310470010CE2D7389250BDAE9F1CD3EFA16F6FE1F1021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:1C:10:2B:FC:58
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Alhamba"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008400d41bf2
                    Extra: Last beacon: 1364ms ago
                    IE: Unknown: 0007416C68616D6261
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 20:AA:4B:68:44:A2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"LamNet2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001053d4313e4
                    Extra: Last beacon: 1684ms ago
                    IE: Unknown: 00074C616D4E657432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD910050F204104A0001101044000102103B00010310470010EAE6B9EEF5E210309E5982EAABB6DD9F10210013436973636F2053797374656D732C20496E632E1023000E4C696E6B737973204541323730301024000645413237303010420001311054000800060050F20400011011000D436973636F3532373536204150100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 00:22:75:B2:66:80
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Rusty"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003686c8c608
                    Extra: Last beacon: 1692ms ago
                    IE: Unknown: 00055275737479
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE110FFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C33EE110FFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406070500000000000000000000000000000000000000
                    IE: Unknown: DD9F0050F204104A0001101044000102103B000103104700102880288028801880A880002275B266801021001242656C6B696E20436F72706F726174696F6E1023001642656C6B696E20576972656C65737320526F75746572102400034635441042000C3131313131313131313131311054000800060050F20400011011001642656C6B696E20576972656C65737320526F75746572100800020084103C000101
          Cell 09 - Address: EC:1A:59:83:52:D8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MineNotYours"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004af42f180
                    Extra: Last beacon: 1704ms ago
                    IE: Unknown: 000C4D696E654E6F74596F757273
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFFFF00000000000000000001000000000406E6470D00
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 10 - Address: E0:3F:49:ED:5B:28
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"bedlam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000132b4a5c
                    Extra: Last beacon: 1664ms ago
                    IE: Unknown: 00066265646C616D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DDAC0050F204104A0001101044000102103B00010310470010B9D72B31B3084E48957E4413826B077C102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000752542D4E3636551042001165303A33663A34393A65643A35623A32381054000800060050F20400011011000752542D4E363655100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 11 - Address: C4:04:15:10:46:CE
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR15"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001053fc6a03f
                    Extra: Last beacon: 1312ms ago
                    IE: Unknown: 00094E4554474541523135
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AF0181FFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD890050F204104A0001101044000102103B000103104700106DFD8FE2AACD5F739EEC23B10B7EB1E31021000D4E4554474541522C20496E632E1023000A574E44523334303076331024000A574E44523334303076331042000230311054000800060050F20400011011000A574E4452333430307633100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: 96:E6:E8:A5:76:A1
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000001053fbf522c
                    Extra: Last beacon: 996ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: DD050010180100
          Cell 13 - Address: C4:39:3A:18:69:78
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HOME-6978"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000035e52b016b
                    Extra: Last beacon: 1060ms ago
                    IE: Unknown: 0009484F4D452D36393738
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880C4393A186978103C000101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF00010000000000000000000000000F0000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000029127A
                    IE: Unknown: DD07000C4304000000


```

---

### Post by david253 on 2014-07-21
I am also noob to ubuntu, this happens to me sometimes too. Thank you for helping, I can try some of these things too.

---

### Post by varunendra on 2014-07-22
Permissions on parameter files look okay. I wonder why the script failed to read the files then. Please run the following code to manually grab the parameter values for important drivers -
```
grep [[:graph:]] /sys/module/{ath9k,cfg80211,mac80211}/parameters/*
```
..and post back whatever the terminal returns.

And for now, please try changing the channel in your router to channel 1 or 11 (11 looks better, since 1 is already crowded by neighbourhood APs). Also, if the router's bandwidth is set to 20/40 MHz auto mode, try fixing it to 20 MHz only. Reboot the router after saving any changes.

---

