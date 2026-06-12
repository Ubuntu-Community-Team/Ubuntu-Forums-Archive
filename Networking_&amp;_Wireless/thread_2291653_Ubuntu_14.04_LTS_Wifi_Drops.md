---
title: "Ubuntu 14.04 LTS Wifi Drops"
date: 2015-08-21
forum: Networking &amp; Wireless
---

### Post by Daniel_Newberry on 2015-08-21
Hello!
I relocated my computer to a house with a new network yesterday and I have been having issues connecting to the wifi here. At the old location, my connection worked fine. I have been trying lots of things since last night, so far with only limited success. The output of the code from the sticky thread is below.

```

########## wireless info START ##########

Report from: 21 Aug 2015 19:04 CDT -0500

Booted last: 21 Aug 2015 18:54 CDT -0500

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-46-generic #62~14.04.1-Ubuntu SMP Tue Aug 11 16:27:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 413c:2111 Dell Computer Corp.
Bus 003 Device 002: ID 0461:4d81 Primax Electronics, Ltd Dell N889 Optical Mouse
Bus 003 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              498458  0
ndiswrapper           283985  0
snd_soc_rt5640         93042  0
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
mxm_wmi                13021  0
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  1 mxm_wmi

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
          Interrupt:18

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30724776 (30.7 MB)  TX bytes:1092075 (1.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Cosmodrome"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Cosmodrome' [AC1]>  
          Bit Rate=78 Mb/s   Tx-Power:32 dBm  
          RTS thr:2347 B   Fragment thr:2346 B  
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:18  Invalid misc:15543   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       932     1  0 18:54 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Cosmodrome] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
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
    NETGEAR25:       Infra, <MAC 'NETGEAR25' [AC11]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WPA2
    FreeWiFi:        Infra, <MAC 'FreeWiFi' [AC7]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 57 WPA2
    NETGEAR23:       Infra, <MAC 'NETGEAR23' [AC5]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 55 WPA2
    DIRECT-roku-446-29E526: Infra, <MAC 'DIRECT-roku-446-29E526' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Arbiter:         Infra, <MAC 'Arbiter' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    NETGEAR90:       Infra, <MAC 'NETGEAR90' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    FBI Surveillance Van 2.0: Infra, <MAC 'FBI Surveillance Van 2.0' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA
    BeigeFish:       Infra, <MAC 'BeigeFish' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Bring beer for password: Infra, <MAC 'Bring beer for password' [AC6]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Raeder:          Infra, <MAC 'Raeder' [AC8]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Andy:            Infra, <MAC 'Andy' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    *Cosmodrome:     Infra, <MAC 'Cosmodrome' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 WPA2
    Sundown:         Infra, <MAC 'Sundown' [AN13]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA2
    CRUZADA:         Infra, <MAC 'CRUZADA' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    CenturyLink5766: Infra, <MAC 'CenturyLink5766' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    NG-WNR1000:      Infra, <MAC 'NG-WNR1000' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             216.229.72.10
    DNS:             216.229.73.10

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

[[/etc/NetworkManager/system-connections/NEWBHOME]] (600 root)
[connection] id=NEWBHOME | type=802-11-wireless
[802-11-wireless] ssid=NEWBHOME | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cosmodrome]] (600 root)
[connection] id=Cosmodrome | type=802-11-wireless
[802-11-wireless] ssid=Cosmodrome | mac-address=<MAC 'wlan0' [IF]> | mtu=1500
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/newberry2013]] (600 root)
[connection] id=newberry2013 | type=802-11-wireless
[802-11-wireless] ssid=newberry2013 | mac-address=<MAC 'wlan0' [IF]>
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

eth0      no frequency information.

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Cosmodrome' [AC1]>
                    ESSID:"Cosmodrome"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIRECT-roku-446-29E526' [AC2]>
                    ESSID:"DIRECT-roku-446-29E526"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'NETGEAR' [AC3]>
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: <MAC 'FBI Surveillance Van 2.0' [AC4]>
                    ESSID:"FBI Surveillance Van 2.0"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NETGEAR23' [AC5]>
                    ESSID:"NETGEAR23"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Bring beer for password' [AC6]>
                    ESSID:"Bring beer for password"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'FreeWiFi' [AC7]>
                    ESSID:"FreeWiFi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Raeder' [AC8]>
                    ESSID:"Raeder"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'NETGEAR90' [AC9]>
                    ESSID:"NETGEAR90"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'NG-WNR1000' [AC10]>
                    ESSID:"NG-WNR1000"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'NETGEAR25' [AC11]>
                    ESSID:"NETGEAR25"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-46-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        42:70:EE:2F:79:25:EC:FF:7D:DB:B5:97:82:CC:0D:B2:6E:5C:03:29
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.16.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.16.0-46-generic SMP mod_unload modversions
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

lp
rtc

coretemp

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
options iwlwifi 11n_disable=1 wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0xe091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[    2.096945] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[    2.398314] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[    2.646721] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[    2.648144] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[    2.851178] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.419625] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############
```

