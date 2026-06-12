---
title: "WiFi rtl8xxxu problem"
date: 2016-04-24
forum: Networking &amp; Wireless
---

### Post by slackstick on 2016-04-24
Hi all,

I have an TP-LinkTL-WN822N USB adapter with following ID on Lubuntu 16.04: 
Bus 003 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter

On startup, I usually get following output of dmesg:
```
[    7.749716] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    7.750159] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    8.182939] cfg80211: World regulatory domain updated:
[    8.182942] cfg80211:  DFS Master region: unset
[    8.182942] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    8.182944] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    8.182945] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    8.182946] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    8.182947] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    8.182948] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    8.182949] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    8.182950] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    8.182951] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    8.239670] usb 3-1: Vendor: Realtek
[    8.239673] usb 3-1: Product: USB WLAN
[    8.239675] usb 3-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[    8.239676] usb 3-1: RTL8192CU MAC: 14:cc:20:1a:9a:89
[    8.239677] usb 3-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    8.248557] usb 3-1: Firmware revision 80.0 (signature 0x88c1)
[    8.404959] usb 3-1: Firmware failed to start
[    8.408162] usbcore: registered new interface driver rtl8xxxu
[    8.409465] rtl8xxxu 3-1:1.0 wlx14cc201a9a89: renamed from wlan0
[    8.427864] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready
[    8.433216] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready
[    8.502057] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready

But sometimes it also works from the beginning. When I unplug and re-plug the adapter, everything works well:

[  144.357453] usb 3-1: USB disconnect, device number 2
[  144.357720] usb 3-1: rtl8xxxu_int_complete: Error -108
[  144.363569] usb 3-1: rtl8xxxu_active_to_lps: RX poll timed out (0x05f8)
[  144.368946] usb 3-1: rtl8xxxu_active_to_emu: Disabling MAC timed out
[  144.368953] usb 3-1: disconnecting
[  146.629181] usb 3-1: new high-speed USB device number 6 using xhci_hcd
[  146.758834] usb 3-1: New USB device found, idVendor=0bda, idProduct=8178
[  146.758842] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  146.758846] usb 3-1: Product: USB WLAN
[  146.758849] usb 3-1: Manufacturer: Realtek
[  146.758853] usb 3-1: SerialNumber: 00e04c000001
[  146.816514] usb 3-1: Vendor: Realtek
[  146.816519] usb 3-1: Product: USB WLAN
[  146.816523] usb 3-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[  146.816526] usb 3-1: RTL8192CU MAC: 14:cc:20:1a:9a:89
[  146.816528] usb 3-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  146.816567] usb 3-1: Firmware revision 80.0 (signature 0x88c1)
[  148.261158] rtl8xxxu 3-1:1.0 wlx14cc201a9a89: renamed from wlan0
[  148.281091] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready
[  148.286890] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready
[  148.330137] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready
[  149.350039] wlx14cc201a9a89: authenticate with 08:96:d7:28:25:08
[  149.353911] wlx14cc201a9a89: send auth to 08:96:d7:28:25:08 (try 1/3)
[  149.356439] wlx14cc201a9a89: authenticated
[  149.357046] wlx14cc201a9a89: associate with 08:96:d7:28:25:08 (try 1/3)
[  149.364941] wlx14cc201a9a89: RX AssocResp from 08:96:d7:28:25:08 (capab=0x431 status=0 aid=4)
[  149.365586] usb 3-1: rtl8xxxu_bss_info_changed: HT supported
[  149.366311] wlx14cc201a9a89: associated
[  149.366356] IPv6: ADDRCONF(NETDEV_CHANGE): wlx14cc201a9a89: link becomes ready
[  149.419074] cfg80211: Regulatory domain changed to country: DE
[  149.419077] cfg80211:  DFS Master region: ETSI
[  149.419079] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  149.419081] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  149.419083] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  149.419085] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  149.419087] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
[  149.419088] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[  149.460164] usb 3-1: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
```

As this behaviour is annoying, help would be appreciated.

Thanks.

---

### Post by wildmanne39 on 2016-04-24
Please when posting code put the output here by clicking new reply then above the window you click on # and put the information in between the 2 code boxes ```

```.

Please post the output of the wireless script in my signature, it will provide a lot more information to help diagnose your issue. 
Thanks

---

### Post by slackstick on 2016-04-24
Thanks for the information and support.

When it fails, wireless.info shows:
```

########## wireless info START ##########

Report from: 24 Apr 2016 21:09 CEST +0200

Booted last: 24 Apr 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASRock Incorporation QCA8171 Gigabit Ethernet [1849:10a1]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 12d1:1037 Huawei Technologies Co., Ltd. Ideos
Bus 003 Device 004: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 003 Device 003: ID 045e:077b Microsoft Corp. 
Bus 003 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu               73728  0
mac80211              737280  1 rtl8xxxu
cfg80211              565248  1 mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

