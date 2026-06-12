---
title: "QCA6174 not working in Ubuntu 16.04 after running upgrade yesterday"
date: 2016-07-02
forum: Networking &amp; Wireless
---

### Post by Andask on 2016-07-02
Note: I created a question about the same problem in askubuntu, I hope it's ok to post it here too. If I found a solution in one place I'll past it in the other too, to help others.

I already had a problem with this before, and I was able to get it working using the drivers here: [https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174](https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174).

But after running Ubuntu upgrade (yesterday) I can't get the wifi connection anymore, I created a pastebin with the log of this here: [http://pastebin.com/y6Pyj4nm](http://pastebin.com/y6Pyj4nm).

I have tried replacing the firmware again both with the kvalo and the FireWalkerX fork, with no result.

I'v also created a pastebin with the output of the wireless-info script recommended, here: [http://pastebin.com/Mi6mAqj8](http://pastebin.com/Mi6mAqj8).

```

sudo ethtool -i wlp5s0
    driver: ath10k_pci
    version: 4.5.2-040502-generic
    firmware-version: WLAN.RM.2.0-00180-QCARMSWPZ-1
    expansion-rom-version: 
    bus-info: 0000:05:00.0
    supports-statistics: yes
    supports-test: no
    supports-eeprom-access: no
    supports-register-dump: no
    supports-priv-flags: no

```

```

lspci -nnk | grep 0280 -A2
    05:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)

```

```

sudo rfkill list all
    0: hci0: Bluetooth
        Soft blocked: yes
        Hard blocked: no
    1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

```

sudo lshw -C network
  *-network               
       descrição: Ethernet interface
       produto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       ID físico: 0
       informações do barramento: pci@0000:04:00.0
       nome lógico: enp4s0
       versão: 10
       serial: 20:47:47:75:50:37
       tamanho: 10Mbit/s
       capacidade: 1Gbit/s
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuração: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:319 porta de E/S:d000(tamanho=256) memória:df504000-df504fff memória:df500000-df503fff
  *-network DISABLED
       descrição: Interface sem fio
       produto: QCA6174 802.11ac Wireless Network Adapter
       fabricante: Qualcomm Atheros
       ID físico: 0
       informações do barramento: pci@0000:05:00.0
       nome lógico: wlp5s0
       versão: 32
       serial: a8:a7:95:d2:46:bb
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuração: broadcast=yes driver=ath10k_pci driverversion=4.5.2-040502-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       recursos: irq:323 memória:df200000-df3fffff

```

---

### Post by jeremy31 on 2016-07-02
Use this file for firmware so it will not be replaced with updates

```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```
Reboot

---

### Post by Andask on 2016-07-02
Hi @jeremy31 thanks for the reply.

I've done this with no result, still can't connect to wifi.

I've updated the post with the output of [COLOR=#000000][FONT=&quot]lshw -C network[/FONT][/COLOR].

---

### Post by jeremy31 on 2016-07-02
Run the wireless script again and post the new result.  You dont need to add it to the first post like askubuntu

---

### Post by Andask on 2016-07-02
Oh ok, I edited the first post because I forgot to add it there before.

Also, here is the new result:
```



########## wireless info START ##########


Report from: 02 Jul 2016 12:10 BRT -0300


Booted last: 02 Jul 2016 00:00 BRT -0300


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.5.2-040502-generic #201604200335 SMP Wed Apr 20 07:37:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0706]
	Kernel driver in use: r8169


05:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Dell QCA6174 802.11ac Wireless Network Adapter [1028:0310]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e007 Atheros Communications, Inc. 
Bus 001 Device 004: ID 1bcf:2b8a Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 002: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0
ath10k_pci             45056  0
ath10k_core           319488  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              741376  1 ath10k_core
dell_laptop            20480  0
cfg80211              577536  3 ath,mac80211,ath10k_core
dcdbas                 16384  1 dell_laptop
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp4s0    no wireless extensions.


lo        no wireless extensions.


wlp5s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
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


root       802     1  1 12:07 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/enp4s0
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


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/wlp5s0
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


[[/etc/NetworkManager/system-connections/Casa]] (600 root)
[connection] id=Casa | type=wifi | permissions=user:dirty:;
[wifi] mac-address=<MAC 'wlp5s0' [IF2]> | mac-address-blacklist= | ssid=Casa
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


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


enp4s0    no frequency information.


lo        no frequency information.


wlp5s0    32 channels in total; available frequencies :
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


wlp5s0    Interface doesn't support scanning : Network is down


enp4s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     F411BB3F1A8E9CA7FB30C39
depends:        ath10k_core
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     304D8B128FFE6789A6CDD13
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CC4EF0BEC141C8AE7D0A659
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     CAB0052D4485B3B2226F1ED
depends:        
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N


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


[/etc/modprobe.d/blacklist-nouveau.conf]
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off


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


