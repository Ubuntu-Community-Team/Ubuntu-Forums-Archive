---
title: "Wireless too slow, Intel Pro/Wireless 3945ABG"
date: 2015-02-14
forum: Networking &amp; Wireless
---

### Post by wgw on 2015-02-14
My wireless is pretty reliable but it runs at 10 to a maximum of 17 Mb/s. When my cellphone is attached to the network, it works consistently at 20 Mb. 10 is quite slow; my wired connection runs at 25 Mb/s. 

I've read some posts about how to boost speed, tried a few of the simple ones (mostly from here: [http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)) , but performance remains pretty systematically at about 14 Mb/s.

Sorry to go back over this frequent query, but I can't seem to find a good troubleshooting procedure. My wireless config below.  

```


########## wireless info START ##########

Report from: 13 Feb 2015 20:52 PST -0800

Booted last: 12 Feb 2015 17:37 PST -0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
	Subsystem: Lenovo ThinkPad T60 [17aa:2001]
	Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
	Subsystem: Intel Corporation Device [8086:1010]
	Kernel driver in use: iwl3945

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwl3945                73259  0 
iwlegacy              100569  1 iwl3945
mac80211              630669  2 iwl3945,iwlegacy
cfg80211              484040  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:155926 errors:0 dropped:84 overruns:0 frame:0
          TX packets:93827 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140582760 (140.5 MB)  TX bytes:31070515 (31.0 MB)
          Interrupt:16 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr <MAC 'irda0' [IF]>  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec0:5bd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:335060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:361754268 (361.7 MB)  TX bytes:103286549 (103.2 MB)

##### iwconfig ##########################

irda0     no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"WirelessRus"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'WirelessRus' [AN6]>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:16  Invalid misc:2109   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search telus

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [WirelessRus] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TELUS1020:       Infra, <MAC 'TELUS1020' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    75FFC6:          Infra, <MAC '75FFC6' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    SHAW-D538A7-5G:  Infra, <MAC 'SHAW-D538A7-5G' [AN3]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    2010tix:         Infra, <MAC '2010tix' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    7D3A11:          Infra, <MAC '7D3A11' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    *WirelessRus:    Infra, <MAC 'WirelessRus' [AN6]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 69 WPA2
    6ADA9C:          Infra, <MAC '6ADA9C' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    TELUS8569:       Infra, <MAC 'TELUS8569' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    TELUS1679:       Infra, <MAC 'TELUS1679' [AN9]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    SHAW-D538A7:     Infra, <MAC 'SHAW-D538A7' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    forVISTA:        Infra, <MAC 'forVISTA' [AN11]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 24 WEP
    5B5EAA:          Infra, <MAC '5B5EAA' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Sweet+Salty:     Infra, <MAC 'Sweet+Salty' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Don Carlos:      Infra, <MAC 'Don Carlos' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    BillWiScienceFi: Infra, <MAC 'BillWiScienceFi' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    TELUS2105:       Infra, <MAC 'TELUS2105' [AN16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    SHAW-EE9ECB:     Infra, <MAC 'SHAW-EE9ECB' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254
    DNS:             75.153.176.9

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ubcsecure]] (600 root)
[ipv6] method=auto
[connection] id=ubcsecure | type=802-11-wireless
[802-11-wireless] ssid=ubcsecure
[802-1x] ca-cert=/home/bill/.certificates/ubcsecure-CA.pem
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SFUNET-SECURE]] (600 root)
[ipv6] method=auto
[connection] id=SFUNET-SECURE | type=802-11-wireless
[802-11-wireless] ssid=SFUNET-SECURE | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SFUNET]] (600 root)
[connection] id=SFUNET | type=802-11-wireless
[802-11-wireless] ssid=SFUNET | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WirelessRus]] (600 root)
[connection] id=WirelessRus | type=802-11-wireless | permissions=user:bill:;
[802-11-wireless] ssid=WirelessRus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

irda0     no frequency information.

eth0      no frequency information.

lo        no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.447 GHz (Channel 8)

##### iwlist scan #######################

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     63597F7C72B07A97B142DC2
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     A847A747E4E6066D74E1D6A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

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

sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x109a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[30748.541288] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30755.711490] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=58341 PROTO=2 
[30788.581610] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30788.684093] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=21967 PROTO=2 
[30828.526338] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30833.737454] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=11006 PROTO=2 
[30868.553262] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30871.831978] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=55792 PROTO=2 
[30908.591846] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30910.766263] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36877 PROTO=2 
[30948.527047] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30956.822711] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=11827 PROTO=2 
[30988.567846] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[30997.887070] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=18429 PROTO=2 
[31028.603359] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31034.892090] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=19225 PROTO=2 
[31068.643417] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31073.975521] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=34965 PROTO=2 
[31108.579088] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31113.084903] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=53152 PROTO=2 
[31148.615464] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31153.123211] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=8537 PROTO=2 
[31188.654234] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[31235.142673] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=2579 PROTO=2 
[31268.630944] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31277.229625] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=3749 PROTO=2 
[31308.668893] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31310.201254] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=62538 PROTO=2 
[31348.705078] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31356.280934] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47763 PROTO=2 
[31388.645037] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31393.349617] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=62516 PROTO=2 
[31428.678744] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31438.410603] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39566 PROTO=2 
[31468.716761] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[31517.458011] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=12770 PROTO=2 
[31548.689336] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[31596.612546] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=38283 PROTO=2 
[31628.768095] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31632.555357] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=29149 PROTO=2 
[31668.803753] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31672.594128] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=40675 PROTO=2 
[31708.741245] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31710.697365] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39815 PROTO=2 
[31748.782571] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31756.662101] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=63784 PROTO=2 
[31788.730600] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31797.725598] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=43948 PROTO=2 
[31828.755397] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31837.762343] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=6143 PROTO=2 
[31868.790272] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2  (repeated 3 times)
[31950.916853] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=48201 PROTO=2 
[31988.805654] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[31991.875864] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=46478 PROTO=2 
[32028.840391] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32037.954867] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=61336 PROTO=2 
[32068.880537] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32071.030890] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=54420 PROTO=2 
[32108.916360] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32115.059629] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=61733 PROTO=2 
[32148.851379] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32152.028045] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=65193 PROTO=2 
[32188.893109] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32193.088872] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=5501 PROTO=2 
[32228.928032] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32235.176687] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=14997 PROTO=2 
[32268.863247] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32269.170627] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=9700 PROTO=2 
[32308.901409] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32315.250111] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39271 PROTO=2 
[32348.939558] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32350.272424] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=4438 PROTO=2 
[32388.978304] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32396.355450] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=61698 PROTO=2 
[32428.922510] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32434.341550] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=37968 PROTO=2 
[32468.902433] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32469.330274] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=51338 PROTO=2 
[32508.990638] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32515.454699] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=53333 PROTO=2 
[32549.035315] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32556.635795] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=40244 PROTO=2 
[32588.965477] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32593.470039] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=46332 PROTO=2 
[32629.005463] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32639.139288] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=46698 PROTO=2 
[32669.041702] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32678.564653] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=12510 PROTO=2 
[32708.978286] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32712.663817] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=54595 PROTO=2 
[32749.023348] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32757.718051] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=27402 PROTO=2 
[32789.053762] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:39:44:a2:dd:e8:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[32794.687003] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=239 PROTO=2 

########## wireless info END ############



```

