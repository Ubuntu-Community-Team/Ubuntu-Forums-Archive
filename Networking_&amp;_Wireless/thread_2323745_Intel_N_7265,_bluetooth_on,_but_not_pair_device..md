---
title: "Intel N 7265, bluetooth on, but not pair device."
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by TuxManRemove on 2016-05-07
Hello,

I have an Intel WiFi N 7265 card and it seems to work well in wifi. But bluetooth not work, but is ON. 
When I give search devices, the device name does not appear, only the mac. And when I give match (pair device), and takes just giving a fault.
I have tried several phones and when I do it from the phone tells me after a while, that you have not entered a PIN or PIN is not correct.

Logically I can not send or receive files via Bluetooth.

I tried swcrypto=1 or 0, and bt_coex_active=0 or 1

I also update to the latest kernel, and not work.
I tried to update the latest driver from intel, but still the same.
[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release)
I tried Core 14 first, and core18 after.

```

########## wireless info START ##########

Report from: 07 May 2016 23:15 CEST +0200

Booted last: 07 May 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.9-040409-generic #201605041832 SMP Wed May 4 22:34:16 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, elevator=noop, quiet, splash, i8042.reset, i8042.nomux, vt.handoff=7

##### desktop ###########################

MATE

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 12)
    Subsystem: Intel Corporation Dual Band Wireless-N 7265 [8086:5000]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 1e4e:0110 Cubeternet 
Bus 002 Device 004: ID 8087:0a2a Intel Corp. 
Bus 002 Device 006: ID 046a:b090 Cherry GmbH 
Bus 002 Device 003: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                385024  0
mac80211              700416  1 iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
iwlwifi               315392  1 iwlmvm
cfg80211              581632  3 iwlwifi,mac80211,iwlmvm
compat                 16384  4 cfg80211,iwlwifi,mac80211,iwlmvm
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5351:8985:e54c:2004/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59604559 (59.6 MB)  TX bytes:6641779 (6.6 MB)

pan1      Link encap:Ethernet  HWaddr <MAC 'pan1' [IF]>  
          inet addr:10.35.3.1  Bcast:10.35.3.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'pan1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:132455 (132.4 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

pan1      no wireless extensions.

wlp2s0    no wireless extensions.

lo        no wireless extensions.

enp1s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0
10.35.3.0       0.0.0.0         255.255.255.0   U     0      0        0 pan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       709     1  0 22:22 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         pan1
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'pan1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/pan1
GENERAL.IP-IFACE:                       pan1
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     pan1
GENERAL.CON-UUID:                       4fa84ca0-3b6c-4c15-acb8-423b2d799434
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{12}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4fa84ca0-3b6c-4c15-acb8-423b2d799434 | pan1
IP4.ADDRESS[1]:                         10.35.3.1/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::<IP6 'pan1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     GO-OFICINA
GENERAL.CON-UUID:                       d736be97-1246-419e-b163-9ddb41fe5fd5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c4e4d785-c0a3-45bb-81b1-b408b887e4e7 | Auto
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   d736be97-1246-419e-b163-9ddb41fe5fd5 | GO-OFICINA
IP4.ADDRESS[1]:                         192.168.1.100/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.4.4
IP4.DNS[2]:                             208.67.220.220
IP4.DNS[3]:                             62.81.16.148
IP6.ADDRESS[1]:                         fe80::5351:8985:e54c:2004/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-N 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.9-040409-generic
GENERAL.FIRMWARE-VERSION:               17.311016.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
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

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  *       
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2 802.1X  no        
JRC              <MAC 'JRC' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2         no        
NETGEAR_GUEST_2  <MAC 'NETGEAR_GUEST_2' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2         no        
_ONOWiFi         <MAC '_ONOWiFi' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  --           no        
vodafone34D8     <MAC 'vodafone34D8' [AN6]>  Infra  3     2422 MHz  54 Mbit/s  15      &#9602;___  WPA2         no        
ONOD7E0          <MAC 'ONOD7E0' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  15      &#9602;___  WPA1 WPA2    no        

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

pan1      no frequency information.

wlp2s0    no frequency information.

lo        no frequency information.

enp1s0    no frequency information.

##### iwlist scan #######################

pan1      Interface doesn't support scanning.

wlp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.9-040409-generic/updates/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
version:        iwlwifi-stack-public:release/LinuxCore18:5190:1e83f3d1
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     278E1B912347D259FD69CD7
depends:        iwlwifi,mac80211,compat,cfg80211
vermagic:       4.4.9-040409-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.9-040409-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        iwlwifi-stack-public:release/LinuxCore18:5190:1e83f3d1
srcversion:     DBEB1008E3B87DD1F905BBF
depends:        cfg80211,compat
vermagic:       4.4.9-040409-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.9-040409-generic/updates/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
version:        iwlwifi-stack-public:release/LinuxCore18:5190:1e83f3d1
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3168-20.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8265-20.ucode
firmware:       iwlwifi-8000-13.ucode
firmware:       iwlwifi-9000--13.ucode
srcversion:     52C988D479E1044D519229E
depends:        compat,cfg80211
vermagic:       4.4.9-040409-generic SMP mod_unload modversions 
parm:           debug:debug output mask (uint)
parm:           xvt_default_mode:xVT is the default operation mode (default: false) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0:4K 1:8K 2:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: N) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.4.9-040409-generic/updates/net/wireless/cfg80211.ko
version:        iwlwifi-stack-public:release/LinuxCore18:5190:1e83f3d1
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D40DD2D41A5F60374476497
depends:        compat
vermagic:       4.4.9-040409-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 1
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: N
d0i3_disable: N
d0i3_timeout: 1000
debug: 0
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 5
power_save: N
swcrypto: 1
uapsd_disable: 3
xvt_default_mode: N

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
options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1 power_save=0 power_level=5
options iwlwifi swcrypto=1

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

[/etc/pm/sleep.d/00_check_touchpad_status] (755 root)
LOGFILE="/var/log/sleep.log"
case "$1" in
        resume|thaw)
                echo "Resumed normal from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/check_touchpad_status.py resume
                echo "Touchpad enabled"
                ;;
esac

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   10.683133] iwlwifi-stack-public:release/LinuxCore18:5190:1e83f3d1
[   10.725073] iwlwifi 0000:02:00.0: Unsupported splx structure
[   10.737359] iwlwifi 0000:02:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[   10.737768] iwlwifi 0000:02:00.0: loaded firmware version 17.311016.0 op_mode iwlmvm
[   10.761133] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless N 7265, REV=0x184
[   10.761286] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   10.841880] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   10.867887] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[   11.495908] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   11.496107] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   11.579938] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   11.583492] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   11.767477] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   11.767533] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   11.871662] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   12.428031] bluetooth hci0: Direct firmware load for intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq failed with error -2
[   12.428034] Bluetooth: hci0 failed to open Intel firmware file: intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq(-2)
[   12.428856] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.bseq
[   12.432718] Bluetooth: hci0: Intel Bluetooth firmware patch completed
[   13.298761] r8169 0000:01:00.0 enp1s0: link up
[   13.298772] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready

########## wireless info END ############


```

