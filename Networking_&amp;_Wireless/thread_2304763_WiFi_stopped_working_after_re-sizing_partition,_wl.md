---
title: "WiFi stopped working after re-sizing partition, wlan0 gone in Ubuntu 14.04"
date: 2015-11-29
forum: Networking &amp; Wireless
---

### Post by Saiful_Islam on 2015-11-29
[COLOR=#333333][FONT=Ubuntu]I needed to increase my ubuntu root partition size. I booted from live USB then resized the partition. After rebooting to Ubuntu everything was ok, but Wifi stopped working and wlan0 is gone from "iwconfig". Then I rebooted with the live cd, wifi was working. And was also working with windows 10. I tried reinstalling linux-firmware, and installing "linux-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]generic-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]lts-vivid" but no luck. 
Here is my wireless-info

[/FONT][/COLOR]```


########## wireless info START ##########


Report from: 30 Nov 2015 04:29 BDT +0600


Booted last: 30 Nov 2015 04:27 BDT +0600


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


03:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]


##### lsusb #############################


Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 04f2:b370 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 148e:099a EVATRONIX SA 
Bus 003 Device 003: ID 138a:003d Validity Sensors, Inc. VFS491
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0421:069a Nokia Mobile Phones 130 [RM-1035] (Charging only)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
wl                   6369280  0 
cfg80211              524288  1 wl
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth4      Link encap:Ethernet  HWaddr <MAC 'eth4' [IF]>  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth4' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61231 (61.2 KB)  TX bytes:37675 (37.6 KB)


##### iwconfig ##########################


eth4      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth4
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth4


##### resolv.conf #######################


nameserver 127.0.1.1
search local


##### network managers ##################


Installed:


    NetworkManager


Running:


root       823     1  0 04:26 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth4  [Banglalion] ---------------------------------------------------
  Type:              Wired
  Driver:            cdc_ether
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth4' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.2.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.61.62
    DNS:             58.97.254.25


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


no-auto-default=<MAC address>,6C:AD:EF:12:CE:6C,00:0A:3B:F0:01:30,<MAC 'eth4' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Xiaomi Mi4 ]] (600 root)
[connection] id=Xiaomi Mi4  | type=802-11-wireless
[802-11-wireless] ssid=Xiaomi Mi4  | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Plabon]] (600 root)
[connection] id=Plabon | type=802-11-wireless | permissions=user:plabon:;
[802-11-wireless] ssid=no free wifi
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Con]] (600 root)
[connection] id=Con | type=802-11-wireless | permissions=user:plabon:;
[802-11-wireless] ssid=my_shared_connection
[ipv6] method=auto
[ipv4] method=shared


[[/etc/NetworkManager/system-connections/Mordor]] (600 root)
[connection] id=Mordor | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=Mordor
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/P]] (600 root)
[connection] id=P | type=802-11-wireless | permissions=user:plabon_lab:;
[802-11-wireless] ssid=P | mac-address=<MAC address>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/P-503eac04-ebbe-46ea-91ba-5fc74852c852]] (600 root)
[connection] id=P | type=802-11-wireless | permissions=user:plabon_lab:;
[802-11-wireless] ssid=P | mac-address=<MAC address>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DHN_BB]] (600 root)
[connection] id=DHN_BB | type=802-11-wireless
[802-11-wireless] ssid=DHN_BB
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Xiaomi Mi4  1]] (600 root)
[connection] id=Xiaomi Mi4  1 | type=802-11-wireless
[802-11-wireless] ssid=Xiaomi Mi4 
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Dhaka (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth4      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth4      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/3.19.0-33-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.19.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


coretemp


coretemp


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
blacklist rt2800pci
blacklist rt2x00pci
blacklist rtrt2860
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


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


##### rc.local ##########################


echo X > /sys/class/backlight/intel_backlight/brightness


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth4' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"


##### dmesg #############################


[   16.941591] cdc_ether 3-1.2:1.0 eth0: register 'cdc_ether' at usb-0000:00:1a.0-1.2, CDC Ethernet Device, <MAC 'eth4' [IF]>
[   16.956628] cdc_ether 3-1.2:1.0 eth4: renamed from eth0
[   16.970657] systemd-udevd[422]: renamed network interface eth0 to eth4
[   26.574342] cdc_ether 3-1.2:1.0 eth4: kevent 12 may have been dropped (repeated 3 times)


########## wireless info END ############



```[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

---

