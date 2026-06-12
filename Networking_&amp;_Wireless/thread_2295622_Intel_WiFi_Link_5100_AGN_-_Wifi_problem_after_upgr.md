---
title: "Intel WiFi Link 5100 AGN - Wifi problem after upgrade 14.10 to 15.04"
date: 2015-09-20
forum: Networking &amp; Wireless
---

### Post by Jakub_Kitaj on 2015-09-20
After upgrade from Ubuntu 14.10 to 15.04 i have some problem with my wifi. I don't see option with wireless network on menu bar.There is report from wireless-info script [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) :


```
########## wireless info START ##########

Report from: 19 Sep 2015 19:08 CEST +0200
Booted last: 19 Sep 2015 16:04 CEST +0200
Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:   vivid

##### kernel ############################

Linux 3.2.0-70-generic #105-Ubuntu SMP Wed Sep 24 19:49:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
Kernel modules: iwlwifi

06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
Subsystem: Samsung Electronics Co Ltd Device [144d:c04a]
Kernel driver in use: sky2

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:c302 Z-Star Microelectronics Corp. Vega USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
Soft blocked: yes
Hard blocked: no

##### lsmod #############################

iwlwifi               401083  0 
mac80211              506862  1 iwlwifi
cfg80211              205774  2 mac80211,iwlwifi
mxm_wmi                13021  1 nouveau
wmi                    19256  1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
      Interrupt:19 

##### iwconfig ##########################

lo        no wireless extensions.
eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

NetworkManager

Running:

root       578     1  0 16:05 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8055 PCI-E Gigabit Ethernet   Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:06:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

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

[[/etc/NetworkManager/system-connections/Hot-Spot Bulwar]] (600 root)
[connection] id=Hot-Spot Bulwar | type=802-11-wireless
[802-11-wireless] ssid=Hot-Spot Bulwar | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WRS_EiTI]] (600 root)
[connection] id=WRS_EiTI | type=802-11-wireless
[802-11-wireless] ssid=WRS_EiTI | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/L70]] (600 root)
[connection] id=L70 | type=802-11-wireless
[802-11-wireless] ssid=L70 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Warsaw (based on set time zone)

country 00: DFS-UNSET
(2402 - 2472 @ 40), (N/A, 20), (N/A)
(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
(5250 - 5330 @ 80), (N/A, 20), (N/A), DFS, NO-IR
(5490 - 5730 @ 160), (N/A, 20), (N/A), DFS, NO-IR
(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.
eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

##### module infos ######################

[iwlwifi]
filename:       /lib/modules/3.2.0-70-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     AF0D27A3E5369F7401307D5
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-70-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)

[mac80211]
filename:       /lib/modules/3.2.0-70-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1944D882391CC5F32CA6325
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-70-generic SMP mod_unload modversions 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[cfg80211]
filename:       /lib/modules/3.2.0-70-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A289A224DC04F871A44431D
depends:        
intree:         Y
vermagic:       3.2.0-70-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlwifi]
11n_disable: 0
ack_check: N
amsdu_size_8K: 1
antenna_coupling: 0
auto_agg: Y
bt_ch_inhibition: Y
bt_coex_active: Y
fw_restart: 1
led_mode: 0
no_sleep_autoadjust: Y
plcp_check: Y
power_level: 0
power_save: N
queues_num: 0
swcrypto: 0
ucode_alternative: 1
wd_disable: 0

[mac80211]
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

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.3/0000:06:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg | grep iwlwifi #############################

[   62.144763] iwlwifi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   62.144896] iwlwifi 0000:02:00.0: setting latency timer to 64
[   62.144951] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   62.144953] iwlwifi 0000:02:00.0: pci_resource_base = ffffc90000658000
[   62.144956] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   62.145823] iwlwifi 0000:02:00.0: irq 46 for MSI/MSI-X
[   62.146092] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   62.146577] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   62.175234] iwlwifi 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   62.175237] iwlwifi 0000:02:00.0: Device SKU: 0Xf0
[   62.207045] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   62.506823] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-5.ucode' failed.
[   62.527136] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-4.ucode' failed.
[   62.531093] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-3.ucode' failed.
[   62.532054] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-2.ucode' failed.
[   62.532825] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-1.ucode' failed.
[   62.532829] iwlwifi 0000:02:00.0: no suitable firmware found!
[   62.533051] iwlwifi 0000:02:00.0: PCI INT A disabled

########## wireless info END ############



ls /lib/firmware/ | grep iwlwifi

iwlwifi-1000-5.ucode
iwlwifi-100-5.ucode
iwlwifi-105-6.ucode
iwlwifi-135-6.ucode
iwlwifi-2000-6.ucode
iwlwifi-2030-6.ucode
iwlwifi-3160-10.ucode
iwlwifi-3160-12.ucode
iwlwifi-3160-13.ucode
iwlwifi-3160-7.ucode
iwlwifi-3160-8.ucode
iwlwifi-3160-9.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2a-6.ucode
iwlwifi-6000g2b-6.ucode
iwlwifi-6050-5.ucode
iwlwifi-7260-10.ucode
iwlwifi-7260-12.ucode
iwlwifi-7260-13.ucode
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode
iwlwifi-7260-9.ucode
iwlwifi-7265-10.ucode
iwlwifi-7265-12.ucode
iwlwifi-7265-13.ucode
iwlwifi-7265-8.ucode
iwlwifi-7265-9.ucode
iwlwifi-7265D-10.ucode
iwlwifi-7265D-12.ucode
iwlwifi-7265D-13.ucode
iwlwifi-8000C-13.ucode
```

