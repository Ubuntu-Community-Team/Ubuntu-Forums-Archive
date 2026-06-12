---
title: "No internet connection either wireless and wire"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by uberstig on 2016-05-14
My Acer 5755G with Ubuntu 14.04 LTS suddenly didn't have any connection. sudo ifconfig wlan0 up or eth0 up didn't work.

Can you help me?

Here's some info:


```
_Release (lsb_release -a): _
Distributor ID:           Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:          14.04
Codename:     trusty
 
 
_sudo lspci -v:_
 
Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
            Subsystem: Acer Incorporated [ALI] Device 0504
            Flags: bus master, fast devsel, latency 0, IRQ 16
            Memory at d1830000 (64-bit, prefetchable) [size=64K]
            Memory at d1840000 (64-bit, prefetchable) [size=64K]
            Expansion ROM at d1850000 [disabled] [size=2K]
            Capabilities: [48] Power Management version 3
            Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
            Capabilities: [a0] MSI-X: Enable- Count=5 Masked-
            Capabilities: [ac] Express Endpoint, MSI 00
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [13c] Device Serial Number 00-00-b8-70-f4-a0-1c-61
            Capabilities: [150] Power Budgeting <?>
            Capabilities: [160] Virtual Channel
            Kernel driver in use: tg3
 
SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10) (prog-if 01)
            Subsystem: Acer Incorporated [ALI] Device 0504
            Flags: bus master, fast devsel, latency 0, IRQ 17
            Memory at d1800000 (64-bit, prefetchable) [size=64K]
            Capabilities: [48] Power Management version 3
            Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit+
            Capabilities: [ac] Express Endpoint, MSI 00
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [150] Power Budgeting <?>
            Capabilities: [160] Virtual Channel
            Kernel driver in use: sdhci-pci
 
Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
            Subsystem: Foxconn International, Inc. T77H167.00
            Flags: bus master, fast devsel, latency 0, IRQ 17
            Memory at d1a00000 (64-bit, non-prefetchable) [size=64K]
            Capabilities: [40] Power Management version 3
            Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
            Capabilities: [60] Express Legacy Endpoint, MSI 00
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [140] Virtual Channel
            Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
            Capabilities: [170] Power Budgeting <?>
            Kernel driver in use: ath9k
 
 
 
_lsusb:_
 
Bus 002 Device 003: ID 0461:4d20 Primax Electronics, Ltd HP Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b23d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
 
 
_rfkill (rfkill list all):_
 
0: acer-wireless: Wireless LAN
            Soft blocked: no
            Hard blocked: no
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
 
 
_lsmod:_
 
 
 
_ifconfig:_
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228820 (228.8 KB)  TX bytes:228820 (228.8 KB)
 
vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.9.1  Bcast:172.16.9.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.181.1  Bcast:172.16.181.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
wlan0     Link encap:Ethernet  HWaddr cc:af:78:30:82:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 
_iwconfig_
 
vmnet8    no wireless extensions.
 
eth0      no wireless extensions.
 
lo        no wireless extensions.
 
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
         
vmnet1    no wireless extensions.
 
 
_route:_
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.9.0      *               255.255.255.0   U     0      0        0 vmnet1
172.16.181.0    *               255.255.255.0   U     0      0        0 vmnet8
 
 
_nm-tool:_
 
** (process:5040): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
 
NetworkManager Tool
 
State: unknown
 
 
** (process:5040): WARNING **: error: could not connect to NetworkManager
 
 
_NetworkManager.conf:_
 
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
 
[ifupdown]
managed=false
 
 
_etc/modprobe.d/blacklist.conf:_
 
blacklist evbug
 
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
 
# replaced by e100
blacklist eepro100
 
# replaced by tulip
blacklist de4x5
 
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
 
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
 
# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2
 
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
 
# replaced by p54pci
blacklist prism54
 
# replaced by b43 and ssb.
blacklist bcm43xx
 
 
_dmesg | grep -i eth0:_
 
[    2.070151] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM57785) rev 57785100] (PCI Express) MAC address b8:70:f4:a0:1c:61
[    2.070157] tg3 0000:02:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    2.070161] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.070164] tg3 0000:02:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[   28.831958] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.638091] init: network-interface (eth0) pre-start process (457) terminated with status 1
[   29.647539] init: network-interface (eth0) post-stop process (468) terminated with status 1
 
 
 
_dmesg | grep -i wlan0:_
 
[   29.691129] init: network-interface (wlan0) pre-start process (506) terminated with status 1
[   29.693866] init: network-interface (wlan0) post-stop process (511) terminated with status 1
[ 6407.790574] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6407.790848] bridge-wlan0: device is wireless, enabling SMAC
[ 6407.790851] bridge-wlan0: up
[ 6407.793531] bridge-wlan0: attached
[ 6407.793568] bridge-wlan0: disabling the bridge
[ 6407.806150] bridge-wlan0: down
[ 6407.806170] bridge-wlan0: detached

```


Very difficult to say what's the reason for this problem

---

