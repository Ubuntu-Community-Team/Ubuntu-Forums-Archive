---
title: "Ubuntu 14.04 LTS, WNDA3100v2, Can see networks, but does not connect."
date: 2015-11-15
forum: Networking &amp; Wireless
---

### Post by jesse42 on 2015-11-15
I'm trying to get my wireless working.  When I try to connect to my home WiFi it just keeps asking me to enter the pass-phrase over and over, but never connects. I've searched tons of threads from people with similar issues, but haven't had success.  Script output follows.

```

########## wireless info START ##########

Report from: 15 Nov 2015 10:15 CST -0600

Booted last: 15 Nov 2015 09:34 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:18:00 UTC 2015 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2a26]
    Kernel driver in use: 8139too

##### lsusb #############################

Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 1bcf:000a Sunplus Innovation Technology Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              450560  0 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
ndiswrapper           196608  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6217900 (6.2 MB)  TX bytes:312122 (312.1 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270 (270.0 B)  TX bytes:3869 (3.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       838     1  0 09:34 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ASUS:            Infra, <MAC 'ASUS' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    NETGEAR:         Infra, <MAC 'NETGEAR' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2
    mouser15:        Infra, <MAC 'mouser15' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2
    WIELESS MOSS:    Infra, <MAC 'WIELESS MOSS' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA2
    Veith:           Infra, <MAC 'Veith' [AC8]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 52 WPA2
    gmgp7:           Infra, <MAC 'gmgp7' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    ATT096:          Infra, <MAC 'ATT096' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    BuckyNet:        Infra, <MAC 'BuckyNet' [AN8]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WPA2
    MonkeyJack:      Infra, <MAC 'MonkeyJack' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    ATT944:          Infra, <MAC 'ATT944' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    NETGEAR40:       Infra, <MAC 'NETGEAR40' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    andrews:         Infra, <MAC 'andrews' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA
    Stew:            Infra, <MAC 'Stew' [AN13]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Mouser15-5G_2GEXT: Infra, <MAC 'Mouser15-5G_2GEXT' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ATT504:          Infra, <MAC 'ATT504' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    T4Cabs-PC_Network: Infra, <MAC 'T4Cabs-PC_Network' [AN16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    DIRECT-roku-9F1B6C: Infra, <MAC 'DIRECT-roku-9F1B6C' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    ATT768:          Infra, <MAC 'ATT768' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Chadwick Wireless: Infra, <MAC 'Chadwick Wireless' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    NETGEAR87:       Infra, <MAC 'NETGEAR87' [AN20]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Vonwick-2-4:     Infra, <MAC 'Vonwick-2-4' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    ATT152:          Infra, <MAC 'ATT152' [AN22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Blue 2.4GHz:     Infra, <MAC 'Blue 2.4GHz' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2

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

[[/etc/NetworkManager/system-connections/Blue 2.4GHz]] (600 root)
[connection] id=Blue 2.4GHz | type=802-11-wireless
[802-11-wireless] ssid=Blue 2.4GHz | mac-address=<MAC 'wlan0' [IF]>
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ASUS' [AC1]>
                    ESSID:"ASUS"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Blue 2.4GHz' [AC2]>
                    ESSID:"Blue 2.4GHz"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-9 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT504' [AC3]>
                    ESSID:"ATT504"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ATT096' [AC4]>
                    ESSID:"ATT096"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'mouser15' [AC5]>
                    ESSID:"mouser15"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'gmgp7' [AC6]>
                    ESSID:"gmgp7"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'NETGEAR40' [AC7]>
                    ESSID:"NETGEAR40"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Veith' [AC8]>
                    ESSID:"Veith"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
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
filename:       /lib/modules/3.19.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        BB:26:8D:6D:EE:CB:ED:52:27:34:75:F8:CB:66:1B:D2:CA:20:8A:1B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.19.0-25-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     C101C962263FFF26465A483
depends:        
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
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

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   19.002454] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[   19.261676] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx32, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[   19.264262] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   31.099943] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.113994] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 2149.114555] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2317.447842] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)

########## wireless info END ############

```

---

### Post by praseodym on 2015-11-17
Change to b/g mode in your router, pure WPA2-AES (CCMP) encryption and to a fixed channel. Check the router manual

---

