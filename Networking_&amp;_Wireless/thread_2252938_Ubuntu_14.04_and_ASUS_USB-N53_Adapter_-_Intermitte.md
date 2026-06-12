---
title: "Ubuntu 14.04 and ASUS USB-N53 Adapter - Intermittent freezes"
date: 2014-11-16
forum: Networking &amp; Wireless
---

### Post by prosmart on 2014-11-16
Greetings

I have a mythbuntu box that is suffering some mysterious freezes that I suspect are due to the USB WiFi dongle I have installed.

Intermittently, although video playback is working fine, the network appears to be unresponsive - can't ssh in from another machine or connect from my phone with mythmote. If I try to ssh it just hangs for up to a couple of minutes and then continues normally. Other times it works perfectly as expected.

When I look im dmesg and syslog I see this sort of thing:

DMESG:

```
[Sun Nov 16 12:56:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[Sun Nov 16 12:56:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[Sun Nov 16 12:56:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[Sun Nov 16 12:56:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[Sun Nov 16 12:58:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[Sun Nov 16 12:58:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[Sun Nov 16 12:58:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[Sun Nov 16 12:58:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[Sun Nov 16 13:04:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[Sun Nov 16 13:04:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[Sun Nov 16 13:04:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[Sun Nov 16 13:04:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[Sun Nov 16 13:04:35 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[Sun Nov 16 14:42:44 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[Sun Nov 16 14:42:44 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[Sun Nov 16 14:42:44 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[Sun Nov 16 14:42:44 2014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
```

SYSLOG:
```
Nov 16 13:40:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 13:41:26 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 13:42:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 13:50:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 13:51:27 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 13:52:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 14:00:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 14:01:27 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 14:02:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 14:09:01 mythtv CRON[8064]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Nov 16 14:10:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 14:11:27 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 14:12:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 14:16:46 mythtv avahi-daemon[913]: Withdrawing address record for fd32:dfce:ffde:0:f66d:4ff:fe5e:58d4 on wlan0.
Nov 16 14:17:01 mythtv CRON[8085]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 16 14:20:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 14:21:27 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 14:22:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 14:17:33 mythtv mythbackend: message repeated 2 times: [ mythbackend[1964]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min]
Nov 16 14:30:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 14:31:26 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 14:32:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 14:36:01 mythtv CRON[8117]: (dna) CMD (nice /usr/bin/mythfilldatabase > /dev/null)
Nov 16 14:39:01 mythtv CRON[8179]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Nov 16 14:40:22 mythtv kernel: [97445.714453] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
Nov 16 14:40:22 mythtv kernel: [97445.714500] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
Nov 16 14:40:22 mythtv kernel: [97445.714505] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
Nov 16 14:40:22 mythtv kernel: [97445.714543] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
Nov 16 14:40:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 14:41:26 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 14:42:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 14:46:25 mythtv avahi-daemon[913]: Registering new address record for fd32:dfce:ffde:0:f66d:4ff:fe5e:58d4 on wlan0.*.
Nov 16 14:50:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 14:51:26 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 16 14:52:10 mythtv wpa_supplicant[1229]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 16 15:00:10 mythtv wpa_supplicant[1229]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 16 15:01:27 mythtv wpa_supplicant[1229]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
```

Here is the output from wireless_script

