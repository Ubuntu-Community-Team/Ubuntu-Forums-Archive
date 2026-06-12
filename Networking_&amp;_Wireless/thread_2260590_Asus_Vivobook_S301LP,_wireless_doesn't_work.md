---
title: "Asus Vivobook S301LP, wireless doesn't work"
date: 2015-01-13
forum: Networking &amp; Wireless
---

### Post by laetitia on 2015-01-13
I have an asus vivobook S301LP and I the wireless doesn't work...

I did this:

 wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script

and this is the results:

########## wireless info START ##########

Report from: 13 Jan 2015 11:03 CET +0100

Booted last: 13 Jan 2015 10:48 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e074]

04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mars LE [Radeon HD 8530M / R5 M240] [1002:6607] (rev ff)

##### lsusb #############################

Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0457:1026 Silicon Integrated Systems Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 13d3:5195 IMC Networks 
Bus 002 Device 002: ID 0e8d:763f MediaTek Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt73usb                31580  0 
rt2x00usb              20742  1 rt73usb
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00lib              55307  7 rt73usb,rt2x00pci,rt2x00usb,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
crc_itu_t              12707  1 rt73usb
mac80211              630669  4 rt2x00lib,rt2x00pci,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
eeprom_93cx6           13344  1 rt2800pci
wmi                    19177  1 asus_wmi
ndiswrapper           283985  0 
video                  19476  2 i915,asus_wmi

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

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Livebox-C7C4]] (600 root)
[connection] id=Livebox-C7C4 | type=802-11-wireless
[802-11-wireless] ssid=Livebox-C7C4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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

[rt2800pci]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     5C88E1E4BD840C950F493E4
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     A6B5D01725492005F5918FA
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     3AF2621F166C8604D7D8AA5
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt73usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     66CCBB24DCA72AAD23E9588
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     1B9A9CB4CAAB78DFE7974EA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.13.0-44-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[rt73usb]
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

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