### Post by jkeenan on 2016-05-14
Sounds like what happened to me today.  This explanation solved the problem:  [http://ubuntuforums.org/showthread.php?t=2324504](http://ubuntuforums.org/showthread.php?t=2324504)

---

### Post by wildmanne39 on 2016-05-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2016-05-14
Did this issue occur right after an upgrade?

Did you get this error message?
> The system network services are not compatible with this version
if not click on the wireless script in my signature and follow the directions for running the script without internet connection and post the file here.
Thanks

---

### Post by uberstig on 2016-05-15
Hi! 
I did an upgrade so that is implicated. Although I didn't get The system... error message. Btw the Networkmanager icon is also missing. The wireless-info.txt file:


[COLOR=#000000]```
[/COLOR]
########## wireless info START ##########


Report from: 15 May 2016 14:16 CEST +0200


Booted last: 14 May 2016 11:57 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-86-generic #130-Ubuntu SMP Mon Apr 18 18:27:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0504]
	Kernel driver in use: tg3


03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Foxconn International, Inc. T77H167.00 [105b:e034]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 003: ID 0461:4d20 Primax Electronics, Ltd HP Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b23d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


##### lsmod #############################


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              638915  1 ath9k
cfg80211              496328  3 ath,ath9k,mac80211
acer_wmi               32522  0 
mxm_wmi                13021  0 
sparse_keymap          13948  1 acer_wmi
video                  19476  2 i915,acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto wlan0
oface wlan0 inet dhcp


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:172.16.9.1  Bcast:172.16.9.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.181.1  Bcast:172.16.181.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet8' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


vmnet8    no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


vmnet1    no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.9.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.181.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager


Running:


	None found.


##### NetworkManager info ###############


** (process:7361): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files


** (process:7361): WARNING **: error: could not connect to NetworkManager


NetworkManager Tool


State: unknown


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


[[/etc/NetworkManager/system-connections/DRG-08FD]] (600 root)
[connection] id=DRG-08FD | type=802-11-wireless
[802-11-wireless] ssid=DRG-08FD | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Oslo (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


vmnet8    no frequency information.


eth0      no frequency information.


lo        no frequency information.


vmnet1    no frequency information.


wlan0     13 channels in total; available frequencies :
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


##### iwlist scan #######################


vmnet8    Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


vmnet1    Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1F2BE74683868C04A429DFF
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4D7E3FBEBDFF649364222B3
depends:        ath
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-86-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-86-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


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
blacklist nouveau
options nouveau modeset=0


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


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############
[COLOR=#000000]
```[/COLOR]



[COLOR=#000000][I]


[/I][/COLOR]

---

### Post by wildmanne39 on 2016-05-15
Hi, please follow the directions in post 2 of this link then report back.
[http://ubuntuforums.org/showthread.php?t=2324504](http://ubuntuforums.org/showthread.php?t=2324504)
Thanks

---

### Post by uberstig on 2016-05-15
Downgraded libnl* to 21*, but still no connection. Do you guys have any ideas?

---

### Post by wildmanne39 on 2016-05-15
Did you reboot afterwards? where there any errors while running commands? double check and make sure you ran all commands, then if it does not work click on the wireless script in my signature and post the info file created by it here in the forum using code tags.
Thanks

---

### Post by uberstig on 2016-05-15
Yes I rebooted and runned all the commands. The only change was the error message while booting: waiting for network configuration.

wireless-info-txt:

```




########## wireless info START ##########


Report from: 15 May 2016 22:44 CEST +0200


Booted last: 15 May 2016 20:15 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-86-generic #130-Ubuntu SMP Mon Apr 18 18:27:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3


03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. T77H167.00 [105b:e034]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 003: ID 0461:4d20 Primax Electronics, Ltd HP Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b23d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              638915  1 ath9k
cfg80211              496328  3 ath,ath9k,mac80211
acer_wmi               32522  0 
mxm_wmi                13021  0 
sparse_keymap          13948  1 acer_wmi
video                  19476  2 i915,acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto wlan0
oface wlan0 inet dhcp


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:172.16.9.1  Bcast:172.16.9.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.181.1  Bcast:172.16.181.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet8' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


vmnet8    no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


vmnet1    no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.9.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.181.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


    None found.


##### NetworkManager info ###############


** (process:3031): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files


** (process:3031): WARNING **: error: could not connect to NetworkManager


NetworkManager Tool


State: unknown


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


[[/etc/NetworkManager/system-connections/DRG-08FD]] (600 root)
[connection] id=DRG-08FD | type=802-11-wireless
[802-11-wireless] ssid=DRG-08FD | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Oslo (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


vmnet8    no frequency information.


eth0      no frequency information.


lo        no frequency information.


vmnet1    no frequency information.


wlan0     13 channels in total; available frequencies :
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


##### iwlist scan #######################


vmnet8    Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


vmnet1    Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1F2BE74683868C04A429DFF
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4D7E3FBEBDFF649364222B3
depends:        ath
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-86-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-86-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-86-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-86-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:32:2F:56:0D:D6:AB:64:F9:E4:23:E2:9D:46:B6:23:F4:AE:04:59
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


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
blacklist nouveau
options nouveau modeset=0


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


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   32.524424] init: networking pre-start process (719) terminated with status 1
[   32.527999] init: networking post-stop process (729) terminated with status 100
[  149.259766] init: networking pre-start process (1016) terminated with status 1
[  149.272855] init: networking post-stop process (1026) terminated with status 100
[  152.195974] init: network-interface (vmnet1) pre-start process (1248) terminated with status 1
[  152.199316] init: network-interface (vmnet1) post-stop process (1253) terminated with status 1
[  152.953569] init: network-interface (vmnet8) pre-start process (1281) terminated with status 1
[  152.957052] init: network-interface (vmnet8) post-stop process (1286) terminated with status 1


########## wireless info END ############




```

---

### Post by wildmanne39 on 2016-05-15
We need to clean up your interfaces file. Please do:
> gksu gedit /etc/network/interfaces
and remove everything but:
```

auto lo
iface lo inet loopback
```
save, close gedit and reboot.

You may have to install gksu first.

---

### Post by uberstig on 2016-05-16
It worked! I will not put anything on that interface-file anymore!

Thank you so much Wild Man! (and [COLOR=#000000]jkeenan[/COLOR])

---

