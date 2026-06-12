---
title: "(1)Tagged Wired Nic (2vlans) &lt;-Bridged- (2)Wireless Nics.. no routing for localhost"
date: 2015-05-04
forum: Networking &amp; Wireless
---

### Post by david144 on 2015-05-04
Hi all, hoping you can help me here so I can get updates, install new software, etc.

I built a wireless AP system using Trusty Tahr 14.04.02, installed hostapd 1:2.1-0ubuntu1, and bridge-utils 1.5-6ubuntu2.

My system has a single gigabit wired nic which I want to bridge two wireless segments using vlan tagging (guests on my dmz, and trusted devices on my inside network)

I'm trunking two vlans from my switch (10 dmz & 192 inside) to my interface and using bridges to connect two wireless nics to the tagged interfaces.

Bridging is working for my wireless clients on both networks. However the access point host itself has no way to route to the gateway and I can't figure out why. WGET returns "failed: No route to host." and apt-get returns "connect (101: Network is unreachable)".

My tagged, and bridge interface has the default gateway added in the interfaces file, I can ping devices on the local subnets in both vlans, resolve DNS from my local dns servers, and I can ping the gateway (firewall has ICMP blocked except for specific internal hosts, but I can see the drops in my firewall logs as they happen) so I know the physical interface is all fine but can't figure out why I'm not able to route traffic outside the local subnets from the hostapd server itself. (again wireless traffic is forwarding fine and routing as desired)

I appreciate any help you can give, below are what I hope are all the relevant needed configs and troubleshooting gathered. 

Let me know if I need to add anything else that helps give you an idea what might be wrong   Thanks!