Thanks

---

### Post by jeremy31 on 2016-05-07
Are you using the included bluetooth manager or blueman?  This one has me stumped for now

---

### Post by TuxManRemove on 2016-05-08
> **jeremy31 said:**
> Are you using the included bluetooth manager or blueman?  This one has me stumped for now

First I had installed Ubuntu 16.04 and I not installed blueman.
After I install Ubuntu Mate, and already installed Blueman.

Thanks,

---

### Post by jeremy31 on 2016-05-08
What happens if you use terminal?
```
sudo bluetoothctl
```

Since you are dealing with phones, you can turn on visibility mode with
```
discoverable on
```

Then try pairing to the computer from the phone and see if it works

Commands available in bluetoothctl:
```

  list                       List available controllers
  show [ctrl]                Controller information
  select <ctrl>              Select default controller
  devices                    List available devices
  paired-devices             List paired devices
  power <on/off>             Set controller power
  pairable <on/off>          Set controller pairable mode
  discoverable <on/off>      Set controller discoverable mode
  agent <on/off/capability>  Enable/disable agent with given capability
  default-agent              Set agent as the default one
  set-scan-filter-uuids [uuid1 uuid2 ...] Set scan filter uuids
  set-scan-filter-rssi [rssi] Set scan filter rssi, and clears pathloss
  set-scan-filter-pathloss [pathloss] Set scan filter pathloss, and clears rssi
  set-scan-filter-transport [transport] Set scan filter transport
  set-scan-filter-clear      Clears discovery filter.
  scan <on/off>              Scan for devices
  info [dev]                 Device information
  pair [dev]                 Pair with device
  trust [dev]                Trust device
  untrust [dev]              Untrust device
  block [dev]                Block device
  unblock [dev]              Unblock device
  remove <dev>               Remove device
  connect <dev>              Connect device
  disconnect [dev]           Disconnect device
  list-attributes [dev]      List attributes
  select-attribute <attribute> Select attribute
  attribute-info [attribute] Select attribute
  read                       Read attribute value
  write <data=[xx xx ...]>   Write attribute value
  notify <on/off>            Notify attribute value
  register-profile <UUID ...> Register profile to connect
  unregister-profile         Unregister profile
  version                    Display version
  quit                       Quit program

```

---

### Post by TuxManRemove on 2016-05-08
Thanks,

sudo bluetoothctl
[sudo] password for user:
[NEW] Controller 00:15:00:E4:6E:60 ordenador [default]
[bluetooth]# discoverable on
Changing discoverable on succeeded
[CHG] Controller 00:15:00:E4:6E:60 Discoverable: yes

If I tried im my phone, end without connect.

And if I tried in my laptop:

connect 42:51:11:xxxxxxx
Attempting to connect to 42:51:11xxxxxx
Failed to connect: org.bluez.Error.Failed

thanks

---

### Post by jeremy31 on 2016-05-08
Do you have the USB or DVD you installed from to see if something didn't get corrupted during install?

I just used a USB in my laptop with an Intel 7260 and I was able to pair with my phone and transfer files with 16.04.

---

### Post by TuxManRemove on 2016-05-08
I triend first with Ubuntu and after Ubuntu Mate, with 2 differents USB.
My wifi card Intel is 7265, I think that driver is different, right?

---

### Post by jeremy31 on 2016-05-08
They use the same drivers but different firmware.  The wifi uses iwlmvm and iwlwifi for drivers and bluetooth uses btusb, btintel, and bluetooth 

You will likely need to file a bug report to get some help.  Some info at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by TuxManRemove on 2016-05-08
I think that is real bug.
A friend has the Intel 7265 **AC** and I have the Intel 7265 **N**. I opened my computer and removed my card and put the wifi card of my friend, the AC, and it works! I could pair devices and send / receive files. With Blueman.

Then I quit the AC and relocated my wireless N card, and the problem continues, does not pair and does not send files with any device (not shown names when found, only mac addresses)

I think it's important to report the bug, but as you've seen my English is not good. Can you help me bug report?
Thank you very much

---

### Post by jeremy31 on 2016-05-08
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)  Is a good write up

Can you put your card in your friends computer and see if the bluetooth works correctly in the other computer

Also try pairing again and post ```
cat /var/log/syslog | grep -i blue
```

---

### Post by TuxManRemove on 2016-05-08
Tomorrow I sned you the log of my friend. No problem.

