---
title: "Wireless connection stopped working IPW2200 on HP TC4200"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by jfhuguet on 2014-12-06
My wireless connection stopped working. I have been on 12.04.4 LTS for months without problems.
When I run #rfkill list# I get:
#0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
6: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no
I did "rfkill unblock all" but I still get the "hard blocked:yes" on phy0. 
The on/off switch for bluetooth/wifi is on.
Could it be only HW?

Here is the wifi config test result which I ran before executing the #rfkill unblock all# command

########## wireless info START ##########

Report from: 06 Dec 2014 16:21 CET +0100

Booted last: 06 Dec 2014 16:14 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.8.0-44-generic #66~precise1-Ubuntu SMP Tue Jul 15 04:04:23 UTC 2014 i686 i686 i386 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Hewlett-Packard Company nc6120/nx8220/nw8240 [103c:12f6]
    Kernel driver in use: ipw2200

10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:0938]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Bluetooth 1.2 Interface [Broadcom BCM2035]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

##### lsmod #############################

ath9k_htc              91124  0 
mac80211              546110  1 ath9k_htc
ath9k_common           13781  1 ath9k_htc
ath9k_hw              406677  2 ath9k_htc,ath9k_common
ath                    19435  3 ath9k_htc,ath9k_common,ath9k_hw
ipw2200               142064  0 
libipw                 33469  1 ipw2200
hp_wmi                 17748  0 
cfg80211              454468  5 ath9k_htc,mac80211,ath,ipw2200,libipw
sparse_keymap          13658  1 hp_wmi
lib80211               14040  2 ipw2200,libipw
wmi                    18744  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2e13:6490:41db:820a:aa5d:3768/64 Scope:Global
          inet6 addr: 2a01:e35:2e13:6490:216:d4ff:fe0e:bc86/64 Scope:Global
          inet6 addr: fe80::216:d4ff:fe0e:bc86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99791 (99.7 KB)  TX bytes:41294 (41.2 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             192.168.0.254

  IPv6 Settings:
    Address:         2a01:e35:2e13:6490:41db:820a:aa5d:3768
    Prefix:          64
    Gateway:         fe80::160c:76ff:fe6a:6153

    Address:         2a01:e35:2e13:6490:216:d4ff:fe0e:bc86
    Prefix:          64
    Gateway:         fe80::160c:76ff:fe6a:6153

    Address:         fe80::216:d4ff:fe0e:bc86
    Prefix:          64
    Gateway:         fe80::160c:76ff:fe6a:6153

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Family 2]] (600 root)
[connection] id=Family 2 | type=802-11-wireless
[802-11-wireless] ssid=Family | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NEUF_42B8]] (600 root)
[connection] id=NEUF_42B8 | type=802-11-wireless
[802-11-wireless] ssid=NEUF_42B8 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR_EXT]] (600 root)
[connection] id=NETGEAR_EXT | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR_EXT | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/freebox_ZE]] (600 root)
[connection] id=freebox_ZE | type=802-11-wireless
[802-11-wireless] ssid=freebox_ZE | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Family]] (600 root)
[connection] id=Family | type=802-11-wireless
[802-11-wireless] ssid=Family | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Family 1]] (600 root)
[connection] id=Family 1 | type=802-11-wireless
[802-11-wireless] ssid=Family | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIRELESS-STATION]] (600 root)
[connection] id=WIRELESS-STATION | type=802-11-wireless
[802-11-wireless] ssid=WIRELESS-STATION | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

eth1      14 channels in total; available frequencies :
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
          Current Channel=0

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     9B96BF592DBE18986BE65DD
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[mac80211]
filename:       /lib/modules/3.8.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1FF78E380549BFAADC883E4
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath9k_common]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     3FC27688A6C53D91F60FDBA
depends:        ath
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 686 

[ath]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 686 

[ipw2200]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     C4303D31F5DF5C5762BD516
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 686 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[cfg80211]
filename:       /lib/modules/3.8.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     37EA28891FFED476061D81A
depends:        
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:10:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x0846:0x9030 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   10.980105] ipw2200: Radio Frequency Kill Switch is On:
[   10.980105] Kill switch must be turned off for wireless networking to work.
[   10.992753] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   11.657037] usb 1-3: ath9k_htc: Firmware htc_9271.fw requested
[   11.657765] usbcore: registered new interface driver ath9k_htc
[   12.075076] usb 1-3: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   12.310043] ath9k_htc 1-3:1.0: ath9k_htc: HTC initialized with 33 credits
[   12.508562] ath9k_htc 1-3:1.0: ath9k_htc: FW Version: 1.3
[   12.508569] ath: EEPROM regdomain: 0x60
[   12.508571] ath: EEPROM indicates we should expect a direct regpair map
[   12.508575] ath: Country alpha2 being used: 00
[   12.508577] ath: Regpair used: 0x60
[   20.561945] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.564090] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.392042] ipw2200: Failed to send POWER_MODE: Command timed out. (repeated 2 times)
[   41.357999] usb 1-3: ath9k_htc: USB layer deinitialized
[   41.957568] usb 1-3: ath9k_htc: Firmware htc_9271.fw requested
[   42.273713] usb 1-3: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   43.272053] ath9k_htc 1-3:1.0: ath9k_htc: Target is unresponsive
[   43.272070] ath9k_htc: Failed to initialize the device
[   43.272111] usb 1-3: ath9k_htc: USB layer deinitialized

########## wireless info END ############.
#
Many thanks for any help

---