[    5.871507] ath10k_pci 0000:05:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    7.287751] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[    7.357139] r8169 0000:04:00.0 enp4s0: link down
[    7.357192] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[    8.015516] ath10k_pci 0000:05:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   11.014694] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   11.083184] ath: EEPROM regdomain: 0x6c
[   11.083186] ath: EEPROM indicates we should expect a direct regpair map
[   11.083188] ath: Country alpha2 being used: 00
[   11.083188] ath: Regpair used: 0x6c
[   11.088933] ath10k_pci 0000:05:00.0 wlp5s0: renamed from wlan0
[   11.106065] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   16.346167] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   22.345563] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   27.685048] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   33.684457] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   38.996066] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   44.995341] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   60.241868] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   66.241156] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   71.552738] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   77.552171] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   93.246621] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   99.246196] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  104.557501] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  110.556770] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  126.243200] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  132.242640] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  137.554308] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  143.553820] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  159.240122] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  165.239390] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  170.551119] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  176.550502] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  192.236720] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  198.236215] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  203.547864] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  209.547192] ath10k_pci 0000:05:00.0: could not suspend target (-11)


########## wireless info END ############



```

---

### Post by jeremy31 on 2016-07-02
Lets remove the firmware folder and use that download to reinstall ```
sudo rm -r /lib/firmware/ath10k/QCA6174/hw3.0/
```
```
sudo dpkg -i linux-firmware_1.158_all.deb
```

---

### Post by Andask on 2016-07-02
[https://www.diffchecker.com/ct9kyqzjDid](https://www.diffchecker.com/ct9kyqzjDid) it, but without results.
Removed, installed and rebooted.

Here is the new wireless-info result if it's needed:
```



########## wireless info START ##########


Report from: 02 Jul 2016 15:33 BRT -0300


Booted last: 02 Jul 2016 00:00 BRT -0300


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.5.2-040502-generic #201604200335 SMP Wed Apr 20 07:37:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0706]
    Kernel driver in use: r8169


05:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Dell QCA6174 802.11ac Wireless Network Adapter [1028:0310]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e007 Atheros Communications, Inc. 
Bus 001 Device 004: ID 1bcf:2b8a Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 002: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           319488  1 ath10k_pci
dell_wmi               16384  0
ath                    32768  1 ath10k_core
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0
mac80211              741376  1 ath10k_core
dell_laptop            20480  0
cfg80211              577536  3 ath,mac80211,ath10k_core
dcdbas                 16384  1 dell_laptop
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp4s0    no wireless extensions.


lo        no wireless extensions.


wlp5s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
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


root       738     1  1 15:31 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/enp4s0
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


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/wlp5s0
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


[[/etc/NetworkManager/system-connections/Casa]] (600 root)
[connection] id=Casa | type=wifi | permissions=user:dirty:;
[wifi] mac-address=<MAC 'wlp5s0' [IF2]> | mac-address-blacklist= | ssid=Casa
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


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


enp4s0    no frequency information.


lo        no frequency information.


wlp5s0    32 channels in total; available frequencies :
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


wlp5s0    Interface doesn't support scanning : Network is down


enp4s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     F411BB3F1A8E9CA7FB30C39
depends:        ath10k_core
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     304D8B128FFE6789A6CDD13
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CC4EF0BEC141C8AE7D0A659
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     CAB0052D4485B3B2226F1ED
depends:        
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N


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


[/etc/modprobe.d/blacklist-nouveau.conf]
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off


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


[    4.600673] ath10k_pci 0000:05:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    4.846770] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/cal-pci-0000:05:00.0.bin failed with error -2
[    4.850122] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.850125] ath10k_pci 0000:05:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    5.015873] ath10k_pci 0000:05:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1028:0310
[    5.015875] ath10k_pci 0000:05:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    5.016285] ath10k_pci 0000:05:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    5.109031] ath10k_pci 0000:05:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=1028,subsystem-device=0310 from ath10k/QCA6174/hw3.0/board-2.bin
[    5.116511] ath10k_pci 0000:05:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    5.518555] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[    5.545325] r8169 0000:04:00.0 enp4s0: link down
[    5.545400] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[    7.260258] ath10k_pci 0000:05:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   10.258783] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   10.328628] ath: EEPROM regdomain: 0x6c
[   10.328630] ath: EEPROM indicates we should expect a direct regpair map
[   10.328632] ath: Country alpha2 being used: 00
[   10.328632] ath: Regpair used: 0x6c
[   10.333465] ath10k_pci 0000:05:00.0 wlp5s0: renamed from wlan0
[   10.350608] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   15.598485] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   21.598024] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   26.913565] ath10k_pci 0000:05:00.0: failed to set tx-chainmask: -11, req 0x3
[   29.913415] ath10k_pci 0000:05:00.0: failed to set arp ac override parameter: -11
[   35.912830] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   41.232549] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   47.231938] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   62.254829] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   68.254479] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   73.566072] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   79.565599] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   95.252284] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  101.251981] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  106.563567] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  112.563142] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  128.253785] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  134.253458] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[  139.564949] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[  145.564641] ath10k_pci 0000:05:00.0: could not suspend target (-11)


########## wireless info END ############



