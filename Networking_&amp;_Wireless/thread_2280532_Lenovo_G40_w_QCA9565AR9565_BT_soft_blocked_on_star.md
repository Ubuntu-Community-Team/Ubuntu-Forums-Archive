---
title: "Lenovo G40 w/ QCA9565/AR9565: BT soft blocked on start up"
date: 2015-05-31
forum: Networking &amp; Wireless
---

### Post by smittie2 on 2015-05-31
I have a Levono G40 running Kubuntu 14.10. Bluetooth works but is always soft blocked on startup (according to rfkill list all). sudo rfkill unblock all gets things working normally but I would prefer to fix the source of the problem.

Per the instructions on Wild Man's posts about similar problems, here is the output from the script in his sig:

```
##### dmesg #############################


[    6.756173] ath: phy0: Set BT/WLAN RX diversity capability
[    6.765370] ath: phy0: Enable LNA combining
[    6.766618] ath: phy0: ASPM enabled: 0x43
[    6.766621] ath: EEPROM regdomain: 0x6a
[    6.766622] ath: EEPROM indicates we should expect a direct regpair map
[    6.766624] ath: Country alpha2 being used: 00
[    6.766625] ath: Regpair used: 0x6a
[    7.895689] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.037360] wlan0: authenticate with <MAC 'SmithNet-Buffalo' [AC6]>
[    9.043613] wlan0: send auth to <MAC 'SmithNet-Buffalo' [AC6]> (try 1/3)
[    9.046123] wlan0: authenticated
[    9.048263] wlan0: associate with <MAC 'SmithNet-Buffalo' [AC6]> (try 1/3)
[    9.051973] wlan0: RX AssocResp from <MAC 'SmithNet-Buffalo' [AC6]> (capab=0x411 status=0 aid=6)
[    9.052020] wlan0: associated
[    9.052028] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   14.172049] wlan0: authenticate with <MAC 'SmithNet-Buffalo' [AC1]>
[   14.178322] wlan0: send auth to <MAC 'SmithNet-Buffalo' [AC1]> (try 1/3)
[   14.180619] wlan0: authenticated
[   14.183464] wlan0: associate with <MAC 'SmithNet-Buffalo' [AC1]> (try 1/3)
[   14.187721] wlan0: RX AssocResp from <MAC 'SmithNet-Buffalo' [AC1]> (capab=0x431 status=0 aid=5)
[   14.187772] wlan0: associated


########## wireless info END ############



```

Thank you for the help I have already obtained through this forum. My apologies if the answer to this issue is already there somewhere. I tried a lot of the things suggested for others but did not get any to work on my set up.

Respectfully,
   Smittie

---

### Post by jeremy31 on 2015-05-31
It is possible that the FN combo to enable wifi might prevent the softblock

---

### Post by smittie2 on 2015-05-31
Here is the FULL output from Wild Man's script:

```

########## wireless info START ##########


Report from: 31 May 2015 10:02 PDT -0700


Booted last: 31 May 2015 09:59 PDT -0700


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-38-generic #52-Ubuntu SMP Thu May 7 10:51:21 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


KDE Plasma Workspace


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380a]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lenovo Device [17aa:4026]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 002 Device 003: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
ath3k                  13331  0 
mac80211              660651  1 ath9k
bluetooth             446190  23 bnep,ath3k,btusb,rfcomm
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
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
          inet addr:192.168.11.144  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::5e93:a2ff:feb8:58eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:675482 (675.4 KB)  TX bytes:222987 (222.9 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"SmithNet-Buffalo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'SmithNet-Buffalo' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:32   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 wlan0
192.168.11.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       830     1  0 09:59 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: wlan0  [SmithNet-Buffalo] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Zoomd25b:        Infra, <MAC 'Zoomd25b' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    RMS912:          Infra, <MAC 'RMS912' [AC9]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 35 WPA2
    RMS912:          Infra, <MAC 'RMS912' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ATT2C6j3b7:      Infra, <MAC 'ATT2C6j3b7' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    RMS912:          Infra, <MAC 'RMS912' [AC8]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 20 WPA2
    GRATTAN_2G:      Infra, <MAC 'GRATTAN_2G' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    belkin.510_EXT:  Infra, <MAC 'belkin.510_EXT' [AC15]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 19 WPA2
    NETGEAR12:       Infra, <MAC 'NETGEAR12' [AC16]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 19 WPA2
    GRATTAN_GUEST:   Infra, <MAC 'GRATTAN_GUEST' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    SmithNet-Buffalo:Infra, <MAC 'SmithNet-Buffalo' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    *SmithNet-Buffalo: Infra, <MAC 'SmithNet-Buffalo' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2
    HOWARD FAMILY:   Infra, <MAC 'HOWARD FAMILY' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    MyConnection:    Infra, <MAC 'MyConnection' [AC14]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    NETGEAR57:       Infra, <MAC 'NETGEAR57' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    2WIRE725:        Infra, <MAC '2WIRE725' [AN16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15
    HOME-BE72:       Infra, <MAC 'HOME-BE72' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    RMS912:          Infra, <MAC 'RMS912' [AN19]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HOWARD FAMILY_2GEXT: Infra, <MAC 'HOWARD FAMILY_2GEXT' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    tla53080:        Infra, <MAC 'tla53080' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA2
    Apple Network ec91c5: Infra, <MAC 'Apple Network ec91c5' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2


  IPv4 Settings:
    Address:         192.168.11.144
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1


    DNS:             192.168.11.1


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


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/SmithNet-Buffalo]] (600 root)
[connection] id=SmithNet-Buffalo | type=802-11-wireless
[802-11-wireless] ssid=SmithNet-Buffalo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


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


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      4   APs on   Frequency:2.432 GHz (Channel 5)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'SmithNet-Buffalo' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"SmithNet-Buffalo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001caf9d42b0
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Zoomd25b' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Zoomd25b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ac5f20ef9
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d223dc4e5d
                    Extra: Last beacon: 2312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NETGEAR57' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR57"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003bfce1b8180
                    Extra: Last beacon: 284ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001c65fa2903a
                    Extra: Last beacon: 256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SmithNet-Buffalo' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"SmithNet-Buffalo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001880bcabf
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e28ed2a8aa
                    Extra: Last beacon: 624ms ago
          Cell 08 - Address: <MAC 'RMS912' [AC8]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"RMS912"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e28ece5b80
                    Extra: Last beacon: 920ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'RMS912' [AC9]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"RMS912"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011f1517bf4
                    Extra: Last beacon: 1968ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '' [AC10]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011f158e715
                    Extra: Last beacon: 1468ms ago
          Cell 11 - Address: <MAC 'Apple Network ec91c5' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Apple Network ec91c5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000712799f518d
                    Extra: Last beacon: 748ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'HOWARD FAMILY' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HOWARD FAMILY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d6317f23c
                    Extra: Last beacon: 716ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'xfinitywifi' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d223dc5556
                    Extra: Last beacon: 2312ms ago
          Cell 14 - Address: <MAC 'MyConnection' [AC14]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MyConnection"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013d6fed65e
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'belkin.510_EXT' [AC15]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"belkin.510_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a103091fc
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'NETGEAR12' [AC16]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000357ee08beaf


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5C1878F185424DB0329389D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FF:39:7E:98:A3:02:94:38:C2:56:A9:07:57:7B:66:5A:3C:93:7D:FC
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FF:39:7E:98:A3:02:94:38:C2:56:A9:07:57:7B:66:5A:3C:93:7D:FC
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FF:39:7E:98:A3:02:94:38:C2:56:A9:07:57:7B:66:5A:3C:93:7D:FC
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FF:39:7E:98:A3:02:94:38:C2:56:A9:07:57:7B:66:5A:3C:93:7D:FC
sig_hashalgo:   sha512


[ath3k]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     8449188E53D477A663A0DBF
depends:        bluetooth
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FF:39:7E:98:A3:02:94:38:C2:56:A9:07:57:7B:66:5A:3C:93:7D:FC
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FF:39:7E:98:A3:02:94:38:C2:56:A9:07:57:7B:66:5A:3C:93:7D:FC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FF:39:7E:98:A3:02:94:38:C2:56:A9:07:57:7B:66:5A:3C:93:7D:FC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0


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


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    5.717576] ath: phy0: WB335 2-ANT card detected
[    5.717579] ath: phy0: Set BT/WLAN RX diversity capability
[    5.726433] ath: phy0: Enable LNA combining
[    5.727702] ath: phy0: ASPM enabled: 0x43
[    5.727705] ath: EEPROM regdomain: 0x6a
[    5.727707] ath: EEPROM indicates we should expect a direct regpair map
[    5.727709] ath: Country alpha2 being used: 00
[    5.727710] ath: Regpair used: 0x6a
[   17.038903] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.939217] wlan0: authenticate with <MAC 'SmithNet-Buffalo' [AC1]>
[   17.945502] wlan0: send auth to <MAC 'SmithNet-Buffalo' [AC1]> (try 1/3)
[   17.947392] wlan0: authenticated
[   17.950453] wlan0: associate with <MAC 'SmithNet-Buffalo' [AC1]> (try 1/3)
[   17.954713] wlan0: RX AssocResp from <MAC 'SmithNet-Buffalo' [AC1]> (capab=0x431 status=0 aid=5)
[   17.954769] wlan0: associated
[   17.954777] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

```

---

### Post by praseodym on 2015-05-31
Try
```

gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
Change "false" to "true", save, close the editor and try it again

---

### Post by smittie2 on 2015-05-31
Thank you for your reply.

Not sure I understand why changing WWANEnabled to true would affect BlueTooth soft blocking? All the other items in NetworkManager.state are already 'true'.

  -- Smittie

---

### Post by jeremy31 on 2015-05-31
This might work if ideapad-latop is loaded ```
lsmod | grep ideapad
```

If it shows ideapad-laptop in terminal then ```
echo "options ideapad-laptop no_bt_rfkill=Y" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Reboot

And if you have wifi issues with bluetooth going you may also need to ```
echo "options ath9k btcoex_enable=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

---