lp
rtc
eeprom
eeprom_93cx6
crc-ccitt
cfg80211
mac80211
rt2x00lib
rt2x00pci
rt2x00mmio
rt2800lib
rt2800pci

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

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000014C3d00007610sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv0000180Dsd000010CFbc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv0000197Csd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv00002166sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv00007630sd000011ADbc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv0000B630sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv0000E074sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv0000E084sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000014C3d00007630sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014C3d00007650sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000015sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000016sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000022sd000017F9bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000023sd000017F9bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000002Asd00006409bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000061sd000017CFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000063sd000017CFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000067sd00001737bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000300sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000359sd00001154bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000361sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000364sd00001154bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000500sd000018EBbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000130Esd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000130Fsd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00002860sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00002860sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C0Asd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C43sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C85sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C86sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C87sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C88sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C89sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C8Asd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C8Bsd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007322sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007708sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007728sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007758sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00008322sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00009161sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00009261sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00009262sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000C124sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000C129sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000C12Asd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000D057sd000010FCbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000E937sd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000ED07sd000014EAbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000ED09sd000014EAbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000002Bsd00006409bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00000300sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00000503sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00002890sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00003C85sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00003C86sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00006247sd000018E8bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007722sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007738sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007748sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007768sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00008722sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000E938sd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000E939sd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000E93Asd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000ED08sd000014EAbc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000037sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000043sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000301sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000302sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00001205sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00001206sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00002760sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C8Csd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C8Dsd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C90sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C91sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C92sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C93sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00007312sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00007727sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00009151sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00009251sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00009252sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv0000C12Bsd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv0000C12Csd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000036sd00001B0Abc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000297sd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000298sd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000299sd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000029Asd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000302sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00001059sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000130Fsd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00002790sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00002790sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006263sd000018E8bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006600sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006601sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006890sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00007600sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00007712sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00008320sd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000832Esd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000890Asd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000E002sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000E93Bsd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003060sd00001B75bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003C04sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003C44sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003C95sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00007711sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv000084E2sd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00000038sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv0000005Esd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv0000006Dsd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00003062sd00001B75bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00003062sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00007722sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000307sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E40sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E41sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E42sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E43sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E44sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001057sd000013BDbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001087sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001453sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00002041sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00002A41sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003000sd00001854bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003001sd00001854bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003090sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003090sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003872sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006602sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006622sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006632sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006891sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006894sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00007186sd0000144Fbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00007602sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000872Asd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000872Bsd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000891Asd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000891Bsd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000E93Csd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000E93Dsd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000F101sd000017AAbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00001088sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00001A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00003091sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00006892sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv0000E93Esd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003092sv00000015sd000015A9bc*sc*i* ndiswrapper
alias pci:v00001814d00003092sv00003092sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003092sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00001771sd000010CFbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv000018ECsd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv0000191Csd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002101sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002B87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002C87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002E87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00006009sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00006010sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00006019sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00007196sd0000144Fbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv0000E055sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv0000F0B0sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003562sv00003562sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003562sv0000D05Esd000010FCbc*sc*i* ndiswrapper
alias pci:v00001814d00003562sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv00001638sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv00003592sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv00006007sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv0000F003sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003593sv0000F102sd000017AAbc*sc*i* ndiswrapper
alias pci:v00001814d00003593sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000359Fsv00003390sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000359Fsv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005360sv00003C05sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00005360sv0000703Asd000020F4bc*sc*i* ndiswrapper
alias pci:v00001814d00005360sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005362sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00001155sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00001636sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00001A55sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00006008sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00006605sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv000085A4sd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000E054sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000E088sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000F001sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000F051sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000F052sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv00003C06sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv00006606sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv000085A5sd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv0000F053sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv0000F054sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Asv00001839sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Asv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Bsv000018EDsd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Bsv0000191Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv00001637sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv00001774sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv0000F002sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005592sv0000851Asd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00005592sv000085E6sd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00005592sv0000D722sd00007392bc*sc*i* ndiswrapper
alias pci:v00001814d00005592sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00006590sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00007650sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00008592sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x148f:0x2573 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  378.333675] ieee80211 phy2: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[  378.347726] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[  378.347753] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[  378.431424] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  380.840364] wlan0: authenticate with <MAC address>
[  380.897733] wlan0: send auth to <MAC address> (try 1/3)
[  380.900078] wlan0: authenticated
[  380.903630] wlan0: associate with <MAC address> (try 1/3)
[  380.906928] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=2)
[  380.918032] wlan0: associated
[  380.918086] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  380.927467] wlan0: deauthenticating from <MAC address> by local choice (reason=2)
[  380.961270] wlan0: authenticate with <MAC address>
[  380.973160] wlan0: send auth to <MAC address> (try 1/3)
[  382.259934] wlan0: send auth to <MAC address> (try 2/3)
[  382.262024] wlan0: authenticated
[  382.263525] wlan0: associate with <MAC address> (try 1/3)
[  382.266787] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=2)
[  382.278396] wlan0: associated
[  890.157557] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[  920.499317] ieee80211 phy3: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[  920.523544] ieee80211 phy3: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[  920.523576] ieee80211 phy3: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[  920.603480] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  921.818341] wlan0: authenticate with <MAC address>
[  921.863906] wlan0: send auth to <MAC address> (try 1/3)
[  921.866366] wlan0: authenticated
[  921.867866] wlan0: associate with <MAC address> (try 1/3)
[  921.871123] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=2)
[  921.881856] wlan0: associated
[  921.881901] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  936.464595] wlan0: deauthenticating from <MAC address> by local choice (reason=3)

########## wireless info END ############


there are some problems at the end but i don't know what it means ...

please i really need help on this !!!

---

### Post by chili555 on 2015-01-13
WOW! Just wow. You have a great big pile of drivers there, don't you?

We have some repairs to do first. Please do:```
gksudo gedit /etc/modules
```Change the file to remove what I have highlighted:```
lp
rtc
eeprom
eeprom_93cx6
crc-ccitt
[COLOR="#FF0000"]cfg80211
mac80211
rt2x00lib
rt2x00pci
rt2x00mmio
rt2800lib
rt2800pci[/COLOR]
```Proofread carefully, save and close gedit. Now reboot and do:```
sudo modprobe ndiswrapper
```And show us:```
ndiswrapper -l
iwconfig
lsmod
```Thanks.

---

### Post by laetitia on 2015-01-13
Yes a lot of drivers indeed ^^

this is what I have after doing what you said :