```


########## wireless info START ##########


Report from: 16 Nov 2014 15:29 AEST +1000


Booted last: 15 Nov 2014 11:38 AEST +1000


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xfce (from ~/.dmrc)


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0b05:179d ASUSTek Computer, Inc. USB-N53 802.11abgn Network Adapter [Ralink RT3572]
Bus 003 Device 002: ID 1415:0003 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


./wireless_script: line 176: rfkill: command not found


##### lsmod #############################


rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              630653  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib


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
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fd32:dfce:ffde:0:887e:dbe2:766a:c25a/64 Scope:Global
          inet6 addr: fd32:dfce:ffde::178/128 Scope:Global
          inet6 addr: fe80::f66d:4ff:fe5e:58d4/64 Scope:Link
          inet6 addr: fd32:dfce:ffde:0:f66d:4ff:fe5e:58d4/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:161493137 (161.4 MB)  TX bytes:9364917 (9.3 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"OpenWrt"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'OpenWrt' [AC1]>   
          Bit Rate:78 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:576  Invalid misc:244   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


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


  Wired Properties
    Carrier:         off


- Device: wlan0  [OpenWrt] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           78 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    OpenWrt:         Infra, <MAC 'OpenWrt' [AC3]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 61 WPA2
    BigPond25E10D:   Infra, <MAC 'BigPond25E10D' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    *OpenWrt:        Infra, <MAC 'OpenWrt' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2
    NetComm Wireless:Infra, <MAC 'NetComm Wireless' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


  IPv6 Settings:
    Address:         fd32:dfce:ffde::178
    Prefix:          128
    Gateway:         ::


    Address:         fd32:dfce:ffde:0:887e:dbe2:766a:c25a
    Prefix:          64
    Gateway:         ::


    Address:         fd32:dfce:ffde:0:f66d:4ff:fe5e:58d4
    Prefix:          64
    Gateway:         ::


    Address:         fe80::f66d:4ff:fe5e:58d4
    Prefix:          64
    Gateway:         ::


    DNS:             fd32:dfce:ffde::1


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


[[/etc/NetworkManager/system-connections/OpenWrt]] (600 root)
[connection] id=OpenWrt | type=802-11-wireless
[802-11-wireless] ssid=OpenWrt | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Australia/Brisbane (based on set time zone)


country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 110 : 5.55 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 118 : 5.59 GHz
          Channel 132 : 5.66 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'OpenWrt' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"OpenWrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ed53023c1c
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BigPond25E10D' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"BigPond25E10D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000394c98f0186
                    Extra: Last beacon: 5092ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'OpenWrt' [AC3]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"OpenWrt"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000eefb53ce3a
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     98B048D64D7288E7C870495
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1C7B3D09AA920FB776204BA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[rt2800lib]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7A7EEDE3C2270AE56EB54F8
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E9BB2D2E4429AB671216A29
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[68603.182600] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0 (repeated 2 times)
[68603.182676] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[68603.182698] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[70439.569580] wlan0: authenticate with <MAC 'OpenWrt' [AC3]>
[70439.602134] wlan0: send auth to <MAC 'OpenWrt' [AC3]> (try 1/3)
[70439.603184] wlan0: authenticated
[70439.605406] wlan0: associate with <MAC 'OpenWrt' [AC3]> (try 1/3)
[70439.606664] wlan0: RX AssocResp from <MAC 'OpenWrt' [AC3]> (capab=0x11 status=0 aid=2)
[70439.610970] wlan0: associated
[75574.334046] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2 (repeated 3 times)
[75574.334071] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[76054.285839] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0 (repeated 3 times)
[76054.285936] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[79178.901346] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0 (repeated 3 times)
[79178.901462] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[79299.074960] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0 (repeated 3 times)
[79299.075049] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[83024.573694] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0 (repeated 3 times)
[83024.573738] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[84226.342685] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0 (repeated 3 times)
[84226.342771] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[84226.342798] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[89064.378738] wlan0: authenticate with <MAC 'OpenWrt' [AC1]>
[89064.408904] wlan0: send auth to <MAC 'OpenWrt' [AC1]> (try 1/3)
[89064.410677] wlan0: authenticated
[89064.412180] wlan0: associate with <MAC 'OpenWrt' [AC1]> (try 1/3)
[89064.415592] wlan0: RX AssocResp from <MAC 'OpenWrt' [AC1]> (capab=0x431 status=0 aid=1)
[89064.419773] wlan0: associated
[91076.322227] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0 (repeated 3 times)
[91076.322318] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[91196.499627] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0 (repeated 3 times)
[91196.499654] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[91556.586237] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0 (repeated 3 times)
[91556.586274] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[91556.586286] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[97445.714453] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0 (repeated 3 times)
[97445.714543] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[100329.968865] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0 (repeated 3 times)
[100329.968954] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0


########## wireless info END ############



```

