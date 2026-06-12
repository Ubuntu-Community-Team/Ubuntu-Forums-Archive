---
title: "WiFi can't connecto after upgrade but to hotspot"
date: 2018-02-16
forum: Networking &amp; Wireless
---

### Post by leggy77 on 2018-02-16
Hello,

I upgraded ubuntu to 17.10 a couple of days ago and WiFi stopped behaving correctly.

By default it tries to work as a hotspot. 
If I turn hotspot off and I choose one wireless connection to connect to it tries until timeout. The only connection which I can connect to is my mobile phone hotspot.

What should I check in order to understand where the problem could be?

---

### Post by wildmanne39 on 2018-02-16
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by leggy77 on 2018-02-18
i guess this

04:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
    Subsystem: Foxconn International, Inc. AR9462 Wireless Network Adapter
    Kernel driver in use: ath9k
    Kernel modules: ath9k

is the device to consider but I cannot even think what could be the problem if I can connect to my mobile hotspot and not to my wifi (consider that before upgrading OS it worked perfectly).

The wireless connection configuration is the same as my desktop with 16.04 on. 

For some reason trying to connect reaches timeout.

Any clue?

---

### Post by wildmanne39 on 2018-02-18
Hi, please click on the wireless script in my signature, follow the directions for running it while trying to connect to the network you are having issues with and post the results back here using the pastebin link created.

---

### Post by leggy77 on 2018-02-18
Hi wildmanne39, thanks for your availability. Here you can find results