Wireless-info.txt:
```

########## wireless info START ##########

Report from: 04 May 2015 20:45 PDT -0700

Booted last: 04 May 2015 19:03 PDT -0700

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, nomodeset, noplymouth, vt.handoff=7

##### desktop ###########################

sed: can't read /home/davery/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
        Subsystem: Dell OptiPlex 755 [1028:0211]
        Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Qualcomm Atheros AR9227 Wireless Network Adapter [168c:002d] (rev 01)
        Subsystem: Qualcomm Atheros Device [168c:0300]
        Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2070L]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info.sh: line 176: rfkill: command not found

##### lsmod #############################

rt2800usb              27034  0
ath9k                 164164  0
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  4 ath9k,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  4 ath,ath9k,mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0.192
iface eth0.192 inet static
address 192.168.4.7
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
dns-nameservers 192.168.4.2 192.168.4.3 192.168.4.1
vlan-raw-device eth0

auto eth0.10
iface eth0.10 inet static
address 10.1.100.2
netmask 255.255.255.0
dns-nameservers 10.1.100.1
vlan-raw-device eth0

auto wlan0
iface wlan0 inet manual
pre-up ifconfig $IFACE up
pre-down ifconfig $IFACE down

auto wlan1
iface wlan1 inet manual
pre-up ifconfig $IFACE up
pre-down ifconfig $IFACE down

auto br192
iface br192 inet static
address 192.168.4.7
netmask 255.255.255.0
gateway 192.168.4.1
dns-nameservers 192.168.4.2 192.168.4.3 192.168.4.1
bridge-ports eth0.192

auto br10
iface br10 inet static
address 10.1.100.2
netmask 255.255.255.0
dns-nameservers 10.1.100.1
bridge-ports eth0.10

##### ifconfig ##########################

br10      Link encap:Ethernet  HWaddr <MAC 'br10' [IF]>
          inet addr:10.1.100.2  Bcast:10.1.100.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:48449 (48.4 KB)  TX bytes:1658 (1.6 KB)

br192     Link encap:Ethernet  HWaddr <MAC 'br10' [IF]>
          inet addr:192.168.4.7  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1504053 (1.5 MB)  TX bytes:539020 (539.0 KB)

eth0      Link encap:Ethernet  HWaddr <MAC 'br10' [IF]>
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34357 errors:0 dropped:305 overruns:0 frame:0
          TX packets:12999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5924869 (5.9 MB)  TX bytes:1545607 (1.5 MB)
          Interrupt:21 Memory:fe9e0000-fea00000

eth0.10   Link encap:Ethernet  HWaddr <MAC 'br10' [IF]>
          inet addr:10.1.100.2  Bcast:10.1.100.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:48449 (48.4 KB)  TX bytes:2306 (2.3 KB)

eth0.192  Link encap:Ethernet  HWaddr <MAC 'br10' [IF]>
          inet addr:192.168.4.7  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4958411 (4.9 MB)  TX bytes:1420323 (1.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>
          inet6 addr: fe80::12fe:edff:feeb:48d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:884213 (884.2 KB)  TX bytes:2646262 (2.6 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>
          inet6 addr: fe80::225:9cff:fea5:fc34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:59017 (59.0 KB)

wlan0_0   Link encap:Ethernet  HWaddr <MAC 'wlan0_0' [IF]>
          inet6 addr: fe80::12fe:edff:feeb:48d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:613916 (613.9 KB)

##### iwconfig ##########################

br192     no wireless extensions.

br10      no wireless extensions.

eth0.10   no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

eth0.192  no wireless extensions.

wlan0_0   IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

wlan1     IEEE 802.11bg  Mode:Master  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.4.1     0.0.0.0         UG    0      0        0 eth0.192
10.1.100.0      0.0.0.0         255.255.255.0   U     0      0        0 br10
192.168.4.0     0.0.0.0         255.255.255.0   U     0      0        0 br192

##### resolv.conf #######################

nameserver 10.1.100.1
nameserver 192.168.4.2
nameserver 192.168.4.3

##### NetworkManager info ###############

./wireless-info.sh: line 201: nmcli: command not found

./wireless-info.sh: line 203: nmcli: command not found

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

Acquisition of admin privileges failed.

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country CN:
        (2402 - 2482 @ 40), (N/A, 20)
        (5735 - 5835 @ 40), (N/A, 30)
        (57240 - 59400 @ 2160), (N/A, 28)
        (59400 - 63720 @ 2160), (N/A, 44)
        (63720 - 65880 @ 2160), (N/A, 28)

##### iwlist channels ###################

br192     no frequency information.

br10      no frequency information.

eth0.10   no frequency information.

eth0      no frequency information.

lo        no frequency information.

eth0.192  no frequency information.

wlan0_0   13 channels in total; available frequencies :
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
wlan1     13 channels in total; available frequencies :
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

br192     Interface doesn't support scanning.

br10      Interface doesn't support scanning.

wlan0_0   Interface doesn't support scanning : Operation not supported

wlan1     Interface doesn't support scanning : Operation not supported

eth0.10   Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0.192  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Operation not supported

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     98B048D64D7288E7C870495
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[ath9k]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[rt2x00usb]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1C7B3D09AA920FB776204BA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7A7EEDE3C2270AE56EB54F8
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[ath9k_common]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E9BB2D2E4429AB671216A29
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

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

loop
lp
rtc
8021q

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'br10' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x1737:0x0077 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0_0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0_0"

##### dmesg #############################

[    3.717748] ath: EEPROM regdomain: 0x809c
[    3.717751] ath: EEPROM indicates we should expect a country code
[    3.717753] ath: doing EEPROM country->regdmn map search
[    3.717754] ath: country maps to regdmn code: 0x52
[    3.717756] ath: Country alpha2 being used: CN
[    3.717757] ath: Regpair used: 0x52
[    3.742247] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[    3.786975] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0006 detected
[    4.437126] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.441712] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[    4.444637] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[    4.867757] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[    6.034660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.034751] device wlan0 entered promiscuous mode
[    6.034983] device wlan1 entered promiscuous mode
[    6.128999] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[    6.129030] br10: port 2(wlan1) entered forwarding state (repeated 2 times)
[    6.153454] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.153479] br192: port 2(wlan0) entered forwarding state (repeated 2 times)
[    6.154235] device wlan0_0 entered promiscuous mode
[    6.154335] IPv6: ADDRCONF(NETDEV_UP): wlan0_0: link is not ready
[    6.154339] br192: port 3(wlan0_0) entered forwarding state (repeated 2 times)
[    6.201206] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0_0: link becomes ready
[   21.148016] br10: port 2(wlan1) entered forwarding state
[   21.180025] br192: port 2(wlan0) entered forwarding state
[   21.180041] br192: port 3(wlan0_0) entered forwarding state

########## wireless info END ############

```