---

### Post by chili555 on 2015-09-20
The driver is looking for firmware:> [   62.506823] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-5000-5.ucode' failed.But you seem to *have* the firmware:> iwlwifi-5000-5.ucodeI wonder if the permissions are correct:```
ls -al /lib/firmware | grep iwlwifi-5000
```We hope we see:```
[COLOR="#FF0000"]-rw-r--r--  1 root root [/COLOR] 340696 Jul 29 08:57 iwlwifi-5000-5.ucode

```In human words, owned by root and readable by all. If not, correct it:```
sudo chmod +r /lib/firmware/iwlwifi*
```Reboot and check the log:```
dmesg | grep iwl
```

---

### Post by Jakub_Kitaj on 2015-09-20
I checked permissions for iwlwifi-5000-5.ucode file, and I have: 

```
[COLOR=#FF0000]-rw-r--r--  1 root root [/COLOR] 340696 Jul 29 08:57 iwlwifi-5000-5.ucode
```

so anybody can read it.

:(

---

### Post by Jakub_Kitaj on 2015-09-22
What else can I do? Can somebody help me, please?

---

### Post by chili555 on 2015-09-22
Would you please try:```
echo iwlwifi  >>  /etc/modules
```And with a temporary connection by ethernet or otherwise:```
sudo apt-get install --reinstall linux-firmware
```Reboot.

---

### Post by Jakub_Kitaj on 2015-09-22
[FONT=arial]I made what you write. [/FONT]

To do this operation
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install --reinstall linux-firmware[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[FONT=arial]I don't not need internet connection - this not make any request to internet, this only get installed package, remove it and install again.

Unfortunatly this not resolve problem, I can't still connect to wifi.[/FONT][/FONT][/COLOR]

---

### Post by Jakub_Kitaj on 2015-09-22
Ok, I found what is problem.

It turned out, that I don't have corect version of kernel. I [COLOR=#111111][FONT=Ubuntu]have a wrong kernel 3.2. In 15.04 it should be 3.19.

For more info look here [http://askubuntu.com/questions/676000/wifi-problem-after-upgrade-14-10-to-15-04](http://askubuntu.com/questions/676000/wifi-problem-after-upgrade-14-10-to-15-04)


@chili555 - thank you for your help :)
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

---