---

### Post by mikewhatever on 2015-02-14
The outputs below show it runs at 54Mbps and not 10. How do you test it?

---

### Post by wgw on 2015-02-14
I use both speedtest-cli and [http://www.speedtest.net/](http://www.speedtest.net/) .

---

### Post by jeremy31 on 2015-02-14
Try disabling the firewall as it is blocking a lot of local traffic

---

### Post by wgw on 2015-02-14
With the firewall down (first try) it was slower; with it up, faster.... but probably just network variability. But both tests were higher than I usually get: 16 and 17 Mb/s. I think 20 would be max, since I don't use 802.11n (and maybe my cell does, which comes in at 23 usually). 

```
bill@bill-laptop:~/Documents/ubuntu$ speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Telus Communications (99.199.88.216)...
Selecting best server based on latency...
Hosted by TELUS (Vancouver, BC) [3.11 km]: 13.331 ms
Testing download speed........................................
Download: 16.01 Mbits/s
Testing upload speed..................................................
Upload: 6.56 Mbits/s
bill@bill-laptop:~/Documents/ubuntu$ speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Telus Communications (99.199.88.216)...
Selecting best server based on latency...
Hosted by FullHost (Vancouver, BC) [3.11 km]: 13.003 ms
Testing download speed........................................
Download: 17.83 Mbits/s
Testing upload speed..................................................
Upload: 5.92 Mbits/s

```

---

### Post by jeremy31 on 2015-02-15
Might want to try this command, reboot and test the speed again ```
echo "options iwlegacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwlegacy.conf
```
If it fails to help, remove it with ```
sudo rm /etc/modprobe.d/iwlegacy.conf
```

---

### Post by wgw on 2015-02-15
thanks for the suggestion; tweak had no effect (I include the wired connection speed at the end: big difference!) 

after tweak and reboot: 

```
bill@bill-laptop:~$ speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Telus Communications (99.199.88.216)...
Selecting best server based on latency...
Hosted by FullHost (Vancouver, BC) [3.11 km]: 14.247 ms
Testing download speed........................................
Download: 14.05 Mbits/s
Testing upload speed..................................................
Upload: 5.86 Mbits/s

 
```

then deleted the tweak, and back to original after reboot: 

```

bill@bill-laptop:~$ speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Telus Communications (99.199.88.216)...
Selecting best server based on latency...
Hosted by Skyway West Business Internet Services (Vancouver, BC) [3.11 km]: 14.034 ms
Testing download speed........................................
Download: 13.99 Mbits/s
Testing upload speed..................................................
Upload: 5.03 Mbits/s
bill@bill-laptop:~$
```

With wired connection: 

```
bill@bill-laptop:~$ speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Telus Communications (99.199.88.216)...
Selecting best server based on latency...
Hosted by TELUS (Vancouver, BC) [3.11 km]: 11.132 ms
Testing download speed........................................
Download: 26.63 Mbits/s
Testing upload speed..................................................
Upload: 5.51 Mbits/s
bill@bill-laptop:~$ 

```

---

### Post by wgw on 2015-02-15
The other mystery is the line in report that reads: 

[30755.711490] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=58341 PROTO=2  

The source is my ipad on my network; why would my firewall be blocking my ipad ... or rather why would the ipad be going through my ubuntu machine? No reason for that, afaik.

---

### Post by jeremy31 on 2015-02-15
> **wgw said:**
> The other mystery is the line in report that reads: 

[30755.711490] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:70:de:e2:3e:c4:86:08:00 SRC=192.168.1.82 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=58341 PROTO=2  

The source is my ipad on my network; why would my firewall be blocking my ipad ... or rather why would the ipad be going through my ubuntu machine? No reason for that, afaik.

It isn't blocking any thing from the ipad, that is from [http://en.wikipedia.org/wiki/Multicast_DNS](http://en.wikipedia.org/wiki/Multicast_DNS) the MAC and DST addresses are correct for it, and the source if the IP of your computer, this is from the wireless script results ```
[COLOR=#000000][FONT=Ubuntu Mono]wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  [/FONT][/COLOR]          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec0:5bd9/64 Scope:Link
```

---

### Post by wgw on 2015-02-15
iwlwifi.conf is a mystery, but I will create a /etc/modprobe.d/iwl3945.conf and put in there: options iwl3945 swcrypto=0

For the moment, this is iwlwifi.conf:

```

bill@bill-laptop:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

```

bill@bill-laptop:~$ /sbin/lsmod | grep mac
mac80211              630669  2 iwl3945,iwlegacy
cfg80211              484040  3 iwl3945,iwlegacy,mac80211
mac_hid                13205  0 

```

---

### Post by jeremy31 on 2015-02-15
> **wgw said:**
> iwlwifi.conf is a mystery, but I will create a /etc/modprobe.d/iwl3945.conf and put in there: options iwl3945 swcrypto=0

For the moment, this is iwlwifi.conf:

```

bill@bill-laptop:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

```

bill@bill-laptop:~$ /sbin/lsmod | grep mac
mac80211              630669  2 iwl3945,iwlegacy
cfg80211              484040  3 iwl3945,iwlegacy,mac80211
mac_hid                13205  0 

```

The iwlwifi.conf file simply make it easier for people to insert and remove the module using modprobe( -r) or insmod or rmmod as it will automatically remove iwlmvm or iwldvm rather than giving an error that iwlwifi is in use

---

### Post by wgw on 2015-02-15
Thanks for you explanations J31! 

I tried > I will create a /etc/modprobe.d/iwl3945.conf and put in there: options iwl3945 swcrypto=0, but that was a flop: wireless would not connect. (That conf file is probably not the right place to add the option.)

---

### Post by jeremy31 on 2015-02-15
> **wgw said:**
> Thanks for you explanations J31! 

I tried , but that was a flop: wireless would not connect. (That conf file is probably not the right place to add the option.)

If it said ```
options iwl3945 swcrypto=0
```
It could have been in /etc/modprobe.d/crash.conf and worked the same, it obviously doesn't want to use hardware encryption.  It might be one of the times that TKIP encryption might help as that usually causes issues but it might be worth a shot

---

### Post by wgw on 2015-02-15
TKIP seems to be a problem on ubuntu, at least in the past: 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432)

I didn't find any options to set TKIP (in the connection security tab), but as far as I can tell, the card does use TKIP (or does it? -- I don't know!). 

```

bill@bill-laptop:~$ iwlist wlan0 scanning 
wlan0     Scan completed :
          Cell 01 - Address: <mac removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"WirelessRus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000396f2075ab
                    Extra: Last beacon: 25216ms ago

                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
  

```

---

### Post by jeremy31 on 2015-02-15
If that is the case, when the script was run scanning wasn't possible, disable TKIP in the router settings if you can.  It may help some but I think TKIP supports up to wireless g speed

---

### Post by wgw on 2015-02-16
I'm going to kill the encryption and see if that will localize the problem. It may take a while (my router is not cooperating); thanks so much for your help. I have a feeling this is going to be a long (painful!) process of just breaking the system down to bare bones and then putting it back together to find the location of the lag. I will post here the log of my experiments,  if they are not all dead-ends. 

This speed issue seems to be fairly common, so a more robust troubleshooting guide is needed -- one that is a bit more than "do this; is it better?". We need to be able to monitor the data flow to find the bottleneck. Maybe something like wireshark would help. So, I will have to educate myself more and do some long term exploring.

Again, thanks Jeremy for all the suggestions and attention. 

Best,

Bill

---

