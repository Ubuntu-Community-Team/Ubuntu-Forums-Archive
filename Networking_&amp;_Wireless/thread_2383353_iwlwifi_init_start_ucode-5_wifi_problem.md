---
title: "iwlwifi init start ucode-5 wifi problem"
date: 2018-01-23
forum: Networking &amp; Wireless
---

### Post by aif1 on 2018-01-23
Hi. I recently attempted to upgrade from 14.04 to 16 but somehow the version remains at 14.04 after updating.  Coincidentally the wifi button (acer laptop) stopped working after that. Upon reading various threads, and tested many random things, wifi is still not working. Yesterday, i updated ubuntu again, but no luck.
Also, after so many reboots, sometimes a black screen appeared for long time showing hundreds of rapid lines on iwlwifi not working or error. However, when i pressed the wifi button during this black screen, those lines will stop and boot the laptop into the purple splash screen and eventually into login screen. 
 I very much appreciate any help on this please. 
 Below are the wireless info text, hopefully i do the codes right :
```


########## wireless info START ##########

Report from: 23 Jan 2018 11:57 +08 +0800

Booted last: 23 Jan 2018 07:22 +08 +0800

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-137-generic #186-Ubuntu SMP Mon Dec 4 19:09:19 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: loop=/ubuntu/disks/root.disk, rw, rootflags=sync, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
	Kernel driver in use: iwlwifi

05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:0260]
	Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

##### lsmod #############################

iwldvm                236381  0 
mac80211              638901  1 iwldvm
iwlwifi               174028  1 iwldvm
cfg80211              496328  3 iwlwifi,mac80211,iwldvm
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  0 
video                  19476  2 i915,acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.133  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41226 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:73614831 (73.6 MB)  TX bytes:3961876 (3.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:71426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5830841 (5.8 MB)  TX bytes:5830841 (5.8 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       842     1  0 07:22 ?        00:00:16 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.133
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             192.168.100.3

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AndroidAP9355 AI]] (600 root)
[connection] id=AndroidAP9355 AI | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP9355 AI | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAzT]] (600 root)
[connection] id=AndroidAzT | type=802-11-wireless
[802-11-wireless] ssid=AndroidAzT | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAzJ3 1]] (600 root)
[connection] id=AndroidAzJ3 1 | type=802-11-wireless
[802-11-wireless] ssid=AndroidAzJ3 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP 1]] (600 root)
[connection] id=AndroidAP 1 | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SumbanganLagendaSdnBhd]] (600 root)
[connection] id=SumbanganLagendaSdnBhd | type=802-11-wireless
[802-11-wireless] ssid=SumbanganLagendaSdnBhd | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAzJ3a 1]] (600 root)
[connection] id=AndroidAzJ3a 1 | type=802-11-wireless
[802-11-wireless] ssid=AndroidAzJ3a | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SKY489A3]] (600 root)
[connection] id=SKY489A3 | type=802-11-wireless
[802-11-wireless] ssid=SKY489A3 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAzJ3a]] (600 root)
[connection] id=AndroidAzJ3a | type=802-11-wireless
[802-11-wireless] ssid=AndroidAzJ3a | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/AndroidAz]] (600 root)
[connection] id=AndroidAz | type=802-11-wireless
[802-11-wireless] ssid=AndroidAz | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAzJ3]] (600 root)
[connection] id=AndroidAzJ3 | type=802-11-wireless
[802-11-wireless] ssid=AndroidAzJ3 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Aztech8800(2.4GHz)-7F99]] (600 root)
[connection] id=Aztech8800(2.4GHz)-7F99 | type=802-11-wireless
[802-11-wireless] ssid=Aztech8800(2.4GHz)-7F99 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/EM London]] (600 root)
[connection] id=EM London | type=802-11-wireless
[802-11-wireless] ssid=EM London | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/sarah]] (600 root)
[connection] id=sarah | type=802-11-wireless
[802-11-wireless] ssid=sarah | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Asia/Kuala_Lumpur (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-137-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9036600D780304CB32B6EF2
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-137-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:08:22:C0:B4:94:28:C1:D9:1D:26:5D:12:34:02:60:C6:1C:89:08
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-137-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-137-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:08:22:C0:B4:94:28:C1:D9:1D:26:5D:12:34:02:60:C6:1C:89:08
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-137-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     F935FAF50D9A6B3215203C9
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-137-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:08:22:C0:B4:94:28:C1:D9:1D:26:5D:12:34:02:60:C6:1C:89:08
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-137-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-137-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:08:22:C0:B4:94:28:C1:D9:1D:26:5D:12:34:02:60:C6:1C:89:08
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 1
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

loop
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

[/etc/modprobe.d/Centrino.conf]
options Centrino fwlps=N

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[14348.229000] iwlwifi 0000:04:00.0: 0x00000000 | l2p_mhvalid
[14348.229003] iwlwifi 0000:04:00.0: 0x00100040 | l2p_addr_match
[14348.229005] iwlwifi 0000:04:00.0: 0x00000007 | lmpm_pmg_sel
[14348.229007] iwlwifi 0000:04:00.0: 0x00000000 | timestamp
[14348.229010] iwlwifi 0000:04:00.0: 0x0000F808 | flow_handler
[14348.229073] iwlwifi 0000:04:00.0: Start IWL Event Log Dump: display last 3 entries
[14348.229094] iwlwifi 0000:04:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14348.229108] iwlwifi 0000:04:00.0: EVT_LOGT:0000000021:0x00000000:1208
[14348.229121] iwlwifi 0000:04:00.0: EVT_LOGT:0000000302:0x00000000:0125
[14348.229132] iwlwifi 0000:04:00.0: BUG_ON, Stop restarting
[14348.229484] iwlwifi 0000:04:00.0: Failed to run INIT ucode: -5
[14348.229588] iwlwifi 0000:04:00.0: Unable to initialize device.
[14348.232892] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[14348.248063] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[14348.255472] iwlwifi 0000:04:00.0: Microcode SW error detected.  Restarting 0x82000000.
[14348.255479] iwlwifi 0000:04:00.0: CSR values:
[14348.255482] iwlwifi 0000:04:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[14348.255489] iwlwifi 0000:04:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c8330c
[14348.255495] iwlwifi 0000:04:00.0:          CSR_INT_COALESCING: 0X00000040
[14348.255502] iwlwifi 0000:04:00.0:                     CSR_INT: 0X80000000
[14348.255508] iwlwifi 0000:04:00.0:                CSR_INT_MASK: 0X00000000
[14348.255515] iwlwifi 0000:04:00.0:           CSR_FH_INT_STATUS: 0X40010000
[14348.255521] iwlwifi 0000:04:00.0:                 CSR_GPIO_IN: 0X00000000
[14348.255527] iwlwifi 0000:04:00.0:                   CSR_RESET: 0X00000000
[14348.255534] iwlwifi 0000:04:00.0:                CSR_GP_CNTRL: 0X080403c5
[14348.255540] iwlwifi 0000:04:00.0:                  CSR_HW_REV: 0X0000006c
[14348.255547] iwlwifi 0000:04:00.0:              CSR_EEPROM_REG: 0X00000000
[14348.255553] iwlwifi 0000:04:00.0:               CSR_EEPROM_GP: 0X90000001
[14348.255560] iwlwifi 0000:04:00.0:              CSR_OTP_GP_REG: 0X00030001
[14348.255566] iwlwifi 0000:04:00.0:                 CSR_GIO_REG: 0X00080046
[14348.255573] iwlwifi 0000:04:00.0:            CSR_GP_UCODE_REG: 0X00000000
[14348.255579] iwlwifi 0000:04:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[14348.255585] iwlwifi 0000:04:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[14348.255591] iwlwifi 0000:04:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[14348.255598] iwlwifi 0000:04:00.0:                 CSR_LED_REG: 0X00000018
[14348.255604] iwlwifi 0000:04:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[14348.255610] iwlwifi 0000:04:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[14348.255617] iwlwifi 0000:04:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[14348.255623] iwlwifi 0000:04:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[14348.255630] iwlwifi 0000:04:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[14348.255632] iwlwifi 0000:04:00.0: FH register values:
[14348.255650] iwlwifi 0000:04:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X1271f700
[14348.255666] iwlwifi 0000:04:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01272de0
[14348.255683] iwlwifi 0000:04:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[14348.255700] iwlwifi 0000:04:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[14348.255717] iwlwifi 0000:04:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[14348.255734] iwlwifi 0000:04:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[14348.255751] iwlwifi 0000:04:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[14348.255768] iwlwifi 0000:04:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[14348.255784] iwlwifi 0000:04:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[14348.255788] iwlwifi 0000:04:00.0: Loaded firmware version: 39.31.5.1 build 35138
[14348.255928] iwlwifi 0000:04:00.0: Start IWL Error Log Dump:
[14348.255931] iwlwifi 0000:04:00.0: Status: 0x00000400, count: 5
[14348.255934] iwlwifi 0000:04:00.0: 0x00000005 | SYSASSERT                   
[14348.255936] iwlwifi 0000:04:00.0: 0x00004CB0 | uPc
[14348.255939] iwlwifi 0000:04:00.0: 0x00004C1E | branchlink1
[14348.255941] iwlwifi 0000:04:00.0: 0x00004C1E | branchlink2
[14348.255944] iwlwifi 0000:04:00.0: 0x00000000 | interruptlink1
[14348.255946] iwlwifi 0000:04:00.0: 0x00000000 | interruptlink2
[14348.255948] iwlwifi 0000:04:00.0: 0x000000FE | data1
[14348.255950] iwlwifi 0000:04:00.0: 0x00000000 | data2
[14348.255952] iwlwifi 0000:04:00.0: 0x0000016A | line
[14348.255955] iwlwifi 0000:04:00.0: 0x00018ED7 | beacon time
[14348.255957] iwlwifi 0000:04:00.0: 0x00000129 | tsf low
[14348.255959] iwlwifi 0000:04:00.0: 0x00000000 | tsf hi
[14348.255962] iwlwifi 0000:04:00.0: 0x00000000 | time gp1
[14348.255964] iwlwifi 0000:04:00.0: 0x0000012E | time gp2
[14348.255966] iwlwifi 0000:04:00.0: 0x00000000 | time gp3
[14348.255969] iwlwifi 0000:04:00.0: 0x0001271F | uCode version
[14348.255971] iwlwifi 0000:04:00.0: 0x0000006C | hw version
[14348.255973] iwlwifi 0000:04:00.0: 0x00C8330C | board version
[14348.255976] iwlwifi 0000:04:00.0: 0x00000000 | hcmd
[14348.255978] iwlwifi 0000:04:00.0: 0x00122000 | isr0
[14348.255980] iwlwifi 0000:04:00.0: 0x00000000 | isr1
[14348.255983] iwlwifi 0000:04:00.0: 0x00000002 | isr2
[14348.255985] iwlwifi 0000:04:00.0: 0x004000C0 | isr3
[14348.255987] iwlwifi 0000:04:00.0: 0x00000000 | isr4
[14348.255989] iwlwifi 0000:04:00.0: 0x00000000 | isr_pref
[14348.255992] iwlwifi 0000:04:00.0: 0x000047DE | wait_event
[14348.255994] iwlwifi 0000:04:00.0: 0x00000000 | l2p_control
[14348.255997] iwlwifi 0000:04:00.0: 0x00000000 | l2p_duration
[14348.255999] iwlwifi 0000:04:00.0: 0x00000000 | l2p_mhvalid
[14348.256017] iwlwifi 0000:04:00.0: 0x00100040 | l2p_addr_match
[14348.256019] iwlwifi 0000:04:00.0: 0x00000007 | lmpm_pmg_sel
[14348.256022] iwlwifi 0000:04:00.0: 0x00000000 | timestamp
[14348.256024] iwlwifi 0000:04:00.0: 0x0000F808 | flow_handler
[14348.256087] iwlwifi 0000:04:00.0: Start IWL Event Log Dump: display last 3 entries
[14348.256109] iwlwifi 0000:04:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14348.256123] iwlwifi 0000:04:00.0: EVT_LOGT:0000000022:0x00000000:1208
[14348.256136] iwlwifi 0000:04:00.0: EVT_LOGT:0000000304:0x00000000:0125
[14348.256144] iwlwifi 0000:04:00.0: BUG_ON, Stop restarting
[14348.260373] iwlwifi 0000:04:00.0: Failed to run INIT ucode: -5
[14348.260463] iwlwifi 0000:04:00.0: Unable to initialize device.
[14348.260890] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[14348.268390] iwlwifi 0000:04:00.0: RF_KILL bit toggled to disable radio.
[14348.270375] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[14348.277640] iwlwifi 0000:04:00.0: Loaded ucode is not valid!
[14348.277974] iwlwifi 0000:04:00.0: Failed to run INIT ucode: -5
[14348.278141] iwlwifi 0000:04:00.0: Unable to initialize device.

########## wireless info END ############



```

---

