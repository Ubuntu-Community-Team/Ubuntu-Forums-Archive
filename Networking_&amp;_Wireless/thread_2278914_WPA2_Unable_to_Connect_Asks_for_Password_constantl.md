---
title: "WPA2 Unable to Connect: Asks for Password constantly, Intel, Ubuntu 14.04"
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by FAJALOU on 2015-05-19
Hello.

I am down in Mexico for work, and I am having major difficulties connecting to my residence's wifi network.
I am able to connect via Ethernet, and my phone (Android) and other devices in the residence (Macs) are able to connect.

Things I have tried:
WICD (Fails with "WPA-CLI INTERFACE IS DISABLED)

Following these:
[http://www.linux.org/threads/cannot-connect-to-wifi-at-home-after-upgrade-to-ubuntu-14-04.5873/](http://www.linux.org/threads/cannot-connect-to-wifi-at-home-after-upgrade-to-ubuntu-14-04.5873/)
     (No line found in /etc/NetworkManager/system-connections/INFINITUM869696F)
Adding lines to /etc/Networking/Interfaces as shown here:
     [http://linuxconfig.org/setup-wireless-interface-with-wpa-and-wpa2-on-ubuntu](http://linuxconfig.org/setup-wireless-interface-with-wpa-and-wpa2-on-ubuntu)

I am attempting to connect to:     
```
 INFINITUM89696F: Infra, <MAC 'INFINITUM89696F' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
```

I believe wpa-supplicant is installed and running:
```
~$ ps ax | grep wpa
 1166 ?        Ss     0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
 3407 pts/0    S+     0:00 grep --color=auto wpa

```

I am certain I have the correct passcode, but I believe this might be a problem with PSKs... Any help that can be given would be greatly appreciated, since I'm at this residence for nearly two months!

~~~
/etc/NetworkManager/system-connections/INFINITUM89696F (with password redacted)
```
[connection]
id=INFINITUM89696F
uuid=f3ca0da4-1ae4-4b40-b80a-b1b539eb02b1
type=802-11-wireless

[802-11-wireless]
ssid=INFINITUM89696F
mode=infrastructure
mac-address=00:26:C7:1C:3B:B0
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=xxxxxxxxx

[ipv4]
method=auto

[ipv6]
method=auto

```
~~~~~~
./wireless-info.txt
```

########## wireless info START ##########

Report from: 19 May 2015 18:00 PDT -0700

Booted last: 19 May 2015 17:57 PDT -0700

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-52-generic #86-Ubuntu SMP Mon May 4 04:32:15 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
	Kernel driver in use: iwlwifi

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Lenovo Device [17aa:2131]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 17ef:4811 Lenovo Integrated Webcam [R5U877]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05c6:9201 Qualcomm, Inc. Gobi Wireless Modem (QDL mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 050d:016a Belkin Components Bluetooth Mini Dongle
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_wwan_sw: Wireless WAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwldvm                214950  0 
mac80211              546067  1 iwldvm
iwlwifi               152049  1 iwldvm
cfg80211              409394  3 iwlwifi,mac80211,iwldvm
wmi                    18673  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fe1b:6748/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:743359 (743.3 KB)  TX bytes:298756 (298.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.1.134
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    INFINITUM89696F: Infra, <MAC 'INFINITUM89696F' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    MAXCOM_C030:     Infra, <MAC 'MAXCOM_C030' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    INFINITUMCDD2BE: Infra, <MAC 'INFINITUMCDD2BE' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    ZyXEL:           Infra, <MAC 'ZyXEL' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    MAXCOM_249A:     Infra, <MAC 'MAXCOM_249A' [AC4]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 50 WPA2
    ZTE_AKYmgp:      Infra, <MAC 'ZTE_AKYmgp' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    MAXCOM_B747:     Infra, <MAC 'MAXCOM_B747' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    2WIRE524:        Infra, <MAC '2WIRE524' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP
    REDSCF:          Infra, <MAC 'REDSCF' [AN9]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WEP
    INFINITUMudja:   Infra, <MAC 'INFINITUMudja' [AC7]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2

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

[[/etc/NetworkManager/system-connections/MU_Wireless]] (600 root)
[connection] id=MU_Wireless | type=802-11-wireless
[802-11-wireless] ssid=MU_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/bookcellar_guest]] (600 root)
[connection] id=bookcellar_guest | type=802-11-wireless
[802-11-wireless] ssid=bookcellar_guest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/INFINITUM89696F]] (600 root)
[connection] id=INFINITUM89696F | type=802-11-wireless
[802-11-wireless] ssid=INFINITUM89696F | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Prairie Bread Kitchen]] (600 root)
[connection] id=Prairie Bread Kitchen | type=802-11-wireless
[802-11-wireless] ssid=Prairie Bread Kitchen | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Cignot-guest]] (600 root)
[connection] id=Cignot-guest | type=802-11-wireless
[802-11-wireless] ssid=Cignot-guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Rectory]] (600 root)
[connection] id=Rectory | type=802-11-wireless
[802-11-wireless] ssid=Rectory | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Mickey Finns]] (600 root)
[connection] id=Mickey Finns | type=802-11-wireless
[802-11-wireless] ssid=Mickey Finns | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HOME-CBC2]] (600 root)
[connection] id=HOME-CBC2 | type=802-11-wireless
[802-11-wireless] ssid=HOME-CBC2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/redroof]] (600 root)
[connection] id=redroof | type=802-11-wireless
[802-11-wireless] ssid=redroof | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Marytown-Guest]] (600 root)
[connection] id=Marytown-Guest | type=802-11-wireless
[802-11-wireless] ssid=Marytown-Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/USML-GUEST]] (600 root)
[connection] id=USML-GUEST | type=802-11-wireless
[802-11-wireless] ssid=USML-GUEST | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CCHS-Guest]] (600 root)
[connection] id=CCHS-Guest | type=802-11-wireless
[802-11-wireless] ssid=CCHS-Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HansaFamily2]] (600 root)
[connection] id=HansaFamily2 | type=802-11-wireless
[802-11-wireless] ssid=HansaFamily2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hansa Family]] (600 root)
[connection] id=Hansa Family | type=802-11-wireless
[802-11-wireless] ssid=Hansa Family | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HowardJohnson]] (600 root)
[connection] id=HowardJohnson | type=802-11-wireless
[802-11-wireless] ssid=HowardJohnson | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/colectivo]] (600 root)
[connection] id=colectivo | type=802-11-wireless
[802-11-wireless] ssid=colectivo | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

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

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'INFINITUM89696F' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"INFINITUM89696F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bc930d19ba
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'INFINITUMCDD2BE' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"INFINITUMCDD2BE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d86ca852e7
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ZTE_AKYmgp' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ZTE_AKYmgp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a437eddc09
                    Extra: Last beacon: 364ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MAXCOM_249A' [AC4]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"MAXCOM_249A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d7814f7ca0
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'MAXCOM_C030' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"MAXCOM_C030"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bc97da452d
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'MAXCOM_B747' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MAXCOM_B747"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006b22eed4da
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'INFINITUMudja' [AC7]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"INFINITUMudja"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000196af66c1c1
                    Extra: Last beacon: 8900ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'ZyXEL' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bcb2201432
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '2WIRE524' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"2WIRE524"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000308cb6181
                    Extra: Last beacon: 352ms ago

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     496F157C6045EF8314B48BC
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E1:7C:1A:20:0E:70:82:2E:A7:1B:75:F9:A6:8F:D2:E2:5D:B8:9A:5A
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-52-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E1:7C:1A:20:0E:70:82:2E:A7:1B:75:F9:A6:8F:D2:E2:5D:B8:9A:5A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     A45BAACCAD263355629DB7A
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E1:7C:1A:20:0E:70:82:2E:A7:1B:75:F9:A6:8F:D2:E2:5D:B8:9A:5A
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
filename:       /lib/modules/3.13.0-52-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E1:7C:1A:20:0E:70:82:2E:A7:1B:75:F9:A6:8F:D2:E2:5D:B8:9A:5A
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0084 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.311137] iwlwifi 0000:05:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   15.720346] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   15.720348] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   15.720349] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   15.720351] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   15.720417] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.808628] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   25.892337] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   25.899745] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[   25.937030] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   25.944531] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[   25.984199] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############
```

Attached: wireless-info.tar.gz

---

