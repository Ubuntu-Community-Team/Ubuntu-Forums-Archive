---
title: "Wifi doesn't work after (some) reboots."
date: 2017-06-25
forum: Networking &amp; Wireless
---

### Post by js10002 on 2017-06-25
Hello everyone,

My wifi is acting weird again. Since few weeks, after a regular reboot, the wifi will not be working anymore. The little wifi icon on top is empty, showing that no signal is received. the rolldown list from that icon shows that "Enable Wifi" is active and ticked. But there is no wireless network to choose.

Then, after I reboot a few times, the Wifi becomes available again and will remain available.

The wifi _usually_ remains available after waking up from sleep mode. 

Please help :KS

Here is the wireless info when WIFI is NOK

```



########## wireless info START ##########


Report from: 25 Jun 2017 09:09 CEST +0200


Booted last: 25 Jun 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-81-generic #104-Ubuntu SMP Wed Jun 14 08:17:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################


01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    DeviceName: Realtek PCIe GBE Family Controller
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:1894]


02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Ada
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c0e Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:7160 (7.1 KB)  TX bytes:7160 (7.1 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:off/any  
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


root       798     1  1 09:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.2/net/eno1
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


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-81-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlo1
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
WIFI-PROPERTIES.5GHZ:                   no
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
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/DELIONNETFAMILY]] (600 root)
[connection] id=DELIONNETFAMILY | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=DELIONNETFAMILY
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Livebox-4881]] (600 root)
[connection] id=Livebox-4881 | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=Livebox-4881
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Livebox-0FB2]] (600 root)
[connection] id=Livebox-0FB2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=Livebox-0FB2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HUAWEI-B310-96D3]] (600 root)
[connection] id=HUAWEI-B310-96D3 | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=HUAWEI-B310-96D3
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Livebox-F2DE]] (600 root)
[connection] id=Livebox-F2DE | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=Livebox-F2DE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HUAWEI B310FF40]] (600 root)
[connection] id=HUAWEI B310FF40 | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=HUAWEI B310FF40
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/mon-reseau]] (600 root)
[connection] id=mon-reseau | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=mon-reseau
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/yougorgeous]] (600 root)
[connection] id=yougorgeous | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=yougorgeous
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/kieboom]] (600 root)
[connection] id=kieboom | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=kieboom
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


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


eno1      no frequency information.


wlo1      14 channels in total; available frequencies :
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


lo        Interface doesn't support scanning.


wlo1      Interface doesn't support scanning : Network is down


eno1      Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-81-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5EFE430950E66A71D6E20F9
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-81-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     48C96882CCDC964173BE1D1
depends:        
intree:         Y
vermagic:       4.4.0-81-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: N


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


coretemp


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


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


##### dmesg #############################


[    4.229793] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[    4.233409] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[    4.641968] rt2800pci 0000:02:00.0 wlo1: renamed from wlan0
[    6.194700] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    6.194750] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[    6.196713] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[    7.812152] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[    9.412201] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[    9.416762] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    9.491213] r8169 0000:01:00.2 eno1: link down
[    9.491277] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   11.152196] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   12.752205] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   14.368162] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   15.968171] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   27.648227] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   29.248269] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   30.864297] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   32.464310] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   44.656394] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   46.256415] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   47.872350] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   49.480440] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   61.656473] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   63.260535] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   64.876538] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   66.476585] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)


########## wireless info END ############

```

I'll try to get the wifi back ON and get a log from there, in the next post.


Thanks a lot !!!

Xavier

---

### Post by js10002 on 2017-06-25
And here is the log when wifi finally works .. maybe you can find it of some use.

