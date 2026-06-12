---
title: "Intel Corporation Pro/Wireless 3945ABG(Golan) not working after upgrading to Lubuntu"
date: 2015-02-17
forum: Networking &amp; Wireless
---

### Post by harshalkshatriya on 2015-02-17
Gathered Wireless info using wireless_script 



########## wireless info START ##########


Report from: 18 Feb 2015 10:21 IST +0530


Booted last: 17 Feb 2015 13:35 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: sky2


07:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135b]


08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)


##### lsusb #############################


Bus 002 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


##### lsmod #############################


hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
mac80211              484602  0 
cfg80211              430998  1 mac80211
compat                 13617  2 cfg80211,mac80211
wmi                    18673  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fef5:c7ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:167690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106955565 (106.9 MB)  TX bytes:15657260 (15.6 MB)
          Interrupt:17 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


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


[[/etc/NetworkManager/system-connections/ADHOC]] (600 root)
[connection] id=ADHOC | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=ADHOC | mac-address=<MAC address>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/IXUS255HS-791]] (600 root)
[connection] id=IXUS255HS-791 | type=802-11-wireless
[802-11-wireless] ssid=IXUS255HS-791 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dlink-EFB5]] (600 root)
[connection] id=dlink-EFB5 | type=802-11-wireless | permissions=user:fireandice:;
[802-11-wireless] ssid=dlink-EFB5 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/IXUS255HS-353]] (600 root)
[connection] id=IXUS255HS-353 | type=802-11-wireless
[802-11-wireless] ssid=IXUS255HS-353 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dlink-trial]] (600 root)
[connection] id=dlink-trial | type=802-11-wireless
[802-11-wireless] ssid=dlink-trial | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Dlink - Mazda]] (600 root)
[connection] id=Dlink - Mazda | type=802-11-wireless
[802-11-wireless] ssid=Dlink - Mazda | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=dlink | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


[mac80211]
filename:       /lib/modules/3.13.0-45-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
srcversion:     8DBA16EE557D6ADE9A75097
depends:        cfg80211,compat
vermagic:       3.13.0-45-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     67813FD63FE30A8DC22E6B7
depends:        compat
vermagic:       3.13.0-45-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4353 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  102.419242] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[  102.419252] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[  102.419305] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[  102.419310] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[  102.419325] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[  102.419330] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[  102.419348] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[  102.419352] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[  102.419369] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[  102.419373] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[  102.419400] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  102.419404] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[  102.419486] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[  102.419490] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[  102.419528] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[  102.419532] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[  775.289108] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[  775.289117] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[  775.289157] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[  775.289161] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[  775.289172] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[  775.289175] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[  775.289188] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[  775.289192] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[  775.289204] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[  775.289207] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[  775.289228] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  775.289231] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[  775.289292] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[  775.289295] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[  775.289324] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[  775.289327] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)


########## wireless info END ############

---

### Post by chili555 on 2015-02-18
The errors may suggest that you tried a different driver suite; either compat-wireless or backports or some such. We will probably need to remove it. Do you have anything you'd care to confess to Doc Chili under strict patient-doctor confidentiality??

May we see:```
modinfo iwl3945  | head -n4
```Thanks.

---

