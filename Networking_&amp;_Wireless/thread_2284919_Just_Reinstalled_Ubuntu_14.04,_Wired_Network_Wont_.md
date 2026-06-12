---
title: "Just Reinstalled Ubuntu 14.04, Wired Network Wont Work (Ion Chip)"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by benharvey1985 on 2015-07-02
Hi, thanks for taking the time to look at my post, i have just fresh installed Ubuntu 14.04 on my system (having previously had another version installed as a HTPC solution)

My network card (wired) will not obtain an ip address and it keeps telling me the wired network has been disconnected.

Any help would be appreciated!


```


########## wireless info START ##########


Report from: 02 Jul 2015 10:39 BST +0100


Booted last: 02 Jul 2015 10:18 BST +0100


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
	Subsystem: ASRock Incorporation Device [1849:0ab0]
	Kernel driver in use: forcedeth


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


rt73usb                31602  0 
crc_itu_t              12707  1 rt73usb
rt2500usb              31447  0 
rt2x00usb              20742  2 rt73usb,rt2500usb
rt2x00lib              55307  3 rt73usb,rt2x00usb,rt2500usb
mac80211              652718  4 p54common,rt2x00lib,rt2x00usb,p54usb
mxm_wmi                13021  1 nouveau
cfg80211              494330  3 mac80211,p54common,rt2x00lib
wmi                    19193  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::92e6:baff:fe0d:4e9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3802 (3.8 KB)  TX bytes:5799 (5.7 KB)


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


root       717     1  0 10:18 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connecting


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


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


[[/etc/NetworkManager/system-connections/HRV Net]] (600 root)
[connection] id=HRV Net | type=802-11-wireless
[802-11-wireless] ssid=HRV Net | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


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


[rt73usb]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5E87676D58DF749133AFCC7
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2500usb]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
license:        GPL
description:    Ralink RT2500 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     42E3E7F229ED13A20C1A619
depends:        rt2x00lib,rt2x00usb
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     21417B97E30FD4E6E469E1F
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     71EFA3CA86D02D0528C49EE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D421794D4F30DF3A540FD24
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt73usb]
nohwcrypt: N


[rt2500usb]
nohwcrypt: N


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:0x0ab0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2500usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 1142.432051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 6 times)
[ 1155.805121] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 0 DMA timed out, invoke forced forced reset (repeated 45 times)
[ 1231.600061] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 2 times)
[ 1231.776101] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 0 DMA timed out, invoke forced forced reset
[ 1232.200050] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 4 times)
[ 1232.974242] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 0 DMA timed out, invoke forced forced reset
[ 1233.400048] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 2 times)
[ 1233.776115] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 0 DMA timed out, invoke forced forced reset
[ 1234.000063] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1235.812058] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 0 DMA timed out, invoke forced forced reset
[ 1235.988048] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 7 times)
[ 1237.914109] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 0 DMA timed out, invoke forced forced reset (repeated 10 times)
[ 1255.104139] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)


########## wireless info END ############



```

---