```



########## wireless info START ##########


Report from: 25 Jun 2017 16:59 CEST +0200


Booted last: 25 Jun 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-81-generic #104-Ubuntu SMP Wed Jun 14 08:17:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################




01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
	DeviceName: Realtek PCIe GBE Family Controller
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:1894]


02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Ada
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c0e Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr 6c:3b:e5:80:b6:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:37713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31684952 (31.6 MB)  TX bytes:4514130 (4.5 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:483045 (483.0 KB)  TX bytes:483045 (483.0 KB)


wlo1      Link encap:Ethernet  HWaddr a4:17:31:47:f2:b3  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a01:cb04:5ab:d300:f26a:a9bd:54e0:7226/64 Scope:Global
          inet6 addr: fe80::7b45:8243:e8ce:ccd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1873438 (1.8 MB)  TX bytes:1162440 (1.1 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:"Livebox-0FB2"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: B8:26:6C:C5:0F:B2   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:58   Missed beacon:0




##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       865     1  0 11:05 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-81-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         xx:17:31:47:F2:B3
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Livebox-0FB2
GENERAL.CON-UUID:                       xxxxxxx-bf86-4a2d-a428-ed30b170bec2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/9
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     26 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{11}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   xxxxxxxxx-bf86-4a2d-a428-ed30b170bec2 | Livebox-0FB2
IP4.ADDRESS[1]:                         192.168.1.16/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.16
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1498489122
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:42:38:32:36:36:43:5:f:41:4e:31:35:33:30:39:32:35:38:32:39:32:32:36:6:9:4c:69:76:65:62:6f:78:20:33
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         2a01:cb04:5ab:d300:f26a:a9bd:54e0:7226/64
IP6.ADDRESS[2]:                         fe80::7b45:8243:e8ce:ccd5/64
IP6.GATEWAY:                            fe80::ba26:6cff:fec5:fb2
IP6.ROUTE[1]:                           dst = 2a01:cb04:5ab:d300::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fe80::ba26:6cff:fec5:fb2
IP6.DOMAIN[1]:                          home
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::ba26:6cff:fec5:fb2
DHCP6.OPTION[3]:                        dhcp6_domain_search = home.
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_server_id = 0:1:0:1:20:db:b0:8f:b8:26:6c:c5:f:b2
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:78:3e:f4:15:b5:22:ca:ed:6a:7:24:ba:4c:79:9b:45


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         xx:3B:E5:80:B6:41
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.2/net/eno1
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 




SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
orange           CA:26:6C:C5:0F:B2  Infra  12    2467 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  --           no        
Livebox-0FB2     xx:xx:6C:C5:0F:B2  Infra  12    2467 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA1 WPA2    yes     * 
PJFreebox        F4:CA:E5:C8:18:BC  Infra  3     2422 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        
Livebox-D8BD     30:7C:B2:2E:D8:BD  Infra  6     2437 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2    no        
FreeWifi_secure  E6:A6:53:55:50:03  Infra  12    2467 MHz  54 Mbit/s  20      &#9602;___  WPA1 802.1X  no        
orange           9A:26:6C:5B:86:12  Infra  1     2412 MHz  54 Mbit/s  17      &#9602;___  --           no        
Livebox-8612     B8:26:6C:5B:86:12  Infra  1     2412 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2    no        
FreeWifi         E6:A6:53:55:50:02  Infra  12    2467 MHz  54 Mbit/s  17      &#9602;___  --           no        
SFR_7EA8         24:95:04:7F:7E:AC  Infra  6     2437 MHz  54 Mbit/s  14      &#9602;___  WPA1         no        
Doume            E6:A6:53:55:50:00  Infra  12    2467 MHz  54 Mbit/s  14      &#9602;___  WPA1         no        


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
managed=true


##### NetworkManager profiles ###########




```

---

### Post by js10002 on 2017-06-25
but just to be clear, the issue is still here :) i just got lucky that wifi finally started working  ...

---

### Post by jeremy31 on 2017-06-25
It might be wifi power management causing the issue
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

I think chili555 has found that disabling Wireless N mode on the wireless router might also fix it

---

### Post by js10002 on 2017-06-25
Hi Jeremy,

The commands above didn't work, but thanks a lot for taking the time to try and help me.
Just to be sure, I checked the file "[COLOR=#000000][FONT=&quot]/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf"[/FONT][/COLOR]
and it does contain the following text :
> [connection]
wifi.powersave = 2


I rebooted twice.

I have no such control over the router because it's integrated in the internet box. Can't choose the wifi mode. But I don't think the router is "blinding" my wifi. There are other wifi networks around and I can't see them either when my PC wifi is "down". 

Looks like my internal wifi antenna is getting disconnected ? That's weird though...

