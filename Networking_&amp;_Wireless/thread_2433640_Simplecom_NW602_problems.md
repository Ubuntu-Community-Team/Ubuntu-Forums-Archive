---
title: "Simplecom NW602 problems"
date: 2019-12-22
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2019-12-22
Hi all,

Just purchased a Simplecom NW602 nano AC600 usb wifi adapter. Can't get it working. When I plug it in and issue dmesg in a terminal, I get this.

```
[ 2997.179845] usb 2-1.3: new high-speed USB device number 8 using ehci-pci
[ 2997.273106] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=c811
[ 2997.273114] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2997.273118] usb 2-1.3: Product: 802.11ac NIC
[ 2997.273122] usb 2-1.3: Manufacturer: Realtek
[ 2997.273125] usb 2-1.3: SerialNumber: 123456
```

I followed some instructions from here ...

[https://forums.linuxmint.com/viewtopic.php?t=238399](https://forums.linuxmint.com/viewtopic.php?t=238399)

... then realised these instructions were for the Simplecom NW611. Not my dongle. Now I'm a simpleton with a Simplecom!

Any suggestions anyone? Hoping so else I'll need to fork out for the NW611 as at least I know that works (by the looks of it).

Cheers. ;)

PS: I'm using Xubuntu-core 16.04.

PPS: Further info. Just been screwing around with wireless.info script, and pretty sure this is the info for my Simplecom. The working dongle was not plugged in, only the Simplecom NW602, so ...