wlx14cc201a9a89 Link encap:Ethernet  HWaddr <MAC 'wlx14cc201a9a89' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlx14cc201a9a89  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       718     1  0 21:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx14cc201a9a89
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        USB WLAN
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx14cc201a9a89' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/net/wlx14cc201a9a89
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8171 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/enp2s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e05c6dfc-2be8-4bc0-9bb9-07eee39a66ae | Kabelnetzwerkverbindung 1

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/udmurtien]] (600 root)
[connection] id=udmurtien | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx14cc201a9a89' [IF]> | mac-address-blacklist= | ssid=udmurtien
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

wlx14cc201a9a89  14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlx14cc201a9a89  No scan results

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
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
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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
blacklist bluetooth

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

powertop --auto-tune
echo 'on' > '/sys/bus/usb/devices/3-2/power/control'
exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    7.859634] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready (repeated 2 times)
[    8.297457] usb 3-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    8.466079] rtl8xxxu 3-1:1.0 wlx14cc201a9a89: renamed from wlan0
[    8.481004] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready (repeated 3 times)

########## wireless info END ############

```

When it works, (after unplugging and re-plugging) I get:
```

########## wireless info START ##########

Report from: 24 Apr 2016 21:05 CEST +0200

Booted last: 24 Apr 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASRock Incorporation QCA8171 Gigabit Ethernet [1849:10a1]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 12d1:1037 Huawei Technologies Co., Ltd. Ideos
Bus 003 Device 004: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 003 Device 003: ID 045e:077b Microsoft Corp. 
Bus 003 Device 006: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

4: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu               73728  0
mac80211              737280  1 rtl8xxxu
cfg80211              565248  1 mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

wlx14cc201a9a89 Link encap:Ethernet  HWaddr <MAC 'wlx14cc201a9a89' [IF]>  
          inet addr:192.168.178.33  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlx14cc201a9a89' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104560553 (104.5 MB)  TX bytes:5731017 (5.7 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlx14cc201a9a89  IEEE 802.11bgn  ESSID:"udmurtien"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'udmurtien' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:553   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    600    0        0 wlx14cc201a9a89
192.168.178.0   0.0.0.0         255.255.255.0   U     600    0        0 wlx14cc201a9a89

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root       723     1  0 15:30 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx14cc201a9a89
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        USB WLAN
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx14cc201a9a89' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/net/wlx14cc201a9a89
GENERAL.IP-IFACE:                       wlx14cc201a9a89
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     udmurtien
GENERAL.CON-UUID:                       86bff9f8-d451-4749-85dd-b84009666499
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   86bff9f8-d451-4749-85dd-b84009666499 | udmurtien
IP4.ADDRESS[1]:                         192.168.178.33/24
IP4.GATEWAY:                            192.168.178.1
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.33
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1462385303
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlx14cc201a9a89' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8171 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/enp2s0
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

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
udmurtien  <MAC 'udmurtien' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/udmurtien]] (600 root)
[connection] id=udmurtien | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx14cc201a9a89' [IF]> | mac-address-blacklist= | ssid=udmurtien
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlx14cc201a9a89  13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlx14cc201a9a89  Scan completed :
          Cell 01 - Address: <MAC 'udmurtien' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"udmurtien"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a06196083b
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
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
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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
blacklist bluetooth

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

powertop --auto-tune
echo 'on' > '/sys/bus/usb/devices/3-2/power/control'
exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 7157.611475] usb 3-1: rtl8xxxu_active_to_emu: Disabling MAC timed out
[ 7162.126120] usb 3-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 7162.574731] rtl8xxxu 3-1:1.0 wlx14cc201a9a89: renamed from wlan0
[ 7162.612975] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready (repeated 2 times)
[ 7162.614618] IPv6: ADDRCONF(NETDEV_UP): wlx14cc201a9a89: link is not ready (repeated 3 times)
[ 7163.683875] wlx14cc201a9a89: authenticate with <MAC 'udmurtien' [AC1]>
[ 7163.687756] wlx14cc201a9a89: send auth to <MAC 'udmurtien' [AC1]> (try 1/3)
[ 7163.691756] wlx14cc201a9a89: authenticated
[ 7163.696072] wlx14cc201a9a89: associate with <MAC 'udmurtien' [AC1]> (try 1/3)
[ 7163.705387] wlx14cc201a9a89: RX AssocResp from <MAC 'udmurtien' [AC1]> (capab=0x431 status=0 aid=3)
[ 7163.705936] usb 3-1: rtl8xxxu_bss_info_changed: HT supported
[ 7163.706661] wlx14cc201a9a89: associated
[ 7163.706705] IPv6: ADDRCONF(NETDEV_CHANGE): wlx14cc201a9a89: link becomes ready
[ 7163.758065] usb 3-1: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START

########## wireless info END ############

```

---