```
laetitia@laetitia-S301LP:~$ ndiswrapper -l
netr28x : driver installed
    device (14C3:7630) present
laetitia@laetitia-S301LP:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

laetitia@laetitia-S301LP:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
ctr                    13049  0 
ccm                    17773  0 
mt76xx                 17595  0 
bnep                   19624  2 
rfcomm                 69160  12 
nls_iso8859_1          12713  1 
arc4                   12608  0 
btusb                  32412  0 
bluetooth             391136  22 bnep,btusb,rfcomm
rt73usb                31580  0 
rt2x00usb              20742  1 rt73usb
rt2x00lib              55307  2 rt73usb,rt2x00usb
asus_nb_wmi            16990  0 
mac80211              630669  2 rt2x00lib,rt2x00usb
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
cfg80211              484040  2 mac80211,rt2x00lib
uvcvideo               80885  0 
crc_itu_t              12707  1 rt73usb
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
intel_powerclamp       14705  0 
videodev              134688  2 uvcvideo,videobuf2_core
coretemp               13435  0 
kvm_intel             143187  0 
rts5139               335409  0 
snd_hda_intel          56451  5 
kvm                   455835  1 kvm_intel
parport_pc             32701  0 
ppdev                  17671  0 
crct10dif_pclmul       14289  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
crc_ccitt              12707  0 
hid_multitouch         17407  0 
crc32_pclmul           13113  0 
i915                  784207  4 
radeon               1522640  2 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
eeprom_93cx6           13344  0 
eeprom                 12841  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ttm                    85150  1 radeon
joydev                 17381  0 
drm_kms_helper         55071  2 i915,radeon
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
drm                   303102  7 ttm,i915,drm_kms_helper,radeon
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13462  0 
wmi                    19177  1 asus_wmi
i2c_algo_bit           13413  2 i915,radeon
ndiswrapper           283985  0 
soundcore              12680  1 snd
lp                     17759  0 
mei_me                 18627  0 
parport                42348  3 lp,ppdev,parport_pc
mei                    82276  1 mei_me
intel_smartconnect     12619  0 
video                  19476  2 i915,asus_wmi
lpc_ich                21080  0 
mac_hid                13205  0 
usbhid                 52659  0 
hid                   106148  2 hid_multitouch,usbhid
ahci                   25819  3 
psmouse               106714  0 
libahci                32716  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169


```

---

### Post by chili555 on 2015-01-13
We're closer! Let's see:```
cat /etc/rc.local
ls /etc/modprobe.d
```I am trying to find out why rt73usb is loading. Also:```
dmesg | grep ndis
```

---

### Post by laetitia on 2015-01-13
so this is the result :

```
laetitia@laetitia-S301LP:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
laetitia@laetitia-S301LP:~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-modem.conf         fbdev-blacklist.conf
blacklist-ath_pci.conf      blacklist-oss.conf           iwlwifi.conf
blacklist.conf              blacklist-rare-network.conf  mlx4.conf
blacklist-firewire.conf     blacklist-watchdog.conf      ndiswrapper.conf
blacklist-framebuffer.conf  dkms.conf                    vmwgfx-fbdev.conf
laetitia@laetitia-S301LP:~$ dmesg | grep ndis
[   15.902302] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   15.903224] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   25.167297] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'isxdigit'
[   25.167307] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[   25.167320] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeSetCoalescableTimer'
[   25.167331] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   25.167341] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   25.167347] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   25.167354] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCopySendNetBufferListInfo'
[   25.167361] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   25.167369] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   25.167375] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   25.167381] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   25.167388] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   25.167394] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   25.167400] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   25.167408] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   25.167420] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   25.167424] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   25.167428] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   25.167432] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   25.167436] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   25.167440] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   25.167444] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   25.167448] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   25.167471] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   25.167483] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   25.167494] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   25.167505] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   25.167520] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   25.167548] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   25.167560] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   25.167572] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   25.167584] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   25.167600] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   25.167612] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   25.167623] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   25.167635] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   25.167647] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   25.167658] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   25.167670] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   25.167681] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   25.167699] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   25.167711] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   25.167755] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   25.167759] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   25.167763] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   25.167767] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   25.167770] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netr28x'
[   25.168286] ndiswrapper (load_wrap_driver:103): couldn't load driver netr28x; check system log for messages from 'loadndisdriver'
[   25.168358] usbcore: registered new interface driver ndiswrapper


```

---

### Post by chili555 on 2015-01-13
So you have no idea how or why rt73usb is loading? I see no reason at all, yet, after a fresh reboot, it loads. We need to get it out of the way before we proceed.

Your wireless device is tricky to get going but you have a pretty good start with ndiswrapper so I suggest we pursue it as long as we can.

