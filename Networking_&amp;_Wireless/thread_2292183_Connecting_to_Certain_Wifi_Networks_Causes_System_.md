---
title: "Connecting to Certain Wifi Networks Causes System Freeze"
date: 2015-08-25
forum: Networking &amp; Wireless
---

### Post by Alan_L on 2015-08-25
Asus F554L
Mediatek MT7630e
Ubuntu 14.04 


I'm a bit new to ubuntu/linux, so any help would be appreciated. 


Right now, I installed the driver from [http://community.linuxmint.com/tutorial/view/1796](http://community.linuxmint.com/tutorial/view/1796) and it worked for my home wifi network. I was able to connect and use it without any issues. 


Right now though, when I try to connect to my college's wifi network, through the guest or the secured wifi options, after I login (or accept terms of use) to the wifi network, the laptop completely freezes. When I run through the auto-configuration tool provided by the school, which sets the option to auto-connect to the secure wifi network, it makes my laptop freeze about one or two seconds after login to my user account. However, if I ethernet tether to the school network or use usb tethering through my phone and have it connect to the school network, both methods allow me to access the internet. 

Logs below:
```



########## wireless info START ##########




Report from: 25 Aug 2015 22:56 EDT -0400




Booted last: 25 Aug 2015 22:52 EDT -0400




Script from: 14 Jul 2015 17:04 UTC +0000




##### release ###########################




Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty




##### kernel ############################




Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux




Parameters: ro, acpi_backlight=vendor, "acpi_osi=!Windows, 2012"




##### desktop ###########################




Ubuntu




##### lspci #############################




02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169




03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e084]
    Kernel driver in use: mt7630e




##### lsusb #############################




Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0489:e080 Foxconn / Hon Hai 
Bus 001 Device 003: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 05c6:676a Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




##### PCMCIA card info ##################




##### rfkill ############################




0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no




##### lsmod #############################




asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
mac80211              708608  1 mt7630e
cfg80211              524288  2 mac80211,mt7630e
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  1 asus_wmi
video                  20480  2 i915,asus_wmi




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




usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.56  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3373 errors:1 dropped:0 overruns:0 frame:1
          TX packets:2728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3107520 (3.1 MB)  TX bytes:770192 (770.1 KB)




wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




##### iwconfig ##########################




eth0      no wireless extensions.




usb0      no wireless extensions.




lo        no wireless extensions.




wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




##### route #############################




Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0




##### resolv.conf #######################




nameserver 127.0.1.1




##### network managers ##################




Installed:




    NetworkManager




Running:




root       985     1  0 22:52 ?        00:00:00 NetworkManager




##### NetworkManager info ###############




NetworkManager Tool




State: connected (global)




- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>




  Capabilities:
    Carrier Detect:  yes




  Wired Properties
    Carrier:         on




  IPv4 Settings:
    Address:         192.168.42.56
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129




    DNS:             192.168.42.129




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            mt7630e
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>




  Capabilities:




  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes




  Wireless Access Points 
    YaleSecure:      Infra, <MAC 'YaleSecure' [AC1]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 74 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN2]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 74 WPA2 Enterprise
    YaleSecure:      Infra, <MAC 'YaleSecure' [AC20]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 74 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC21]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 74 WPA2 Enterprise
    YaleSecure:      Infra, <MAC 'YaleSecure' [AN5]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC16]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70 WPA2 Enterprise
    YaleSecure:      Infra, <MAC 'YaleSecure' [AN7]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN8]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70 WPA2 Enterprise
    YaleSecure:      Infra, <MAC 'YaleSecure' [AC5]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 68 WPA WPA2 Enterprise
    YaleSecure:      Infra, <MAC 'YaleSecure' [AC15]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 68 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC6]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 68 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC18]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 68 WPA2 Enterprise
    Crestron:        Infra, <MAC 'Crestron' [AC7]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 54 WPA2
    YaleSecure:      Infra, <MAC 'YaleSecure' [AC10]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 56 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC11]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 55 WPA2 Enterprise
    YaleSecure:      Infra, <MAC 'YaleSecure' [AC30]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 54 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC31]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 54 WPA2 Enterprise
    yale wireless:   Infra, <MAC 'yale wireless' [AC2]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 74
    YaleGuest:       Infra, <MAC 'YaleGuest' [AC19]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 74
    yale wireless:   Infra, <MAC 'yale wireless' [AC13]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70
    YaleGuest:       Infra, <MAC 'YaleGuest' [AC12]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70
    yale wireless:   Infra, <MAC 'yale wireless' [AN22]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 69
    YaleGuest:       Infra, <MAC 'YaleGuest' [AN23]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 69
    yale wireless:   Infra, <MAC 'yale wireless' [AC22]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70
    YaleGuest:       Infra, <MAC 'YaleGuest' [AN25]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 70
    yale wireless:   Infra, <MAC 'yale wireless' [AC4]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 68
    YaleGuest:       Infra, <MAC 'YaleGuest' [AC28]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 68
    YaleGuest:       Infra, <MAC 'YaleGuest' [AC27]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 68
    linksys:         Infra, <MAC 'linksys' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    yale wireless:   Infra, <MAC 'yale wireless' [AC14]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 55
    YaleGuest:       Infra, <MAC 'YaleGuest' [AC9]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 55
    yale wireless:   Infra, <MAC 'yale wireless' [AC25]>, Freq 2437 MHz, Rate 48 Mb/s, Strength 54
    yale wireless:   Infra, <MAC 'yale wireless' [AC8]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 54
    badger:          Infra, <MAC 'badger' [AC26]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    YaleSecure:      Infra, <MAC 'YaleSecure' [AN35]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 71 WPA WPA2 Enterprise
    YaleGuest:       Infra, <MAC 'YaleGuest' [AC29]>, Freq 2462 MHz, Rate 48 Mb/s, Strength 62
    yale wireless:   Infra, <MAC 'yale wireless' [AC23]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 72
    eduroam:         Infra, <MAC 'eduroam' [AN38]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 71 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN39]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 68 WPA2 Enterprise
    YaleGuest:       Infra, <MAC 'YaleGuest' [AN40]>, Freq 2412 MHz, Rate 48 Mb/s, Strength 71




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
WWANEnabled=true
WimaxEnabled=true




##### NetworkManager.conf ###############




[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq




[ifupdown]
managed=false




##### NetworkManager profiles ###########




[[/etc/NetworkManager/system-connections/PB5M2]] (600 root)
[connection] id=PB5M2 | type=802-11-wireless
[802-11-wireless] ssid=PB5M2 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto




[[/etc/NetworkManager/system-connections/bulldog]] (600 root)
[connection] id=bulldog | type=802-11-wireless
[802-11-wireless] ssid=bulldog | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto




[[/etc/NetworkManager/system-connections/1911knight]] (600 root)
[connection] id=1911knight | type=802-11-wireless
[802-11-wireless] ssid=1911knight | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto




##### iw reg get ########################




Region: America/New_York (based on set time zone)




country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




##### iwlist channels ###################




eth0      no frequency information.




usb0      no frequency information.




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




##### iwlist scan #######################




eth0      Interface doesn't support scanning.




usb0      Interface doesn't support scanning.




lo        Interface doesn't support scanning.




Channel occupancy:




      10   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      10   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      8   APs on   Frequency:2.462 GHz (Channel 11)




wlan0     Scan completed :
          Cell 01 - Address: <MAC 'YaleSecure' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"YaleSecure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001877da27d5
                    Extra: Last beacon: 1016ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC 'yale wireless' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cf5346c27
                    Extra: Last beacon: 952ms ago
          Cell 03 - Address: <MAC 'linksys' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000091275739050
                    Extra: Last beacon: 620ms ago
          Cell 04 - Address: <MAC 'yale wireless' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=51 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b7c803a0d
                    Extra: Last beacon: 684ms ago
          Cell 05 - Address: <MAC 'YaleSecure' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:on
                    ESSID:"YaleSecure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c0561554
                    Extra: Last beacon: 692ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'eduroam' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=51 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b7c813780
                    Extra: Last beacon: 684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'Crestron' [AC7]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-191 dBm  
                    Encryption key:on
                    ESSID:"Crestron"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000050c3cca98a9
                    Extra: Last beacon: 500ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'yale wireless' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=57 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ceb64ab00
                    Extra: Last beacon: 376ms ago
          Cell 09 - Address: <MAC 'YaleGuest' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=57 dBm  
                    Encryption key:off
                    ESSID:"YaleGuest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000fe8675d
                    Extra: Last beacon: 372ms ago
          Cell 10 - Address: <MAC 'YaleSecure' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=57 dBm  
                    Encryption key:on
                    ESSID:"YaleSecure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000fe86a56
                    Extra: Last beacon: 372ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC 'eduroam' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=57 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000009295f64
                    Extra: Last beacon: 404ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC 'YaleGuest' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:off
                    ESSID:"YaleGuest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001877da24ff
                    Extra: Last beacon: 1016ms ago
          Cell 13 - Address: <MAC 'yale wireless' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001877da2019
                    Extra: Last beacon: 1016ms ago
          Cell 14 - Address: <MAC 'yale wireless' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=57 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000fe75e22
                    Extra: Last beacon: 440ms ago
          Cell 15 - Address: <MAC 'YaleSecure' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=51 dBm  
                    Encryption key:on
                    ESSID:"YaleSecure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b7c813438
                    Extra: Last beacon: 692ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 16 - Address: <MAC 'eduroam' [AC16]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-186 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a75d596dc0
                    Extra: Last beacon: 1008ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 17 - Address: <MAC '' [AC17]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-192 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019dc964d80
                    Extra: Last beacon: 832ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'eduroam' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c056269d
                    Extra: Last beacon: 688ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: <MAC 'YaleGuest' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=48 dBm  
                    Encryption key:off
                    ESSID:"YaleGuest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cf53381d0
                    Extra: Last beacon: 1012ms ago
          Cell 20 - Address: <MAC 'YaleSecure' [AC20]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"YaleSecure"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cf533674d
                    Extra: Last beacon: 1020ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC 'eduroam' [AC21]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cf533694d
                    Extra: Last beacon: 1020ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 22 - Address: <MAC 'yale wireless' [AC22]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-184 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019299fdc180
                    Extra: Last beacon: 996ms ago
          Cell 23 - Address: <MAC 'yale wireless' [AC23]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-186 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002490f180
                    Extra: Last beacon: 992ms ago
          Cell 24 - Address: <MAC '' [AC24]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=62 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a0eb1fd80
                    Extra: Last beacon: 880ms ago
          Cell 25 - Address: <MAC 'yale wireless' [AC25]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c05513f7
                    Extra: Last beacon: 760ms ago
          Cell 26 - Address: <MAC 'badger' [AC26]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"badger"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000066a6f403185
                    Extra: Last beacon: 716ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'YaleGuest' [AC27]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:off
                    ESSID:"YaleGuest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c056125a
                    Extra: Last beacon: 696ms ago
          Cell 28 - Address: <MAC 'YaleGuest' [AC28]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=51 dBm  
                    Encryption key:off
                    ESSID:"YaleGuest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b7c81313f
                    Extra: Last beacon: 684ms ago
          Cell 29 - Address: <MAC 'YaleGuest' [AC29]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=57 dBm  
                    Encryption key:off
                    ESSID:"YaleGuest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ceb64b05c
                    Extra: Last beacon: 376ms ago
          Cell 30 - Address: <MAC 'YaleSecure' [AC30]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:on
                    ESSID:"YaleSecure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ceb64b357
                    Extra: Last beacon: 368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 31 - Address: <MAC 'eduroam' [AC31]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ceb64b694
                    Extra: Last beacon: 368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x




##### module infos ######################




[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)




[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




##### module parameters #################




[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0




[/etc/pm/sleep.d/20_custom-ehci_hcd] (755 root)
VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1
unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}
bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}
case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac




##### udev rules ########################




[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14c3:0x7630 (mt7630e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




##### dmesg #############################




[   20.465031] ===>rt2x00lib_start
[   20.465279] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'MT7650E234.bin'
[   20.791394] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 112.3
[   20.862557] rt2800pci_write_firmware: COM_REG0(0x730) = 0x1
[   20.862561] rt2800_load_firmware: COM_REG0(0x730) = 0x1
[   20.869502] ===>rt2x00lib_enable_radio
[   20.869543] ===>rt2800_enable_radio: 
[   20.869871] rt2800_init_bbp(): Init BBP Registers MT7630 (repeated 2 times)
[   20.870908] rt2800_init_bbp(): Init BBP Registers MT7630 complete
[   20.870909] ==>rt2800lib_init_queues
[   20.870922] <===rt2800lib_init_queues
[   20.870930] rt2800_enable_radio -7630 Dual antenna mode
[   20.885434] rt2800_init_rfcsr(): Init RF Registers MT7630
[   20.885821] rt2800_init_rfcsr: B0.R22 = 0x65
[   20.885835] rt2800_init_rfcsr(): Init RF Registers MT7630 complete
[   20.933483] rt2800pci_toggle_irq(1):Check if PDMA is idle!
[   20.933486] rt2800pci_toggle_irq(2):Check if PDMA is idle!
[   20.945420] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready




########## wireless info END ############





```
 syslog dump after attempting to connect to wireless:
```
Aug 25 23:26:15 alan-X555LAB rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="871" x-info="http://www.rsyslog.com"] startAug 25 23:26:15 alan-X555LAB rsyslogd: rsyslogd's groupid changed to 104
Aug 25 23:26:15 alan-X555LAB rsyslogd: rsyslogd's userid changed to 101
Aug 25 23:26:15 alan-X555LAB rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Initializing cgroup subsys cpuacct
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Linux version 3.19.0-26-generic (buildd@lgw01-04) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 (Ubuntu 3.19.0-26.28~14.04.1-generic 3.19.8-ckt4)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-26-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro acpi_backlight=vendor "acpi_osi=!Windows 2012"
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] KERNEL supported cpus:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   Intel GenuineIntel
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   AMD AuthenticAMD
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   Centaur CentaurHauls
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d76a2fff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000d76a3000-0x00000000d79f8fff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000d79f9000-0x00000000dae72fff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000dae73000-0x00000000daed1fff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000daed2000-0x00000000db331fff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000db332000-0x00000000dc46dfff] ACPI NVS
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000dc46e000-0x00000000dceeafff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000dceeb000-0x00000000dcffefff] type 20
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000dcfff000-0x00000000dcffffff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000dd800000-0x00000000dfffffff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021effffff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] efi: EFI v2.40 by American Megatrends
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] efi:  ACPI=0xdb778000  ACPI 2.0=0xdb778000  SMBIOS=0xdce33a18 
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] SMBIOS 2.8 present.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] DMI: ASUSTeK COMPUTER INC. X555LAB/X555LAB, BIOS X555LAB.303 12/19/2014
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] AGP: No AGP bridge found
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] e820: last_pfn = 0x21f000 max_arch_pfn = 0x400000000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] MTRR default type: uncachable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   00000-9FFFF write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   A0000-DFFFF uncachable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   E0000-FFFFF write-protect
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] MTRR variable ranges enabled:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   0 base 0000000000 mask 7F80000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   2 base 00C0000000 mask 7FF0000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   3 base 00D0000000 mask 7FF8000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   4 base 00D8000000 mask 7FFC000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   5 base 00DC000000 mask 7FFF000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   6 base 0100000000 mask 7F00000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   7 base 0200000000 mask 7FE0000000 write-back
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   8 base 021F000000 mask 7FFF000000 uncachable
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   9 disabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] original variable MTRRs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 3, base: 3328MB, range: 128MB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 4, base: 3456MB, range: 64MB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 5, base: 3520MB, range: 16MB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 6, base: 4GB, range: 4GB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 7, base: 8GB, range: 512MB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 8, base: 8688MB, range: 16MB, type UC
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] total RAM covered: 8128M
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Found optimal setting for mtrr clean up
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] New variable MTRRs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 3, base: 3536MB, range: 16MB, type UC
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 4, base: 3552MB, range: 32MB, type UC
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 5, base: 4GB, range: 4GB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 6, base: 8GB, range: 512MB, type WB
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] reg 7, base: 8688MB, range: 16MB, type UC
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] e820: update [mem 0xdd000000-0xffffffff] usable ==> reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] e820: last_pfn = 0xdd000 max_arch_pfn = 0x400000000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Using GB pages for direct mapping
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BRK [0x02fd4000, 0x02fd4fff] PGTABLE
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BRK [0x02fd5000, 0x02fd5fff] PGTABLE
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BRK [0x02fd6000, 0x02fd6fff] PGTABLE
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0x21ee00000-0x21effffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x21ee00000-0x21effffff] page 2M
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BRK [0x02fd7000, 0x02fd7fff] PGTABLE
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x21edfffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x200000000-0x21edfffff] page 2M
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0x1e0000000-0x1ffffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x1e0000000-0x1ffffffff] page 1G
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xd76a2fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xc0000000-0xd75fffff] page 2M
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xd7600000-0xd76a2fff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0xd79f9000-0xdae72fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xd79f9000-0xd79fffff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xd7a00000-0xdadfffff] page 2M
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xdae00000-0xdae72fff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BRK [0x02fd8000, 0x02fd8fff] PGTABLE
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] BRK [0x02fd9000, 0x02fd9fff] PGTABLE
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0xdaed2000-0xdb331fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xdaed2000-0xdaffffff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xdb000000-0xdb1fffff] page 2M
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xdb200000-0xdb331fff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0xdcfff000-0xdcffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0xdcfff000-0xdcffffff] page 4k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1dfffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [mem 0x100000000-0x1dfffffff] page 1G
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] RAMDISK: [mem 0x3589a000-0x36c44fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: Early table checksum verification disabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: RSDP 0x00000000DB778000 000024 (v02 _ASUS_)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: XSDT 0x00000000DB7780A8 0000D4 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: FACP 0x00000000DB790278 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: DSDT 0x00000000DB778210 018063 (v02 _ASUS_ Notebook 01072009 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: FACS 0x00000000DC46BF80 000040
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: APIC 0x00000000DB790388 000084 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: FPDT 0x00000000DB790410 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: FIDT 0x00000000DB790458 00009C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: ECDT 0x00000000DB7904F8 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: MCFG 0x00000000DB7905C0 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: HPET 0x00000000DB790600 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB790638 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: UEFI 0x00000000DB790950 000042 (v01                 00000000      00000000)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB790998 000194 (v01 Intel  zpodd    00001000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB790B30 000C7D (v02 Ther_R Ther_Rvp 00001000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: ASF! 0x00000000DB7917B0 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB791850 000539 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB791D90 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB792908 003245 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB795B50 000394 (v02 CppcTa CppcTabl 00001000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: PCCT 0x00000000DB795EE8 00006E (v05 PcctTa PcctTabl 00001000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB795F58 000AC4 (v02 Cpc_Ta Cpc_Tabl 00001000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: SSDT 0x00000000DB796A20 006622 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: DMAR 0x00000000DB79D048 0000A8 (v01 INTEL  BDW      00000001 INTL 00000001)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: BGRT 0x00000000DB79D0F0 000038 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: MSDM 0x00000000DAED0E18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] No NUMA configuration found
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021effffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x21eff7000-0x21effbfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216600000-ffff88021e5fffff] on node 0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Zone ranges:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   Normal   [mem 0x100000000-0x21effffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Movable zone start for each node
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Early memory node ranges
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   node   0: [mem 0x00001000-0x00057fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   node   0: [mem 0x00059000-0x0009dfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   node   0: [mem 0x00100000-0xd76a2fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   node   0: [mem 0xd79f9000-0xdae72fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   node   0: [mem 0xdaed2000-0xdb331fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   node   0: [mem 0xdcfff000-0xdcffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   node   0: [mem 0x100000000-0x21effffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Initmem setup node 0 [mem 0x00001000-0x21effffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] On node 0 totalpages: 2072346
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   DMA zone: 22 pages reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   DMA32 zone: 13950 pages used for memmap
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   DMA32 zone: 892798 pages, LIFO batch:31
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   Normal zone: 18368 pages used for memmap
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]   Normal zone: 1175552 pages, LIFO batch:31
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Reserving Intel graphics stolen memory at 0xde000000-0xdfffffff
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x0])
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x0])
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x0])
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x0])
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd76a3000-0xd79f8fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdae73000-0xdaed1fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdb332000-0xdc46dfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdc46e000-0xdceeafff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdceeb000-0xdcffefff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdd000000-0xdd7fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdd800000-0xdfffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xf7ffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88021ec00000 s86144 r8192 d32640 u524288
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2039942
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Policy zone: Normal
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-26-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro acpi_backlight=vendor "acpi_osi=!Windows 2012"
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] AGP: Checking aperture...
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] AGP: No AGP bridge found
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Memory: 7990016K/8289384K available (7919K kernel code, 1174K rwdata, 3756K rodata, 1408K init, 1292K bss, 299368K reserved, 0K cma-reserved)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Hierarchical RCU implementation.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] NR_IRQS:16640 nr_irqs:728 16
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] Console: colour dummy device 80x25
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] console [tty0] enabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] hpet clockevent registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000000] tsc: Detected 2196.890 MHz processor
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000026] Calibrating delay loop (skipped), value calculated using timer frequency.. 4393.78 BogoMIPS (lpj=8787560)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000031] pid_max: default: 32768 minimum: 301
Aug 25 23:26:15 alan-X555LAB kernel: [    0.000037] ACPI: Core revision 20141107
Aug 25 23:26:15 alan-X555LAB kernel: [    0.025920] ACPI: All ACPI Tables successfully acquired
Aug 25 23:26:15 alan-X555LAB kernel: [    0.026787] Security Framework initialized
Aug 25 23:26:15 alan-X555LAB kernel: [    0.026801] AppArmor: AppArmor initialized
Aug 25 23:26:15 alan-X555LAB kernel: [    0.026802] Yama: becoming mindful.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.027284] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.028725] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029341] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029352] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029538] Initializing cgroup subsys memory
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029544] Initializing cgroup subsys devices
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029547] Initializing cgroup subsys freezer
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029550] Initializing cgroup subsys net_cls
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029552] Initializing cgroup subsys blkio
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029555] Initializing cgroup subsys perf_event
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029557] Initializing cgroup subsys net_prio
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029560] Initializing cgroup subsys hugetlb
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029584] CPU: Physical Processor ID: 0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029586] CPU: Processor Core ID: 0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029590] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Aug 25 23:26:15 alan-X555LAB kernel: [    0.029590] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.030564] mce: CPU supports 7 MCE banks
Aug 25 23:26:15 alan-X555LAB kernel: [    0.030576] CPU0: Thermal monitoring enabled (TM1)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.030584] process: using mwait in idle threads
Aug 25 23:26:15 alan-X555LAB kernel: [    0.030588] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
Aug 25 23:26:15 alan-X555LAB kernel: [    0.030588] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
Aug 25 23:26:15 alan-X555LAB kernel: [    0.030925] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.034301] ftrace: allocating 30016 entries in 118 pages
Aug 25 23:26:15 alan-X555LAB kernel: [    0.045971] dmar: Host address width 39
Aug 25 23:26:15 alan-X555LAB kernel: [    0.045974] dmar: DRHD base: 0x000000fed90000 flags: 0x0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.045983] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
Aug 25 23:26:15 alan-X555LAB kernel: [    0.045985] dmar: DRHD base: 0x000000fed91000 flags: 0x1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.045990] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
Aug 25 23:26:15 alan-X555LAB kernel: [    0.045992] dmar: RMRR base: 0x000000dce44000 end: 0x000000dce52fff
Aug 25 23:26:15 alan-X555LAB kernel: [    0.045994] dmar: RMRR base: 0x000000dd800000 end: 0x000000dfffffff
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046116] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046118] HPET id 0 under DRHD base 0xfed91000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046119] Queued invalidation will be enabled to support x2apic and Intr-remapping.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046121] Your BIOS is broken and requested that x2apic be disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046121] This will slightly decrease performance.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046121] Use 'intremap=no_x2apic_optout' to override BIOS request.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046324] Enabled IRQ remapping in xapic mode
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046326] x2apic not enabled, IRQ remapping is in xapic mode
Aug 25 23:26:15 alan-X555LAB kernel: [    0.046936] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086611] smpboot: CPU0: Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz (fam: 06, model: 3d, stepping: 04)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086618] TSC deadline timer enabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086637] Performance Events: PEBS fmt2+, generic architected perfmon, full-width counters, Intel PMU driver.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086643] ... version:                3
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086644] ... bit width:              48
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086645] ... generic registers:      4
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086647] ... value mask:             0000ffffffffffff
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086648] ... max period:             0000ffffffffffff
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086649] ... fixed-purpose events:   3
Aug 25 23:26:15 alan-X555LAB kernel: [    0.086651] ... event mask:             000000070000000f
Aug 25 23:26:15 alan-X555LAB kernel: [    0.087433] x86: Booting SMP configuration:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.087436] .... node  #0, CPUs:      #1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.101601] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.101676]  #2 #3
Aug 25 23:26:15 alan-X555LAB kernel: [    0.130018] x86: Booted up 1 node, 4 CPUs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.130022] smpboot: Total of 4 processors activated (17575.12 BogoMIPS)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.133512] devtmpfs: initialized
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135493] evm: security.selinux
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135495] evm: security.SMACK64
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135496] evm: security.SMACK64EXEC
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135497] evm: security.SMACK64TRANSMUTE
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135499] evm: security.SMACK64MMAP
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135500] evm: security.ima
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135501] evm: security.capability
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135544] PM: Registering ACPI NVS region [mem 0xdb332000-0xdc46dfff] (18071552 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135837] pinctrl core: initialized pinctrl subsystem
Aug 25 23:26:15 alan-X555LAB kernel: [    0.135927] RTC time: 23:25:56, date: 08/25/15
Aug 25 23:26:15 alan-X555LAB kernel: [    0.136020] NET: Registered protocol family 16
Aug 25 23:26:15 alan-X555LAB kernel: [    0.137334] cpuidle: using governor ladder
Aug 25 23:26:15 alan-X555LAB kernel: [    0.141348] cpuidle: using governor menu
Aug 25 23:26:15 alan-X555LAB kernel: [    0.141397] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Aug 25 23:26:15 alan-X555LAB kernel: [    0.141400] ACPI: bus type PCI registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.141402] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Aug 25 23:26:15 alan-X555LAB kernel: [    0.141463] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.141466] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Aug 25 23:26:15 alan-X555LAB kernel: [    0.141544] PCI: Using configuration type 1 for base access
Aug 25 23:26:15 alan-X555LAB kernel: [    0.145706] ACPI: Added _OSI(Module Device)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.145709] ACPI: Added _OSI(Processor Device)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.145711] ACPI: Added _OSI(3.0 _SCP Extensions)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.145713] ACPI: Added _OSI(Processor Aggregator Device)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.145715] ACPI: Deleted _OSI(Windows 2012)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.148657] ACPI : EC: EC description table is found, configuring boot EC
Aug 25 23:26:15 alan-X555LAB kernel: [    0.151605] ACPI: Executed 9 blocks of module-level executable AML code
Aug 25 23:26:15 alan-X555LAB kernel: [    0.157516] ACPI: Dynamic OEM Table Load:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.157523] ACPI: SSDT 0xFFFF880214F96400 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.158426] ACPI: Dynamic OEM Table Load:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.158432] ACPI: SSDT 0xFFFF880214F3B000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.159369] ACPI: Dynamic OEM Table Load:
Aug 25 23:26:15 alan-X555LAB kernel: [    0.159374] ACPI: SSDT 0xFFFF880214FB8A00 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.160904] ACPI: Interpreter enabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.160913] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.160920] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.160933] ACPI: (supports S0 S3 S4 S5)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.160935] ACPI: Using IOAPIC for interrupt routing
Aug 25 23:26:15 alan-X555LAB kernel: [    0.160959] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug 25 23:26:15 alan-X555LAB kernel: [    0.162824] ACPI: Power Resource [PG00] (on)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.163130] ACPI: Power Resource [PG01] (on)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.163426] ACPI: Power Resource [PG02] (on)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.171048] ACPI: Power Resource [FN00] (off)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.171109] ACPI: Power Resource [FN01] (off)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.171167] ACPI: Power Resource [FN02] (off)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.171224] ACPI: Power Resource [FN03] (off)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.171281] ACPI: Power Resource [FN04] (off)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.172080] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Aug 25 23:26:15 alan-X555LAB kernel: [    0.172086] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.172531] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.172534] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173018] PCI host bridge to bus 0000:00
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173021] pci_bus 0000:00: root bus resource [bus 00-3e]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173023] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173025] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173027] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173029] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173031] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173033] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173035] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173037] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173038] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173040] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173042] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173044] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173052] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173136] pci 0000:00:02.0: [8086:1616] type 00 class 0x030000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173146] pci 0000:00:02.0: reg 0x10: [mem 0xf6000000-0xf6ffffff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173152] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173156] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173235] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173242] pci 0000:00:03.0: reg 0x10: [mem 0xf721c000-0xf721ffff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173328] pci 0000:00:04.0: [8086:1603] type 00 class 0x118000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173339] pci 0000:00:04.0: reg 0x10: [mem 0xf7210000-0xf7217fff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173449] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173464] pci 0000:00:14.0: reg 0x10: [mem 0xf7200000-0xf720ffff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173517] pci 0000:00:14.0: PME# supported from D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173564] pci 0000:00:14.0: System wakeup disabled by ACPI
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173597] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173615] pci 0000:00:16.0: reg 0x10: [mem 0xf7224000-0xf722401f 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173679] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173753] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173769] pci 0000:00:1b.0: reg 0x10: [mem 0xf7218000-0xf721bfff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173821] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173864] pci 0000:00:1b.0: System wakeup disabled by ACPI
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173894] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173953] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.173998] pci 0000:00:1c.0: System wakeup disabled by ACPI
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174028] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174088] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174130] pci 0000:00:1c.2: System wakeup disabled by ACPI
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174158] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174218] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174260] pci 0000:00:1c.3: System wakeup disabled by ACPI
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174296] pci 0000:00:1f.0: [8086:9cc3] type 00 class 0x060100
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174464] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174477] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174483] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174488] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174494] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174500] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174506] pci 0000:00:1f.2: reg 0x24: [mem 0xf7222000-0xf72227ff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174539] pci 0000:00:1f.2: PME# supported from D3hot
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174601] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174613] pci 0000:00:1f.3: reg 0x10: [mem 0xf7221000-0xf72210ff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174630] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174712] pci 0000:00:1f.6: [8086:9ca4] type 00 class 0x118000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174741] pci 0000:00:1f.6: reg 0x10: [mem 0xf7220000-0xf7220fff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174952] acpiphp: Slot [1] registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.174957] pci 0000:00:1c.0: PCI bridge to [bus 01]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.175034] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.175051] pci 0000:02:00.0: reg 0x10: [io  0xe000-0xe0ff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.175077] pci 0000:02:00.0: reg 0x18: [mem 0xf7104000-0xf7104fff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.175094] pci 0000:02:00.0: reg 0x20: [mem 0xf7100000-0xf7103fff 64bit]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.175186] pci 0000:02:00.0: supports D1 D2
Aug 25 23:26:15 alan-X555LAB kernel: [    0.175187] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.181414] pci 0000:00:1c.2: PCI bridge to [bus 02]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.181418] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.181421] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.181502] pci 0000:03:00.0: [14c3:7630] type 00 class 0x028000
Aug 25 23:26:15 alan-X555LAB kernel: [    0.181520] pci 0000:03:00.0: reg 0x10: [mem 0xf7000000-0xf70fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.181649] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Aug 25 23:26:15 alan-X555LAB kernel: [    0.189430] pci 0000:00:1c.3: PCI bridge to [bus 03]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.189435] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190220] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190267] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190310] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190353] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190395] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190436] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190478] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190519] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.190950] ACPI: Enabled 4 GPEs in block 00 to 7F
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191016] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191098] vgaarb: setting as boot device: PCI:0000:00:02.0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191101] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191104] vgaarb: loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191106] vgaarb: bridge control possible 0000:00:02.0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191304] SCSI subsystem initialized
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191344] libata version 3.00 loaded.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191361] ACPI: bus type USB registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191377] usbcore: registered new interface driver usbfs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191384] usbcore: registered new interface driver hub
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191398] usbcore: registered new device driver usb
Aug 25 23:26:15 alan-X555LAB kernel: [    0.191541] PCI: Using ACPI for IRQ routing
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192722] PCI: pci_cache_line_size set to 64 bytes
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192760] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192761] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192762] e820: reserve RAM buffer [mem 0xd76a3000-0xd7ffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192763] e820: reserve RAM buffer [mem 0xdae73000-0xdbffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192765] e820: reserve RAM buffer [mem 0xdb332000-0xdbffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192766] e820: reserve RAM buffer [mem 0xdd000000-0xdfffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192767] e820: reserve RAM buffer [mem 0x21f000000-0x21fffffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192858] NetLabel: Initializing
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192860] NetLabel:  domain hash size = 128
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192861] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192873] NetLabel:  unlabeled traffic allowed by default
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192930] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.192936] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Aug 25 23:26:15 alan-X555LAB kernel: [    0.194970] Switched to clocksource hpet
Aug 25 23:26:15 alan-X555LAB kernel: [    0.199850] AppArmor: AppArmor Filesystem Enabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.199906] pnp: PnP ACPI init
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200052] system 00:00: [io  0x0240-0x0259] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200056] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200122] pnp 00:01: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200154] pnp 00:02: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200219] system 00:03: [io  0x0680-0x069f] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200222] system 00:03: [io  0xffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200224] system 00:03: [io  0xffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200226] system 00:03: [io  0xffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200229] system 00:03: [io  0x1800-0x18fe] could not be reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200231] system 00:03: [io  0x164e-0x164f] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200233] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200270] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200299] system 00:05: [io  0x1854-0x1857] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200301] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200421] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200423] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200425] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200427] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200430] system 00:06: [mem 0xf8000000-0xfbffffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200432] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200434] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200436] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200438] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200441] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200443] system 00:06: [mem 0xf7fe0000-0xf7feffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200445] system 00:06: [mem 0xf7ff0000-0xf7ffffff] has been reserved
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200447] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.200755] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.201192] pnp: PnP ACPI: found 8 devices
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207042] pci 0000:00:1c.0: PCI bridge to [bus 01]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207052] pci 0000:00:1c.2: PCI bridge to [bus 02]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207055] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207059] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207066] pci 0000:00:1c.3: PCI bridge to [bus 03]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207070] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207077] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207078] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207080] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207081] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207082] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207083] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207085] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207086] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207087] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207088] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207090] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207091] pci_bus 0000:00: resource 15 [mem 0xe0000000-0xfeafffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207092] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207094] pci_bus 0000:02: resource 1 [mem 0xf7100000-0xf71fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207095] pci_bus 0000:03: resource 1 [mem 0xf7000000-0xf70fffff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207117] NET: Registered protocol family 2
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207267] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207388] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207498] TCP: Hash tables configured (established 65536 bind 65536)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207516] TCP: reno registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207527] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207552] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207596] NET: Registered protocol family 1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207608] pci 0000:00:02.0: Video device with shadowed ROM
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207784] PCI: CLS 64 bytes, default 64
Aug 25 23:26:15 alan-X555LAB kernel: [    0.207827] Trying to unpack rootfs image as initramfs...
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488055] Freeing initrd memory: 20140K (ffff88003589a000 - ffff880036c45000)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488094] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488098] software IO TLB [mem 0xd2875000-0xd6875000] (64MB) mapped at [ffff8800d2875000-ffff8800d6874fff]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488258] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488306] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x13
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488315] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x13
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488321] microcode: CPU2 sig=0x306d4, pf=0x40, revision=0x13
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488327] microcode: CPU3 sig=0x306d4, pf=0x40, revision=0x13
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488374] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488396] Scanning for low memory corruption every 60 seconds
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488632] futex hash table entries: 1024 (order: 4, 65536 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488648] Initialise system trusted keyring
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488667] audit: initializing netlink subsys (disabled)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488682] audit: type=2000 audit(1440545156.484:1): initialized
Aug 25 23:26:15 alan-X555LAB kernel: [    0.488929] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490039] zpool: loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490043] zbud: loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490169] VFS: Disk quotas dquot_6.5.2
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490195] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490533] fuse init (API version 7.23)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490638] Key type big_key registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490933] Key type asymmetric registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490936] Asymmetric key parser 'x509' registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490967] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.490997] io scheduler noop registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491000] io scheduler deadline registered (default)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491035] io scheduler cfq registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491535] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491540] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491553] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491555] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491559] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491571] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491573] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491576] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491582] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491597] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491633] efifb: probing for efifb
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491649] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90004f00000, using 4160k, total 4160k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491652] efifb: mode is 1366x768x32, linelength=5504, pages=1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491653] efifb: scrolling: redraw
Aug 25 23:26:15 alan-X555LAB kernel: [    0.491656] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.493769] Console: switching to colour frame buffer device 170x48
Aug 25 23:26:15 alan-X555LAB kernel: [    0.495715] fb0: EFI VGA frame buffer device
Aug 25 23:26:15 alan-X555LAB kernel: [    0.495738] intel_idle: MWAIT substates: 0x11142120
Aug 25 23:26:15 alan-X555LAB kernel: [    0.495739] intel_idle: v0.4 model 0x3D
Aug 25 23:26:15 alan-X555LAB kernel: [    0.495740] intel_idle: lapic_timer_reliable_states 0xffffffff
Aug 25 23:26:15 alan-X555LAB kernel: [    0.496013] ACPI: AC Adapter [AC0] (on-line)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.496136] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.496844] ACPI: Lid Switch [LID]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.496888] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.496919] ACPI: Sleep Button [SLPB]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.496961] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Aug 25 23:26:15 alan-X555LAB kernel: [    0.496988] ACPI: Power Button [PWRF]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.497785] thermal LNXTHERM:00: registered as thermal_zone0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.497808] ACPI: Thermal Zone [THRM] (44 C)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.498116] thermal LNXTHERM:01: registered as thermal_zone1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.498137] ACPI: Thermal Zone [TZ00] (28 C)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.498303] thermal LNXTHERM:02: registered as thermal_zone2
Aug 25 23:26:15 alan-X555LAB kernel: [    0.498324] ACPI: Thermal Zone [TZ01] (30 C)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.498390] GHES: HEST is not enabled!
Aug 25 23:26:15 alan-X555LAB kernel: [    0.498487] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.500177] Linux agpgart interface v0.103
Aug 25 23:26:15 alan-X555LAB kernel: [    0.501278] brd: module loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.501832] loop: module loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.502007] libphy: Fixed MDIO Bus: probed
Aug 25 23:26:15 alan-X555LAB kernel: [    0.502024] tun: Universal TUN/TAP device driver, 1.6
Aug 25 23:26:15 alan-X555LAB kernel: [    0.502042] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 25 23:26:15 alan-X555LAB kernel: [    0.502093] PPP generic driver version 2.4.2
Aug 25 23:26:15 alan-X555LAB kernel: [    0.502968] xhci_hcd 0000:00:14.0: xHCI Host Controller
Aug 25 23:26:15 alan-X555LAB kernel: [    0.503700] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.504501] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Aug 25 23:26:15 alan-X555LAB kernel: [    0.504561] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Aug 25 23:26:15 alan-X555LAB kernel: [    0.505302] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.506046] usb usb1: Product: xHCI Host Controller
Aug 25 23:26:15 alan-X555LAB kernel: [    0.506787] usb usb1: Manufacturer: Linux 3.19.0-26-generic xhci-hcd
Aug 25 23:26:15 alan-X555LAB kernel: [    0.507569] usb usb1: SerialNumber: 0000:00:14.0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.508395] hub 1-0:1.0: USB hub found
Aug 25 23:26:15 alan-X555LAB kernel: [    0.509117] hub 1-0:1.0: 11 ports detected
Aug 25 23:26:15 alan-X555LAB kernel: [    0.513349] xhci_hcd 0000:00:14.0: xHCI Host Controller
Aug 25 23:26:15 alan-X555LAB kernel: [    0.514044] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Aug 25 23:26:15 alan-X555LAB kernel: [    0.514768] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Aug 25 23:26:15 alan-X555LAB kernel: [    0.515499] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.516213] usb usb2: Product: xHCI Host Controller
Aug 25 23:26:15 alan-X555LAB kernel: [    0.516842] usb usb2: Manufacturer: Linux 3.19.0-26-generic xhci-hcd
Aug 25 23:26:15 alan-X555LAB kernel: [    0.517554] usb usb2: SerialNumber: 0000:00:14.0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.518372] hub 2-0:1.0: USB hub found
Aug 25 23:26:15 alan-X555LAB kernel: [    0.519105] hub 2-0:1.0: 4 ports detected
Aug 25 23:26:15 alan-X555LAB kernel: [    0.524909] ACPI: Battery Slot [BAT0] (battery present)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.526219] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.526909] ehci-pci: EHCI PCI platform driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.527588] ehci-platform: EHCI generic platform driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.528253] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.528920] ohci-pci: OHCI PCI platform driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.529583] ohci-platform: OHCI generic platform driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.530245] uhci_hcd: USB Universal Host Controller Interface driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.530973] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug 25 23:26:15 alan-X555LAB kernel: [    0.534191] i8042: Detected active multiplexing controller, rev 1.1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.535916] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.536581] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug 25 23:26:15 alan-X555LAB kernel: [    0.537239] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug 25 23:26:15 alan-X555LAB kernel: [    0.537879] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug 25 23:26:15 alan-X555LAB kernel: [    0.538501] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug 25 23:26:15 alan-X555LAB kernel: [    0.539407] mousedev: PS/2 mouse device common for all mice
Aug 25 23:26:15 alan-X555LAB kernel: [    0.540550] rtc_cmos 00:04: RTC can wake from S4
Aug 25 23:26:15 alan-X555LAB kernel: [    0.541378] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.541971] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.542541] i2c /dev entries driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.543215] device-mapper: uevent: version 1.0.3
Aug 25 23:26:15 alan-X555LAB kernel: [    0.543904] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
Aug 25 23:26:15 alan-X555LAB kernel: [    0.544466] Intel P-state driver initializing.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.545209] Consider also installing thermald for improved thermal control.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.545837] ledtrig-cpu: registered to indicate activity on CPUs
Aug 25 23:26:15 alan-X555LAB kernel: [    0.546473] EFI Variables Facility v0.08 2004-May-17
Aug 25 23:26:15 alan-X555LAB kernel: [    0.548571] Error parsing PCC subspaces from PCCT
Aug 25 23:26:15 alan-X555LAB kernel: [    0.549206] ACPI PCC probe failed.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.549903] TCP: cubic registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.550600] NET: Registered protocol family 10
Aug 25 23:26:15 alan-X555LAB kernel: [    0.551467] NET: Registered protocol family 17
Aug 25 23:26:15 alan-X555LAB kernel: [    0.552095] Key type dns_resolver registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.553107] Loading compiled-in X.509 certificates
Aug 25 23:26:15 alan-X555LAB kernel: [    0.554353] Loaded X.509 cert 'Magrathea: Glacier signing key: ed8339fd1a2f8dc0efdc5df7129dfb170a6f6dab'
Aug 25 23:26:15 alan-X555LAB kernel: [    0.555019] registered taskstats version 1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.557143] Key type trusted registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.560598] Key type encrypted registered
Aug 25 23:26:15 alan-X555LAB kernel: [    0.561269] AppArmor: AppArmor sha1 policy hashing enabled
Aug 25 23:26:15 alan-X555LAB kernel: [    0.561946] ima: No TPM chip found, activating TPM-bypass!
Aug 25 23:26:15 alan-X555LAB kernel: [    0.562636] evm: HMAC attrs: 0x1
Aug 25 23:26:15 alan-X555LAB kernel: [    0.563667]   Magic number: 11:706:454
Aug 25 23:26:15 alan-X555LAB kernel: [    0.564427] rtc_cmos 00:04: setting system clock to 2015-08-25 23:25:57 UTC (1440545157)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.565152] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 25 23:26:15 alan-X555LAB kernel: [    0.565779] EDD information not available.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.566465] PM: Hibernation image not present or could not be loaded.
Aug 25 23:26:15 alan-X555LAB kernel: [    0.566743] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.567417] Write protecting the kernel read-only data: 12288k
Aug 25 23:26:15 alan-X555LAB kernel: [    0.568386] Freeing unused kernel memory: 260K (ffff8800027bf000 - ffff880002800000)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.569173] Freeing unused kernel memory: 340K (ffff880002bab000 - ffff880002c00000)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.580080] systemd-udevd[119]: starting version 204
Aug 25 23:26:15 alan-X555LAB kernel: [    0.580531] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Aug 25 23:26:15 alan-X555LAB kernel: [    0.590678] sdhci: Secure Digital Host Controller Interface driver
Aug 25 23:26:15 alan-X555LAB kernel: [    0.591950] sdhci: Copyright(c) Pierre Ossman
Aug 25 23:26:15 alan-X555LAB kernel: [    0.604914] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug 25 23:26:15 alan-X555LAB kernel: [    0.605658] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Aug 25 23:26:15 alan-X555LAB kernel: [    0.606467] ahci 0000:00:1f.2: version 3.0
Aug 25 23:26:15 alan-X555LAB kernel: [    0.609117] psmouse: module verification failed: signature and/or  required key missing - tainting kernel
Aug 25 23:26:15 alan-X555LAB kernel: [    0.612734] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xffffc90000ca6000, 14:dd:a9:21:07:64, XID 10900800 IRQ 47
Aug 25 23:26:15 alan-X555LAB kernel: [    0.613928] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug 25 23:26:15 alan-X555LAB kernel: [    0.620795] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x3 impl SATA mode
Aug 25 23:26:15 alan-X555LAB kernel: [    0.622241] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
Aug 25 23:26:15 alan-X555LAB kernel: [    0.624613] scsi host0: ahci
Aug 25 23:26:15 alan-X555LAB kernel: [    0.626230] scsi host1: ahci
Aug 25 23:26:15 alan-X555LAB kernel: [    0.627838] scsi host2: ahci
Aug 25 23:26:15 alan-X555LAB kernel: [    0.628744] scsi host3: ahci
Aug 25 23:26:15 alan-X555LAB kernel: [    0.629586] ata1: SATA max UDMA/133 abar m2048@0xf7222000 port 0xf7222100 irq 46
Aug 25 23:26:15 alan-X555LAB kernel: [    0.630402] ata2: SATA max UDMA/133 abar m2048@0xf7222000 port 0xf7222180 irq 46
Aug 25 23:26:15 alan-X555LAB kernel: [    0.631191] ata3: DUMMY
Aug 25 23:26:15 alan-X555LAB kernel: [    0.631910] ata4: DUMMY
Aug 25 23:26:15 alan-X555LAB kernel: [    0.818245] input: PS/2 FocalTech FocalTech Touchpad as /devices/platform/i8042/serio4/input/input11
Aug 25 23:26:15 alan-X555LAB kernel: [    0.822840] usb 1-1: new high-speed USB device number 2 using xhci_hcd
Aug 25 23:26:15 alan-X555LAB kernel: [    0.950825] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.951754] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 25 23:26:15 alan-X555LAB kernel: [    0.955764] ata2.00: ATAPI: MATSHITA DVD-RAM UJ8HC, 1.00, max UDMA/100
Aug 25 23:26:15 alan-X555LAB kernel: [    0.960733] ata2.00: configured for UDMA/100
Aug 25 23:26:15 alan-X555LAB kernel: [    0.981477] ata1.00: ATA-8: ST500LT012-1DG142, 0003SDM1, max UDMA/133
Aug 25 23:26:15 alan-X555LAB kernel: [    0.982295] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 25 23:26:15 alan-X555LAB kernel: [    1.007588] usb 1-1: New USB device found, idVendor=05c6, idProduct=676a
Aug 25 23:26:15 alan-X555LAB kernel: [    1.008413] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 25 23:26:15 alan-X555LAB kernel: [    1.009258] usb 1-1: Product: A0001
Aug 25 23:26:15 alan-X555LAB kernel: [    1.009993] usb 1-1: Manufacturer: OnePlus
Aug 25 23:26:15 alan-X555LAB kernel: [    1.010726] usb 1-1: SerialNumber: e057c9a3
Aug 25 23:26:15 alan-X555LAB kernel: [    1.108895] ata1.00: configured for UDMA/133
Aug 25 23:26:15 alan-X555LAB kernel: [    1.109979] scsi 0:0:0:0: Direct-Access     ATA      ST500LT012-1DG14 SDM1 PQ: 0 ANSI: 5
Aug 25 23:26:15 alan-X555LAB kernel: [    1.111174] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Aug 25 23:26:15 alan-X555LAB kernel: [    1.111196] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 25 23:26:15 alan-X555LAB kernel: [    1.112953] sd 0:0:0:0: [sda] 4096-byte physical blocks
Aug 25 23:26:15 alan-X555LAB kernel: [    1.113753] sd 0:0:0:0: [sda] Write Protect is off
Aug 25 23:26:15 alan-X555LAB kernel: [    1.114496] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 25 23:26:15 alan-X555LAB kernel: [    1.114504] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 25 23:26:15 alan-X555LAB kernel: [    1.115854] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8HC    1.00 PQ: 0 ANSI: 5
Aug 25 23:26:15 alan-X555LAB kernel: [    1.138599] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 25 23:26:15 alan-X555LAB kernel: [    1.139538] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 25 23:26:15 alan-X555LAB kernel: [    1.140546] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug 25 23:26:15 alan-X555LAB kernel: [    1.140624] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug 25 23:26:15 alan-X555LAB kernel: [    1.178758] usb 1-5: new high-speed USB device number 3 using xhci_hcd
Aug 25 23:26:15 alan-X555LAB kernel: [    1.183235]  sda: sda1 sda2 sda3
Aug 25 23:26:15 alan-X555LAB kernel: [    1.184412] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 25 23:26:15 alan-X555LAB kernel: [    1.405848] usb 1-5: New USB device found, idVendor=04f2, idProduct=b483
Aug 25 23:26:15 alan-X555LAB kernel: [    1.406787] usb 1-5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Aug 25 23:26:15 alan-X555LAB kernel: [    1.407539] usb 1-5: Product: USB2.0 VGA UVC WebCam
Aug 25 23:26:15 alan-X555LAB kernel: [    1.486747] tsc: Refined TSC clocksource calibration: 2196.842 MHz
Aug 25 23:26:15 alan-X555LAB kernel: [    1.685826] random: lvm urandom read with 85 bits of entropy available
Aug 25 23:26:15 alan-X555LAB kernel: [    2.086502] usb 1-6: new high-speed USB device number 4 using xhci_hcd
Aug 25 23:26:15 alan-X555LAB kernel: [    2.214290] random: nonblocking pool is initialized
Aug 25 23:26:15 alan-X555LAB kernel: [    2.284496] usb 1-6: New USB device found, idVendor=0489, idProduct=e080
Aug 25 23:26:15 alan-X555LAB kernel: [    2.285374] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 25 23:26:15 alan-X555LAB kernel: [    2.286103] usb 1-6: Product: BT
Aug 25 23:26:15 alan-X555LAB kernel: [    2.286820] usb 1-6: Manufacturer: MediaTek
Aug 25 23:26:15 alan-X555LAB kernel: [    2.287488] usb 1-6: SerialNumber: 1.0
Aug 25 23:26:15 alan-X555LAB kernel: [    2.454395] usb 1-8: new high-speed USB device number 5 using xhci_hcd
Aug 25 23:26:15 alan-X555LAB kernel: [    2.486515] Switched to clocksource tsc
Aug 25 23:26:15 alan-X555LAB kernel: [    2.582684] usb 1-8: New USB device found, idVendor=0bda, idProduct=0129
Aug 25 23:26:15 alan-X555LAB kernel: [    2.583534] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 25 23:26:15 alan-X555LAB kernel: [    2.584380] usb 1-8: Product: USB2.0-CRW
Aug 25 23:26:15 alan-X555LAB kernel: [    2.585067] usb 1-8: Manufacturer: Generic
Aug 25 23:26:15 alan-X555LAB kernel: [    2.585757] usb 1-8: SerialNumber: 20100201396000000
Aug 25 23:26:15 alan-X555LAB kernel: [    2.589787] usbcore: registered new interface driver rtsx_usb
Aug 25 23:26:15 alan-X555LAB kernel: [    2.874908] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Aug 25 23:26:15 alan-X555LAB kernel: [    2.875747] EXT4-fs (dm-0): write access will be enabled during recovery
Aug 25 23:26:15 alan-X555LAB kernel: [    3.506727] EXT4-fs (dm-0): orphan cleanup on readonly fs
Aug 25 23:26:15 alan-X555LAB kernel: [    3.507560] EXT4-fs (dm-0): 5 orphan inodes deleted
Aug 25 23:26:15 alan-X555LAB kernel: [    3.508297] EXT4-fs (dm-0): recovery complete
Aug 25 23:26:15 alan-X555LAB kernel: [    3.710590] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Aug 25 23:26:15 alan-X555LAB kernel: [   14.337483] Adding 8286204k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:8286204k FS
Aug 25 23:26:15 alan-X555LAB kernel: [   14.471561] systemd-udevd[326]: starting version 204
Aug 25 23:26:15 alan-X555LAB kernel: [   14.666491] lp: driver loaded but no devices found
Aug 25 23:26:15 alan-X555LAB kernel: [   14.670755] ppdev: user-space parallel port driver
Aug 25 23:26:15 alan-X555LAB kernel: [   14.718516] wmi: Mapper loaded
Aug 25 23:26:15 alan-X555LAB kernel: [   14.728000] hidraw: raw HID events driver (C) Jiri Kosina
Aug 25 23:26:15 alan-X555LAB kernel: [   14.773080] [drm] Initialized drm 1.1.0 20060810
Aug 25 23:26:15 alan-X555LAB kernel: [   14.778821] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 25 23:26:15 alan-X555LAB kernel: [   14.800848] cfg80211: Calling CRDA to update world regulatory domain
Aug 25 23:26:15 alan-X555LAB kernel: [   14.812051] [drm] Memory usable by graphics device = 4096M
Aug 25 23:26:15 alan-X555LAB kernel: [   14.812055] checking generic (e0000000 410000) vs hw (e0000000 10000000)
Aug 25 23:26:15 alan-X555LAB kernel: [   14.812057] fb: switching to inteldrmfb from EFI VGA
Aug 25 23:26:15 alan-X555LAB kernel: [   14.812091] Console: switching to colour dummy device 80x25
Aug 25 23:26:15 alan-X555LAB kernel: [   14.812156] [drm] Replacing VGA console driver
Aug 25 23:26:15 alan-X555LAB kernel: [   14.823630] ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word = 0x0, Reg-WlanFunCtrl=0xff000402
Aug 25 23:26:15 alan-X555LAB kernel: [   14.823632] WlanFunCtrl.word = 0xffff0403
Aug 25 23:26:15 alan-X555LAB kernel: [   14.823684] MACVersion = 0x76502000
Aug 25 23:26:15 alan-X555LAB kernel: [   14.823690] <== MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0403, Reg->WlanFunCtrl=0xffff0f03!
Aug 25 23:26:15 alan-X555LAB kernel: [   14.823698] MAC_version=0x76300002
Aug 25 23:26:15 alan-X555LAB kernel: [   14.823702] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 7630, rev 0002 detected
Aug 25 23:26:15 alan-X555LAB kernel: [   14.825594] MAC: d8:5d:e2:53:2c:83
Aug 25 23:26:15 alan-X555LAB kernel: [   14.825599] MAC_version=0x76300002
Aug 25 23:26:15 alan-X555LAB kernel: [   14.825600] RFIC =0x7630
Aug 25 23:26:15 alan-X555LAB kernel: [   14.825603] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 7630 detected
Aug 25 23:26:15 alan-X555LAB kernel: [   14.825605] rt2x00dev->chip.rt = 0x7630
Aug 25 23:26:15 alan-X555LAB kernel: [   14.825606] rt2x00dev->chip.rf = 0x7630
Aug 25 23:26:15 alan-X555LAB kernel: [   14.830838] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Aug 25 23:26:15 alan-X555LAB kernel: [   14.831171] -->RTMPAllocTxRxRingMemory
Aug 25 23:26:15 alan-X555LAB kernel: [   14.831174] CTRL Ring: total 512 bytes allocated
Aug 25 23:26:15 alan-X555LAB kernel: [   14.831176] <-- RTMPAllocTxRxRingMemory, Status=0
Aug 25 23:26:15 alan-X555LAB kernel: [   14.839205] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Aug 25 23:26:15 alan-X555LAB kernel: [   14.839208] [drm] Driver supports precise vblank timestamp query.
Aug 25 23:26:15 alan-X555LAB kernel: [   14.839497] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Aug 25 23:26:15 alan-X555LAB kernel: [   14.857013] AVX2 version of gcm_enc/dec engaged.
Aug 25 23:26:15 alan-X555LAB kernel: [   14.857016] AES CTR mode by8 optimization enabled
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914053] audit: type=1400 audit(1440559571.848:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=442 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914060] audit: type=1400 audit(1440559571.848:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=442 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914065] audit: type=1400 audit(1440559571.848:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=442 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914094] audit: type=1400 audit(1440559571.848:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=439 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914102] audit: type=1400 audit(1440559571.848:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=439 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914108] audit: type=1400 audit(1440559571.848:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=439 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914533] audit: type=1400 audit(1440559571.848:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=442 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914538] audit: type=1400 audit(1440559571.848:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=442 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914592] audit: type=1400 audit(1440559571.848:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=439 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.914599] audit: type=1400 audit(1440559571.848:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=439 comm="apparmor_parser"
Aug 25 23:26:15 alan-X555LAB kernel: [   14.919817] intel_rapl: Found RAPL domain package
Aug 25 23:26:15 alan-X555LAB kernel: [   14.919820] intel_rapl: Found RAPL domain core
Aug 25 23:26:15 alan-X555LAB kernel: [   14.919822] intel_rapl: Found RAPL domain uncore
Aug 25 23:26:15 alan-X555LAB kernel: [   14.919823] intel_rapl: Found RAPL domain dram
Aug 25 23:26:15 alan-X555LAB kernel: [   14.938374] asus_wmi: ASUS WMI generic driver loaded
Aug 25 23:26:15 alan-X555LAB kernel: [   14.939384] asus_wmi: Initialization: 0x1
Aug 25 23:26:15 alan-X555LAB kernel: [   14.939408] asus_wmi: BIOS WMI version: 7.9
Aug 25 23:26:15 alan-X555LAB kernel: [   14.939431] asus_wmi: SFUN value: 0xa0077
Aug 25 23:26:15 alan-X555LAB kernel: [   14.940013] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
Aug 25 23:26:15 alan-X555LAB kernel: [   14.952299] fbcon: inteldrmfb (fb0) is primary device
Aug 25 23:26:15 alan-X555LAB kernel: [   14.958736] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Aug 25 23:26:15 alan-X555LAB kernel: [   14.962689] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input13
Aug 25 23:26:15 alan-X555LAB kernel: [   14.963290] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
Aug 25 23:26:15 alan-X555LAB kernel: [   14.966066] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Aug 25 23:26:15 alan-X555LAB kernel: [   14.972837] asus_wmi: Disabling ACPI video driver
Aug 25 23:26:15 alan-X555LAB kernel: [   14.978842] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
Aug 25 23:26:15 alan-X555LAB kernel: [   14.980289] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Aug 25 23:26:15 alan-X555LAB kernel: [   14.980291] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Aug 25 23:26:15 alan-X555LAB kernel: [   14.980292] sound hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Aug 25 23:26:15 alan-X555LAB kernel: [   14.980293] sound hdaudioC1D0:    mono: mono_out=0x0
Aug 25 23:26:15 alan-X555LAB kernel: [   14.980294] sound hdaudioC1D0:    inputs:
Aug 25 23:26:15 alan-X555LAB kernel: [   14.980296] sound hdaudioC1D0:      Mic=0x1b
Aug 25 23:26:15 alan-X555LAB kernel: [   15.007316] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
Aug 25 23:26:15 alan-X555LAB kernel: [   15.007452] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input16
Aug 25 23:26:15 alan-X555LAB kernel: [   15.205594] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input17
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303340] cfg80211: World regulatory domain updated:
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303342] cfg80211:  DFS Master region: unset
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303342] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303344] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303345] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303345] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303346] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Aug 25 23:26:15 alan-X555LAB kernel: [   15.303347] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Aug 25 23:26:15 alan-X555LAB kernel: [   16.130938] Console: switching to colour frame buffer device 170x48
Aug 25 23:26:15 alan-X555LAB kernel: [   16.133413] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Aug 25 23:26:15 alan-X555LAB kernel: [   16.133415] i915 0000:00:02.0: registered panic notifier
Aug 25 23:26:15 alan-X555LAB kernel: [   16.442173] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Aug 25 23:26:15 alan-X555LAB kernel: [   17.008793] usbcore: registered new interface driver cdc_ether
Aug 25 23:26:15 alan-X555LAB kernel: [   17.011496] rndis_host 1-1:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, 02:5c:51:06:37:63
Aug 25 23:26:15 alan-X555LAB kernel: [   17.011520] usbcore: registered new interface driver rndis_host
Aug 25 23:26:15 alan-X555LAB kernel: [   17.036742] media: Linux media interface: v0.10
Aug 25 23:26:15 alan-X555LAB kernel: [   17.041339] Linux video capture interface: v2.00
Aug 25 23:26:15 alan-X555LAB kernel: [   17.130695] uvcvideo: Found UVC 1.00 device USB2.0 VGA UVC WebCam (04f2:b483)
Aug 25 23:26:15 alan-X555LAB kernel: [   17.173627] input: USB2.0 VGA UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input18
Aug 25 23:26:15 alan-X555LAB kernel: [   17.173753] usbcore: registered new interface driver uvcvideo
Aug 25 23:26:15 alan-X555LAB kernel: [   17.173755] USB Video Class driver (1.1.1)
Aug 25 23:26:15 alan-X555LAB kernel: [   18.562719] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
Aug 25 23:26:15 alan-X555LAB kernel: [   18.583860] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
Aug 25 23:26:15 alan-X555LAB kernel: [   18.823879] init: failsafe main process (786) killed by TERM signal
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: Successfully dropped root privileges.
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: avahi-daemon 0.6.31 starting up.
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: Successfully called chroot().
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: Successfully dropped remaining capabilities.
Aug 25 23:26:16 alan-X555LAB kernel: [   19.219659] init: cups main process (882) killed by HUP signal
Aug 25 23:26:16 alan-X555LAB kernel: [   19.219666] init: cups main process ended, respawning
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: No service file found in /etc/avahi/services.
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: Network interface enumeration completed.
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: Registering HINFO record with values 'X86_64'/'LINUX'.
Aug 25 23:26:16 alan-X555LAB avahi-daemon[886]: Server startup complete. Host name is alan-X555LAB.local. Local service cookie is 76389184.
Aug 25 23:26:16 alan-X555LAB kernel: [   19.350618] Bluetooth: Core ver 2.20
Aug 25 23:26:16 alan-X555LAB kernel: [   19.350634] NET: Registered protocol family 31
Aug 25 23:26:16 alan-X555LAB kernel: [   19.350635] Bluetooth: HCI device and connection manager initialized
Aug 25 23:26:16 alan-X555LAB kernel: [   19.350638] Bluetooth: HCI socket layer initialized
Aug 25 23:26:16 alan-X555LAB kernel: [   19.350640] Bluetooth: L2CAP socket layer initialized
Aug 25 23:26:16 alan-X555LAB kernel: [   19.350645] Bluetooth: SCO socket layer initialized
Aug 25 23:26:16 alan-X555LAB kernel: [   19.353451] Bluetooth: RFCOMM TTY layer initialized
Aug 25 23:26:16 alan-X555LAB kernel: [   19.353457] Bluetooth: RFCOMM socket layer initialized
Aug 25 23:26:16 alan-X555LAB kernel: [   19.353462] Bluetooth: RFCOMM ver 1.11
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Bluetooth daemon 4.101
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Starting SDP server
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: DIS cannot start: GATT is disabled
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Failed to init deviceinfo plugin
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Failed to init proximity plugin
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Failed to init time plugin
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Failed to init alert plugin
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Failed to init thermometer plugin
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Failed to init gatt_example plugin
Aug 25 23:26:16 alan-X555LAB bluetoothd[941]: Bluetooth Management interface initialized
Aug 25 23:26:16 alan-X555LAB kernel: [   19.365142] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 25 23:26:16 alan-X555LAB kernel: [   19.365145] Bluetooth: BNEP filters: protocol multicast
Aug 25 23:26:16 alan-X555LAB kernel: [   19.365148] Bluetooth: BNEP socket layer initialized
Aug 25 23:26:16 alan-X555LAB ModemManager[858]: <info>  ModemManager (version 1.0.0) starting...
Aug 25 23:26:16 alan-X555LAB NetworkManager[971]: <info> NetworkManager (version 0.9.8.8) is starting...
Aug 25 23:26:16 alan-X555LAB NetworkManager[971]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 25 23:26:16 alan-X555LAB NetworkManager[971]: <info> WEXT support is enabled
Aug 25 23:26:16 alan-X555LAB NetworkManager[971]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 25 23:26:16 alan-X555LAB NetworkManager[971]: <info> DNS: loaded plugin dnsmasq
Aug 25 23:26:16 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Aug 25 23:26:16 alan-X555LAB anacron[1099]: Anacron 2.3 started on 2015-08-25
Aug 25 23:26:16 alan-X555LAB cron[1026]: (CRON) INFO (pidfile fd = 3)
Aug 25 23:26:16 alan-X555LAB cron[1115]: (CRON) STARTUP (fork ok)
Aug 25 23:26:16 alan-X555LAB acpid: starting up with netlink and the input layer
Aug 25 23:26:16 alan-X555LAB cron[1115]: (CRON) INFO (Running @reboot jobs)
Aug 25 23:26:16 alan-X555LAB polkitd[1073]: started daemon version 0.105 using authority implementation `local' version `0.105'
Aug 25 23:26:16 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Aug 25 23:26:16 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: init!
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: update_system_hostname
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:       interface-parser: parsing file /etc/network/interfaces
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:       interface-parser: finished parsing file /etc/network/interfaces
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPluginIfupdown: management mode: unmanaged
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/usb0, iface: usb0)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/usb0, iface: usb0): no ifupdown configuration found.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0, iface: wlan0)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: end _init.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ofono: init!
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ofono: end _init.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Loaded plugin (null): (null)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    Ifupdown: get unmanaged devices count: 0
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: (26608176) ... get_connections.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ifupdown: (26608176) ... get_connections (managed=false): return empty list.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure-2bebfa15-bc34-4253-acc5-47a13500611e ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing PB5M2 ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     read connection 'PB5M2'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure-2d6b013f-d7d6-488f-8302-0f43d48869d6 ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleGuest-9df8ba3f-faf0-4830-90e6-c7ea5d40568b ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleGuest ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure-05dc5faf-e442-42b8-909d-c53f6f0dd439 ... 
Aug 25 23:26:17 alan-X555LAB anacron[1099]: Normal exit (0 jobs run)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     read connection 'YaleSecure'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure-2a2ccf5b-b3c0-4590-a2e9-05f83a9b6cad ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing bulldog ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     read connection 'bulldog'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure-a7902ceb-68e1-497e-8058-fa1ff1908d0f ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure-cb69a0dd-f178-4145-b794-0c933b2965bc ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing 1911knight ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     read connection '1911knight'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile: parsing YaleSecure-1ec45b31-bf1c-40f1-afe4-9aeffb4973ad ... 
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: Connection failed to verify: (unknown)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    keyfile:     error: invalid or missing connection property '(null)/connection setting not found'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ofono: (26389872) ... get_connections.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    SCPlugin-Ofono: (26389872) connections count: 0
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]:    Ifupdown: get unmanaged devices count: 0
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/ieee80211/phy0/rfkill0) (driver mt7630e)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/platform/asus-nb-wmi/rfkill/rfkill1) (platform driver asus-nb-wmi)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Networking is enabled by state file
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <warn> failed to allocate link cache: (-12) Object not found
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): carrier is OFF
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): new Ethernet device (driver: 'rndis_host' ifindex: 4)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): bringing up device.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): carrier now ON (device state 20)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): preparing device.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): deactivating device (reason 'managed') [2]
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/usb0
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <warn> failed to allocate link cache: (-12) Object not found
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (eth0): carrier is OFF
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (eth0): bringing up device.
Aug 25 23:26:17 alan-X555LAB acpid: 10 rules loaded
Aug 25 23:26:17 alan-X555LAB acpid: waiting for events: event logging is off
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (eth0): preparing device.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): using nl80211 for WiFi device control
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): driver supports Access Point (AP) mode
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): new 802.11 WiFi device (driver: 'mt7630e' ifindex: 3)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): bringing up device.
Aug 25 23:26:17 alan-X555LAB kernel: [   20.783589] r8169 0000:02:00.0 eth0: link down
Aug 25 23:26:17 alan-X555LAB kernel: [   20.783627] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785087] ===>rt2x00lib_start
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785107] ==>MT76x0_WLAN_ChipOnOff(): OnOff:1 pAd->WlanFunCtrl.word = 0xffff0403, Reg-WlanFunCtrl=0xffff0103
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785108] Reset(1) WlanFunCtrl.word = 0xffff010f
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785167] Reset(2) WlanFunCtrl.word = 0xffff0103
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785217] WlanFunCtrl.word = 0xffff0103
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785269] MACVersion = 0x76502000
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785275] <== MT76x0_WLAN_ChipOnOff():  pAd->WlanFunCtrl.word = 0xffff0103, Reg->WlanFunCtrl=0xffff0103!
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785329] ASIC is ready
Aug 25 23:26:17 alan-X555LAB kernel: [   20.785334] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'MT7650E234.bin'
Aug 25 23:26:17 alan-X555LAB kernel: [   20.844521] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 112.3
Aug 25 23:26:17 alan-X555LAB kernel: [   20.844532] FW Version:16.0.151 Build:370
Aug 25 23:26:17 alan-X555LAB kernel: [   20.844533] Build Time:201404211629____
Aug 25 23:26:17 alan-X555LAB kernel: [   20.844539] ILM Length = 334408(bytes)
Aug 25 23:26:17 alan-X555LAB kernel: [   20.844540] DLM Length = 47772(bytes)
Aug 25 23:26:17 alan-X555LAB kernel: [   20.915681] rt2800pci_write_firmware: COM_REG0(0x730) = 0x1
Aug 25 23:26:17 alan-X555LAB kernel: [   20.915685] rt2800_load_firmware: COM_REG0(0x730) = 0x1
Aug 25 23:26:17 alan-X555LAB kernel: [   20.921567] ===>rt2x00lib_enable_radio
Aug 25 23:26:17 alan-X555LAB kernel: [   20.921609] ===>rt2800_enable_radio: 
Aug 25 23:26:17 alan-X555LAB kernel: [   20.921925] reg FCE_PSE_CTRL =x0
Aug 25 23:26:17 alan-X555LAB kernel: [   20.921937] rt2800_init_bbp(): Init BBP Registers MT7630
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922938] BBP version = f000f200
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922939] rt2800_init_bbp(): Init BBP Registers MT7630
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922974] rt2800_init_bbp(): Init BBP Registers MT7630 complete
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922975] ==>rt2800lib_init_queues
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922977] -->TX_RING: Base=0x0x00000000cfdc2000, Cnt=64
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922978] -->TX_RING: Base=0x0x00000000cfdc1000, Cnt=64
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922980] -->TX_RING: Base=0x0x00000000cfebb000, Cnt=64
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922981] -->TX_RING: Base=0x0x00000000cfe4c000, Cnt=64
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922982] -->RX_RING: Base=0x0x00000000362e4000, Cnt=128
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922983] AsicInitTxRxRing
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922984] -->TX_RING_CTRL: Base=0xd9087000, Cnt=32!
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922989] <===rt2800lib_init_queues
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922990] MAC d8:5d:e2:53:2c:83 
Aug 25 23:26:17 alan-X555LAB kernel: [   20.922997] rt2800_enable_radio -7630 Dual antenna mode
Aug 25 23:26:17 alan-X555LAB kernel: [   20.937495] rt2800_init_rfcsr(): Init RF Registers MT7630
Aug 25 23:26:17 alan-X555LAB kernel: [   20.937880] rt2800_init_rfcsr: B0.R22 = 0x65
Aug 25 23:26:17 alan-X555LAB kernel: [   20.937895] rt2800_init_rfcsr(): Init RF Registers MT7630 complete
Aug 25 23:26:17 alan-X555LAB kernel: [   20.958823] --> AsicCheckCommanFail2 Timeout Command = 2, CmdStatus= 0x0 
Aug 25 23:26:17 alan-X555LAB kernel: [   20.979746] --> AsicCheckCommanFail2 Timeout Command = 3, CmdStatus= 0x0 
Aug 25 23:26:17 alan-X555LAB kernel: [   20.979755] rtmp_bbp_set_rxpath(): rxpath=1, Set AGC1_R0=0x21400, agc_r0=0x21400
Aug 25 23:26:17 alan-X555LAB kernel: [   20.979758] rtmp_bbp_set_txdac(): txdac=0, Set txbe=0x0, txbe_r5=0x0
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985475] set INT_MASK_CSR = 0xdff3ff3
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985478] ==> RTMPEnableRxTx
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985481] ==>  DMAIdle, GloCfg=0x50
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985587] <== WRITE DMA offset 0x208 = 0x75
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985588] <== RTMPEnableRxTx
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985590] 0x1300 = 00064300
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985591] rt2800pci_toggle_irq(1):Check if PDMA is idle!
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985594] ==>  DMAIdle, GloCfg=0x75
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985595] rt2800pci_toggle_irq(2):Check if PDMA is idle!
Aug 25 23:26:17 alan-X555LAB kernel: [   20.985597] ==>  DMAIdle, GloCfg=0x75
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): preparing device.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (wlan0): deactivating device (reason 'managed') [2]
Aug 25 23:26:17 alan-X555LAB dbus[829]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> urfkill disappeared from the bus
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Aug 25 23:26:17 alan-X555LAB kernel: [   20.997539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Auto-activating connection 'Wired connection 1'.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) starting connection 'Wired connection 1'
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> NetworkManager state is now CONNECTING
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) started...
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) starting...
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) successful.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) complete.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) started...
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> (usb0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 25 23:26:17 alan-X555LAB dbus[829]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Aug 25 23:26:17 alan-X555LAB wpa_supplicant[1151]: Successfully initialized wpa_supplicant
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> dhclient started with pid 1154
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Beginning IP6 addrconf.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) complete.
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> ModemManager available in the bus
Aug 25 23:26:17 alan-X555LAB NetworkManager[971]: <info> wpa_supplicant started
Aug 25 23:26:17 alan-X555LAB dhclient: Internet Systems Consortium DHCP Client 4.2.4
Aug 25 23:26:17 alan-X555LAB dhclient: Copyright 2004-2012 Internet Systems Consortium.
Aug 25 23:26:17 alan-X555LAB dhclient: All rights reserved.
Aug 25 23:26:17 alan-X555LAB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 25 23:26:17 alan-X555LAB dhclient: 
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> (wlan0) supports 4 scan SSIDs
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <warn> Trying to remove a non-existant call id.
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> (wlan0): supplicant interface state: starting -> ready
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Aug 25 23:26:18 alan-X555LAB wpa_supplicant[1153]: wlan0: Reject scan trigger since one is already pending
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> (wlan0): supplicant interface state: ready -> disconnected
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> (wlan0) supports 4 scan SSIDs
Aug 25 23:26:18 alan-X555LAB wpa_supplicant[1153]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> (usb0): DHCPv4 state changed nbi -> preinit
Aug 25 23:26:18 alan-X555LAB dhclient: Listening on LPF/usb0/02:5c:51:06:37:63
Aug 25 23:26:18 alan-X555LAB dhclient: Sending on   LPF/usb0/02:5c:51:06:37:63
Aug 25 23:26:18 alan-X555LAB dhclient: Sending on   Socket/fallback
Aug 25 23:26:18 alan-X555LAB dhclient: DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 3 (xid=0x15fe0954)
Aug 25 23:26:18 alan-X555LAB dhclient: DHCPREQUEST of 192.168.42.56 on usb0 to 255.255.255.255 port 67 (xid=0x5409fe15)
Aug 25 23:26:18 alan-X555LAB dhclient: DHCPOFFER of 192.168.42.56 from 192.168.42.129
Aug 25 23:26:18 alan-X555LAB whoopsie[1093]: whoopsie 0.2.24.6 starting up.
Aug 25 23:26:18 alan-X555LAB dhclient: DHCPACK of 192.168.42.56 from 192.168.42.129
Aug 25 23:26:18 alan-X555LAB dhclient: bound to 192.168.42.56 -- renewal in 1742 seconds.
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> (usb0): DHCPv4 state changed preinit -> bound
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info>   address 192.168.42.56
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info>   prefix 24 (255.255.255.0)
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info>   gateway 192.168.42.129
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info>   hostname 'alan-X555LAB'
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info>   nameserver '192.168.42.129'
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 25 23:26:18 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) started...
Aug 25 23:26:18 alan-X555LAB avahi-daemon[886]: Joining mDNS multicast group on interface usb0.IPv4 with address 192.168.42.56.
Aug 25 23:26:18 alan-X555LAB avahi-daemon[886]: New relevant interface usb0.IPv4 for mDNS.
Aug 25 23:26:18 alan-X555LAB avahi-daemon[886]: Registering new address record for 192.168.42.56 on usb0.IPv4.
Aug 25 23:26:18 alan-X555LAB whoopsie[1093]: Using lock path: /var/lock/whoopsie/lock
Aug 25 23:26:18 alan-X555LAB ModemManager[858]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1': not supported by any plugin
Aug 25 23:26:18 alan-X555LAB ModemManager[858]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0': not supported by any plugin
Aug 25 23:26:18 alan-X555LAB ModemManager[858]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0': not supported by any plugin
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (usb0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (usb0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Aug 25 23:26:19 alan-X555LAB whoopsie[1157]: offline
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> NetworkManager state is now CONNECTED_GLOBAL
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Policy set 'Wired connection 1' (usb0) as default for IPv4 routing and DNS.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> DNS: starting dnsmasq...
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <warn> dnsmasq not available on the bus, can't update servers.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <error> [1440559579.115982] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <warn> DNS: plugin dnsmasq update failed
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Writing DNS information to /sbin/resolvconf
Aug 25 23:26:19 alan-X555LAB dnsmasq[1170]: started, version 2.68 cache disabled
Aug 25 23:26:19 alan-X555LAB dnsmasq[1170]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Aug 25 23:26:19 alan-X555LAB dnsmasq[1170]: DBus support enabled: connected to system bus
Aug 25 23:26:19 alan-X555LAB dnsmasq[1170]: warning: no upstream servers configured
Aug 25 23:26:19 alan-X555LAB avahi-daemon[886]: Joining mDNS multicast group on interface usb0.IPv6 with address fe80::5c:51ff:fe06:3763.
Aug 25 23:26:19 alan-X555LAB avahi-daemon[886]: New relevant interface usb0.IPv6 for mDNS.
Aug 25 23:26:19 alan-X555LAB avahi-daemon[886]: Registering new address record for fe80::5c:51ff:fe06:3763 on usb0.*.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) successful, device activated.
Aug 25 23:26:19 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 25 23:26:19 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <warn> dnsmasq appeared on DBus: :1.13
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Writing DNS information to /sbin/resolvconf
Aug 25 23:26:19 alan-X555LAB dnsmasq[1170]: setting upstream servers from DBus
Aug 25 23:26:19 alan-X555LAB dnsmasq[1170]: using nameserver 192.168.42.129#53
Aug 25 23:26:19 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Auto-activating connection 'YaleSecure'.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0) starting connection 'YaleSecure'
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0/wireless): access point 'YaleSecure' has security, but secrets are required.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <warn> No agents were available for this request.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> Marking connection 'YaleSecure' invalid.
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <warn> Activation (wlan0) failed for connection 'YaleSecure'
Aug 25 23:26:19 alan-X555LAB whoopsie[1157]: offline
Aug 25 23:26:19 alan-X555LAB whoopsie[1157]: online
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 25 23:26:19 alan-X555LAB NetworkManager[971]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 25 23:26:20 alan-X555LAB accounts-daemon[1334]: started daemon version 0.6.35
Aug 25 23:26:20 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.Accounts'
Aug 25 23:26:20 alan-X555LAB acpid: client connected from 1331[0:0]
Aug 25 23:26:20 alan-X555LAB acpid: 1 client rule loaded
Aug 25 23:26:20 alan-X555LAB kernel: [   23.906524] init: plymouth-upstart-bridge main process ended, respawning
Aug 25 23:26:24 alan-X555LAB kernel: [   27.635696] Non-volatile memory driver v1.3
Aug 25 23:26:25 alan-X555LAB kernel: [   28.194069] init: plymouth-stop pre-start process (1606) terminated with status 1
Aug 25 23:26:25 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Aug 25 23:26:25 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.UPower'
Aug 25 23:26:25 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Aug 25 23:26:25 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Successfully called chroot.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Successfully dropped privileges.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Successfully limited resources.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Running.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Canary thread running.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Watchdog thread running.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 1640 of process 1640 (n/a) owned by '112' high priority at nice level -11.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Supervising 1 threads of 1 processes of 1 users.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 1701 of process 1640 (n/a) owned by '112' RT at priority 5.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Supervising 2 threads of 1 processes of 1 users.
Aug 25 23:26:25 alan-X555LAB anacron[1708]: Anacron 2.3 started on 2015-08-25
Aug 25 23:26:25 alan-X555LAB anacron[1708]: Normal exit (0 jobs run)
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 1719 of process 1640 (n/a) owned by '112' RT at priority 5.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Supervising 3 threads of 1 processes of 1 users.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 1723 of process 1640 (n/a) owned by '112' RT at priority 5.
Aug 25 23:26:25 alan-X555LAB rtkit-daemon[1642]: Supervising 4 threads of 1 processes of 1 users.
Aug 25 23:26:25 alan-X555LAB ntpdate[1270]: step time server 91.189.89.199 offset -0.768926 sec
Aug 25 23:26:27 alan-X555LAB NetworkManager[971]: <info> WiFi hardware radio set enabled
Aug 25 23:26:37 alan-X555LAB NetworkManager[971]: <info> (usb0): IP6 addrconf timed out or failed.
Aug 25 23:26:37 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 25 23:26:37 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 25 23:26:37 alan-X555LAB NetworkManager[971]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 25 23:26:44 alan-X555LAB NetworkManager[971]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.29': no such name
Aug 25 23:26:45 alan-X555LAB kernel: [   49.117424] audit_printk_skb: 186 callbacks suppressed
Aug 25 23:26:45 alan-X555LAB kernel: [   49.117427] audit: type=1400 audit(1440559605.293:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1823 comm="apparmor_parser"
Aug 25 23:26:45 alan-X555LAB kernel: [   49.117433] audit: type=1400 audit(1440559605.293:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1823 comm="apparmor_parser"
Aug 25 23:26:45 alan-X555LAB kernel: [   49.117717] audit: type=1400 audit(1440559605.293:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1823 comm="apparmor_parser"
Aug 25 23:26:46 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Aug 25 23:26:46 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.systemd1'
Aug 25 23:26:46 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Aug 25 23:26:46 alan-X555LAB colord: Using config file /etc/colord.conf
Aug 25 23:26:46 alan-X555LAB colord: Using mapping database file /var/lib/colord/mapping.db
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 2098 of process 2098 (n/a) owned by '1000' high priority at nice level -11.
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Supervising 5 threads of 2 processes of 2 users.
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 2108 of process 2098 (n/a) owned by '1000' RT at priority 5.
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Supervising 6 threads of 2 processes of 2 users.
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 2112 of process 2098 (n/a) owned by '1000' RT at priority 5.
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Supervising 7 threads of 2 processes of 2 users.
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Successfully made thread 2113 of process 2098 (n/a) owned by '1000' RT at priority 5.
Aug 25 23:26:46 alan-X555LAB rtkit-daemon[1642]: Supervising 8 threads of 2 processes of 2 users.
Aug 25 23:26:46 alan-X555LAB colord: Using device database file /var/lib/colord/storage.db
Aug 25 23:26:46 alan-X555LAB colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Aug 25 23:26:46 alan-X555LAB colord: loaded plugin libcd_plugin_scanner.so
Aug 25 23:26:46 alan-X555LAB colord: loaded plugin libcd_plugin_camera.so
Aug 25 23:26:46 alan-X555LAB colord: Daemon ready for requests
Aug 25 23:26:46 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Aug 25 23:26:46 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Aug 25 23:26:46 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.locale1'
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Aug 25 23:26:46 alan-X555LAB colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Aug 25 23:26:47 alan-X555LAB colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Aug 25 23:26:47 alan-X555LAB colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Aug 25 23:26:47 alan-X555LAB colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Aug 25 23:26:47 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Aug 25 23:26:47 alan-X555LAB udisksd[2254]: udisks daemon version 2.1.3 starting
Aug 25 23:26:47 alan-X555LAB colord: Device added: xrandr-eDP1
Aug 25 23:26:47 alan-X555LAB colord: Automatic metadata add icc-1d8bf11b4e06b66774e4aa96380b1314 to xrandr-eDP1
Aug 25 23:26:47 alan-X555LAB colord: Profile added: icc-1d8bf11b4e06b66774e4aa96380b1314
Aug 25 23:26:48 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Aug 25 23:26:48 alan-X555LAB udisksd[2254]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Aug 25 23:26:49 alan-X555LAB nautilus: [N-A] Nautilus-Actions Tracker 3.2.3 initializing...
Aug 25 23:26:49 alan-X555LAB nautilus: [N-A] Nautilus-Actions Menu Extender 3.2.3 initializing...
Aug 25 23:27:15 alan-X555LAB dbus[829]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Aug 25 23:27:15 alan-X555LAB dbus[829]: [system] Successfully activated service 'org.freedesktop.hostname1'



```

---