My log with my card 7265 N: 
```
May  8 14:09:28 computer bluetoothd[1083]: 42:51:11:00:E1:1E: error updating services: Operation already in progress (114)
May  8 14:47:53 computer bluetoothd[1083]: 42:51:11:00:E1:1E: error updating services: Host is down (112)
May  8 14:48:10 computer bluetoothd[1083]: 42:51:11:00:E1:1E: error updating services: Host is down (112)
May  8 14:49:12 computer bluetoothd[1083]: 42:51:11:00:E1:1E: error updating services: Host is down (112)
May  8 14:50:03 computer bluetoothd[1083]: 42:51:11:00:E1:1E: error updating services: Connection timed out (110)
May  8 14:51:09 computer bluetoothd[1083]: 42:51:11:00:E1:1E: error updating services: Connection timed out (110)
May  8 14:56:37 computer systemd[1]: [/lib/systemd/system/bluetooth-touch.service:10] Invalid escape sequences in line, correcting: "/bin/sh -ec 'SCRIPT=/usr/share/bluetooth-touch/`getprop ro.product.device`; [ \( ! -x $SCRIPT \) -o \( ! -f $SCRIPT \) ] || exec $SCRIPT'"
May  8 14:56:37 computer systemd[1]: [/lib/systemd/system/bluetooth-touch.service:10] Invalid escape sequences in line, correcting: "/bin/sh -ec 'SCRIPT=/usr/share/bluetooth-touch/`getprop ro.product.device`; [ \( ! -x $SCRIPT \) -o \( ! -f $SCRIPT \) ] || exec $SCRIPT'"
May  8 14:56:38 computer systemd[1]: [/lib/systemd/system/bluetooth-touch.service:10] Invalid escape sequences in line, correcting: "/bin/sh -ec 'SCRIPT=/usr/share/bluetooth-touch/`getprop ro.product.device`; [ \( ! -x $SCRIPT \) -o \( ! -f $SCRIPT \) ] || exec $SCRIPT'"
May  8 14:56:38 computer systemd[1]: [/lib/systemd/system/bluetooth-touch.service:10] Invalid escape sequences in line, correcting: "/bin/sh -ec 'SCRIPT=/usr/share/bluetooth-touch/`getprop ro.product.device`; [ \( ! -x $SCRIPT \) -o \( ! -f $SCRIPT \) ] || exec $SCRIPT'"
May  8 14:56:38 computer systemd[1]: [/lib/systemd/system/bluetooth-touch.service:10] Invalid escape sequences in line, correcting: "/bin/sh -ec 'SCRIPT=/usr/share/bluetooth-touch/`getprop ro.product.device`; [ \( ! -x $SCRIPT \) -o \( ! -f $SCRIPT \) ] || exec $SCRIPT'"
May  8 14:56:38 computer systemd[1]: Stopping Bluetooth service...
May  8 14:56:38 computer bluetoothd[1083]: Terminating
May  8 14:56:48 computer bluetoothd[1083]: Endpoint unregistered: sender=:1.49 path=/MediaEndpoint/A2DPSource
May  8 14:56:48 computer bluetoothd[1083]: Endpoint unregistered: sender=:1.49 path=/MediaEndpoint/A2DPSink
May  8 14:56:49 computer bluetoothd[1083]: Stopping SDP server
May  8 14:56:49 computer bluetoothd[1083]: Exit
May  8 14:56:49 computer systemd[1]: Stopped Bluetooth service.
May  8 14:56:49 computer systemd[1]: Starting Bluetooth service...
May  8 14:56:49 computer bluetoothd[8313]: Bluetooth daemon 5.37
May  8 14:56:49 computer bluetoothd[8313]: Starting SDP server
May  8 14:56:49 computer bluetoothd[8313]: Bluetooth management interface 1.10 initialized
May  8 14:56:49 computer bluetoothd[8313]: Failed to obtain handles for "Service Changed" characteristic
May  8 14:56:49 computer bluetoothd[8313]: Not enough free handles to register service
May  8 14:56:49 computer bluetoothd[8313]: Error adding Link Loss service
May  8 14:56:49 computer bluetoothd[8313]: Not enough free handles to register service
May  8 14:56:49 computer bluetoothd[8313]: message repeated 2 times: [ Not enough free handles to register service]
May  8 14:56:49 computer bluetoothd[8313]: Current Time Service could not be registered
May  8 14:56:49 computer bluetoothd[8313]: gatt-time-server: Input/output error (5)
May  8 14:56:49 computer bluetoothd[8313]: Not enough free handles to register service
May  8 14:56:49 computer bluetoothd[8313]: Not enough free handles to register service
May  8 14:56:49 computer bluetoothd[8313]: Sap driver initialization failed.
May  8 14:56:49 computer bluetoothd[8313]: sap-server: Operation not permitted (1)
May  8 14:56:49 computer bluetoothd[8313]: Endpoint registered: sender=:1.49 path=/MediaEndpoint/A2DPSource
May  8 14:56:49 computer bluetoothd[8313]: Endpoint registered: sender=:1.49 path=/MediaEndpoint/A2DPSink
May  8 14:56:49 computer systemd[1]: Started Bluetooth service.
May  8 14:59:11 computer bluetoothd[8313]: 42:51:11:00:E1:1E: error updating services: Connection timed out (110)
May  8 15:00:27 computer bluetoothd[8313]: Pair device timed out for hci0
May  8 15:21:25 computer systemd[1]: Stopped target Bluetooth.
May  8 15:21:25 computer bluetoothd[8313]: Endpoint unregistered: sender=:1.49 path=/MediaEndpoint/A2DPSource
May  8 15:21:25 computer bluetoothd[8313]: Endpoint unregistered: sender=:1.49 path=/MediaEndpoint/A2DPSink
May  8 15:21:26 computer systemd[1]: Stopping LSB: Bluetooth monitoring daemon...
May  8 17:33:46 computer kernel: [    6.770712] Bluetooth: Core ver 2.21
May  8 17:33:46 computer kernel: [    6.770725] Bluetooth: HCI device and connection manager initialized
May  8 17:33:46 computer kernel: [    6.770728] Bluetooth: HCI socket layer initialized
May  8 17:33:46 computer kernel: [    6.770730] Bluetooth: L2CAP socket layer initialized
May  8 17:33:46 computer kernel: [    6.770734] Bluetooth: SCO socket layer initialized
May  8 17:33:46 computer systemd[1]: Starting LSB: Bluetooth monitoring daemon...
May  8 17:33:46 computer kernel: [    6.890715] Bluetooth: hci0: read Intel version: 370810011001140d00
May  8 17:33:46 computer kernel: [    6.892653] bluetooth hci0: Direct firmware load for intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq failed with error -2
May  8 17:33:46 computer kernel: [    6.892659] Bluetooth: hci0 failed to open Intel firmware file: intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq(-2)
May  8 17:33:46 computer kernel: [    6.904867] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.bseq
May  8 17:33:46 computer bluemon[832]:  * Starting bluemon...
May  8 17:33:46 computer bluemon[832]: disabled in /etc/default/bluemon
May  8 17:33:46 computer systemd[1]: Started LSB: Bluetooth monitoring daemon.
May  8 17:33:46 computer kernel: [    6.908707] Bluetooth: hci0: Intel Bluetooth firmware patch completed
May  8 17:33:46 computer systemd[1]: [/lib/systemd/system/bluetooth-touch.service:10] Invalid escape sequences in line, correcting: "/bin/sh -ec 'SCRIPT=/usr/share/bluetooth-touch/`getprop ro.product.device`; [ \( ! -x $SCRIPT \) -o \( ! -f $SCRIPT \) ] || exec $SCRIPT'"
May  8 17:33:46 computer systemd[1]: Starting Bluetooth service...
May  8 17:33:46 computer bluetoothd[907]: Bluetooth daemon 5.37
May  8 17:33:46 computer systemd[1]: Started Bluetooth service.
May  8 17:33:46 computer systemd[1]: Reached target Bluetooth.
May  8 17:33:46 computer bluetoothd[907]: Starting SDP server
May  8 17:33:46 computer bluetoothd[907]: Bluetooth management interface 1.10 initialized
May  8 17:33:46 computer bluetoothd[907]: Failed to obtain handles for "Service Changed" characteristic
May  8 17:33:46 computer kernel: [    7.040001] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  8 17:33:46 computer kernel: [    7.040004] Bluetooth: BNEP filters: protocol multicast
May  8 17:33:46 computer kernel: [    7.040009] Bluetooth: BNEP socket layer initialized
May  8 17:33:46 computer bluetoothd[907]: Not enough free handles to register service
May  8 17:33:46 computer bluetoothd[907]: Error adding Link Loss service
May  8 17:33:46 computer bluetoothd[907]: Not enough free handles to register service
May  8 17:33:46 computer bluetoothd[907]: message repeated 2 times: [ Not enough free handles to register service]
May  8 17:33:46 computer bluetoothd[907]: Current Time Service could not be registered
May  8 17:33:46 computer bluetoothd[907]: gatt-time-server: Input/output error (5)
May  8 17:33:46 computer bluetoothd[907]: Not enough free handles to register service
May  8 17:33:46 computer bluetoothd[907]: Not enough free handles to register service
May  8 17:33:46 computer bluetoothd[907]: Sap driver initialization failed.
May  8 17:33:46 computer bluetoothd[907]: sap-server: Operation not permitted (1)
May  8 17:33:46 computer NetworkManager[822]: <info>  [1462721626.5902] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
May  8 17:33:46 computer NetworkManager[822]: <info>  [1462721626.9147] bluez: use BlueZ version 5
May  8 17:33:56 computer mate-session[1242]: WARNING: Could not launch application 'blueproximity-autostart.desktop': Unable to start application: Falló al ejecutar el proceso hijo «blueproximity» (No existe el archivo o el directorio)
May  8 17:33:57 computer bluetoothd[907]: Endpoint registered: sender=:1.57 path=/MediaEndpoint/A2DPSource
May  8 17:33:57 computer bluetoothd[907]: Endpoint registered: sender=:1.57 path=/MediaEndpoint/A2DPSink
May  8 17:33:57 computer kernel: [   18.690446] Bluetooth: RFCOMM TTY layer initialized
May  8 17:33:57 computer kernel: [   18.690458] Bluetooth: RFCOMM socket layer initialized
May  8 17:33:57 computer kernel: [   18.690464] Bluetooth: RFCOMM ver 1.11
May  8 17:33:58 computer dbus[743]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
May  8 17:33:58 computer org.blueman.Mechanism[743]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
May  8 17:33:58 computer org.blueman.Mechanism[743]: Unable to init server: Could not connect: Connection refused
May  8 17:33:59 computer org.blueman.Mechanism[743]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
May  8 17:33:59 computer org.blueman.Mechanism[743]: Unable to init server: Could not connect: Connection refused
May  8 17:33:59 computer blueman-mechanism: Starting blueman-mechanism
May  8 17:33:59 computer dbus[743]: [system] Successfully activated service 'org.blueman.Mechanism'
May  8 17:33:59 computer org.blueman.Mechanism[743]: (blueman-mechanism:1847): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
May  8 17:33:59 computer blueman-mechanism: loading RfKill
May  8 17:33:59 computer blueman-mechanism: loading Network
May  8 17:33:59 computer blueman-mechanism: loading Ppp
May  8 17:33:59 computer blueman-mechanism: loading Rfcomm
May  8 17:33:59 computer org.blueman.Mechanism[743]: iptables: No chain/target/match by that name.
May  8 17:33:59 computer org.blueman.Mechanism[743]: iptables: Bad rule (does a matching rule exist in that chain?).
May  8 17:33:59 computer org.blueman.Mechanism[743]: message repeated 2 times: [ iptables: Bad rule (does a matching rule exist in that chain?).]
May  8 17:33:59 computer blueman-mechanism: Return code 0
May  8 17:33:59 computer blueman-mechanism: message repeated 3 times: [ Return code 0]
May  8 17:34:29 computer blueman-mechanism: Exiting
```

