---
title: "Broadcom BCM4313: WiFi random disconnects"
date: 2014-12-10
forum: Networking &amp; Wireless
---

### Post by Harish_V_G on 2014-12-10
Even i have the same problem....and i am noob to linux....pls help me with this issue....

My wifi is getting disconnected randomly....i tried to create a wifi hotspot, it worked for one day and then boom...frm nxt day onwards it works for few minutes and ets diconnected automatically....

to create wifi hotspot, i have done some changes as per this site....
[http://ubuntuhandbook.org/index.php/2014/09/3-ways-create-wifi-hotspot-ubuntu/](http://ubuntuhandbook.org/index.php/2014/09/3-ways-create-wifi-hotspot-ubuntu/)
[http://www.ubuntuhandbook.org/index.php/2014/09/wifi-hotspot-access-point-not-supported/](http://www.ubuntuhandbook.org/index.php/2014/09/wifi-hotspot-access-point-not-supported/)


dunno whether its due to that or not....

i have run wifiscript and the result is as per this 

```

########## wireless info START ##########

Report from: 10 Dec 2014 12:49 IST +0530

Booted last: 10 Dec 2014 11:40 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: bcma-pci-bridge

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0456]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6461 Microdia 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387371  0 
mac80211              630653  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
bcma                   52096  3 b43,brcmsmac
wmi                    19177  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe66:eb0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6095 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1694489 (1.6 MB)  TX bytes:736134 (736.1 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:186780 (186.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/OPO~]] (600 root)
[connection] id=OPO | type=802-11-wireless
[802-11-wireless] ssid=OPO1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/OPO]] (600 root)
[connection] id=OPO | type=802-11-wireless
[802-11-wireless] ssid=OPO1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Spice~]] (600 root)
[connection] id=Spice | type=802-11-wireless
[802-11-wireless] ssid=hotspot | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

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

wlan0     No scan results

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/iwlmvm.conf]
options iwlmvm power_scheme=1

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x2060 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 3978.102098] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3978.104278] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 3979.445403] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 3979.553947] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3979.553967] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3979.555263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3983.103765] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3983.103781] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3983.103966] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3983.124599] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: true
[ 3983.126334] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3983.127454] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 3984.412073] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 3984.518424] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3984.518445] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3984.518761] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3988.097139] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3988.097159] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3988.097369] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3988.127232] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: true
[ 3988.128593] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 3988.129869] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3989.226698] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 3989.333123] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3989.333143] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3989.333470] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3993.075261] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3993.075280] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3993.075484] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3993.097796] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: true
[ 3993.097819] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3993.099170] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 3994.197297] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 3994.303587] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3994.303605] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3994.304391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3998.086815] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3998.086831] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3998.087052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3998.108512] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: true
[ 3998.108544] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3998.110575] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 3999.403862] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 3999.510600] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3999.510615] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3999.511380] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4003.089066] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 4003.089082] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 4003.089353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4003.115051] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: true
[ 4003.115092] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4003.117127] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 4004.226524] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 4004.334582] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 4004.334604] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 4004.335934] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4008.107690] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 4008.107707] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 4008.107920] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4008.137709] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: true
[ 4008.138734] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 4008.139839] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4009.245108] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 4009.359411] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 4009.359432] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 4009.359813] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4013.074703] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 4013.074719] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 4013.074903] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4013.096303] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: true
[ 4013.096326] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4013.097710] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) (repeated 4 times)
[ 4014.208047] brcmsmac bcma0:0: brcms_ops_bss_info_changed: Beacon enabled: false
[ 4014.313172] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 4014.313188] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 4014.313793] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```


Pls check above the same and tell me wat corrections should i do....( i am noob in linux...:P)
Thanx in advance....:)

---

### Post by Hadaka on 2014-12-10
Hi, please copy and paste one command at a time
```
sudo modprobe -r ssb
sudodprobe -r b43
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
boot

---

### Post by Harish_V_G on 2014-12-10
thanx man...:)
its working now...after restart....

btw i modified the second line to sudo modprobe

...thanx once again..:)

---

### Post by Hadaka on 2014-12-10
Glad that worked for you.
and thanks for correcting my typo
please mark this thread solved
how to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Harish_V_G on 2014-12-12
Do i have to execute these commands everytime i restart....
because after few restarts it was not working...
then again i executed those commands and then it worked...

---

### Post by Hadaka on 2014-12-12
H, please do..
```
echo "brcmsmac" >>  /etc/modules
```
thanks.

---