[http://paste.ubuntu.com/p/tQ5yyNpMF7/](http://paste.ubuntu.com/p/tQ5yyNpMF7/)

---

### Post by jeremy31 on 2018-02-18
Try ```
sudo rm /etc/NetworkManager/system-connections/motoglu
```
As that seems to be the hotspot, reboot and see if the issue persists, if it does please include new wireless script results

---

### Post by leggy77 on 2018-02-18
output after removing connections:


```
########## wireless info START ##########

Report from: 19 Feb 2018 00:02 CET +0100

Booted last: 19 Feb 2018 00:00 CET +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-32-generic #35-Ubuntu SMP Thu Jan 25 09:13:46 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

04:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Foxconn International, Inc. AR9462 Wireless Network Adapter [105b:e052]
    Kernel driver in use: ath9k

05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 14)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:079b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 22b8:2e76 Motorola PCS 
Bus 002 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 002 Device 002: ID 04f2:b3d6 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

##### lsmod #############################

ath9k                 151552  0
ath3k                  20480  0
ath9k_common           36864  1 ath9k
ath9k_hw              462848  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
bluetooth             540672  32 btrtl,btintel,bnep,btbcm,rfcomm,ath3k,btusb
mac80211              778240  1 ath9k
acer_wmi               20480  0
cfg80211              610304  4 mac80211,ath9k,ath,ath9k_common
sparse_keymap          16384  1 acer_wmi
wmi_bmof               16384  0
mxm_wmi                16384  1 nouveau
wmi                    24576  4 wmi_bmof,acer_wmi,mxm_wmi,nouveau
video                  40960  3 acer_wmi,nouveau,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp5s0f1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2943  bytes 193544 (193.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2943  bytes 193544 (193.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 524  bytes 286535 (286.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 680  bytes 154951 (154.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp5s0f1  no wireless extensions.

wlp4s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1000     1  0 Feb18 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp5s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.1/net/enp5s0f1
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9462 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.13.0-32-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/wlp4s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/EPC]] (600 root)
[connection] id=EPC | type=wifi | permissions=user:leggy:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=EPC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Webtek Ufficio]] (600 root)
[connection] id=Webtek Ufficio | type=wifi | permissions=user:leggy:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Webtek Ufficio
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Webtekspa5g]] (600 root)
[connection] id=Webtekspa5g | type=wifi | permissions=user:leggy:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Webtekspa5g
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Webtekspa]] (600 root)
[connection] id=Webtekspa | type=wifi | permissions=user:leggy:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Webtekspa
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/InfostradaWiFi2]] (600 root)
[connection] id=InfostradaWiFi2 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=InfostradaWiFi2
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp5s0f1  no frequency information.

wlp4s0    32 channels in total; available frequencies :
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

wlp4s0    Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp5s0f1  Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     55EFCC9F539475103977285
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
name:           ath9k
vermagic:       4.13.0-32-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath3k]
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     36C0F7AEF3B569F1798216D
depends:        bluetooth
intree:         Y
name:           ath3k
vermagic:       4.13.0-32-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_common]
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8A1D2C60031409F8A50F895
depends:        ath9k_hw,cfg80211,ath
intree:         Y
name:           ath9k_common
vermagic:       4.13.0-32-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_hw]
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF13127B5F7FC2736913C0C
depends:        ath
intree:         Y
name:           ath9k_hw
vermagic:       4.13.0-32-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath]
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
intree:         Y
name:           ath
vermagic:       4.13.0-32-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-32-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-32-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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

[/etc/modprobe.d/rt18723be.conf]
options rt18723be ant_sel=2

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 3039.377762] ath9k 0000:04:00.0 wlp4s0: renamed from wlan0
[ 3056.782276] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready (repeated 3 times)
[ 3237.457575] wlp4s0: authenticate with <MAC address>
[ 3237.470280] wlp4s0: send auth to <MAC address> (try 1/3)
[ 3237.472215] wlp4s0: authenticated
[ 3237.480101] wlp4s0: associate with <MAC address> (try 1/3)
[ 3237.484124] wlp4s0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=4)
[ 3237.484250] wlp4s0: associated
[ 3237.484307] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
[ 3283.033753] wlp4s0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3423.241485] wlp4s0: authenticate with <MAC address>
[ 3423.253877] wlp4s0: send auth to <MAC address> (try 1/3)
[ 3423.255718] wlp4s0: authenticated
[ 3423.260074] wlp4s0: associate with <MAC address> (try 1/3)
[ 3423.269173] wlp4s0: RX AssocResp from <MAC address> (capab=0x8431 status=0 aid=7)
[ 3423.269280] wlp4s0: associated
[ 3716.769251] wlp4s0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############
```

---

### Post by wildmanne39 on 2018-02-18
You have a softblock and a hardblock at the moment, please do:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot your computer and make sure your wifi is turn on with the swith/button/key combination and let us know if it is work.

Please use code tags when posting by clicking on the # button and put the output between them.

---

### Post by leggy77 on 2018-02-18
As I rebooted after running that line the wifi was turned on but no connection was established.
I had to manually connect to hotspot again to reply here.

Notice that I have no idea what to have a soft and/or hard block means.. could you please enlighten me?

ps. sorry, I'll pay attention to codeblocks later on ... :)

---

### Post by wildmanne39 on 2018-02-18
No worries that is how we all learn new things.

What is the name of the network you are trying to connect too? When you are trying to connect to it all other networks including your mobile hotspot is off correct? because network manager will connect to the strongest signal, you also want the ethernet to be unplugged or disabled.

---

### Post by leggy77 on 2018-02-19
I tried to connect also with hotspot turned off.. it just hangs there.

Ethernet cable is unpugged.

I don't know if there could be other networks to turn off. 

Strangest thing is that as system is booted hotspot is turned on on pc and I have to turn it off to be able to select wifi network to connect to. This wasn't prior 17.10 upgrade.

Absolutely no idea what to look after

---

### Post by leggy77 on 2018-02-19
Ok, I feel very sorry for wasting your time.

Today at launch break I went home and my wife told me that the whole day our desktop ubuntu 16.04 wasn't connecting. I checked it and sorted out that my wifi ssid was out of range, rebboting the system didn't help so an alarm rang out loud. I reset the router and it came back to work. Also my laptop got the connection back.

Murphy's law (and my dumbness too) are always ready to strike. My very bad that, seen perfect timing of upgrading ubuntu and router failure, I didn't try to reset the router at first but, on my side, router signals were ok and my laptop connections list didn't say out of range as it's prior version did.

So, thank you very much for your time and effort. Now everything is back on track.

Cheers!

---

### Post by wildmanne39 on 2018-02-19
That is good to hear, please use thread tools at the top of the page to mark the thread solved.

---

