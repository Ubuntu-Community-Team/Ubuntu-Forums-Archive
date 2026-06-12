---
title: "WiFi connects with 14.04.4 but not 16.04"
date: 2016-05-21
forum: Networking &amp; Wireless
---

### Post by moot2 on 2016-05-21
16.04 is a clean/new install on:
IBM ThinkPad T30, Memory: 1000.3 MiB, Processor: Mobile Intel®  Pentium(R) 4 - M CPU 1.80GHz, Graphics: R100 (RV200 4C57) x86/MMX/SSE2  DRI2, OS type: 32-bit, Wi-Fi Intel Model: M3AWEB56GA 802.11b.

I did the install without Ethernet and selected not to start Wi-Fi.  The installation succeeded and I was able to boot from HDD to desktop. I  still left the cable out and when I went to connect to my Wi-Fi there  were duplicate wi-fi networks (Intersil ISL3874 [Prism 2.5] / ISL3872  [Prism3] (wireless 802.11b MiniPCI Adapter))
I saw my SSID and when I clicked I got the Authentication dialogue - but it would not connect.
I booted off the install dvd and selected the 'try' option - same thing, duplicate, no connect.

Running the desktop from 14.04.4 I am connected  wireless, interface 802.11 WiFi(wlan0), Security WEP 40/128-bit Key(Hex  or ASCII), Mode: Infrastructure, Authentication: Open System

What I would like to do, and hopefully someone can help...
First remove duplicate WiFi Networks from 16.04 and install the proper  drivers for this adapter, i.e., the same one 14.04.4 is using now... or  better...
Also, the adapter is wireless and modem... which could explain duplicate entry...?


wireless-info from 14.04.4 - connected
```

########## wireless info START ##########

Report from: 20 May 2016 07:09 EDT -0400

Booted last: 19 May 2016 15:35 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:27 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:02.0 Network controller [0280]: Intersil Corporation ISL3874 [Prism 2.5]/ISL3872 [Prism 3] [1260:3873] (rev 01)
    Subsystem: Intel Corporation Wireless 802.11b MiniPCI Adapter [8086:2513]
    Kernel driver in use: hostap_pci

02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
    Subsystem: IBM ThinkPad A/T/X Series [1014:0209]
    Kernel driver in use: e100

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e8d:1836 MediaTek Inc. Samsung SE-S084 Super WriteMaster Slim External DVD writer
Bus 002 Device 003: ID 0781:5575 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

##### lsmod #############################

cfg80211              471040  0 

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

irda0     Link encap:IrLAP  HWaddr <MAC 'irda0' [IF]>  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr <MAC 'wifi0' [IF]>  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:162 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.85  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:30c9:6070:<IP6 'wlan0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: 2602:306:30c9:6070:3556:62aa:6239:a28b/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:711743 errors:0 dropped:3 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212943895 (212.9 MB)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe000 

##### iwconfig ##########################

irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"mywifinet"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'mywifinet' [AC2]>   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-52 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:300  Rx invalid frag:2
          Tx excessive retries:176  Invalid misc:7377   Missed beacon:0

wifi0     IEEE 802.11b  ESSID:"mywifinet"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'mywifinet' [AC2]>   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       813     1  0 May19 ?        00:00:11 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

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

- Device: wlan0  [mywifinet] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            hostap_pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *mywifinet:      Infra, <MAC 'mywifinet' [AC2]>, Freq 2457 MHz, Rate 22 Mb/s, Strength 54 WEP
    otherwifi:      Infra, <MAC 'otherwifi' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP

  IPv4 Settings:
    Address:         192.168.1.85
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

  IPv6 Settings:
    Address:         2602:306:30c9:6070:3556:62aa:6239:a28b
    Prefix:          64
    Gateway:         fe80::2a16:2eff:fe9f:4749

    Address:         2602:306:30c9:6070:<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         fe80::2a16:2eff:fe9f:4749

    Address:         fe80::<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         fe80::2a16:2eff:fe9f:4749

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/mywifinet]] (600 root)
[connection] id=mywifinet | type=802-11-wireless
[802-11-wireless] ssid=mywifinet | mac-address=<MAC 'wlan0' [IF]>
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

irda0     no frequency information.

lo        no frequency information.

eth0      no frequency information.

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
          Current Frequency=2.457 GHz (Channel 10)

wifi0     14 channels in total; available frequencies :
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
          Current Frequency=2.457 GHz (Channel 10)

##### iwlist scan #######################

irda0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.457 GHz (Channel 10)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'otherwifi' [AC1]>
                    ESSID:"otherwifi"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-79 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 02 - Address: <MAC 'mywifinet' [AC2]>
                    ESSID:"mywifinet"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Signal level=-51 dBm  Noise level=-100 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=110

wifi0     Scan completed :
          Cell 01 - Address: <MAC 'otherwifi' [AC1]>
                    ESSID:"otherwifi"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-84 dBm  Noise level=-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 02 - Address: <MAC 'mywifinet' [AC2]>
                    ESSID:"mywifinet"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Signal level=-51 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=110

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        5F:B5:5B:9A:9C:55:9D:10:EE:62:74:37:BF:A5:E8:C5:F0:5C:A3:50
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
# PCI device 0x8086:0x1031 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1260:0x3873 (hostap_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   46.291859] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.365992] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.687883] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled (repeated 2 times)
[  315.910532] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

wireless-info from 16.04 - wifi disconnected
```