---

### Post by jeremy31 on 2016-05-08
Post ```
dpkg -l | grep -i bluetooth
```
You have a strange error in there

---

### Post by TuxManRemove on 2016-05-08
Ok, as did not work, I tried to install multiple packages for bluetooth ...

```
dpkg -l | grep -i bluetooth
ii  blueman                               2.0.4-1ubuntu2                             amd64        Graphical bluetooth manager
ii  bluemon                               1.4-6ubuntu1                               amd64        Activate or deactivate programs based on Bluetooth link quality
rc  blueproximity                         1.2.5-6                                    all          locks/unlocks your desktop tracking a bluetooth device
ii  bluetooth                             5.37-0ubuntu5                              all          Bluetooth support
ii  bluetooth-touch                       0.3.3+16.04.20160201-0ubuntu1              amd64        Firmware patching utility and config for bluetooth
ii  bluewho                               0.1-2                                      all          notifies new discovered bluetooth devices
ii  bluez                                 5.37-0ubuntu5                              amd64        Bluetooth tools and daemons
ii  bluez-btsco                           1:0.50-0ubuntu6                            amd64        Bluez Bluetooth SCO tool
ii  bluez-cups                            5.37-0ubuntu5                              amd64        Bluetooth printer driver for CUPS
ii  bluez-hcidump                         5.37-0ubuntu5                              amd64        Analyses Bluetooth HCI packets
ii  bluez-tools                           0.2.0~20140808-5                           amd64        Set of tools to manage Bluetooth devices for linux
ii  btscanner                             2.1-5.1build1                              amd64        ncurses-based scanner for Bluetooth devices
ii  libbluetooth3:amd64                   5.37-0ubuntu5                              amd64        Library to use the BlueZ Linux Bluetooth stack
ii  pulseaudio-module-bluetooth           1:8.0-0ubuntu3                             amd64        Bluetooth module for PulseAudio sound server
ii  python-bluez                          0.22-1                                     amd64        Python wrappers around BlueZ for rapid bluetooth development
```