Could anyone suggest a good place to start troubleshooting? I'm not an authority on wifi to say the least.

TIA

Nigel

---

### Post by chili555 on 2014-11-16
Sadly, this is apparently the subject of a long standing bug: [http://unix.stackexchange.com/questions/77998/what-is-tx-status-timeout-and-do-i-have-to-worry-about-it](http://unix.stackexchange.com/questions/77998/what-is-tx-status-timeout-and-do-i-have-to-worry-about-it) Even more sadly, the driver in question, rt2800usb hasn't been updated in some time. We seem to be stuck on version 2.3.0. Installing backports-3.18-rc1, or whatever the newest is, is unlikely to change much.

There is a driver parameter we can try. Please open a terminal and do:```
sudo -i
echo "options rt2800usb nohwcrypt=Y"  >  /etc/modprobe.d/rt2800usb.conf
exit
```Reboot.

Any improvement?

---

### Post by prosmart on 2014-11-16
> **chili555 said:**
> Sadly, this is apparently the subject of a long standing bug: [http://unix.stackexchange.com/questions/77998/what-is-tx-status-timeout-and-do-i-have-to-worry-about-it](http://unix.stackexchange.com/questions/77998/what-is-tx-status-timeout-and-do-i-have-to-worry-about-it) Even more sadly, the driver in question, rt2800usb hasn't been updated in some time. We seem to be stuck on version 2.3.0. Installing backports-3.18-rc1, or whatever the newest is, is unlikely to change much.

There is a driver parameter we can try. Please open a terminal and do:```
sudo -i
echo "options rt2800usb nohwcrypt=Y"  >  /etc/modprobe.d/rt2800usb.conf
exit
```Reboot.

Any improvement?


Thanks for the suggestion.

Have set the option but have to dash off to work. Will reboot now and check this evening.

Much appreciated.

N/

---

### Post by prosmart on 2014-11-17
<sigh>

Still the same I'm afraid

Found these when I got home this afternoon. I was ssh'ed in and typing when nothing happened. Twice.

```

Nov 17 17:09:53 mythtv wpa_supplicant[1214]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 17 17:11:27 mythtv wpa_supplicant[1214]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:43 [GTK=CCMP]
Nov 17 17:11:53 mythtv wpa_supplicant[1214]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 17 17:14:04 mythtv kernel: [36877.761871] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
Nov 17 17:14:04 mythtv kernel: [36877.761893] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
Nov 17 17:14:04 mythtv kernel: [36877.761897] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
Nov 17 17:17:01 mythtv CRON[4486]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 17 17:19:53 mythtv wpa_supplicant[1214]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 17 17:21:17 mythtv wpa_supplicant[1214]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c0:4a:00:e4:74:43 reason=4 locally_generated=1
Nov 17 17:21:17 mythtv NetworkManager[899]: <warn> Connection disconnected (reason -4)
Nov 17 17:21:17 mythtv kernel: [37311.973684] cfg80211: Calling CRDA to update world regulatory domain
Nov 17 17:21:17 mythtv NetworkManager[899]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 17 17:21:17 mythtv kernel: [37311.979682] cfg80211: World regulatory domain updated:
Nov 17 17:21:17 mythtv kernel: [37311.979692] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 17 17:21:17 mythtv kernel: [37311.979699] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:17 mythtv kernel: [37311.979706] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:17 mythtv kernel: [37311.979712] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:17 mythtv kernel: [37311.979718] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:17 mythtv kernel: [37311.979724] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:17 mythtv wpa_supplicant[1214]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 17 17:21:17 mythtv NetworkManager[899]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 17 17:21:18 mythtv wpa_supplicant[1214]: wlan0: SME: Trying to authenticate with c0:4a:00:e4:74:44 (SSID='OpenWrt' freq=5180 MHz)
Nov 17 17:21:18 mythtv kernel: [37312.194277] wlan0: authenticate with c0:4a:00:e4:74:44
Nov 17 17:21:18 mythtv NetworkManager[899]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 17 17:21:18 mythtv kernel: [37312.226663] wlan0: direct probe to c0:4a:00:e4:74:44 (try 1/3)
Nov 17 17:21:18 mythtv wpa_supplicant[1214]: wlan0: Trying to associate with c0:4a:00:e4:74:44 (SSID='OpenWrt' freq=5180 MHz)
Nov 17 17:21:18 mythtv kernel: [37312.430183] wlan0: send auth to c0:4a:00:e4:74:44 (try 2/3)
Nov 17 17:21:18 mythtv kernel: [37312.431289] wlan0: authenticated
Nov 17 17:21:18 mythtv kernel: [37312.434205] wlan0: associate with c0:4a:00:e4:74:44 (try 1/3)
Nov 17 17:21:18 mythtv NetworkManager[899]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 17 17:21:18 mythtv kernel: [37312.435559] wlan0: RX AssocResp from c0:4a:00:e4:74:44 (capab=0x11 status=0 aid=2)
Nov 17 17:21:18 mythtv wpa_supplicant[1214]: wlan0: Associated with c0:4a:00:e4:74:44
Nov 17 17:21:18 mythtv kernel: [37312.440744] wlan0: associated
Nov 17 17:21:18 mythtv kernel: [37312.440874] cfg80211: Calling CRDA for country: US
Nov 17 17:21:18 mythtv wpa_supplicant[1214]: wlan0: WPA: Key negotiation completed with c0:4a:00:e4:74:44 [PTK=CCMP GTK=CCMP]
Nov 17 17:21:18 mythtv wpa_supplicant[1214]: wlan0: CTRL-EVENT-CONNECTED - Connection to c0:4a:00:e4:74:44 completed [id=0 id_str=]
Nov 17 17:21:18 mythtv NetworkManager[899]: <info> (wlan0): supplicant interface state: associating -> completed
Nov 17 17:21:18 mythtv NetworkManager[899]: <info> (wlan0): roamed from BSSID C0:4A:00:E4:74:43 (OpenWrt) to C0:4A:00:E4:74:44 (OpenWrt)
Nov 17 17:21:18 mythtv kernel: [37312.446553] cfg80211: Regulatory domain changed to country: US
Nov 17 17:21:18 mythtv kernel: [37312.446561] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 17 17:21:18 mythtv kernel: [37312.446566] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov 17 17:21:18 mythtv kernel: [37312.446570] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov 17 17:21:18 mythtv kernel: [37312.446573] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:18 mythtv kernel: [37312.446576] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:18 mythtv kernel: [37312.446579] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 17 17:21:18 mythtv kernel: [37312.446582] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov 17 17:21:18 mythtv kernel: [37312.446585] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Nov 17 17:21:53 mythtv wpa_supplicant[1214]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 17 17:22:53 mythtv wpa_supplicant[1214]: wlan0: WPA: Group rekeying completed with c0:4a:00:e4:74:44 [GTK=CCMP]
Nov 17 17:23:53 mythtv wpa_supplicant[1214]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 17 17:26:49 mythtv mythfrontend.real: message repeated 2 times: [ mythfrontend[2085]: N CoreContext mythmainwindow.cpp:2638 (PauseIdleTimer) Suspending idle timer]
Nov 17 17:30:04 mythtv kernel: [37839.663740] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
Nov 17 17:30:04 mythtv kernel: [37839.663761] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
Nov 17 17:30:04 mythtv kernel: [37839.663769] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2

```

I think this may have to go on the too-hard pile as much as it sh*ts me to do that.

If I give up, I'd appreciate a heads up for a USB NIC that will work. Well. Out of the box.

Cheers

N/

---

