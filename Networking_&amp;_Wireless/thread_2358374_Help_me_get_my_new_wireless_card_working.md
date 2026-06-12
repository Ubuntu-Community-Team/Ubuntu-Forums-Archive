---
title: "Help me get my new wireless card working"
date: 2017-04-12
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2017-04-12
***CHECK TO MAKE SURE YOU DO NOT HAVE A SWITCH TO TURN ON/OFF YOUR WIRELESS BEFORE GOING FURTHER***
TLDR: Wireless LAN was hard blocked. Googled pin 20 hack. Found [this]("http://forum.notebookreview.com/threads/acer-aspire-v5-122p-owners-thread.724071/page-59") which instructs to tape the 20th pin on the crad to block the on/off switch. This worked for me. After reading about this a bit, it seems this is the pin used to hardware block non-approved cards (maybe?), so this may work for you regardless of brand of card you have and your card is hard blocked but not soft blocked.

I bought [this wireless card]("https://www.amazon.com/gp/product/B00MV3N7UO/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1") on recommendation that it works in Ubuntu.
My laptop does boot and Ubuntu does recognize the card.
From dmesg:
```
[    4.188577] iwlwifi 0000:02:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    4.266323] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.266493] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[    4.266857] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[    4.266903] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[    4.660522] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
```

The laptop does not have a hardware or keyboard switch for the wifi.

Is this fixable through the software?

---

### Post by lsutiger on 2017-04-12
Searching on google I found [this thread.]("https://ubuntuforums.org/showthread.php?t=2334522")
Output from wireless-info:
```

########## wireless info START ##########

Report from: 12 Apr 2017 15:26 CDT -0500

Booted last: 12 Apr 2017 00:00 CDT -0500

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-72-generic #93-Ubuntu SMP Fri Mar 31 14:07:41 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Compiz)

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] NetLink BCM57785 Gigabit Ethernet PCIe [1025:0605]
	Kernel driver in use: tg3

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:c21c Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1625 Kingston Technology DataTraveler 101 II
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

##### lsmod #############################

acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  1 acer_wmi
video                  40960  1 acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0f0  Link encap:Ethernet  HWaddr <MAC 'enp1s0f0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:29224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2159284 (2.1 MB)  TX bytes:2159284 (2.1 MB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0f0  no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

	NetworkManager

Running:

root       861     1  0 13:31 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetLink BCM57785 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         <MAC 'enp1s0f0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/enp1s0f0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-72-generic
GENERAL.FIRMWARE-VERSION:               17.352738.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Affordable Upstairs]] (600 root)
[connection] id=Affordable Upstairs | type=wifi | permissions=user:complexity:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Affordable Upstairs
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tiga 1]] (600 root)
[connection] id=Tiga 1 | type=wifi | permissions=user:complexity:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tiga
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Tiga]] (600 root)
[connection] id=Tiga | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tiga
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR25]] (600 root)
[connection] id=NETGEAR25 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR25
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0f0  no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

enp1s0f0  Interface doesn't support scanning.

wlp2s0    Interface doesn't support scanning : Network is down

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-72-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     60ED6558F1225672289299A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-72-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-72-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     95AEC776A5F508489477F0E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-72-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-72-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     4116E844336D79483D28F6F
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-72-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-72-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A7DC879B6551813C20004F1
depends:        
intree:         Y
vermagic:       4.4.0-72-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 1213.665834] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 1213.666370] IPv6: ADDRCONF(NETDEV_UP): enp1s0f0: link is not ready (repeated 2 times)

########## wireless info END ############

```

---

### Post by jeremy31 on 2017-04-12
*Thread moved to **Networking & Wireless**.*

I don't like this from your script results
```
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```

I would check BIOS settings to see if WLAN is enabled and check the computer for a physical switch to enable wifi.  I have a couple Intel 7260 wifi cards that haven't caused any issues like this

---

### Post by lsutiger on 2017-04-12
Blacklisted acer-wmi in /etc/modprobe.d/blacklist.conf, but that did not help.

---

### Post by lsutiger on 2017-04-12
> **jeremy31 said:**
> *Thread moved to **Networking & Wireless**.*

I don't like this from your script results
```
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```

I would check BIOS settings to see if WLAN is enabled and check the computer for a physical switch to enable wifi.  I have a couple Intel 7260 wifi cards that haven't caused any issues like this

Thanks for your reply.
There is nothing in BIOS for WLAN/Wireless/Network other than Network Boot. I am 100% positive that there is not hardware switch or keyboard switch on the computer for wireless.
There is a keyboard switch for bluetooth. When I press that key I get a message:
atkbd serio0:unknown key pressed

---

### Post by lsutiger on 2017-04-12
PS - the item in question is the Acer 5560-7414 in my signature

---

### Post by lsutiger on 2017-04-12
PS - the item in question is the Acer 5560-7414 in my signature
Googling a little more there is a physical 'hack' to cover pin 20 on this card. May try that

---

### Post by chili555 on 2017-04-12
Is this your laptop? [http://tim.id.au/laptops/acer/aspire%205540%205560.pdf](http://tim.id.au/laptops/acer/aspire%205540%205560.pdf)

Please see page 14.

---

### Post by lsutiger on 2017-04-12
> **chili555 said:**
> Is this your laptop? [http://tim.id.au/laptops/acer/aspire%205540%205560.pdf](http://tim.id.au/laptops/acer/aspire%205540%205560.pdf)

Please see page 14.
Thanks for the effort! That is not my laptop. All I have is an SD card reader in front.
I am happy to report that I am currently on my 5GHz wireless from my new Intel 7260 card. The pin 20 hack worked!

---

