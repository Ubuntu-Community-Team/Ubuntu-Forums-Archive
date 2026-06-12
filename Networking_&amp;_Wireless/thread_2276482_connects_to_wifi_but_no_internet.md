---
title: "connects to wifi but no internet"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by vbdanl-yahoo on 2015-05-02
hi. i started with dell usb wireless adapter and trendnet wireless router.
kept having to reboot router and cox modem.  replaced router with tp-link.
dell usb would connect to wifi, but not internet.
bought new d-link 140 usb wireless adapter, and now have different router..
still can connect to wifi, but can't use internet or ping websites from terminal via ubuntu.
i can use internet with ms vista, and can also connect to internet when booting from ubuntu live cd.
have read countless posts, but no idea where to start, other than i have the wireless info.txt
one other weird thing.. i thought i used to have wlan0 instead of wlan1.  not sure if this is root of problem.
would prefer it be wlan0 if that is easy to do..
thanks for your help !!

```

########## wireless info START ##########

Report from: 02 May 2015 12:41 CDT -0500

Booted last: 02 May 2015 05:26 CDT -0500

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:14:51 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1094] (rev 01)
    Subsystem: Gateway, Inc. Device [107b:7201]
    Kernel driver in use: e100

##### lsusb #############################

Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 005: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT3072]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              546067  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  2 mac80211,rt2x00lib
crc_ccitt              12627  1 rt2800lib

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

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:30a:c0d0:f7e0::36/128 Scope:Global
          inet6 addr: 2602:30a:c0d0:f7e0:7189:8043:9071:4cbf/64 Scope:Global
          inet6 addr: fe80::7262:b8ff:fe2b:690d/64 Scope:Link
          inet6 addr: 2602:30a:c0d0:f7e0:7262:b8ff:fe2b:690d/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22694591 (22.6 MB)  TX bytes:56986 (56.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"ATT7n9Z9G5"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ATT7n9Z9G5' [AC1]>   
          Bit Rate=115.6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:33  Invalid misc:269   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 192.168.0.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1  [ATT7n9Z9G5] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           115 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    D2DC65:          Infra, <MAC 'D2DC65' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    2WIRE469:        Infra, <MAC '2WIRE469' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *ATT7n9Z9G5:     Infra, <MAC 'ATT7n9Z9G5' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    54dfa6:          Infra, <MAC '54dfa6' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    D0D8F2:          Infra, <MAC 'D0D8F2' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    D03B10:          Infra, <MAC 'D03B10' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    print server 5E0A98: Ad-Hoc, <MAC 'print server 5E0A98' [AC7]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 15
    2WIRE676:        Infra, <MAC '2WIRE676' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.79
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

  IPv6 Settings:
    Address:         2602:30a:c0d0:f7e0::36
    Prefix:          128
    Gateway:         fe80::ea33:81ff:feb3:a4e0

    Address:         2602:30a:c0d0:f7e0:7189:8043:9071:4cbf
    Prefix:          64
    Gateway:         fe80::ea33:81ff:feb3:a4e0

    Address:         2602:30a:c0d0:f7e0:7262:b8ff:fe2b:690d
    Prefix:          64
    Gateway:         fe80::ea33:81ff:feb3:a4e0

    Address:         fe80::7262:b8ff:fe2b:690d
    Prefix:          64
    Gateway:         fe80::ea33:81ff:feb3:a4e0

    Address:         2602:30a:c0d0:f7e0::36
    Prefix:          128
    Gateway:         ::

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
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

[[/etc/NetworkManager/system-connections/ATT7n9Z9G5]] (600 root)
[connection] id=ATT7n9Z9G5 | type=802-11-wireless
[802-11-wireless] ssid=ATT7n9Z9G5 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan1     14 channels in total; available frequencies :
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
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.462 GHz (Channel 11)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'ATT7n9Z9G5' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"ATT7n9Z9G5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e07181239
                    Extra: Last beacon: 204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'D2DC65' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"D2DC65"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002537fbfec6b
                    Extra: Last beacon: 540ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '2WIRE469' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"2WIRE469"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bdd7830181
                    Extra: Last beacon: 1216ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '2WIRE676' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"2WIRE676"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000076b339b181
                    Extra: Last beacon: 2960ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '\00\00\00\00\00\00\00' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025380e08183
                    Extra: Last beacon: 1904ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '2WIRE750' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"2WIRE750"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000058557de8181
                    Extra: Last beacon: 2340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'print server 5E0A98' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"print server 5E0A98"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000002538028257b
                    Extra: Last beacon: 1148ms ago
          Cell 08 - Address: <MAC '54dfa6' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"54dfa6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000158f9de196
                    Extra: Last beacon: 1132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'D0D8F2' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"D0D8F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024e31902d12
                    Extra: Last beacon: 1100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'WLCSSID' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"WLCSSID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001081f0eb18b
                    Extra: Last beacon: 164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     81F4CDE501CE72D2443EE38
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     3AF2621F166C8604D7D8AA5
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

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
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:04:08.0 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x413c:0x8104 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   31.412878] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   31.555886] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   31.843108] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[  120.865239] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3071, rev 021c detected
[  120.894484] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0008 detected
[  121.004623] systemd-udevd[2299]: renamed network interface wlan0 to wlan1
[  121.008637] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  121.008708] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  121.351117] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[  174.781764] wlan1: authenticate with <MAC 'ATT7n9Z9G5' [AC1]>
[  174.839369] wlan1: send auth to <MAC 'ATT7n9Z9G5' [AC1]> (try 1/3)
[  174.843093] wlan1: authenticated
[  174.844043] wlan1: associate with <MAC 'ATT7n9Z9G5' [AC1]> (try 1/3)
[  174.847118] wlan1: RX AssocResp from <MAC 'ATT7n9Z9G5' [AC1]> (capab=0x411 status=0 aid=2)
[  174.857974] wlan1: associated
[  174.858073] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

########## wireless info END ############


```

---

### Post by vbdanl-yahoo on 2015-05-03
i ran the wireless-info script on a laptop that is working and compared the output to the one that does not work.
the laptop has broadcom instead of dlink wireless, so those differences were expected.
main differences i am seeing are:

module parms:
nohwcrypt:N  vs :0 in the laptop

resolv.conf
nameserver 192.168.0.1  in desktop that does not work
nameserver 127.0.1.1 in laptop, plus "search attlocal.net" on next line in laptop

udev rules:
desktop has 2 entries while laptop only has one for wlan0

am thinking of making a backup of 70-persistent-net.rules file, and trying to make just one entry in it for wlan0

would appreciate any advice from those that know.. thanks.

---

### Post by vbdanl-yahoo on 2015-05-03
not really sure how 192.168.0.1 got in the resolv.conf, or what should really be in there..
Updated the 70* file in the last post, so now it uses wlan0 instead of wlan1.
Changed it to match the laptop, and now can get to the internet.
seems a little slow, but at least it works.

---

