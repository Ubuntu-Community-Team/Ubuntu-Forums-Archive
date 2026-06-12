---
title: "Acer C720 Chromebook Wifi Disconnects, Ubuntu 14.04"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by dave170 on 2015-03-01
Hi all,

I've been running Ubuntu on my Chromebook for the past week without any issues, but now I'm entirely unable to connect to my router. Any attempt to connect to the wifi, results in it coming up saying "Disconnected - you are now offline". I have no ethernet port, so cannot get any internet connection working anymore. I've run the wireless script, and the results are below.

Thanks in advance for any help.

```


########## wireless info START ##########


Report from: 01 Mar 2015 20:25 GMT +0000


Booted last: 01 Mar 2015 20:20 GMT +0000


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.17.1-031701-generic #201410150735 SMP Wed Oct 15 11:57:55 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e058]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 003: ID 0489:e056 Foxconn / Hon Hai 
Bus 002 Device 002: ID 1bcf:2c67 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k                 137329  0 
ath9k_common           20782  1 ath9k
ath9k_hw              439370  2 ath9k_common,ath9k
ath                    24509  3 ath9k_common,ath9k,ath9k_hw
mac80211              593625  1 ath9k
ath3k                  13165  0 
cfg80211              434807  4 ath,ath9k_common,ath9k,mac80211
bluetooth             420517  23 bnep,ath3k,btusb,rfcomm


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


** (process:2507): WARNING **: error: cannot retrieve connection: uid 1001 has no permission to perform this operation


** (process:2507): WARNING **: error: cannot retrieve connection: uid 1001 has no permission to perform this operation


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    BTHub5-F562:     Infra, <MAC 'BTHub5-F562' [AN1]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 54 WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN2]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2 Enterprise
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2 Enterprise
    TALKTALK-68691C: Infra, <MAC 'TALKTALK-68691C' [AN4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    SKYB0A2D:        Infra, <MAC 'SKYB0A2D' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2
    SKYE75D3:        Infra, <MAC 'SKYE75D3' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    SKY300F2:        Infra, <MAC 'SKY300F2' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    SKYE79CD:        Infra, <MAC 'SKYE79CD' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    BTHub3-5MQG:     Infra, <MAC 'BTHub3-5MQG' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    SKYD1577:        Infra, <MAC 'SKYD1577' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    SKY1841E:        Infra, <MAC 'SKY1841E' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    SKY62D99:        Infra, <MAC 'SKY62D99' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BTHub4-S5H7:     Infra, <MAC 'BTHub4-S5H7' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    SKYFE998:        Infra, <MAC 'SKYFE998' [AN14]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN15]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 52
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    BTWiFi-with-FON: Infra, <MAC 'BTWiFi-with-FON' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 2
    BTHub4-85JS:     Infra, <MAC 'BTHub4-85JS' [AN19]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 19 WPA2
    BTHub4-85JS:     Infra, <MAC 'BTHub4-85JS' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BTHub5-F562:     Infra, <MAC 'BTHub5-F562' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA2


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


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BTHub5-6F2Z]] (600 root)
[connection] id=BTHub5-6F2Z | type=802-11-wireless
[802-11-wireless] ssid=BTHub5-6F2Z | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RETAIL_PARK]] (600 root)
[connection] id=RETAIL_PARK | type=802-11-wireless
[802-11-wireless] ssid=RETAIL_PARK | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SHU-USS]] (600 root)
[ipv6] method=auto
[connection] id=SHU-USS | type=802-11-wireless
[802-11-wireless] ssid=SHU-USS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BTWifi-with-FON]] (600 root)
[connection] id=BTWifi-with-FON | type=802-11-wireless
[802-11-wireless] ssid=BTWifi-with-FON | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/hotspot1]] (600 root)
[connection] id=hotspot1 | type=802-11-wireless
[802-11-wireless] ssid=hotspot1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Premier Inn]] (600 root)
[connection] id=Premier Inn | type=802-11-wireless
[802-11-wireless] ssid=Premier Inn | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TamperGuest]] (600 root)
[connection] id=TamperGuest | type=802-11-wireless
[802-11-wireless] ssid=TamperGuest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ASK4 Wireless]] (600 root)
[connection] id=ASK4 Wireless | type=802-11-wireless
[802-11-wireless] ssid=ASK4 Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/hotspot]] (600 root)
[connection] id=hotspot | type=802-11-wireless
[802-11-wireless] ssid=hotspot | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BTHub5-F562]] (600 root)
[connection] id=BTHub5-F562 | type=802-11-wireless
[802-11-wireless] ssid=BTHub5-F562 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/weldrake13.5Ghz]] (600 root)
[connection] id=weldrake13.5Ghz | type=802-11-wireless
[802-11-wireless] ssid=weldrake13.5Ghz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/#ladsladslads]] (600 root)
[connection] id=#ladsladslads | type=802-11-wireless
[802-11-wireless] ssid=#ladsladslads | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AW-GR520]] (600 root)
[connection] id=AW-GR520 | type=802-11-wireless
[802-11-wireless] ssid=AW-GR520 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/home1]] (600 root)
[connection] id=home1 | type=802-11-wireless
[802-11-wireless] ssid=home1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/McDonald's Free WiFi]] (600 root)
[connection] id=McDonald's Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=McDonald's Free WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz


##### iwlist scan #######################


wlan0     Failed to read scan data : Resource temporarily unavailable


lo        Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.17.1-031701-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     40EDC25D9BA894EB68105B1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.17.1-031701-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9A:41:23:B5:35:99:4F:C4:FF:B3:36:3E:7C:9E:A3:62:0C:01:CB:15
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.17.1-031701-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     64198F81A3D3DC3B5C957E6
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.17.1-031701-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9A:41:23:B5:35:99:4F:C4:FF:B3:36:3E:7C:9E:A3:62:0C:01:CB:15
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.17.1-031701-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     ABDFA7E8340C5343C205A98
depends:        ath
intree:         Y
vermagic:       3.17.1-031701-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9A:41:23:B5:35:99:4F:C4:FF:B3:36:3E:7C:9E:A3:62:0C:01:CB:15
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.17.1-031701-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0AB7275A823E46D904ED4C7
depends:        cfg80211
intree:         Y
vermagic:       3.17.1-031701-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9A:41:23:B5:35:99:4F:C4:FF:B3:36:3E:7C:9E:A3:62:0C:01:CB:15
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.17.1-031701-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     50BFD5A22F2717F72E28E1A
depends:        cfg80211
intree:         Y
vermagic:       3.17.1-031701-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9A:41:23:B5:35:99:4F:C4:FF:B3:36:3E:7C:9E:A3:62:0C:01:CB:15
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ath3k]
filename:       /lib/modules/3.17.1-031701-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     9CB3FB381F873BAD63648E5
depends:        bluetooth
intree:         Y
vermagic:       3.17.1-031701-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9A:41:23:B5:35:99:4F:C4:FF:B3:36:3E:7C:9E:A3:62:0C:01:CB:15
sig_hashalgo:   sha512


[cfg80211]
filename:       /lib/modules/3.17.1-031701-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A189C096E57D9F63A205933
depends:        
intree:         Y
vermagic:       3.17.1-031701-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9A:41:23:B5:35:99:4F:C4:FF:B3:36:3E:7C:9E:A3:62:0C:01:CB:15
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


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


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   12.297938] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.181900] wlan0: authenticate with <MAC 'BTHub5-F562' [AN1]>
[   19.194677] wlan0: direct probe to <MAC 'BTHub5-F562' [AN1]> (try 1/3)
[   19.396766] wlan0: direct probe to <MAC 'BTHub5-F562' [AN1]> (try 2/3)
[   19.600690] wlan0: direct probe to <MAC 'BTHub5-F562' [AN1]> (try 3/3)
[   19.804635] wlan0: authentication with <MAC 'BTHub5-F562' [AN1]> timed out


########## wireless info END ############



```

---

### Post by jeremy31 on 2015-03-01
If you can access your router settings, see if it is set for WPA2 only and not a WPA2 mixed mode as Linux doesn't fair well with the mixed modes

---

### Post by dave170 on 2015-03-02
I've checked and the router is set to be WPA2 only. Weirdly I booted up this morning, and it's connecting fine again.

---

### Post by jeremy31 on 2015-03-02
If it happens again, you might want to change the channel your access point is on.  At the time the script was run, there was an access point on the same channel that was stronger than yours

---