---

### Post by jeremy31 on 2016-05-08
The one is causing  a problem and other isn't being allowed to work, so they can be removed
```
sudo apt-get purge bluetooth-touch bluemon
```

I only have these installed
```
ii  blueman                                         2.0.4-1ubuntu2                                amd64        Graphical bluetooth manager
ii  bluez                                           5.37-0ubuntu5                                 amd64        Bluetooth tools and daemons
ii  bluez-cups                                      5.37-0ubuntu5                                 amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                     5.37-0ubuntu5                                 amd64        bluez obex daemon
ii  gnome-bluetooth                                 3.18.2-1ubuntu2                               amd64        GNOME Bluetooth tools
ii  indicator-bluetooth                             0.0.6+16.04.20160214-0ubuntu1                 amd64        System bluetooth indicator.
ii  libbluetooth3:amd64                             5.37-0ubuntu5                                 amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth13:amd64                      3.18.2-1ubuntu2                               amd64        GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth                     1:8.0-0ubuntu3                                amd64        Bluetooth module for PulseAudio sound server
```

gnome-bluetooth is the standard bluetooth manager in Ubuntu but blueman doesn't need it

---

### Post by TuxManRemove on 2016-05-09
Hello,
I purge, but bluetooth fails when pair.

My friend format and re-install his computer, tomorrow we change the wifi cards and send you the logs.
Thanks

---

### Post by jeremy31 on 2016-05-09
I will almost bet yours friends card doesn't show errors similar to
```
May  8 17:33:46 computer kernel: [    6.892653] bluetooth hci0: Direct firmware load for intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq failed with error -2
May  8 17:33:46 computer kernel: [    6.892659] Bluetooth: hci0 failed to open Intel firmware file: intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq(-2)
```

And that is why it works.  I checked the dmesg on my laptop with the 7260 and it doesn't have similar errors

---

### Post by TuxManRemove on 2016-05-10
Hello!
I back! ;)