Bridges:
```

$ brctl show
bridge name     bridge id               STP enabled     interfaces
br10            8000.002170060c65       no              eth0.10
                                                        wlan1
br192           8000.002170060c65       no              eth0.192
                                                        wlan0
                                                        wlan0_0

```

ping from AP host to Inside DNS across switches:
```

$ ping 192.168.4.2
PING 192.168.4.2 (192.168.4.2) 56(84) bytes of data.
64 bytes from 192.168.4.2: icmp_seq=1 ttl=128 time=0.482 ms
64 bytes from 192.168.4.2: icmp_seq=2 ttl=128 time=0.348 ms
64 bytes from 192.168.4.2: icmp_seq=3 ttl=128 time=0.236 ms
64 bytes from 192.168.4.2: icmp_seq=4 ttl=128 time=0.237 ms

--- 192.168.4.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.236/0.325/0.482/0.103 ms

```

ping from gateway back to AP host both br interfaces:
```

fw:/root # ping 10.1.100.2
PING 10.1.100.2 (10.1.100.2) 56(84) bytes of data.
64 bytes from 10.1.100.2: icmp_seq=1 ttl=64 time=0.249 ms
64 bytes from 10.1.100.2: icmp_seq=2 ttl=64 time=0.213 ms
64 bytes from 10.1.100.2: icmp_seq=3 ttl=64 time=0.244 ms
64 bytes from 10.1.100.2: icmp_seq=4 ttl=64 time=0.197 ms
64 bytes from 10.1.100.2: icmp_seq=5 ttl=64 time=0.328 ms
64 bytes from 10.1.100.2: icmp_seq=6 ttl=64 time=0.222 ms
^C
--- 10.1.100.2 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4997ms
rtt min/avg/max/mdev = 0.197/0.242/0.328/0.043 ms
fw:/root # ping 192.168.4.7
PING 192.168.4.7 (192.168.4.7) 56(84) bytes of data.
64 bytes from 192.168.4.7: icmp_seq=1 ttl=64 time=0.295 ms
64 bytes from 192.168.4.7: icmp_seq=2 ttl=64 time=0.234 ms
64 bytes from 192.168.4.7: icmp_seq=3 ttl=64 time=0.205 ms
64 bytes from 192.168.4.7: icmp_seq=4 ttl=64 time=0.337 ms
64 bytes from 192.168.4.7: icmp_seq=5 ttl=64 time=0.253 ms
^C
--- 192.168.4.7 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.205/0.264/0.337/0.050 ms
fw:/root # 

```

Here's a visual of the situation:
[ATTACH=CONFIG]261776[/ATTACH]

---

### Post by david144 on 2015-05-05
also in case you are wondering wlan0 and wlan0_0 are hosting separate SSID's on my inside bridge because my girlfriends laptop won't connect to the same SSID as my devices with my hostapd.conf settings so I setup a separate wireless SSID with settings compatible with her nic:

```

#sets the wifi interface to use, is wlan0 in most cases
interface=wlan0
# Locally administered MAC Address
bssid=10:fe:ed:eb:48:d6
#Bridge to wired ethernet
bridge=br192
#driver to use, nl80211 works in most cases
driver=nl80211
#sets the ssid of the virtual wifi access point
ssid= ****REDACTED****
#HT Mode compatability
ht_capab=[HT40][SHORT-GI-40][DSSS_CCK-40]
#enable 802.11n
ieee80211n=1
#sets the mode of wifi, depends upon the devices you will be using. It can be a,b,g,n. Setting to g ensures backward compatiblity.
hw_mode=g
#sets the channel for your wifi
channel=8
#macaddr_acl sets options for mac address filtering. 0 means "accept unless in deny list"
macaddr_acl=1
#accept connections from these MAC addresses:
accept_mac_file=/etc/hostapd/accept
#setting ignore_broadcast_ssid to 1 will disable the broadcasting of ssid
ignore_broadcast_ssid=0
#ignore_broadcast_ssid=1
#Sets authentication algorithm
#1 - only open system authentication
#2 - both open system authentication and shared key authentication
auth_algs=1
#####Sets WPA and WPA2 authentication#####
#wpa option sets which wpa implementation to use
#1 - wpa only
#2 - wpa2 only
#3 - both
wpa=2
#sets wpa passphrase required by the clients to authenticate themselves on the network
wpa_passphrase= ****REDACTED****
#sets wpa key management
wpa_key_mgmt=WPA-PSK
#sets encryption used by WPA
wpa_pairwise=CCMP TKIP
#sets encryption used by WPA2
rsn_pairwise=CCMP
#################################
#####Sets WEP authentication#####
#WEP is not recommended as it can be easily broken into
#wep_default_key=0
#wep_key0=qwert    #5,13, or 16 characters
#optionally you may also define wep_key2, wep_key3, and wep_key4
#################################
#For No encryption, you don't need to set any options
######
####
######
# SSID for her Laptop
bss=wlan0_0
bridge=br192
ssid= ****REDACTED****
#ht_capab=[HT20]
macaddr_acl=1
accept_mac_file=/etc/hostapd/accept
ignore_broadcast_ssid=0
auth_algs=1
wpa=2
wpa_passphrase= ****REDACTED****
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP TKIP
rsn_pairwise=CCMP

```

---

### Post by david144 on 2015-05-05
To run the bridges and WLANs separately I'm running them in separate @reboot cron jobs:

```

@reboot /usr/sbin/hostapd -dt /etc/hostapd/hostapd10.conf > /var/log/hostapd/dmz-wireless
@reboot /usr/sbin/hostapd -dt /etc/hostapd/hostapd192.conf > /var/log/hostapd/inside-wireless

```

I don't think the wireless logs should be needed, but if there's particular information I should look for in them please let me know.

---

### Post by david144 on 2015-05-05
Think I solved this, so far with three reboots everything seems stable, wireless is working, routing from the AP host is working..

Begin ***TLDR***:

So while trying to come up with a work around in the mean time I setup a proxy server with squid and failing miserably at something that should be so easy I decided to drop the proxy server altogether and re-focus on my issue at the AP host because I swore this used to work. (proxy server probably worked fine since the issue was my local routing, but I don't care to bother setting it up again to test it)

So last year I remember doing an image backup and then release upgrade from 12.04 to to 14.04 LTS to test if my hardware and AP would work better at N speeds (it didn't help the speed issue I still have that even with a different NIC) but I never had this routing issue until recently.

The routing stopped working when I was troubleshooting an issue with my tagged vlan 10 (eth0.10 / br10) interface on the system not being able to traverse the switches. (that was because I hadn't saved my config on the 3Com switch before powering it down to re-organize my closet and vlan10 wasn't configured on the LAGG between the switches, that was fixed but at the time I hadn't noticed the routing issue being a problem because my DMZ wireless devices checked out fine and I moved on forgetting all about what I had done trying to troubleshoot in my interfaces file)

So now fast forward a couple months until this early May weekend and I decided to get back to running my F@H clients on my new VMWare server and other devices which run 24/7 and have the bandwidth (like this wireless AP host) and then I find I can't get packages with aptitude. Couldn't get out with wget, couldn't do anything past the gateway..

:End ***TLDR***

_**Skip to solution..**_
I set the eth0.10 to manual commented out the IP address, mask, etc, but left it in the br10 interface:
```

auto lo
iface lo inet loopback

auto eth0.192
iface eth0.192 inet static
address 192.168.4.7
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
dns-nameservers 192.168.4.2 192.168.4.3 192.168.4.1
vlan-raw-device eth0

auto eth0.10
iface eth0.10 inet manual
#iface eth0.10 inet static
#address 10.1.100.2
#netmask 255.255.255.0
#dns-nameservers 10.1.100.1
vlan-raw-device eth0

#Wireless for VLAN 192 bridge
auto wlan0
iface wlan0 inet manual
pre-up ifconfig $IFACE up
pre-down ifconfig $IFACE down

#Wireless for VLAN 10 bridge
auto wlan1
iface wlan1 inet manual
pre-up ifconfig $IFACE up
pre-down ifconfig $IFACE down

auto br192
iface br192 inet static
address 192.168.4.7
netmask 255.255.255.0
gateway 192.168.4.1
dns-nameservers 192.168.4.2 192.168.4.3 192.168.4.1
bridge-ports eth0.192

auto br10
iface br10 inet static
address 10.1.100.2
netmask 255.255.255.0
dns-nameservers 10.1.100.1
bridge-ports eth0.10

```

I don't know why it works but it does. Something about having both of the tagged interfaces with IP addresses the traffic was trying to go to 192.168.4.1 over eth0.10. Everything shows Metric:1 but I am chalking it up to gremlins
```

br10      Link encap:Ethernet  HWaddr 00:21:70:06:0c:65
          inet addr:10.1.100.2  Bcast:10.1.100.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22709 (22.7 KB)  TX bytes:2623 (2.6 KB)


br192     Link encap:Ethernet  HWaddr 00:21:70:06:0c:65
          inet addr:192.168.4.7  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:52231600 (52.2 MB)  TX bytes:1061967 (1.0 MB)


eth0      Link encap:Ethernet  HWaddr 00:21:70:06:0c:65
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42194 errors:0 dropped:66 overruns:0 frame:0
          TX packets:16273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:54980859 (54.9 MB)  TX bytes:1571791 (1.5 MB)
          Interrupt:21 Memory:fe9e0000-fea00000


eth0.10   Link encap:Ethernet  HWaddr 00:21:70:06:0c:65
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:517267 (517.2 KB)  TX bytes:306503 (306.5 KB)


eth0.192  Link encap:Ethernet  HWaddr 00:21:70:06:0c:65
          inet addr:192.168.4.7  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe06:c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:52417720 (52.4 MB)  TX bytes:1132122 (1.1 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1064 (1.0 KB)  TX bytes:1064 (1.0 KB)


wlan0     Link encap:Ethernet  HWaddr 10:fe:ed:eb:48:d6
          inet6 addr: fe80::12fe:edff:feeb:48d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:70129 (70.1 KB)  TX bytes:253089 (253.0 KB)


wlan1     Link encap:Ethernet  HWaddr 00:25:9c:a5:fc:34
          inet6 addr: fe80::225:9cff:fea5:fc34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:304002 (304.0 KB)  TX bytes:555522 (555.5 KB)


wlan0_0   Link encap:Ethernet  HWaddr 10:fe:ed:eb:48:d7
          inet6 addr: fe80::12fe:edff:feeb:48d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:134291 (134.2 KB)

```

Even though previously it showed the Use Iface as eth0.192 once I commented out the eth0.10 section my default route began using br192:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.4.1     0.0.0.0         UG    0      0        0 br192
10.1.100.0      *               255.255.255.0   U     0      0        0 br10
192.168.4.0     *               255.255.255.0   U     0      0        0 br192

```

---