If there's anything else I can try , please let me know.

X.

---

### Post by him610 on 2017-06-25
Hello js10002,

Are you really in France?
> 
Region: Europe/Paris (based on set time zone)


country 00: DFS-UNSET 

It may help to set your country code permanently. There are one or two steps to take to set your country code, 
```
sudo reg set IS
``` or your country code if not Iceland (this sets it temporarily)
```
sudo nano /etc/default/crda
```
To make it permanent, edit the last line to read
```
REGDOMAIN=IS
```
Learned this corrective procedure from reading chili555's responses in this forum.

---

### Post by js10002 on 2017-07-01
Hi him610,

Yes, I'm in France.

So I set the last line of the file [COLOR=#000000][FONT=&quot]/etc/default/crda [/FONT][/COLOR]to REGDOMAIN=FR. I'll reboot now.

*Note : The "reg" command wasn't found, but it doesn't matter, as long as I changed the CRDA file content*

BR / Xavier

---

### Post by js10002 on 2017-07-01
Hi again ):P

The action didn't work. I'm now connected to the wired nw.
Here are the intesresting bits in the wirelessinfo text :

```
GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-83-generic
GENERAL.FIRMWARE-VERSION:               N/A
[COLOR=#ff0000]**GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>**[/COLOR]
GENERAL.MTU:                            1500[COLOR=#ff0000][B]
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)[/B][/COLOR]
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       
(...)
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no


(...)


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)

[COLOR=#ff0000]
country FR: DFS-ETSI[/COLOR]
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)




##### iwlist scan #######################


lo        Interface doesn't support scanning.


[B][COLOR=#ff0000]wlo1      Interface doesn't support scanning : Network is down
[/COLOR][/B]

eno1      Interface doesn't support scanning.


(...)


##### dmesg #############################


[    3.735971] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[    3.746451] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[B][COLOR=#ff0000][    3.917624] rt2800pci 0000:02:00.0 wlo1: renamed from wlan0
[/COLOR][/B][    5.551735] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    5.551793] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[    5.555411] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[    7.168124] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[    8.768192] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[    8.773650] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    8.851197] r8169 0000:01:00.2 eno1: link down
[    8.851263] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   10.548227] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   12.148288] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   13.764331] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   15.364457] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   27.657064] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   29.257072] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   30.873186] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   32.473259] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   44.653917] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   46.254025] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   47.874078] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   49.474142] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
```


I don't know if that helps... 
But thanks a lot guys for attempting to help ! It's really nice for you to spend some time on this.

Br / Xavier

---

### Post by js10002 on 2017-07-01
And now I just close the lid of the computer, while connected to Wired, and reopened it a minute later. And guess what... Wifi is back !!

```
##### dmesg #############################


[ 1000.282292] r8169 0000:01:00.2 eno1: link down
[ 1003.105118] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[ 1003.227431] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 1003.302313] r8169 0000:01:00.2 eno1: link down
[ 1003.302415] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 1003.362222] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1005.040595] wlo1: authenticate with <MAC 'Livebox-0FB2' [AC3]>
[ 1005.055497] wlo1: send auth to <MAC 'Livebox-0FB2' [AC3]> (try 1/3)
[ 1005.057459] wlo1: authenticated
[ 1005.059321] wlo1: associate with <MAC 'Livebox-0FB2' [AC3]> (try 1/3)
[ 1005.067628] wlo1: RX AssocResp from <MAC 'Livebox-0FB2' [AC3]> (capab=0x431 status=0 aid=3)
[ 1005.067738] wlo1: associated
[ 1005.067794] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[ 1005.280390] r8169 0000:01:00.2 eno1: link up
[ 1005.280401] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready


########## wireless info END ############
```


Shall I post again the 2 latest wireless-info-texts ( With and Without Wifi) ?

---

### Post by js10002 on 2017-07-04
(up) problem was not solved...

---

### Post by jeremy31 on 2017-07-04
Can you make the wireless router use Wireless 11G instead of 11N?

---

### Post by js10002 on 2017-07-05
Hi Jeremy, no that's not possible.

---

### Post by js10002 on 2017-07-10
Hi everyone,