```
########## wireless info START ##########

Report from: 23 Dec 2019 15:54 ACDT +1030

Booted last: 23 Dec 2019 00:00 ACDT +1030

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-170-generic #199-Ubuntu SMP Thu Nov 14 01:45:04 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Toshiba America Info Systems RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1179:ff1e]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8182]
	Kernel modules: rtl8192se

##### lsusb #############################

Bus 002 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 012: ID 0bda:c811 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: Toshiba Bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

rtl8812au            1355776  0
rtl8192cu              98304  0
rtl_usb                24576  1 rtl8192cu
rtl8192c_common        81920  1 rtl8192cu
rtlwifi               102400  3 rtl_usb,rtl8192c_common,rtl8192cu
rtl8xxxu               73728  0
mac80211              741376  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  3 mac80211,rtlwifi,rtl8812au
wmi                    20480  1 toshiba_acpi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       887     1  0 12:34 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
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

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Jetsons 1]] (600 root)
[connection] id=Jetsons 1 | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Jetsons
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_Extender_2.4GHz 1]] (600 root)
[connection] id=TP-LINK_Extender_2.4GHz 1 | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_Extender_2.4GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Orbitty]] (600 root)
[connection] id=Orbitty | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Orbitty
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_Extender_2.4GHz]] (600 root)
[connection] id=TP-LINK_Extender_2.4GHz | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_Extender_2.4GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Jetsons]] (600 root)
[connection] id=Jetsons | type=wifi | permissions=user:xubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Jetsons
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Jetsons 2]] (600 root)
[connection] id=Jetsons 2 | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Jetsons
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Astro-2.4]] (600 root)
[connection] id=Astro-2.4 | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Astro-2.4
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Australia/Adelaide (based on set time zone)

country AU: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 36), (N/A)
	(5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5600 @ 80), (N/A, 27), (0 ms), DFS
	(5650 - 5730 @ 80), (N/A, 27), (0 ms), DFS
	(5730 - 5850 @ 80), (N/A, 36), (N/A)
	(57000 - 66000 @ 2160), (N/A, 43), (N/A), NO-OUTDOOR

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8812au]
filename:       /lib/modules/4.4.0-170-generic/kernel/drivers/net/wireless/rtl8812au.ko
version:        v4.3.14_13455.20150212_BTCOEX20150128-51
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     2C63CE6EC735F21254D08B5
depends:        cfg80211
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_led_enable:Enable status LED (int)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask vaule:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse vaule:0 (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

[rtl8192cu]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     C0496A1B9223D77A7FB126B
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     65DF382D0422EF04172AA08
depends:        mac80211,rtlwifi
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B0DEE3E51180D862FD88C2C
depends:        rtlwifi
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     990116D31097F1C4C1F7006
depends:        mac80211,cfg80211
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 

[rtl8xxxu]
filename:       /lib/modules/4.4.0-170-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     D48EF7138DE4C68FF5E8533
depends:        mac80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[mac80211]
filename:       /lib/modules/4.4.0-170-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5BE99ECBAF9A2B1F00A8A98
depends:        cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-170-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2B99D187C117AD7295AECA
depends:        
retpoline:      Y
intree:         Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8812au]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_adaptivity_dml: 0
rtw_adaptivity_en: 0
rtw_adaptivity_mode: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_amplifier_type_2g: 0
rtw_amplifier_type_5g: 0
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_bw_mode: 33
rtw_channel: 1
rtw_channel_plan: 89
rtw_chip_version: 0
rtw_decrypt_phy_file: 0
rtw_enusbss: 0
rtw_FileMaskEfuse: 0
rtw_hiq_filter: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_led_enable: 1
rtw_load_phy_file: 68
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_OffEfuseMask: 0
rtw_power_mgnt: 1
rtw_qos_opt_enable: 0
rtw_rf_config: 5
rtw_RFE_type: 64
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_special_rf_path: 0
rtw_TxBBSwing_2G: 255
rtw_TxBBSwing_5G: 255
rtw_tx_pwr_by_rate: 0
rtw_tx_pwr_lmt_enable: 0
rtw_usb_rxagg_mode: 2
rtw_vcs_type: 1
rtw_vht_enable: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[rtl8192cu]
debug: 1
swenc: N

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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
blacklist rtl8192ce
blacklist rtl8192se

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

[/etc/modprobe.d/rtl8192se.conf]
options rtl8192se swenc=1 ips=0

##### rc.local ##########################

sleep 10
iwconfig wlp3s0 power off
exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlp3s0 power off

##### udev rules ########################

##### dmesg #############################

[ 4229.478559] wlxe84e060dc5a4: authenticated
[ 4229.479690] wlxe84e060dc5a4: associate with <MAC address> (try 1/3)
[ 4229.483317] wlxe84e060dc5a4: RX AssocResp from <MAC address> (capab=0x1431 status=0 aid=3)
[ 4229.485548] usb 2-1.3: rtl8xxxu_bss_info_changed: HT supported
[ 4229.488690] wlxe84e060dc5a4: associated
[ 4229.488734] usb 2-1.3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 4229.488798] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe84e060dc5a4: link becomes ready
[ 4566.325191] usb 2-1.3: rtl8xxxu_int_complete: Error -71
[ 4566.535600] usb 2-1.3: rtl8xxxu_active_to_lps: RX poll timed out (0x05f8)
[ 4566.540917] usb 2-1.3: rtl8xxxu_active_to_emu: Disabling MAC timed out
[ 4566.552502] wlxe84e060dc5a4: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4566.552525] usb 2-1.3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[ 4778.171599] usb 2-1.3: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 4779.772827] rtl8xxxu 2-1.3:1.0 wlxe84e060dc5a4: renamed from wlan0
[ 4779.801593] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready (repeated 3 times)
[ 4781.683300] wlxe84e060dc5a4: authenticate with <MAC address>
[ 4781.699341] wlxe84e060dc5a4: send auth to <MAC address> (try 1/3)
[ 4781.700944] wlxe84e060dc5a4: authenticated
[ 4781.702110] wlxe84e060dc5a4: associate with <MAC address> (try 1/3)
[ 4781.705666] wlxe84e060dc5a4: RX AssocResp from <MAC address> (capab=0x1431 status=0 aid=3)
[ 4781.707870] usb 2-1.3: rtl8xxxu_bss_info_changed: HT supported
[ 4781.710562] wlxe84e060dc5a4: associated
[ 4781.710649] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe84e060dc5a4: link becomes ready
[ 4781.710935] usb 2-1.3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 5173.467365] usb 2-1.3: rtl8xxxu_int_complete: Error -71
[ 5173.478531] usb 2-1.3: rtl8xxxu_active_to_lps: RX poll timed out (0x05f8)
[ 5173.483804] usb 2-1.3: rtl8xxxu_active_to_emu: Disabling MAC timed out
[ 5173.499976] wlxe84e060dc5a4: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5173.500001] usb 2-1.3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP

########## wireless info END ############
```