########## wireless info START ##########

Report from: 21 May 2016 08:45 EDT -0400

Booted last: 21 May 2016 00:00 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:15 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:02.0 Network controller [0280]: Intersil Corporation ISL3874 [Prism 2.5]/ISL3872 [Prism 3] [1260:3873] (rev 01)
    Subsystem: Intel Corporation Wireless 802.11b MiniPCI Adapter [8086:2513]
    Kernel driver in use: hostap_pci

02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
    Subsystem: IBM ThinkPad A/T/X Series [1014:0209]
    Kernel driver in use: e100

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e8d:1836 MediaTek Inc. Samsung SE-S084 Super WriteMaster Slim External DVD writer
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

##### lsmod #############################

cfg80211              499712  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s2    Link encap:Ethernet  HWaddr <MAC 'enp2s2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x8000 

enp2s8    Link encap:Ethernet  HWaddr <MAC 'enp2s8' [IF]>  
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dfae:21bb:83f3:dab8/64 Scope:Link
          inet6 addr: 2602:306:30c9:6070:a10d:e0f4:580a:a8ac/64 Scope:Global
          inet6 addr: 2602:306:30c9:6070:942e:16aa:69d:ab5a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:278890 errors:25314 dropped:0 overruns:0 frame:25314
          TX packets:4613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23053547 (23.0 MB)  TX bytes:461661 (461.6 KB)

irda0     Link encap:IrLAP  HWaddr <MAC 'irda0' [IF]>  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr <MAC 'wifi0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x8000 

##### iwconfig ##########################

enp2s8    no wireless extensions.

irda0     no wireless extensions.

lo        no wireless extensions.

enp2s2    IEEE 802.11b  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:45073  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13750   Missed beacon:0

wifi0     IEEE 802.11b  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enp2s8
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s8

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       654     1  0 May20 ?        00:00:24 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s8
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (ThinkPad A/T/X Series)
GENERAL.DRIVER:                         e100
GENERAL.DRIVER-VERSION:                 3.5.24-k2-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s8' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/enp2s8
GENERAL.IP-IFACE:                       enp2s8
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       273ad9ac-730f-47aa-a75d-6633210faa14
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   273ad9ac-730f-47aa-a75d-6633210faa14 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.98/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.254
DHCP4.OPTION[11]:                       expiry = 1463885315
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.98
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = attlocal.net
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         2602:306:30c9:6070:a10d:e0f4:580a:a8ac/64
IP6.ADDRESS[2]:                         2602:306:30c9:6070:942e:16aa:69d:ab5a/64
IP6.ADDRESS[3]:                         fe80::dfae:21bb:83f3:dab8/64
IP6.GATEWAY:                            fe80::2a16:2eff:fe9f:4749

GENERAL.DEVICE:                         enp2s2
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intersil Corporation
GENERAL.PRODUCT:                        ISL3874 [Prism 2.5]/ISL3872 [Prism 3] (Wireless 802.11b MiniPCI Adapter)
GENERAL.DRIVER:                         hostap_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               1.4.9
GENERAL.HWADDR:                         <MAC 'enp2s2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/enp2s2
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   06140c19-3a9a-4ea3-9457-453c722487c2 | mywifinet

GENERAL.DEVICE:                         wifi0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intersil Corporation
GENERAL.PRODUCT:                        ISL3874 [Prism 2.5]/ISL3872 [Prism 3] (Wireless 802.11b MiniPCI Adapter)
GENERAL.DRIVER:                         hostap_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               1.4.9
GENERAL.HWADDR:                         <MAC 'enp2s2' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wifi0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   06140c19-3a9a-4ea3-9457-453c722487c2 | mywifinet