Does anyone have other suggestions I could try ? I think the DMESG printout shows weird stuff...
Also, I just rebooted with LAN cable plugged in : the wired interface didn't come up automatically. I had to unplug and replug the cable for the intf to come up !

```
[    1.802450] r8169 0000:01:00.2 eno1: renamed from eth0[    5.743979] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    5.821261] r8169 0000:01:00.2 eno1: link down
[    5.821331] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    7.744223] r8169 0000:01:00.2 eno1: link up
[    9.042574] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   43.058401] r8169 0000:01:00.2 eno1: link down
[   47.542750] r8169 0000:01:00.2 eno1: link up

```

Regarding the wLan those lines are weird : (why does it get renamed ??)

```

[    4.136785] rt2800pci 0000:02:00.0 wlo1: renamed from wlan0
[    5.828119] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready

```

And here, probably the main issue that prevents the proper start of wLan interface :

```

[   44.665065] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.265215] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.265221] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

```

Please help :)

---

### Post by BenginM on 2017-07-10
> **js10002 said:**
> Hi everyone,

Does anyone have other suggestions I could try ? I think the DMESG printout shows weird stuff...
Also, I just rebooted with LAN cable plugged in : the wired interface didn't come up automatically. I had to unplug and replug the cable for the intf to come up !

```
[    1.802450] r8169 0000:01:00.2 eno1: renamed from eth0[    5.743979] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    5.821261] r8169 0000:01:00.2 eno1: link down
[    5.821331] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    7.744223] r8169 0000:01:00.2 eno1: link up
[    9.042574] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   43.058401] r8169 0000:01:00.2 eno1: link down
[   47.542750] r8169 0000:01:00.2 eno1: link up

```


Please help :)