---

### Post by Bucky Ball on 2019-12-23
Well, despite the fact that wireless.info seems to be telling me the chipset is RTL8191SEvB, I did some further digging and under 'Specifications' in the NW602 manual ([https://www.simplecom.com.au/media/linksforce/pdf/n/w/nw602_user_manual.pdf](https://www.simplecom.com.au/media/linksforce/pdf/n/w/nw602_user_manual.pdf)) it tells me it is a RTL8811CU. So ...

After further digging, I got to here and followed the instructions to make/make install ...

[https://github.com/brektrou/rtl8821CU](https://github.com/brektrou/rtl8821CU)

Rebooted the computer, plug the Simplecom NW602 in, get the message 'Wireless networks available', choose my 5G network, input security key and voila, all working! Checked the speed with Ookla and it's racing along.

This looks to be solved, but I'll leave it for 12 hours before marking it solved to see if anyone has any further input and to see if the thing works consistently with no problems. 

Perhaps not such a simpleton after all. Cheers. :)

---

### Post by praseodym on 2019-12-23
Here is the right one

```
sudo apt update
sudo apt install build-essential git dkms
git clone https://github.com/whitebatman2/rtl8821CU.git
DRV_NAME=rtl8821CU
DRV_VERSION=5.2.5.3
sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
cd $DRV_NAME
git archive master | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}
```

---

### Post by Bucky Ball on 2019-12-23
Thanks, praseodym. Should I remove anything I've already installed or just go ahead with what you have there?

I'll go ahead with what you have there for now and let you know what happens. What I have now works (like a rocket), but ... it's patchy. Every now and then things come to a grinding halt and it stops loading pages (although I'm still connected).

Here goes.

* Update. This is the output of the final command you gave.

```
tish@tosh:~/rtl8821CU$ sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}

8821cu:
Running module version sanity check.

Good news! Module version v5.2.5.3_24795.20171031_COEX20170310-1212 for 8821cu.ko
exactly matches what is already found in kernel 4.4.0-170-generic.
DKMS will not replace this module.
You may override by specifying --force.

depmod....

DKMS: install completed.
```

So all much the same as what I had I guess.

---

### Post by Bucky Ball on 2019-12-23
* Further update: This is pretty weird. When I'm using the Simplecom AC600 adapter, all works ok for awhile, but then things stop. Just won't load pages. My wife is streaming some stuff on the TV and it's stopping the stream there, too! When I swap back to using the old adapter (not AC), everything works fine again and she can stream fine and I can use the internet fine.

Swap back to the AC adapter and things come to a grinding halt, both on my computer and on her streaming TV. An anomaly. Any thoughts on that? Have checked what I can and router/modem seems to be working fine. ISP saying there are no faults or outages on their end. We have a dual-band router and other AC devices seem to work fine and don't cause these issues (as far as I know although I haven't done any formal tests to this point).

What is strange is that she is streaming via a Raspberry Pi and that is plugged directly into the router with an ethernet cable. Can't figure out how my dodgy wireless can be affecting that, but she is happily streaming away now as I am posting this using the old, non-AC, non-Simplecom NW602 adapter. I seem to be 'clagging' the router somehow with the NW602. Odd.

---

### Post by jeremy31 on 2019-12-23
Please reboot with only the problem wifi device connected and provide new wireless script results

---

### Post by Bucky Ball on 2019-12-23
This is wireless.info with only the problem Simplecom NW602 plugged in.

```
########## wireless info START ##########

Report from: 24 Dec 2019 00:08 ACDT +1030

Booted last: 24 Dec 2019 00:00 ACDT +1030

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-170-generic #199-Ubuntu SMP Thu Nov 14 01:45:04 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Toshiba America Info Systems RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1179:ff1e]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8182]
	Kernel modules: rtl8192se

##### lsusb #############################

Bus 002 Device 008: ID 0bda:c811 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: Toshiba Bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
6: phy5: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

rtl8192cu              98304  0
rtl_usb                24576  1 rtl8192cu
rtl8192c_common        81920  1 rtl8192cu
rtlwifi               102400  3 rtl_usb,rtl8192c_common,rtl8192cu
rtl8xxxu               73728  0
mac80211              741376  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  3 mac80211,rtlwifi,8821cu
wmi                    20480  1 toshiba_acpi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
8: wlx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 192.168.0.7/24 brd 192.168.0.255 scope global wlx<IF from MAC [IF2]>
       valid_lft forever preferred_lft forever
    inet6 fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11AC  ESSID:"Jetsons_5G"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.745 GHz  Access Point: <MAC 'Jetsons_5G' [AC1]>   
          Bit Rate:434 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/100  Signal level=22/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

default via 192.168.0.1 dev wlx<IF from MAC [IF2]>  proto static  metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF2]>  scope link  metric 1000 
192.168.0.0/24 dev wlx<IF from MAC [IF2]>  proto kernel  scope link  src 192.168.0.7  metric 600 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       974     1  0 Dec23 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11ac NIC
GENERAL.DRIVER:                         rtl8821cu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Jetsons_5G
GENERAL.CON-UUID:                       e3dd2bd7-9f04-4e94-813c-09d88a1c25fd
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     434 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e3dd2bd7-9f04-4e94-813c-09d88a1c25fd | Jetsons_5G
IP4.ADDRESS[1]:                         192.168.0.7/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             202.142.142.142
IP4.DNS[2]:                             202.142.142.242
IP6.ADDRESS[1]:                         fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
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

SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Jetsons       <MAC 'Jetsons' [AC4]>  Infra  7     2442 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2      no        
Jetsons_5G    <MAC 'Jetsons_5G' [AC1]>  Infra  149   5745 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2      yes     * 
BigPond0089   <MAC 'BigPond0089' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2      no        
SkyNet_0x1A4  <MAC 'SkyNet_0x1A4' [AC6]>  Infra  8     2447 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
WiFi-23FF     <MAC 'WiFi-23FF' [AC5]>  Infra  8     2447 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
NETGEAR06     <MAC 'NETGEAR06' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA2      no        
WiFi-23FF-5G  <MAC 'WiFi-23FF-5G' [AC7]>  Infra  36    5180 MHz  54 Mbit/s  10      &#9602;___  WPA2      no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Jetsons 1]] (600 root)
[connection] id=Jetsons 1 | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Jetsons
[ipv4] method=manual
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/TP-LINK_Extender_2.4GHz 1]] (600 root)
[connection] id=TP-LINK_Extender_2.4GHz 1 | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_Extender_2.4GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Orbitty]] (600 root)
[connection] id=Orbitty | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Orbitty
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_Extender_2.4GHz]] (600 root)
[connection] id=TP-LINK_Extender_2.4GHz | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_Extender_2.4GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Jetsons_5G]] (600 root)
[connection] id=Jetsons_5G | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=Jetsons_5G
[ipv4] method=manual
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Jetsons]] (600 root)
[connection] id=Jetsons | type=wifi | permissions=user:xubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Jetsons
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Astro-2.4]] (600 root)
[connection] id=Astro-2.4 | type=wifi | permissions=user:tish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Astro-2.4
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Australia/Adelaide (based on set time zone)

country AU: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 36), (N/A)
	(5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5600 @ 80), (N/A, 27), (0 ms), DFS
	(5650 - 5730 @ 80), (N/A, 27), (0 ms), DFS
	(5730 - 5850 @ 80), (N/A, 36), (N/A)
	(57000 - 66000 @ 2160), (N/A, 43), (N/A), NO-OUTDOOR

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlx<IF from MAC [IF2]>  32 channels in total; available frequencies :
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
          Current Frequency:5.745 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.745 GHz

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'Jetsons_5G' [AC1]>
                    ESSID:"Jetsons_5G"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.745 GHz
                    Encryption key:on
                    Bit Rates:867 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=54/100  Signal level=22/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC 'BigPond0089' [AC2]>
                    ESSID:"BigPond0089"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=16/100  Signal level=20/100  
                    Extra:fm=0003
          Cell 03 - Address: <MAC 'NETGEAR06' [AC3]>
                    ESSID:"NETGEAR06"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:72 Mb/s
                    Extra:rsn_ie=301a0100000fac040100000fac040100000fac028c000000000fac06
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=11/100  
                    Extra:fm=0001
          Cell 04 - Address: <MAC 'Jetsons' [AC4]>
                    ESSID:"Jetsons"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=33/100  
                    Extra:fm=0003
          Cell 05 - Address: <MAC 'WiFi-23FF' [AC5]>
                    ESSID:"WiFi-23FF"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=6/100  Signal level=17/100  
                    Extra:fm=0003
          Cell 06 - Address: <MAC 'SkyNet_0x1A4' [AC6]>
                    ESSID:"SkyNet_0x1A4"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=6/100  Signal level=17/100  
                    Extra:fm=0003
          Cell 07 - Address: <MAC 'WiFi-23FF-5G' [AC7]>
                    ESSID:"WiFi-23FF-5G"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.18 GHz (Channel 36)
                    Encryption key:on
                    Bit Rates:1.3 Gb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=12/100  Signal level=6/100  
                    Extra:fm=0003

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     C0496A1B9223D77A7FB126B
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     65DF382D0422EF04172AA08
depends:        mac80211,rtlwifi
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B0DEE3E51180D862FD88C2C
depends:        rtlwifi
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-170-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     990116D31097F1C4C1F7006
depends:        mac80211,cfg80211
retpoline:      Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 

[rtl8xxxu]
filename:       /lib/modules/4.4.0-170-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     D48EF7138DE4C68FF5E8533
depends:        mac80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[mac80211]
filename:       /lib/modules/4.4.0-170-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5BE99ECBAF9A2B1F00A8A98
depends:        cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-170-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2B99D187C117AD7295AECA
depends:        
retpoline:      Y
intree:         Y
vermagic:       4.4.0-170-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 1
swenc: N

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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
blacklist rtl8192ce
blacklist rtl8192se

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

[/etc/modprobe.d/rtl8192se.conf]
options rtl8192se swenc=1 ips=0

##### rc.local ##########################

sleep 10
iwconfig wlp3s0 power off
exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlp3s0 power off

##### udev rules ########################

##### dmesg #############################

[ 2025.310130] r8169 0000:02:00.0 enp2s0: link down
[ 2027.776136] usb 2-1.3: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2028.403352] rtl8xxxu 2-1.3:1.0 wlxe84e060dc5a4: renamed from wlan0
[ 2028.515039] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 2028.548458] r8169 0000:02:00.0 enp2s0: link down
[ 2028.548564] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 2028.550055] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready (repeated 3 times)
[ 2030.213189] wlxe84e060dc5a4: authenticate with <MAC 'Jetsons' [AC4]>
[ 2030.242427] wlxe84e060dc5a4: send auth to <MAC 'Jetsons' [AC4]> (try 1/3)
[ 2030.244201] wlxe84e060dc5a4: authenticated
[ 2030.249071] wlxe84e060dc5a4: associate with <MAC 'Jetsons' [AC4]> (try 1/3)
[ 2030.252538] wlxe84e060dc5a4: RX AssocResp from <MAC 'Jetsons' [AC4]> (capab=0x1431 status=0 aid=3)
[ 2030.254271] usb 2-1.3: rtl8xxxu_bss_info_changed: HT supported
[ 2030.256780] wlxe84e060dc5a4: associated
[ 2030.256818] usb 2-1.3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 2030.256870] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe84e060dc5a4: link becomes ready
[ 3124.573371] usb 2-1.3: rtl8xxxu_int_complete: Error -71
[ 3124.586374] usb 2-1.3: rtl8xxxu_active_to_lps: RX poll timed out (0x05f8)
[ 3124.591609] usb 2-1.3: rtl8xxxu_active_to_emu: Disabling MAC timed out
[ 3124.606665] wlxe84e060dc5a4: deauthenticating from <MAC 'Jetsons' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3124.606702] usb 2-1.3: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[ 3131.043605] rtl8821cu 2-1.3:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[ 3131.083937] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[ 3141.475336] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############
```

I did install a driver that didn't work (see post #1) and perhaps that is creating some problems? Anyhow, see what you can see from wireless.info.

---

### Post by jeremy31 on 2019-12-23
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
Post results for ```
modinfo -p 8821cu; grep [[:alnum:] /sys/module/8812cu/parameters/*
```

---

### Post by Bucky Ball on 2019-12-23
I ran the first two commands then issued your last command (all with the problematic NW602 dongle plugged in). Here are the results you requested from that last command.

```
:~$ modinfo -p 8821cu; grep [[:alnum:] /sys/module/8812cu/parameters/*
rtw_ips_mode:The default IPS mode (int)
rtw_lps_level:The default LPS level (int)
rtw_usb_rxagg_mode: (int)
rtw_dynamic_agg_enable: (int)
rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
rtw_rx_ampdu_sz_limit_1ss:RX AMPDU size limit for 1SS link of each BW, 0xFF: no limitation (array of uint)
rtw_rx_ampdu_sz_limit_2ss:RX AMPDU size limit for 2SS link of each BW, 0xFF: no limitation (array of uint)
rtw_rx_ampdu_sz_limit_3ss:RX AMPDU size limit for 3SS link of each BW, 0xFF: no limitation (array of uint)
rtw_rx_ampdu_sz_limit_4ss:RX AMPDU size limit for 4SS link of each BW, 0xFF: no limitation (array of uint)
rtw_vht_enable: (int)
rtw_vht_rx_mcs_map:VHT RX MCS map (uint)
rtw_rf_config: (int)
rtw_country_code:The default country code (in alpha2) (charp)
rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
rtw_excl_chs:exclusive channel array (array of uint)
rtw_btcoex_enable:BT co-existence on/off, 0:off, 1:on, 2:by efuse (int)
rtw_ant_num:Antenna number setting, 0:by efuse (int)
rtw_force_igi_lb:force IGI low-bound, 0:no specified (int)
rtw_qos_opt_enable: (int)
ifname:The default name to allocate for first interface (charp)
if2name:The default name to allocate for second interface (charp)
rtw_pwrtrim_enable: (int)
rtw_initmac: (charp)
rtw_special_rf_path: (int)
rtw_chip_version: (int)
rtw_rfintfs: (int)
rtw_lbkmode: (int)
rtw_network_mode: (int)
rtw_channel: (int)
rtw_mp_mode: (int)
rtw_wmm_enable: (int)
rtw_vrtl_carrier_sense: (int)
rtw_vcs_type: (int)
rtw_busy_thresh: (int)
rtw_ht_enable: (int)
rtw_bw_mode: (int)
rtw_ampdu_enable: (int)
rtw_rx_stbc: (int)
rtw_rx_ampdu_amsdu: (int)
rtw_tx_ampdu_amsdu: (int)
rtw_lowrate_two_xmit: (int)
rtw_power_mgnt: (int)
rtw_smart_ps: (int)
rtw_low_power: (int)
rtw_wifi_spec: (int)
rtw_full_ch_in_p2p_handshake: (int)
rtw_antdiv_cfg: (int)
rtw_antdiv_type: (int)
rtw_drv_ant_band_switch: (int)
rtw_single_ant_path: (int)
rtw_switch_usb_mode: (int)
rtw_enusbss: (int)
rtw_hwpdn_mode: (int)
rtw_hwpwrp_detect: (int)
rtw_hw_wps_pbc: (int)
rtw_check_hw_status: (int)
rtw_max_roaming_times:The max roaming times to try (uint)
rtw_mc2u_disable: (int)
rtw_80211d:Enable 802.11d mechanism (int)
rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
rtw_adaptivity_en:0:disable, 1:enable (uint)
rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
rtw_adaptivity_dml:0:disable, 1:enable (uint)
rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
rtw_adaptivity_th_l2h_ini:th_l2h_ini for Adaptivity (int)
rtw_adaptivity_th_edcca_hl_diff:th_edcca_hl_diff for Adaptivity (int)
rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
rtw_RFE_type:default init value:64 (uint)
rtw_powertracking_type:default init value:64 (uint)
rtw_GLNA_type:default init value:0 (uint)
rtw_TxBBSwing_2G:default init value:0xFF (uint)
rtw_TxBBSwing_5G:default init value:0xFF (uint)
rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
rtw_rxgain_offset_5gh: (uint)
rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_a:5G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_b:5G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_c:5G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_d:5G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_phy_file_path:The path of phy parameter (charp)
rtw_load_phy_file:PHY File Bit Map (int)
rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
rtw_en_napi: (int)
rtw_en_gro: (int)
grep: Unmatched [ or [^
```

---

### Post by praseodym on 2019-12-23
It loads 2 other drivers
```

echo -e "blacklist rtl8192cu\nblacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by Bucky Ball on 2019-12-23
Thanks for that, praseodym. Ran the command you gave, rebooted, and I'm using the NW602 and surfing heavily to see if/when it stops working. So far, so good. Still going after about ten minutes. (Make that 36 minutes.)

Getting late here so will try it tomorrow while streaming something on the Raspberry Pi/TV at the same time and see if it keeps working without a conflict and consistently for a few hours before marking as solved. Cheers. :)

---

### Post by Bucky Ball on 2019-12-23
Just tried this morning and as soon as I switched on my computer and tried to open a new webpage, the stream my wife was watching on the RPi in the other room stopped and so webpages stopped opening on my computer. Don't know what's going on here, but I've un-blacklisted the driver for my old wifi dongle and am using that. I've ordered the NW611, which is known to work with Linux, but any further suggestions re. the NW602 more than welcome. 

My mistake for buying the NW602 in the first place, even if it was by accident.

* Just to add to this, got a Youtube vid going on one of my other computers which uses the AC band whilst streaming something on the Raspberry Pi to the TV using ethernet cable. No issues half an hour later. So ... It appears to definitely be some conflict with running the NW602 which is bringing things to a grinding halt and not specific to using the AC band and streaming from the RPi at the same time. Truly befuddling, at least to me, as the NW602 is wireless AC and the Raspberry Pi is running on an ethernet cable. An anomaly.

---

### Post by praseodym on 2019-12-24
Check, if all MAC addresses are allowed. Deactivate the MAC filter in your router settings

---

### Post by jeremy31 on 2019-12-24
You can disable power management for the module of the problem wifi dongle
```
echo "options 8821cu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8821cu.conf
```
Reboot

---

### Post by Bucky Ball on 2019-12-24
Thanks to you all for your continued support with this. Much appreciated.

Whilst looking at the router settings, I noticed something. I run my devices using static IP addresses and the static IP address of the Raspberry Pi is 192.168.0.7. The static IP on the 2.4Ghz band of the computer I was having issues with is 192.168.0.5, but ... when setting up the static IP for the 5Ghz SSID on the problem computer, I'd set it to 192.168.0.7, same as the Raspberry Pi!!! 

All I've done so far is correct that error and set the 5Ghz connection on the computer to 192.168.0.5 and I'll run some more detailed experiments on things tomorrow (getting late here and watching cricket), but I have a feeling that is going to solve the problem. 

It probably explains why I could get a Youtube clip going for twenty minutes today using a different AC connected computer while streaming on the RPi without issue: they weren't both trying to use the same static IP address.

The matching static IP issue would explain a lot, including why my computer still falls in a heap even when nothing is streaming on the RPi. The RPi is always on so it is always using the 192.168.0.7 address and my computer was trying to use it, too.

Will get back after cricket and sleep, hopefully with some good news.

Thanks again. :)

PS: I also set the 5Ghz SSID on the router to 'AC only' rather than 'mixed b/g/n/ac'. That isn't the problem I wouldn't think, but can't hurt.

---

### Post by Bucky Ball on 2019-12-25
Well, I think my oversight has led us on a goose chase since post #4. Sorry about that. Reckon things were right then, except for the fact I'd used the same static IP address on the computer as on the Raspberry Pi. (In fact, if I'd have noticed the static IP conflict, may have been solved by post #2.)

After changing the IP on the computer last night, I used it for about an hour with no issues and the RPi has been streaming and I've been using my computer for a couple of hours today with no issues, no conflicts, and I'm getting better than ever speeds on the computer. So, as far as I can see, solved. I will mark it that way (and 'unsolve' it and get back to this thread if there is a hiccough with the AC dongle again).

Just a note: before I'd figured out the conflicting IP issue I un-blacklisted the driver for my other dongle so I could get back online and that is still unblacklisted and not causing any issues. Means I can use either the Simple[s]ton[/s]com NW602 AC600 dongle or the older wifi dongle if I ever need to. Which hopefully I won't. 

Cheers and thanks to all for your help.

---

