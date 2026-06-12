---
title: "After upgrading 14.04 LTS  wifi is working. It works for 2 day in 2 month."
date: 2015-04-02
forum: Networking &amp; Wireless
---

### Post by aig2 on 2015-04-02
HI, I have also ran Wireless_Script. Output is as below,

==============================
[FONT=Helvetica Neue, Helvetica, Arial, sans-serif] [/FONT]

########## wireless info START ##########


Report from: 03 Apr 2015 07:44 IST +0530


Booted last: 03 Apr 2015 00:00 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:3672]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1461]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 003: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k                  96159  0 
ath9k_common           31865  1 ath9k
ath9k_hw              438152  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              616571  1 ath9k
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
cfg80211              493859  4 ath,ath9k_common,ath9k,mac80211
ath3k                  13318  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
compat                 16281  5 cfg80211,ath9k_common,ath9k,mac80211,ath9k_hw
wmi                    19177  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e76:8aff:fed8:6fff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107482341 (107.4 MB)  TX bytes:3853815 (3.8 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search domain.name


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             125.99.61.254
    DNS:             116.72.253.254


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


[[/etc/NetworkManager/system-connections/prm]] (600 root)
[connection] id=prm | type=802-11-wireless
[802-11-wireless] ssid=prm | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/v8]] (600 root)
[connection] id=v8 | type=802-11-wireless
[802-11-wireless] ssid=v8 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/lab]] (600 root)
[connection] id=lab | type=802-11-wireless
[802-11-wireless] ssid=lab | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/d2BA6R1QtUzcyNjI]] (600 root)
[connection] id=d2BA6R1QtUzcyNjI | type=802-11-wireless
[802-11-wireless] ssid=d2BA6R1QtUzcyNjI | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/googlyduckxell]] (600 root)
[connection] id=googlyduckxell | type=802-11-wireless
[802-11-wireless] ssid=googlyduckxell | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=ninja-zone | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OpenWrt]] (600 root)
[connection] id=OpenWrt | type=802-11-wireless
[802-11-wireless] ssid=OpenWrt | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Belapurkar]] (600 root)
[connection] id=Belapurkar | type=802-11-wireless
[802-11-wireless] ssid=Belapurkar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Go_Away 1]] (600 root)
[connection] id=Go_Away 1 | type=802-11-wireless
[802-11-wireless] ssid=Go_Away | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hahaha]] (600 root)
[connection] id=Hahaha | type=802-11-wireless
[802-11-wireless] ssid=Hahaha | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SuperBeam]] (600 root)
[connection] id=SuperBeam | type=802-11-wireless
[802-11-wireless] ssid=SuperBeam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SPiDiGO]] (600 root)
[connection] id=SPiDiGO | type=802-11-wireless
[802-11-wireless] ssid=SPiDiGO | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Idea_wifi]] (600 root)
[connection] id=Idea_wifi | type=802-11-wireless
[802-11-wireless] ssid=Idea_wifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Hahaha 1]] (600 root)
[connection] id=Hahaha 1 | type=802-11-wireless
[802-11-wireless] ssid=Hahaha | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ENVIROVISION]] (600 root)
[connection] id=ENVIROVISION | type=802-11-wireless
[802-11-wireless] ssid=ENVIROVISION | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RoomWiFi]] (600 root)
[connection] id=RoomWiFi | type=802-11-wireless
[802-11-wireless] ssid=RoomWiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Go_Away]] (600 root)
[connection] id=Go_Away | type=802-11-wireless
[802-11-wireless] ssid=Go_Away | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ForBroadband_SMS_Idea_9623450000]] (600 root)
[connection] id=ForBroadband_SMS_Idea_9623450000 | type=802-11-wireless
[802-11-wireless] ssid=ForBroadband_SMS_Idea_9623450000 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/SuperBeam 1]] (600 root)
[connection] id=SuperBeam 1 | type=802-11-wireless
[802-11-wireless] ssid=SuperBeam | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Khedkar]] (600 root)
[connection] id=Khedkar | type=802-11-wireless
[802-11-wireless] ssid=Khedkar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/20094757]] (600 root)
[connection] id=20094757 | type=802-11-wireless
[802-11-wireless] ssid=20094757 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Idea-Smartwifi-ebcc]] (600 root)
[connection] id=Idea-Smartwifi-ebcc | type=802-11-wireless
[802-11-wireless] ssid=Idea-Smartwifi-ebcc | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     no frequency information.


##### iwlist scan #######################


sudo: unable to resolve host ninja-zone
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-40-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.19-rc1-0-g97bf6af) using backports v3.19-rc1-1-0-g74aaf28
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5B835C4CFC19CAED8B8C813
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-40-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.19-rc1-0-g97bf6af) using backports v3.19-rc1-1-0-g74aaf28
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     B63CB8A1E51BEE0D9132E16
depends:        compat,ath9k_hw,cfg80211,ath
vermagic:       3.13.0-40-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/3.13.0-40-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     632128CDCCF178F0ADAC851
depends:        compat,ath
vermagic:       3.13.0-40-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/3.13.0-40-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     B4CE181E520B1F0D81E3A58
depends:        cfg80211
vermagic:       3.13.0-40-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.13.0-40-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.19-rc1-0-g97bf6af) using backports v3.19-rc1-1-0-g74aaf28
srcversion:     160A70ED2B5AFA688D3BAD5
depends:        cfg80211,compat
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-40-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.19-rc1-0-g97bf6af) using backports v3.19-rc1-1-0-g74aaf28
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DE67EA5A07F19D3DD828D79
depends:        compat
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ath3k]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     661F5D1CDD236CFF7BE3FA5
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[   19.241630] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.243627] wl: disagrees about version of symbol wiphy_register
[   19.243629] wl: Unknown symbol wiphy_register (err -22)
[   19.243652] wl: Unknown symbol wiphy_new (err 0)
[   19.243699] wl: disagrees about version of symbol wiphy_unregister
[   19.243700] wl: Unknown symbol wiphy_unregister (err -22)
[   19.243715] wl: disagrees about version of symbol __ieee80211_get_channel
[   19.243716] wl: Unknown symbol __ieee80211_get_channel (err -22)
[   19.243755] wl: disagrees about version of symbol wiphy_free
[   19.243756] wl: Unknown symbol wiphy_free (err -22)
[   25.627564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############

---