[COLOR=#b22222]Salutations!

regarding the ethernet errors , run[/COLOR]: $

nmcli dev 

and

cat /sys/class/net/eno1/carrier

[COLOR=#ff0000]if a cable is plugged in, and 'ifconfig' shows the interface is UP, then we expect /sys/class/net/[/COLOR][COLOR=#ff0000]eno1/carrier to be 1.  If that's not the case, then there's a driver bug in the kernel.

Run :  [/COLOR][COLOR=#000000]watch -n 1 "dmesg | tail -n 30"[/COLOR][COLOR=#ff0000]

and plug/unplug the cable every 2 seconds or so, do you see a corresponding message for each plug/unplug?  If not, it's almost definitely a kernel bug.

as for the wifi issue , to catch what's happing unplug the ether cable and run:

[/COLOR][COLOR=#000000]tail -f /var/log/syslog[/COLOR][COLOR=#ff0000]

[/COLOR][COLOR=#000000]tail -f /var/log/dmesg[/COLOR][COLOR=#ff0000]

and see what logs through at you ..

[/COLOR]you're kerenl base [COLOR=#000000]currently is [/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]Linux 4.4.0-81-generic[/COLOR]

Did this issue start happening after an update/upgrade?  Was there a 
prior kernel version where you were not having this particular problem? regarding the wifi issue... it might not be a wireless kernel driver issue , but rather a power management suspend/sleep/hibernate issue !  now am curious as to what's inside /etc/pm/sleep.d  !

also , does this file exist !

/etc/pm/config.d/config


## [COLOR=#ff0000]for future references[/COLOR] :

 you might want to install and test a new kernel / kernel 4.10.0-26 for a week or so. you can install a new kernel manually. currently linux kernel 4.10 is available in the repo.

You could always do the following in terminal run:

apt-cache search linux-image

Pick the one you want and then do:

sudo apt-get install linux-image-your_version_choice

and

sudo apt-get install linux-image-extra-your_version_choice

you may install it as a deb package , #See:

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

 ## Or use Ukuu:

[URL="https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu"]https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu


[/URL]

---

### Post by BenginM on 2017-07-10
> **js10002 said:**
> Hi everyone,


And here, probably the main issue that prevents the proper start of wLan interface :

```

[   44.665065] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.265215] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.265221] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

```

Please help :)

i didn't find much about that error! what i w'd suggest to make sure everything in your system is in place and in a good state is to update the kernel and linux-firmware packages .. as you're still running kernel 4.4.- and with a lower inux-firmware version .. my kernel base is 4.8.0-58 which is "hwe-16.04 "  , and inux-firmware 1.57.11

## sudo apt update && sudo apt-get dist-upgrade  , and #see :
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#LTS_Enablement_Stacks](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#LTS_Enablement_Stacks)

---

### Post by BenginM on 2017-07-10
> **js10002 said:**
> 

Regarding the wLan those lines are weird : (why does it get renamed ??)

```

[    4.136785] rt2800pci 0000:02:00.0 wlo1: renamed from wlan0
[    5.828119] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready

```

And here, probably the main issue that prevents the proper start of wLan interface :

```

[   44.665065] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.265215] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.265221] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

```



Well, actually i just came across this ... #See chili's555 comments in :
[https://ubuntuforums.org/showthread.php?t=2334099](https://ubuntuforums.org/showthread.php?t=2334099)

---

### Post by js10002 on 2017-07-12
Hi Sary.sa ,

Thank you so much for taking an interest ! You asked so many things, I'm gonna focus on the wireless fix first.

[SIZE=5]**SLEEP**[/SIZE]

```
ls /etc/pm/sleep.d10_grub-common  10_unattended-upgrades-hibernate  novatel_3g_suspend

```

```
more 10_grub-common 
#!/bin/sh


# Tell grub that resume was successful


case "$1" in
    thaw)
        [ -s /boot/grub/grubenv ] || rm -f /boot/grub/grubenv
        mkdir -p /boot/grub
        grub-editenv /boot/grub/grubenv unset recordfail
        ;;
esac
```

```
more 10_unattended-upgrades-hibernate 
#!/bin/sh


# Action script ensure that unattended-upgrades is finished 
# before a hibernate 


PATH=/sbin:/usr/sbin:/bin:/usr/bin
SHUTDOWN_HELPER=/usr/share/unattended-upgrades/unattended-upgrade-shutdown


if [ -x /usr/bin/python3 ]; then
    PYTHON=python3
else
    PYTHON=python
fi


if [ ! -x /usr/share/unattended-upgrades/unattended-upgrade-shutdown ]; then
    exit 0
fi


case "${1}" in
        hibernate)
                if [ -e $SHUTDOWN_HELPER ]; then
                 $PYTHON $SHUTDOWN_HELPER
                fi
                ;;
        resume|thaw)
        # nothing
                ;;
esac
```

```
more novatel_3g_suspend 
#! /bin/sh


# This script puts the Novatel 3G modem in Toshiba Portege R500 to USB
# suspend before going to sleep. Otherwise it may be in a weird state
# (...)


BUS=2
DEVICE=2


if [ ! -x /sys/bus/usb/devices/${BUS}-${DEVICE}/power/level ]; then
    exit 0
fi


case $1 in
     suspend|suspend_hybrid|hibernate)
    echo suspend > /sys/bus/usb/devices/${BUS}-${DEVICE}/power/level
        ;;
     resume|thaw)
    # No need to do anything here, kernel unsuspends USB devices
    :
        ;;
esac
```



[SIZE=5][B]CONFIG FILE EXIST ?
[/B][SIZE=2]
```
this file does not exist, the conf.d folder is empty
```


[/SIZE][/SIZE]**SW upgrade ?**[SIZE=5][SIZE=2]

You're right, my O/S was due for an upgrade. I ran apt commands, and rebooted. But the Wifi didn't come up.
I went to "hibernate", then woke it up : Wifi was UP !!


[/SIZE][/SIZE][h=1]**[SIZE=5]Thread: [no wireless connection, wlan0 and eth0 devices not found]("https://ubuntuforums.org/showthread.php?t=2334099")[/SIZE]**[/h][SIZE=5]**[https://ubuntuforums.org/showthread.php?t=2334099](https://ubuntuforums.org/showthread.php?t=2334099)**[SIZE=2]

Yes, it looks an awful lot like my issue... but i can't control the wifi type (g or n) from my box. I never had an issue prior to few weeks ago... and the fact that it works after a wake-up, it tells me that it shouldn't be a router issue.

Thanks again for helping ! At least i know the workaround hibernate/wakeup now ;)

[/SIZE][/SIZE]

---