GENERAL.DEVICE:                         irda0
GENERAL.TYPE:                           unknown
GENERAL.NM-TYPE:                        NMDeviceGeneric
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'irda0' [IF]>
GENERAL.MTU:                            2048
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/2
GENERAL.IP-IFACE:                       irda0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

SSID        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
mywifinet   <MAC 'mywifinet' [AC2]>  Infra  10    2457 MHz  22 Mbit/s  84      â–‚â–„â–†â–ˆ  WEP       no        
otherwifi  <MAC 'otherwifi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  25      â–‚___  WEP       no        

SSID        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
mywifinet   <MAC 'mywifinet' [AC2]>  Infra  10    2457 MHz  22 Mbit/s  84      â–‚â–„â–†â–ˆ  WEP       no        
otherwifi  <MAC 'otherwifi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  25      â–‚___  WEP       no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/mywifinet]] (600 root)
[connection] id=mywifinet | type=wifi | permissions=
[wifi] mac-address=<MAC 'enp2s2' [IF]> | mac-address-blacklist= | ssid=mywifinet
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s8    no frequency information.

irda0     no frequency information.

lo        no frequency information.

enp2s2    14 channels in total; available frequencies :
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
          Current Frequency=2.457 GHz (Channel 10)

wifi0     14 channels in total; available frequencies :
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
          Current Frequency=2.457 GHz (Channel 10)

##### iwlist scan #######################

enp2s8    Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.457 GHz (Channel 10)

enp2s2    Scan completed :
          Cell 01 - Address: <MAC 'otherwifi' [AC1]>
                    ESSID:"otherwifi"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-83 dBm  Noise level=-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 02 - Address: <MAC 'mywifinet' [AC2]>
                    ESSID:"mywifinet"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Signal level=-49 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=110

wifi0     Scan completed :
          Cell 01 - Address: <MAC 'otherwifi' [AC1]>
                    ESSID:"otherwifi"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-79 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 02 - Address: <MAC 'mywifinet' [AC2]>
                    ESSID:"mywifinet"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Signal level=-50 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=110

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   17.861540] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[   18.879391] hostap_pci 0000:02:02.0 enp2s2: renamed from wlan0
[   38.195673] IPv6: ADDRCONF(NETDEV_UP): enp2s8: link is not ready (repeated 2 times)
[   38.216224] e100 0000:02:08.0 enp2s8: NIC Link is Up 100 Mbps Full Duplex
[   38.217371] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s8: link becomes ready
[   38.681600] IPv6: ADDRCONF(NETDEV_UP): enp2s2: link is not ready (repeated 2 times)
[   40.869749] enp2s2: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[   41.194253] IPv6: ADDRCONF(NETDEV_UP): enp2s2: link is not ready

########## wireless info END ############

```

-----------------------------------------------------------------------------------------
You can lead a horse to water... but you can't make 'em think

---

### Post by moot2 on 2016-05-22
OK... I did not solve the issue... just a work around... (would be nice to have 'work around' on thread tools menu)

After doing a 'tweak' to the T30 bios, I was able to install a different wireless adapter (not combo, no modem, just 802.11b)... see [https://command-tab.com/2006/02/26/thinkpad-1802-error-fix/](https://command-tab.com/2006/02/26/thinkpad-1802-error-fix/)

Basically, IBM ThinkPad T30 Bios does not allow any other wireless but the original... change 1 bit in Bios and voila... use other wireless adapters...
Of course now I don't have a modem... will try for PCMCIA straight modem ($10) or go with USB if really needed... not a necessity except maybe FAX...

I'm still researching the  Intel Model: M3AWEB56GA but there does not seem to be any working Linux/Ubuntu driver that will identify and use the wireless and modem combo.
see [http://thinkpads.com/support/Thinkpad-Drivers/download.lenovo.com/lenovo/content/ddfm/T30.html](http://thinkpads.com/support/Thinkpad-Drivers/download.lenovo.com/lenovo/content/ddfm/T30.html) ... other references to Lenovo return 'Page Not Found'...

I would still like to really _**solve**_ the adapter driver issue... should I mark this thread solved? I would just as soon not have to hack the Bios and get replacement wireless adapters... (cheap but still $)

I just posted on the Compatibility forum...see: [http://ubuntuforums.org/showthread.php?t=1543006&p=13493434#post13493434](http://ubuntuforums.org/showthread.php?t=1543006&p=13493434#post13493434)
From what I have read the IBM ThinkPad is one of the best laptops for running Linux based OS... have R51 to try next...
The T30 actually runs pretty good, all things considered... I'll still try slimmer versions... just out of curiosity...

So... any wireless driver gurus up to debugging the Intel Model: M3AWEB56GA ... I'll loan a T30 to test on...

---