Log with Intel 7265 N:
```
May 10 18:11:04 laptop systemd[1]: Starting Bluetooth service...
May 10 18:11:04 laptop bluetoothd[688]: Bluetooth daemon 5.37
May 10 18:11:04 laptop kernel: [    3.757559] Bluetooth: Core ver 2.21
May 10 18:11:04 laptop kernel: [    3.757579] Bluetooth: HCI device and connection manager initialized
May 10 18:11:04 laptop kernel: [    3.757583] Bluetooth: HCI socket layer initialized
May 10 18:11:04 laptop kernel: [    3.757586] Bluetooth: L2CAP socket layer initialized
May 10 18:11:04 laptop kernel: [    3.757592] Bluetooth: SCO socket layer initialized
May 10 18:11:04 laptop kernel: [    3.792840] Bluetooth: hci0: read Intel version: 370810011001140d00
May 10 18:11:04 laptop kernel: [    3.793592] bluetooth hci0: Direct firmware load for intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq failed with error -2
May 10 18:11:04 laptop kernel: [    3.793595] Bluetooth: hci0 failed to open Intel firmware file: intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq(-2)
May 10 18:11:04 laptop kernel: [    3.794598] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.bseq
May 10 18:11:04 laptop kernel: [    3.798833] Bluetooth: hci0: Intel Bluetooth firmware patch completed
May 10 18:11:04 laptop systemd[1]: Started Bluetooth service.
May 10 18:11:04 laptop bluetoothd[688]: Starting SDP server
May 10 18:11:04 laptop systemd[1]: Reached target Bluetooth.
May 10 18:11:04 laptop kernel: [    4.796758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 10 18:11:04 laptop kernel: [    4.796764] Bluetooth: BNEP filters: protocol multicast
May 10 18:11:04 laptop kernel: [    4.796768] Bluetooth: BNEP socket layer initialized
May 10 18:11:04 laptop bluetoothd[688]: Bluetooth management interface 1.10 initialized
May 10 18:11:04 laptop bluetoothd[688]: Failed to obtain handles for "Service Changed" characteristic
May 10 18:11:04 laptop bluetoothd[688]: Not enough free handles to register service
May 10 18:11:04 laptop bluetoothd[688]: Error adding Link Loss service
May 10 18:11:04 laptop bluetoothd[688]: Not enough free handles to register service
May 10 18:11:04 laptop bluetoothd[688]: Not enough free handles to register service
May 10 18:11:04 laptop bluetoothd[688]: Not enough free handles to register service
May 10 18:11:04 laptop bluetoothd[688]: Current Time Service could not be registered
May 10 18:11:04 laptop bluetoothd[688]: gatt-time-server: Input/output error (5)
May 10 18:11:04 laptop bluetoothd[688]: Not enough free handles to register service
May 10 18:11:04 laptop bluetoothd[688]: Not enough free handles to register service
May 10 18:11:04 laptop bluetoothd[688]: Sap driver initialization failed.
May 10 18:11:04 laptop bluetoothd[688]: sap-server: Operation not permitted (1)
May 10 18:11:04 laptop NetworkManager[750]: <info>  [1462896664.9682] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
May 10 18:11:05 laptop NetworkManager[750]: <info>  [1462896665.2738] bluez: use BlueZ version 5
May 10 18:11:05 laptop bluetoothd[688]: Endpoint registered: sender=:1.34 path=/MediaEndpoint/A2DPSource
May 10 18:11:05 laptop bluetoothd[688]: Endpoint registered: sender=:1.34 path=/MediaEndpoint/A2DPSink
May 10 18:11:05 laptop kernel: [    5.909443] Bluetooth: RFCOMM TTY layer initialized
May 10 18:11:05 laptop kernel: [    5.909456] Bluetooth: RFCOMM socket layer initialized
May 10 18:11:05 laptop kernel: [    5.909462] Bluetooth: RFCOMM ver 1.11
May 10 18:11:13 laptop bluetoothd[688]: Endpoint registered: sender=:1.64 path=/MediaEndpoint/A2DPSource
May 10 18:11:13 laptop bluetoothd[688]: Endpoint registered: sender=:1.64 path=/MediaEndpoint/A2DPSink
May 10 18:11:13 laptop bluetoothd[688]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
May 10 18:11:30 laptop bluetoothd[688]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSource
May 10 18:11:30 laptop bluetoothd[688]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSink
May 10 18:14:09 laptop bluetoothd[688]: Terminating
May 10 18:14:09 laptop bluetoothd[688]: Endpoint unregistered: sender=:1.64 path=/MediaEndpoint/A2DPSource
May 10 18:14:09 laptop bluetoothd[688]: Endpoint unregistered: sender=:1.64 path=/MediaEndpoint/A2DPSink
May 10 18:14:09 laptop systemd[1]: Stopped target Bluetooth.
May 10 18:14:09 laptop systemd[1]: Stopping Bluetooth service...
May 10 18:14:09 laptop bluetoothd[688]: Stopping SDP server
May 10 18:14:09 laptop bluetoothd[688]: Exit
May 10 18:14:23 laptop kernel: [    3.773873] Bluetooth: Core ver 2.21
May 10 18:14:23 laptop kernel: [    3.773890] Bluetooth: HCI device and connection manager initialized
May 10 18:14:23 laptop kernel: [    3.773894] Bluetooth: HCI socket layer initialized
May 10 18:14:23 laptop kernel: [    3.773897] Bluetooth: L2CAP socket layer initialized
May 10 18:14:23 laptop kernel: [    3.773902] Bluetooth: SCO socket layer initialized
May 10 18:14:23 laptop kernel: [    3.803968] Bluetooth: hci0: read Intel version: 370810011001140d00
May 10 18:14:23 laptop kernel: [    3.812552] bluetooth hci0: Direct firmware load for intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq failed with error -2
May 10 18:14:23 laptop kernel: [    3.812558] Bluetooth: hci0 failed to open Intel firmware file: intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq(-2)
May 10 18:14:23 laptop kernel: [    3.813614] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.bseq
May 10 18:14:23 laptop kernel: [    3.823976] Bluetooth: hci0: Intel Bluetooth firmware patch completed
May 10 18:14:23 laptop systemd[1]: Starting Bluetooth service...
May 10 18:14:23 laptop bluetoothd[705]: Bluetooth daemon 5.37
May 10 18:14:23 laptop bluetoothd[705]: Starting SDP server
May 10 18:14:23 laptop kernel: [    5.305927] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 10 18:14:23 laptop kernel: [    5.305931] Bluetooth: BNEP filters: protocol multicast
May 10 18:14:23 laptop kernel: [    5.305935] Bluetooth: BNEP socket layer initialized
May 10 18:14:23 laptop bluetoothd[705]: Bluetooth management interface 1.10 initialized
May 10 18:14:23 laptop bluetoothd[705]: Failed to obtain handles for "Service Changed" characteristic
May 10 18:14:23 laptop bluetoothd[705]: Not enough free handles to register service
May 10 18:14:23 laptop bluetoothd[705]: Error adding Link Loss service
May 10 18:14:23 laptop bluetoothd[705]: Not enough free handles to register service
May 10 18:14:23 laptop bluetoothd[705]: message repeated 2 times: [ Not enough free handles to register service]
May 10 18:14:23 laptop bluetoothd[705]: Current Time Service could not be registered
May 10 18:14:23 laptop bluetoothd[705]: gatt-time-server: Input/output error (5)
May 10 18:14:23 laptop bluetoothd[705]: Not enough free handles to register service
May 10 18:14:23 laptop bluetoothd[705]: Not enough free handles to register service
May 10 18:14:23 laptop bluetoothd[705]: Sap driver initialization failed.
May 10 18:14:23 laptop bluetoothd[705]: sap-server: Operation not permitted (1)
May 10 18:14:23 laptop systemd[1]: Started Bluetooth service.
May 10 18:14:23 laptop systemd[1]: Reached target Bluetooth.
May 10 18:14:23 laptop NetworkManager[678]: <info>  [1462896863.4093] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
May 10 18:14:23 laptop NetworkManager[678]: <info>  [1462896863.6970] bluez: use BlueZ version 5
May 10 18:14:24 laptop bluetoothd[705]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/A2DPSource
May 10 18:14:24 laptop bluetoothd[705]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/A2DPSink
May 10 18:14:24 laptop kernel: [    6.276104] Bluetooth: RFCOMM TTY layer initialized
May 10 18:14:24 laptop kernel: [    6.276111] Bluetooth: RFCOMM socket layer initialized
May 10 18:14:24 laptop kernel: [    6.276121] Bluetooth: RFCOMM ver 1.11
May 10 18:14:56 laptop bluetoothd[705]: Endpoint registered: sender=:1.65 path=/MediaEndpoint/A2DPSource
May 10 18:14:56 laptop bluetoothd[705]: Endpoint registered: sender=:1.65 path=/MediaEndpoint/A2DPSink
May 10 18:14:56 laptop bluetoothd[705]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
May 10 18:15:14 laptop bluetoothd[705]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/A2DPSource
May 10 18:15:14 laptop bluetoothd[705]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/A2DPSink
May 10 18:16:17 laptop bluetoothd[705]: Terminating
May 10 18:16:17 laptop systemd[1]: Stopped target Bluetooth.
May 10 18:16:17 laptop systemd[1]: Stopping Bluetooth service...
May 10 18:16:17 laptop bluetoothd[705]: Endpoint unregistered: sender=:1.65 path=/MediaEndpoint/A2DPSource
May 10 18:16:17 laptop bluetoothd[705]: Endpoint unregistered: sender=:1.65 path=/MediaEndpoint/A2DPSink
May 10 18:18:06 laptop systemd[1]: Starting Bluetooth service...
May 10 18:18:06 laptop bluetoothd[653]: Bluetooth daemon 5.37
May 10 18:18:06 laptop systemd[1]: Started Bluetooth service.
May 10 18:18:06 laptop systemd[1]: Reached target Bluetooth.
May 10 18:18:06 laptop bluetoothd[653]: Starting SDP server
May 10 18:18:06 laptop kernel: [    3.721772] Bluetooth: Core ver 2.21
May 10 18:18:06 laptop kernel: [    3.721790] Bluetooth: HCI device and connection manager initialized
May 10 18:18:06 laptop kernel: [    3.721793] Bluetooth: HCI socket layer initialized
May 10 18:18:06 laptop kernel: [    3.721797] Bluetooth: L2CAP socket layer initialized
May 10 18:18:06 laptop kernel: [    3.721802] Bluetooth: SCO socket layer initialized
May 10 18:18:06 laptop kernel: [    3.755275] Bluetooth: hci0: read Intel version: 370810011001140d00
May 10 18:18:06 laptop kernel: [    3.773267] bluetooth hci0: Direct firmware load for intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq failed with error -2
May 10 18:18:06 laptop kernel: [    3.773274] Bluetooth: hci0 failed to open Intel firmware file: intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq(-2)
May 10 18:18:06 laptop kernel: [    3.780818] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.bseq
May 10 18:18:06 laptop kernel: [    3.784272] Bluetooth: hci0: Intel Bluetooth firmware patch completed
May 10 18:18:06 laptop kernel: [    4.724273] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 10 18:18:06 laptop kernel: [    4.724276] Bluetooth: BNEP filters: protocol multicast
May 10 18:18:06 laptop kernel: [    4.724281] Bluetooth: BNEP socket layer initialized
May 10 18:18:06 laptop bluetoothd[653]: Bluetooth management interface 1.10 initialized
May 10 18:18:06 laptop bluetoothd[653]: Failed to obtain handles for "Service Changed" characteristic
May 10 18:18:06 laptop bluetoothd[653]: Not enough free handles to register service
May 10 18:18:06 laptop bluetoothd[653]: Error adding Link Loss service
May 10 18:18:06 laptop bluetoothd[653]: Not enough free handles to register service
May 10 18:18:06 laptop bluetoothd[653]: message repeated 2 times: [ Not enough free handles to register service]
May 10 18:18:06 laptop bluetoothd[653]: Current Time Service could not be registered
May 10 18:18:06 laptop bluetoothd[653]: gatt-time-server: Input/output error (5)
May 10 18:18:06 laptop bluetoothd[653]: Not enough free handles to register service
May 10 18:18:06 laptop bluetoothd[653]: Not enough free handles to register service
May 10 18:18:06 laptop bluetoothd[653]: Sap driver initialization failed.
May 10 18:18:06 laptop bluetoothd[653]: sap-server: Operation not permitted (1)
May 10 18:18:06 laptop NetworkManager[730]: <info>  [1462897086.8570] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
May 10 18:18:07 laptop NetworkManager[730]: <info>  [1462897087.1452] bluez: use BlueZ version 5
May 10 18:18:07 laptop bluetoothd[653]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSource
May 10 18:18:07 laptop bluetoothd[653]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSink
May 10 18:18:07 laptop kernel: [    5.735819] Bluetooth: RFCOMM TTY layer initialized
May 10 18:18:07 laptop kernel: [    5.736292] Bluetooth: RFCOMM socket layer initialized
May 10 18:18:07 laptop kernel: [    5.736300] Bluetooth: RFCOMM ver 1.11
May 10 18:20:05 laptop bluetoothd[653]: Endpoint registered: sender=:1.71 path=/MediaEndpoint/A2DPSource
May 10 18:20:05 laptop bluetoothd[653]: Endpoint registered: sender=:1.71 path=/MediaEndpoint/A2DPSink
May 10 18:20:05 laptop bluetoothd[653]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
May 10 18:20:23 laptop bluetoothd[653]: Endpoint unregistered: sender=:1.37 path=/MediaEndpoint/A2DPSource
May 10 18:20:23 laptop bluetoothd[653]: Endpoint unregistered: sender=:1.37 path=/MediaEndpoint/A2DPSink
```

