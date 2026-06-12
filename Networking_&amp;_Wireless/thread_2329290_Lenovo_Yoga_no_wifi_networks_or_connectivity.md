---
title: "Lenovo Yoga no wifi networks or connectivity"
date: 2016-06-28
forum: Networking &amp; Wireless
---

### Post by manuti on 2016-06-28
Another Lenovo Yoga 2 13" not working after update
my **uname -**a is:

```
 Linux agp-Lenovo-Yoga-2-13 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```


Find attached my **wireless-info.txt**:

```

########## wireless info START ##########

Report from: 28 Jun 2016 23:29 CEST +0200

Booted last: 28 Jun 2016 00:00 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 6b)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:c262]
    Kernel modules: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:054a Acer, Inc 
Bus 002 Device 003: ID 04f3:0303 Elan Microelectronics Corp. 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
iwlwifi               200704  0
cfg80211              565248  3 iwlwifi,mac80211,rtlwifi
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
video                  40960  2 i915,ideapad_laptop

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

root      5340     1  0 23:25 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

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

[[/etc/NetworkManager/system-connections/lared2]] (600 root)
[connection] id=lared2 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=lared2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/lared2 1]] (600 root)
[connection] id=lared2 1 | type=wifi | permissions=user:manuti:;
[wifi] mac-address-blacklist= | ssid=lared2
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     6318AD97B9A7F66A430B132
depends:        mac80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[rtl8192cu]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2C9D776AE1B25BDC5405217
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2C9F7031AC4F080527C5C6E
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     68438042FA7FFFCF4EB1B75
depends:        rtlwifi
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     251B17ACC83990EE9A63C56
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[rtl8192cu]
debug: 0
swenc: N

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

##### dmesg #############################

[ 1446.373201] wlx74da380a3257: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1446.572595] IPv6: ADDRCONF(NETDEV_UP): wlx74da380a3257: link is not ready (repeated 2 times)
[ 1447.505683] wlx74da380a3257: authenticate with <MAC address>
[ 1447.516528] wlx74da380a3257: send auth to <MAC address> (try 1/3)
[ 1447.530521] wlx74da380a3257: authenticated
[ 1447.531568] wlx74da380a3257: associate with <MAC address> (try 1/3)
[ 1447.546357] wlx74da380a3257: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=5)
[ 1447.595594] wlx74da380a3257: associated
[ 1447.595605] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74da380a3257: link becomes ready
[ 1451.499738] wlx74da380a3257: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1451.499882] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[ 1451.499887] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x390272a
[ 1451.499891] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x27272700
[ 1451.499897] rtl_usb: reg 0x1cc, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x27272700
[ 1463.486892] rtl8192cu: Chip version 0x10
[ 1463.522982] rtl8192cu: MAC address: <MAC address>
[ 1463.522986] rtl8192cu: Board Type 0
[ 1463.523098] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1463.523132] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 1463.523326] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 1463.524396] usb 2-1: Direct firmware load for rtlwifi/rtl8192cufw_TMSC.bin failed with error -2
[ 1463.524411] usb 2-1: Direct firmware load for rtlwifi/rtl8192cufw.bin failed with error -2
[ 1463.524414] rtlwifi: Loading alternative firmware rtlwifi/rtl8192cufw.bin
[ 1463.524416] rtlwifi: Firmware rtlwifi/rtl8192cufw_TMSC.bin not available
[ 1464.543577] rtl8192cu 2-1:1.0 wlx74da380a3257: renamed from wlan0
[ 1464.568374] IPv6: ADDRCONF(NETDEV_UP): wlx74da380a3257: link is not ready
[ 1464.570634] rtl8192cu: MAC auto ON okay!
[ 1464.589543] rtl8192cu: Tx queue select: 0x05
[ 1465.427691] IPv6: ADDRCONF(NETDEV_UP): wlx74da380a3257: link is not ready (repeated 2 times)
[ 1466.339350] wlx74da380a3257: authenticate with <MAC address>
[ 1466.349955] wlx74da380a3257: send auth to <MAC address> (try 1/3)
[ 1466.355329] wlx74da380a3257: authenticated
[ 1466.360006] wlx74da380a3257: associate with <MAC address> (try 1/3)
[ 1466.374407] wlx74da380a3257: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=5)
[ 1466.375479] wlx74da380a3257: associated
[ 1466.375526] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74da380a3257: link becomes ready
[ 1653.712841] wlx74da380a3257: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```

---

### Post by QDR06VV9 on 2016-06-29
> **manuti said:**
> Another Lenovo Yoga 2 13" not working after update
my **uname -**a is:

```
 Linux agp-Lenovo-Yoga-2-13 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```


Find attached my **wireless-info.txt**:

```

########## wireless info START ##########

Report from: 28 Jun 2016 23:29 CEST +0200

Booted last: 28 Jun 2016 00:00 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 6b)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:c262]
    Kernel modules: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:054a Acer, Inc 
Bus 002 Device 003: ID 04f3:0303 Elan Microelectronics Corp. 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
iwlwifi               200704  0
cfg80211              565248  3 iwlwifi,mac80211,rtlwifi
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
video                  40960  2 i915,ideapad_laptop

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

root      5340     1  0 23:25 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

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

[[/etc/NetworkManager/system-connections/lared2]] (600 root)
[connection] id=lared2 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=lared2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/lared2 1]] (600 root)
[connection] id=lared2 1 | type=wifi | permissions=user:manuti:;
[wifi] mac-address-blacklist= | ssid=lared2
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     6318AD97B9A7F66A430B132
depends:        mac80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[rtl8192cu]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2C9D776AE1B25BDC5405217
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2C9F7031AC4F080527C5C6E
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     68438042FA7FFFCF4EB1B75
depends:        rtlwifi
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     251B17ACC83990EE9A63C56
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[rtl8192cu]
debug: 0
swenc: N

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

##### dmesg #############################

[ 1446.373201] wlx74da380a3257: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1446.572595] IPv6: ADDRCONF(NETDEV_UP): wlx74da380a3257: link is not ready (repeated 2 times)
[ 1447.505683] wlx74da380a3257: authenticate with <MAC address>
[ 1447.516528] wlx74da380a3257: send auth to <MAC address> (try 1/3)
[ 1447.530521] wlx74da380a3257: authenticated
[ 1447.531568] wlx74da380a3257: associate with <MAC address> (try 1/3)
[ 1447.546357] wlx74da380a3257: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=5)
[ 1447.595594] wlx74da380a3257: associated
[ 1447.595605] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74da380a3257: link becomes ready
[ 1451.499738] wlx74da380a3257: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1451.499882] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[ 1451.499887] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x390272a
[ 1451.499891] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x27272700
[ 1451.499897] rtl_usb: reg 0x1cc, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x27272700
[ 1463.486892] rtl8192cu: Chip version 0x10
[ 1463.522982] rtl8192cu: MAC address: <MAC address>
[ 1463.522986] rtl8192cu: Board Type 0
[ 1463.523098] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1463.523132] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 1463.523326] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 1463.524396] usb 2-1: Direct firmware load for rtlwifi/rtl8192cufw_TMSC.bin failed with error -2
[ 1463.524411] usb 2-1: Direct firmware load for rtlwifi/rtl8192cufw.bin failed with error -2
[ 1463.524414] rtlwifi: Loading alternative firmware rtlwifi/rtl8192cufw.bin
[ 1463.524416] rtlwifi: Firmware rtlwifi/rtl8192cufw_TMSC.bin not available
[ 1464.543577] rtl8192cu 2-1:1.0 wlx74da380a3257: renamed from wlan0
[ 1464.568374] IPv6: ADDRCONF(NETDEV_UP): wlx74da380a3257: link is not ready
[ 1464.570634] rtl8192cu: MAC auto ON okay!
[ 1464.589543] rtl8192cu: Tx queue select: 0x05
[ 1465.427691] IPv6: ADDRCONF(NETDEV_UP): wlx74da380a3257: link is not ready (repeated 2 times)
[ 1466.339350] wlx74da380a3257: authenticate with <MAC address>
[ 1466.349955] wlx74da380a3257: send auth to <MAC address> (try 1/3)
[ 1466.355329] wlx74da380a3257: authenticated
[ 1466.360006] wlx74da380a3257: associate with <MAC address> (try 1/3)
[ 1466.374407] wlx74da380a3257: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=5)
[ 1466.375479] wlx74da380a3257: associated
[ 1466.375526] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74da380a3257: link becomes ready
[ 1653.712841] wlx74da380a3257: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```

Hi manuti please do not hijack a thread in progress it confuses every one.
It is best to Start your own Thread even if you think the problem is the same...I have Started your own Thread now.
Good Luck and Thanks

---

### Post by jeremy31 on 2016-06-29
Post the result of ```
dmesg | grep iwl; lsmod | grep iwl; lshw -c net
```

---

### Post by manuti on 2016-06-29
Sorry, I think is better to add similar problems than create new threads.
For me works do:

```
sudo apt-get install linux-firmware
sudo reboot

```

---

### Post by jeremy31 on 2016-06-29
Lenovo Yoga computers are likely to use one of 4 or 5 possible wifi cards, so an answer that works for one doesn't apply to all.

Strange that that command helped as your Intel wifi should have had firmware that worked already but I did find it strange that module iwlmvm wasn't listed in the wireless script results

---

### Post by QDR06VV9 on 2016-06-29
> **jeremy31 said:**
> Lenovo Yoga computers are likely to use one of 4 or 5 possible wifi cards,_** so an answer that works for one doesn't apply to all.**_

Strange that that command helped as your Intel wifi should have had firmware that worked already but I did find it strange that module iwlmvm wasn't listed in the wireless script results
+1 Thanks jeremy31;)

---

### Post by manuti on 2016-06-30
Thanks **jeremy31 **and **runrickus**.
As a post morten I can summarize my case.

After a normal update of Ubuntu 16.04 with -y option an a manual update of Calibre the wireless stop working and is like no exist.
I try several solutions for similar problems found here or in askubuntu. Finally I have found the** linux-firmware** that worked for me.

---