What Windows inf and sys files did you use for ndiswrapper? XP (hint, hint)? Or 7 or 8 or 3.1? Where did they come from?

---

### Post by laetitia on 2015-01-13
rt73usb could be my wireless usb key ? if it's not then I have no idea...

i use this topic for ndiswrapper : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading_Windows_Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading_Windows_Drivers)

---

### Post by chili555 on 2015-01-13
Evidently, your USB wireless wasn't connected when you ran the wireless_script; I don't see it.

My question remains. While the link describes the general process, I am looking for specifically where you got the inf and sys files and if they are specifically XP. Obviously, ndiswrapper doesn't like them:> [   25.167297] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'isxdigit'
[   25.167307] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[   25.167320] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeSetCoalescableTimer'
[   25.167331] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   25.167341] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   25.167347] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   25.167354] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCopySendNetBufferListInfo'
[   25.167361] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'Did you install ndiswrapper from the Software Center or apt-get or where and how?

---

### Post by laetitia on 2015-01-13
The files come from the windows part of my computer.

I installed ndiswrapper from the apt-get, I followed the link that I gave you

---

### Post by chili555 on 2015-01-13
> The files come from the windows part of my computer.From the *XP* partition?

---

### Post by laetitia on 2015-01-14
they come from windows/system 32

and I made a mistake, I have installed it from de software center, sorry.

if you think it need to be uninstall and re install i can do it !

---

### Post by chili555 on 2015-01-14
I have evidently not made myself clear; if so, I apologize. ndiswrapper only works with and requires Windows XP driver files. Here is an excerpt from the manual pages for ndiswrapper. You can access it by entering in a terminal:```
man ndiswrapper-1.9
```> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Win&#8208;
       dows  XP drivers and kernel module to load the Windows XP drivers. Both
       are called ndiswrapper.If you tried to load the Windows 7 or Windows 8 driver, a fairly common error for new Ubuntu users, we need to remove them and look around for XP drivers. If you actually did find and use XP drivers, they obviously won't work at all and we need to remove them and try something else entirely.

Did the Windows/system32 drivers come from a Windows 8 installation or Windows 7 or Windows Vista or Windows XP or Windows what, exactly?

---

### Post by laetitia on 2015-01-14
I'm sorry that I didn't understand right, I'm a new ubuntu user effectively and that's my brother who helps me a little with it.
I don't think we used XP drivers for this, I think it's windows 8 drivers because I have windows 8.1.

So the windows/system 32 drivers come from windows 8.

Maybe we can remove all that I've done with ndiswrapper ?

---

### Post by chili555 on 2015-01-14
We certainly can remove the ndiswrapper installation. Please do:```
sudo apt-get purge ndiswrapper-common
sudo apt-get purge ndiswrapper-utils-1.9
sudo rm /etc/modprobe.d/ndiswrapper.conf
```If the terminal reports that the latter file no longer exists, that's fine, just continue. 

Now, with a working internet connection:```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/lwfinger/mt7630.git
cd mt7630
make
```And if there is no error:```
sudo make install
```Reboot and your wireless should be working.

Please tell us if it works; we will probably have one additional step.

---

### Post by laetitia on 2015-01-14
Yeah it works !!! thanks a lot !!

Do I have to do other things ?

---

### Post by chili555 on 2015-01-14
Yes, indeed. The driver you compiled is for your currently running kernel version only. Your wireless_script suggests it is 3.13.0-44-generic. When Update Manager installs a later kernel version, 3.13.0-4[COLOR="#FF0000"]5[/COLOR]-generic, for example, build the driver again after the required reboot:```
cd ~/mt7630
make clean
make
sudo make install
```And then reboot again.

Please retain the file and these instructions for that time. Also, please use thread tools at the top of the page to mark Solved. The searchers will appreciate it.

---

### Post by laetitia on 2015-01-14
I do this command now or I wait ??

Thanks for your help, I will put this topic solved indeed.

---

### Post by chili555 on 2015-01-14
> **laetitia said:**
> I do this command now or I wait ??You wait until Update Manager installs a later linux-image and tells you to reboot to complete the update. It may be days from now or it may be weeks. You will notice, after the reboot, that your wireless no longer works as always. Then run the code and reboot again.

---

### Post by laetitia on 2015-01-15
Ok thanks a lot ! :)

---

