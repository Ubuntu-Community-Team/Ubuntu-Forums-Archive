---
title: "my wireless network driver doesn't work"
date: 2016-08-29
forum: Networking &amp; Wireless
---

### Post by gwh2 on 2016-08-29
Friends,
I'm new to ubuntu and my ubuntu wireless is very unstable. About 10% of the whole time connection is successful, while the other majority isn't. It seemed to be the driver problem and I tried modprobe command which didn't work. 
Here is the information of my wireless.
Any suggestion?

```



########## wireless info START ##########


Report from: 30 Aug 2016 11:20 CST +0800


Booted last: 30 Aug 2016 11:11 CST +0800


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-95-generic #142-Ubuntu SMP Fri Aug 12 17:00:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
	Kernel driver in use: e1000e


04:01.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)
	Subsystem: Qualcomm Atheros Device [168c:0300]


##### lsusb #############################


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 03f0:0324 Hewlett-Packard SK-2885 keyboard
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              638901  1 ath9k
cfg80211              496328  3 ath,ath9k,mac80211
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
video                  19476  1 asus_wmi
wmi                    19177  2 mxm_wmi,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7f00000-f7f20000 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager


Running:


root       804     1  0 11:11 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


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


no-auto-default=<MAC 'eth0' [IF1]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/RAQDT 1]] (600 root)
[connection] id=RAQDT 1 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=RAQDT | mac-address=<MAC address>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RAQDT]] (600 root)
[connection] id=RAQDT | type=802-11-wireless
[802-11-wireless] ssid=RAQDT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wireless PKU]] (600 root)
[connection] id=Wireless PKU | type=802-11-wireless
[802-11-wireless] ssid=Wireless PKU | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Asia/Shanghai (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-95-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1F2BE74683868C04A429DFF
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        51:D5:D7:73:F1:07:BA:1B:C0:9D:33:68:38:C4:3C:DE:74:9E:4E:05
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-95-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        51:D5:D7:73:F1:07:BA:1B:C0:9D:33:68:38:C4:3C:DE:74:9E:4E:05
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-95-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4D7E3FBEBDFF649364222B3
depends:        ath
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        51:D5:D7:73:F1:07:BA:1B:C0:9D:33:68:38:C4:3C:DE:74:9E:4E:05
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-95-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        51:D5:D7:73:F1:07:BA:1B:C0:9D:33:68:38:C4:3C:DE:74:9E:4E:05
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-95-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        51:D5:D7:73:F1:07:BA:1B:C0:9D:33:68:38:C4:3C:DE:74:9E:4E:05
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-95-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        51:D5:D7:73:F1:07:BA:1B:C0:9D:33:68:38:C4:3C:DE:74:9E:4E:05
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
# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002d (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   14.394065] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[  234.381595] ath9k: ath9k: Driver unloaded
[  241.650210] ath: phy0: address test failed addr: 0x00008000 - wr:0x00040004 != rd:0x00000004
[  241.650212] ath: phy0: Unable to initialize hardware; initialization status: -19
[  241.650214] ath9k 0000:04:01.0: Failed to initialize device


########## wireless info END ############



```

---

### Post by chili555 on 2016-08-30
> [  241.650210] ath: phy0: address test failed addr: 0x00008000 - wr:0x00040004 != rd:0x00000004
[  241.650212] ath: phy0: Unable to initialize hardware; initialization status: -19
[  241.650214] ath9k 0000:04:01.0: Failed to initialize deviceThis sounds like a hardware problem. I suspect that the device is either not quite completely seated in its slot or that it is near to failure. 

If you are handy and confident, you might download the service manual for your laptop and, utilizing all the safety procedures it lists, look into reseating or replacing the device.

Of course, you could blacklist the driver for the internal and get an inexpensive USB wireless.

---

### Post by gwh2 on 2016-08-30
Yeah, that sounds reasonable. I will have a try, on this old desktop computer in my research group. (shaking my head with a forced smile) 
Thanks for replying.

---

