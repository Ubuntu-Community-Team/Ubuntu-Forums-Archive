---
title: "no networking"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by webguy101 on 2015-08-19
i have a dell inspiron 640m just installed ubuntu 15.04  but the only way i can connect to a network is with a usb wifi adapter

neither Ethernet or wifi works

---

### Post by chili555 on 2015-08-19
Please see: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by webguy101 on 2015-08-19
it doesnt work

---

### Post by chili555 on 2015-08-19
> **webguy101 said:**
> It doesn't workIt didn't work because you have no internet connectivity, I assume. Please download the script on some other computer, transfer it on a USB stick or similar to the Ubuntu computer. Run it and then transfer the resulting output on the same USB stick so that you can post it here.

Somehow, we need diagnostics.

---

### Post by webguy101 on 2015-08-19
```
########## wireless info START ##########

Report from: 19 Aug 2015 18:26 EDT -0400

Booted last: 19 Aug 2015 17:48 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:45 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron E1405 [1028:01d8]

02:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

ath9k_htc              65536  0 
ath9k_common           32768  1 ath9k_htc
ath9k_hw              442368  2 ath9k_common,ath9k_htc
ath                    24576  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              626688  1 ath9k_htc
ssb                    57344  1 
wl                   6152192  1 
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
cfg80211              462848  5 wl,ath,ath9k_common,mac80211,ath9k_htc
wmi                    20480  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       559     1  0 17:51 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

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

[[/etc/NetworkManager/system-connections/WHA]] (600 root)
[connection] id=WHA | type=wifi
[wifi] ssid=WHA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     9FC596B0C1CEBEED9FFC60F
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ssb]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[wl]
filename:       /lib/modules/3.19.0-26-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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
blacklist b44
install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl ; modprobe --ignore-install b44

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  680.449803] ath: Country alpha2 being used: CN
[  680.449808] ath: Regpair used: 0x52
[  682.658476] wlan0: authenticate with <MAC address>
[  683.014123] wlan0: send auth to <MAC address> (try 1/3)
[  683.017542] wlan0: authenticated
[  683.020072] wlan0: associate with <MAC address> (try 1/3)
[  683.023546] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=4)
[  683.034141] wlan0: associated
[ 1256.736135] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1256.748076] ath: phy2: Failed to wakeup in 500us
[ 1256.850243] ath: phy2: RX failed to go idle in 10 ms RXSM=0x0
[ 1256.860397] ath: phy2: Failed to wakeup in 500us
[ 1256.962609] ath: phy2: RX failed to go idle in 10 ms RXSM=0x0
[ 1256.972871] ath: phy2: Failed to wakeup in 500us
[ 1257.075055] ath: phy2: RX failed to go idle in 10 ms RXSM=0x0
[ 1257.085110] ath: phy2: Failed to wakeup in 500us
[ 1257.188584] ath: phy2: RX failed to go idle in 10 ms RXSM=0x0
[ 1257.232301] usb 1-6: ath9k_htc: USB layer deinitialized
[ 1258.885864] usb 1-8: ath9k_htc: Firmware htc_9271.fw requested
[ 1259.171968] usb 1-8: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 1259.409788] ath9k_htc 1-8:1.0: ath9k_htc: HTC initialized with 33 credits
[ 1259.686734] ath9k_htc 1-8:1.0: ath9k_htc: FW Version: 1.3
[ 1259.686748] ath: EEPROM regdomain: 0x809c
[ 1259.686754] ath: EEPROM indicates we should expect a country code
[ 1259.686759] ath: doing EEPROM country->regdmn map search
[ 1259.686764] ath: country maps to regdmn code: 0x52
[ 1259.686770] ath: Country alpha2 being used: CN
[ 1259.686775] ath: Regpair used: 0x52
[ 1261.869715] wlan0: authenticate with <MAC address>
[ 1262.234136] wlan0: send auth to <MAC address> (try 1/3)
[ 1262.237702] wlan0: authenticated
[ 1262.240125] wlan0: associate with <MAC address> (try 1/3)
[ 1262.243651] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=4)
[ 1262.254026] wlan0: associated
[ 2243.096252] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2243.109670] ath: phy3: Failed to wakeup in 500us
[ 2243.211804] ath: phy3: RX failed to go idle in 10 ms RXSM=0x0
[ 2243.221964] ath: phy3: Failed to wakeup in 500us
[ 2243.324082] ath: phy3: RX failed to go idle in 10 ms RXSM=0x0 (repeated 2 times)
[ 2243.538720] ath: phy3: Failed to wakeup in 500us
[ 2243.642402] ath: phy3: RX failed to go idle in 10 ms RXSM=0x0
[ 2243.700379] usb 1-8: ath9k_htc: USB layer deinitialized

########## wireless info END ############
```

---

### Post by chili555 on 2015-08-19
You have had a USB wireless inserted at some point. Please set it aside as you won't be needing it. 

Please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe b44
```Your ethernet should now be working. Hook it up and continue:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Reboot and you should be all set.

---