My usual adapter is a refurb NetGear WNDA3100v2 running the bcmn43xx64 driver through ndiswrapper, which will work for an undetermined amount of time before suddenly not working. I have tried another adapter, a small Edimax adapter, and it works for a short while more before crapping out itself. One of the more baffling things to me is that when it appears that I have dropped connection, the wifi applet on the taskbar will usually show that I am still connected despite the fact that I do not get any . The latest thing that I have tried is the disabling of "n" networking on my driver using:

```

sudo modprobe iwlwifi -r
sudo modprobe iwlwifi 11n_disable=1

```

which has allowed me to connect and stay connected for longer, but it will still drop. It has seemed that it may be related to high internet load.  For instance the first and second drops after the fix above occured while I was doing an Ookla speedtest. When I do drop though, it requires a reboot to get it working again, although that doesn't always work, requiring even more reboots.  (Actually, I lost connection while writing this and didn't notice until I found myself unable to post as the wifi applet still showed I was connected.  I then had to reboot twice to get it to work, with the NetGear adapter not appearing to work on the first reboot)

This has been quite frustrating. Any and all help would be much appreciated! Thank you in advance!

[EDIT]  It appears that a reboot is not neccessarily required.  After it loses connection and I notice, I can set it to reconnect where it will reconnect with enough time.

---

### Post by weatherman2 on 2015-08-21
I hate to tell you this, but unless you have an Intel wireless card (besides the Netgear card and the Edimax card), mucking with the iwlwifi driver doesn't do anything.  Your Netgear adapter uses a Broadcom chipset.  I don't know what the Edimax uses but probably not an Intel chipset.  I think you are simply seeing a placebo effect.

You might switch to the Edimax card and run the wireless script again.  I think you will be better off with a card that doesn't use ndiswrapper and uses a native Linux driver if possible.  Maybe some tuning of the options or the driver for your Edimax card will be possible, if we can figure out which chipset/driver it uses.

Do you have any insight into the wireless access point or router you are connecting to?  How is it configured?  Are you further away from it than in the old location?  In any case, if it's an entirely different wireless device, you are using your wireless cards in an entirely different environment than before, and sometimes WiFi works worse in one area than another.  A card that worked OK before in one location may work awful in another.  Those wireless dongles can work OK in some situations but not in others.

I have used those wireless dongles in the past but lately I have been using old wireless routers re-configured as wireless ethernet bridges instead.  The seem to work better than those dongles, which don't have very big antennas in most cases, and there is no wireless driver on the Linux side - you simply connect your computer up via the ethernet port with a cable and the wireless ethernet bridge/router connects to the main router wirelessly.  There are also better wireless cards than those little dongles that can work better.

---

### Post by Daniel_Newberry on 2015-08-21
Thanks for the reply!
Darn!  I thought I had progress with that! Oh well, I suppose.

I tried the Edimax adapter again and it didn't work.  I believe it is an EW-78811UN (atleast that is what it looks like physically), but either way it is a RealTek chipset and is plug and play.  Strangely, this adapter I have used in the past with a Raspberry Pi on this network and it has worked fine.  

The access point is an Arris DG860 Modem/Router combo that I got from the ISP.  As best as I can tell, it is running Arris firmware as opposed to ISP firmware.  It is on the default settings mostly, aside from it is set to channel 11.  I have tried connecting a Linksys router to it and using the router as the access point instead, but with similar results.

Using a router as a bridge does sound like a much simpler idea, or atleast better quality. I will probably pursue that in the near future.
Once again, thanks for the help!

---

### Post by weatherman2 on 2015-08-21
That Edimax probably uses the Realtek 8192CU chipset.  If so, try this to make it work reliably:

[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)

---

### Post by Daniel_Newberry on 2015-08-21
From lsusb

"...
Bus 003 Device 006: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
..."

for the Edimax adapter.

---