```

I've noticed something, I don't know if it's important, but between runs the result can be a bit different, in one the ifconfig had:
```

wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1

```
And in the other:
```

wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF2]>  
          BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

---

### Post by jeremy31 on 2016-07-02
I have seen this before, this Dell model doesn't like the board-2.bin
```
sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin
```

Reboot

Consider rebooting into an Ubuntu kernel and removing the 4.5.2 that you installed to keep your system secure.  Ubuntu does security patches from the newest kernels on its 4.4 kerneland the 4.4.0-28 may have much better security than 4.5.2

---

### Post by Andask on 2016-07-02
It's the Dell 7000 "gaming edition".
Removed and rebooted (4.5.2 kernel, just read your comment about it after coming back to Windows), with no results.

Oh, thx for the heads up, I'll do it.

```



########## wireless info START ##########


Report from: 02 Jul 2016 16:19 BRT -0300


Booted last: 02 Jul 2016 00:00 BRT -0300


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.5.2-040502-generic #201604200335 SMP Wed Apr 20 07:37:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0706]
	Kernel driver in use: r8169


05:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Dell QCA6174 802.11ac Wireless Network Adapter [1028:0310]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e007 Atheros Communications, Inc. 
Bus 001 Device 004: ID 1bcf:2b8a Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 002: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0
ath10k_pci             45056  0
ath10k_core           319488  1 ath10k_pci
ath                    32768  1 ath10k_core
dell_laptop            20480  0
mac80211              741376  1 ath10k_core
dcdbas                 16384  1 dell_laptop
cfg80211              577536  3 ath,mac80211,ath10k_core
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp4s0    no wireless extensions.


lo        no wireless extensions.


wlp5s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
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


root       815     1  4 16:19 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/enp4s0
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


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/wlp5s0
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


[[/etc/NetworkManager/system-connections/Casa]] (600 root)
[connection] id=Casa | type=wifi | permissions=user:dirty:;
[wifi] mac-address=<MAC 'wlp5s0' [IF2]> | mac-address-blacklist= | ssid=Casa
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


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


enp4s0    no frequency information.


lo        no frequency information.


wlp5s0    32 channels in total; available frequencies :
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


wlp5s0    Interface doesn't support scanning : Network is down


enp4s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     F411BB3F1A8E9CA7FB30C39
depends:        ath10k_core
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     304D8B128FFE6789A6CDD13
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CC4EF0BEC141C8AE7D0A659
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     CAB0052D4485B3B2226F1ED
depends:        
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N


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


[/etc/modprobe.d/blacklist-nouveau.conf]
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off


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


[    4.211354] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/cal-pci-0000:05:00.0.bin failed with error -2
[    4.214025] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.214027] ath10k_pci 0000:05:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.222643] ath10k_pci 0000:05:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1028:0310
[    4.222645] ath10k_pci 0000:05:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.223020] ath10k_pci 0000:05:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    4.285193] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    4.285749] ath10k_pci 0000:05:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    5.105604] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[    5.125778] r8169 0000:04:00.0 enp4s0: link down
[    5.125834] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[    6.428590] ath10k_pci 0000:05:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    9.427167] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[    9.498413] ath: EEPROM regdomain: 0x6c
[    9.498416] ath: EEPROM indicates we should expect a direct regpair map
[    9.498419] ath: Country alpha2 being used: 00
[    9.498419] ath: Regpair used: 0x6c
[    9.506430] ath10k_pci 0000:05:00.0 wlp5s0: renamed from wlan0
[    9.527956] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   14.770710] ath10k_pci 0000:05:00.0: failed to enable dynamic BW: -11
[   20.770138] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   26.089886] ath10k_pci 0000:05:00.0: failed to set tx-chainmask: -11, req 0x3
[   29.089484] ath10k_pci 0000:05:00.0: failed to set arp ac override parameter: -11
[   35.088894] ath10k_pci 0000:05:00.0: could not suspend target (-11)
[   40.404393] ath10k_pci 0000:05:00.0: failed to set rx-chainmask: -11, req 0x3
[   43.404164] ath10k_pci 0000:05:00.0: failed to set arp ac override parameter: -11
[   49.403776] ath10k_pci 0000:05:00.0: could not suspend target (-11)


########## wireless info END ############



```

---

### Post by jeremy31 on 2016-07-03
Try this
```
sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/*
```
```
sudo wget https://github.com/FireWalkerX/ath10k-firmware/blob/7e56cbb94182a2fdab110cf5bfeded8fd1d44d30/QCA6174/hw3.0/board-2.bin?raw=true /lib/firmware/ath10k/QCA6174/hw3.0/board.bin
```
```
sudo wget https://github.com/FireWalkerX/ath10k-firmware/blob/7e56cbb94182a2fdab110cf5bfeded8fd1d44d30/QCA6174/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1?raw=true /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin
```

Reboot

---

### Post by Andask on 2016-07-03
Hey, it's working now! :)

Thank you so much for you patience!

I've tried the FireWalkerX fork before, but I didn't renamed the board-2.bin to board.bin that time.
Doing this as you told did the trick.

---