Log with Intel 7265 AC:
```
May 10 17:14:50 laptop systemd[1]: Starting Bluetooth service...
May 10 17:14:50 laptop bluetoothd[747]: Bluetooth daemon 5.37
May 10 17:14:50 laptop bluetoothd[747]: Starting SDP server
May 10 17:14:50 laptop kernel: [    4.144961] Bluetooth: Core ver 2.21
May 10 17:14:50 laptop kernel: [    4.144977] Bluetooth: HCI device and connection manager initialized
May 10 17:14:50 laptop kernel: [    4.144981] Bluetooth: HCI socket layer initialized
May 10 17:14:50 laptop kernel: [    4.144984] Bluetooth: L2CAP socket layer initialized
May 10 17:14:50 laptop kernel: [    4.144989] Bluetooth: SCO socket layer initialized
May 10 17:14:50 laptop kernel: [    4.186074] Bluetooth: hci0: read Intel version: 370810011003110e23
May 10 17:14:50 laptop kernel: [    4.186077] Bluetooth: hci0: Intel device is already patched. patch num: 23
May 10 17:14:50 laptop kernel: [    4.831155] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 10 17:14:50 laptop kernel: [    4.831159] Bluetooth: BNEP filters: protocol multicast
May 10 17:14:50 laptop kernel: [    4.831163] Bluetooth: BNEP socket layer initialized
May 10 17:14:50 laptop bluetoothd[747]: Bluetooth management interface 1.10 initialized
May 10 17:14:50 laptop bluetoothd[747]: Failed to obtain handles for "Service Changed" characteristic
May 10 17:14:50 laptop bluetoothd[747]: Not enough free handles to register service
May 10 17:14:50 laptop bluetoothd[747]: Error adding Link Loss service
May 10 17:14:50 laptop bluetoothd[747]: Not enough free handles to register service
May 10 17:14:50 laptop bluetoothd[747]: message repeated 2 times: [ Not enough free handles to register service]
May 10 17:14:50 laptop bluetoothd[747]: Current Time Service could not be registered
May 10 17:14:50 laptop bluetoothd[747]: gatt-time-server: Input/output error (5)
May 10 17:14:50 laptop bluetoothd[747]: Not enough free handles to register service
May 10 17:14:50 laptop bluetoothd[747]: Not enough free handles to register service
May 10 17:14:50 laptop bluetoothd[747]: Sap driver initialization failed.
May 10 17:14:50 laptop bluetoothd[747]: sap-server: Operation not permitted (1)
May 10 17:14:50 laptop systemd[1]: Started Bluetooth service.
May 10 17:14:50 laptop systemd[1]: Reached target Bluetooth.
May 10 17:14:50 laptop NetworkManager[737]: <info>  [1462893290.9710] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
May 10 17:14:51 laptop NetworkManager[737]: <info>  [1462893291.2783] bluez: use BlueZ version 5
May 10 17:14:51 laptop bluetoothd[747]: Endpoint registered: sender=:1.34 path=/MediaEndpoint/A2DPSource
May 10 17:14:51 laptop bluetoothd[747]: Endpoint registered: sender=:1.34 path=/MediaEndpoint/A2DPSink
May 10 17:14:51 laptop kernel: [    5.927567] Bluetooth: RFCOMM TTY layer initialized
May 10 17:14:51 laptop kernel: [    5.927576] Bluetooth: RFCOMM socket layer initialized
May 10 17:14:51 laptop kernel: [    5.927581] Bluetooth: RFCOMM ver 1.11
May 10 17:16:47 laptop bluetoothd[747]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSource
May 10 17:16:47 laptop bluetoothd[747]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSink
May 10 17:16:47 laptop bluetoothd[747]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
May 10 17:17:03 laptop bluetoothd[747]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSource
May 10 17:17:03 laptop bluetoothd[747]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSink
```

---

### Post by jeremy31 on 2016-05-10
The AC cards bluetooth has a matching firmware file, ibt-hw-37.8.10-fw-1.10.3.11.e.bseq is a match for Intel version: 370810011003110e23

And yours shows read Intel version: 370810011001140d00
```
May 10 18:11:04 laptop kernel: [    3.793592] bluetooth hci0: Direct firmware load for intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq failed with error -2
```
Because currently there is no  intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq file

Added a comment on an old bug report that a bluetooth dev and a couple of Intel people are subscribed to.  Hopefully there is such a file

---

### Post by TuxManRemove on 2016-05-10
Thank you very much!

---

### Post by TuxManRemove on 2016-05-12
Hello,
I found:

[http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/commit/?id=13eb208681bf7cc7434189dd925e587d12707d50](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/commit/?id=13eb208681bf7cc7434189dd925e587d12707d50)

[http://marc.info/?l=linux-bluetooth&m=139483055908653&w=2](http://marc.info/?l=linux-bluetooth&m=139483055908653&w=2)

How can I do?
Thanks

---

### Post by jeremy31 on 2016-05-12
That is the wrong file and it doesn't work even if it is renamed

---

### Post by TuxManRemove on 2016-05-12
I have searched all over the internet and have not found the file.

In the Intel website link the kernel.org website:
[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)
Worse there is only .ucode file that is loaded with the operating system firmware. But not that file of bluetooth.

What I do?
Reported I the bug to ubuntu?

---

### Post by jeremy31 on 2016-05-12
You can do a bug report if you want, if you do a bug report, file it against package linux-firmware, post a link and I will try to help you with it

---

### Post by TuxManRemove on 2016-05-14
Hello,
Sorry for the delay.
I have reinstalled the computer to have a clean and updated operating system.
I read:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
 but do not know how to start. How and what files?
Thanks

---

### Post by jeremy31 on 2016-05-14
I would ```
ubuntu-bug linux-firmware
```
Then send the report and see if it shows up at launchpad, then you can edit to add that linux-firmware is missing intel/ibt-hw-37.8.10-fw-1.10.1.14.d.bseq and your bluetooth isn't working

It seems [this post](http://ubuntuforums.org/showthread.php?t=1011078) does a better job of explaining the process

---

### Post by TuxManRemove on 2016-05-14
Hello jeremy31,
I received an email from the store that sold me the ultrabook, had already informed them of the problem.
They tell me that they are going to report the problem to Ubuntu, I understand that if I do I'll be duplicating the same error. I'll ask them if they have already reported or if they have not done I will.
I inform you! Thank you very much

---

### Post by flmommens on 2017-02-25
Hello, I'm affected by the same issue. Has this bug been resolved? Is there a solution somewhere?

---

