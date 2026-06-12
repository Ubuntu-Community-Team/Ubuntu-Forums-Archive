---
title: "Wifi Hardware Disabled and Airplane Mode on Error"
date: 2019-11-13
forum: Networking &amp; Wireless
---

### Post by selim1781 on 2019-11-13
Hi everyone!

Today, I am getting this error. My open Wifi is sometimes(Average 30 sec.) Wifi Hardware Disabled and Airplane Mode on switching. I'm using dual boot. I'm using Ubuntu 18.04.3 LTS. My laptop is ASUS  X550JK-XO012D.

I'm grateful to help anyone. 

Here is my Wireless info.

```



########## wireless info START ##########


Report from: 14 Nov 2019 00:20 +03 +0300


Booted last: 14 Nov 2019 00:00 +03 +0300


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 4.15.0-70-generic #79-Ubuntu SMP Tue Nov 12 10:36:11 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	Subsystem: Lite-On Communications Inc RT3290 Wireless 802.11n 1T/1R PCIe [11ad:6010]
	Kernel driver in use: rt2800pci


04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b48c Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
mxm_wmi                16384  1 nouveau
mac80211              786432  3 rt2x00pci,rt2x00lib,rt2800lib
cfg80211              622592  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    24576  3 asus_wmi,mxm_wmi,nouveau
video                  45056  3 asus_wmi,i915,nouveau


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp4s0f1' [IF1]> brd <MAC address>
    inet 192.168.1.2/24 brd 192.168.1.255 scope global enp4s0f1
       valid_lft forever preferred_lft forever
    inet6 fe80::<IP6 'enp4s0f1' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp3s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp3s0f0' [IF2]> brd <MAC address>


##### iwconfig ##########################


enp4s0f1  no wireless extensions.


lo        no wireless extensions.


wlp3s0f0  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


default via 192.168.1.1 dev enp4s0f1 
169.254.0.0/16 dev enp4s0f1 scope link metric 1000 
192.168.1.0/24 dev enp4s0f1 proto kernel scope link src 192.168.1.2 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


	NetworkManager
	Wicd


Running:


root      4217     1  0 00:14 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp4s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8411-2_0.0.1 07/08/13
GENERAL.HWADDR:                         <MAC 'enp4s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.1/net/enp4s0f1
GENERAL.IP-IFACE:                       enp4s0f1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     enp4s0f1
GENERAL.CON-UUID:                       75b10f88-88e2-4c0e-9513-cea3484cbdd3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 0
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 0
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         fe80::<IP6 'enp4s0f1' [IF1]>/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   75b10f88-88e2-4c0e-9513-cea3484cbdd3 | enp4s0f1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   ca119ae1-52c1-332f-b74a-1ca804ff9795 | Wired connection 1


GENERAL.DEVICE:                         wlp3s0f0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.15.0-70-generic
GENERAL.FIRMWARE-VERSION:               0.37
GENERAL.HWADDR:                         <MAC 'wlp3s0f0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlp3s0f0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 


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
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Zyxel_6EE1]] (600 root)
[connection] id=Zyxel_6EE1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0f0' [IF2]> | mac-address-blacklist= | ssid=Zyxel_6EE1
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Muyendizler]] (600 root)
[connection] id=Muyendizler | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0f0' [IF2]> | mac-address-blacklist= | ssid=Muyendizler
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/#valarmorghulis_]] (600 root)
[connection] id=#valarmorghulis_ | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0f0' [IF2]> | mac-address-blacklist= | ssid=#valarmorghulis_
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Muyendizler_plus]] (600 root)
[connection] id=Muyendizler_plus | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0f0' [IF2]> | mac-address-blacklist= | ssid=Muyendizler_plus
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Europe/Istanbul (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp4s0f1  no frequency information.


lo        no frequency information.


wlp3s0f0  14 channels in total; available frequencies :
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


wlp3s0f0  Interface doesn't support scanning : Device or resource busy


enp4s0f1  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.15.0-70-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F39EE32C825037AEC74D884
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       4.15.0-70-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.15.0-70-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E9DAC6FF7F101DA345F84CB
depends:        rt2x00mmio,rt2x00lib,rt2800lib
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       4.15.0-70-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[rt2800lib]
filename:       /lib/modules/4.15.0-70-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     6D84032EF6E7036F4B6E120
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       4.15.0-70-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[rt2x00pci]
filename:       /lib/modules/4.15.0-70-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     158296886E96AF784C7C0D0
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       4.15.0-70-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[rt2x00mmio]
filename:       /lib/modules/4.15.0-70-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8C2F50979FA9E3AF4B8AED1
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       4.15.0-70-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[rt2x00lib]
filename:       /lib/modules/4.15.0-70-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B5F1347F74400E2BF5CD69F
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       4.15.0-70-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[mac80211]
filename:       /lib/modules/4.15.0-70-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CA60D8FB7E9197741540867
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-70-generic SMP mod_unload 
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
filename:       /lib/modules/4.15.0-70-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A545B569ABD42802819105C
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-70-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[  242.089050] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready
[  243.170598] wlp3s0f0: authenticate with <MAC address>
[  243.172292] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  243.173696] wlp3s0f0: authenticated
[  243.174312] wlp3s0f0: associate with <MAC address> (try 1/3)
[  243.177960] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  243.178030] wlp3s0f0: associated
[  243.279465] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  251.870405] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  257.130502] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  258.276108] wlp3s0f0: authenticate with <MAC address>
[  258.277799] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  258.283010] wlp3s0f0: authenticated
[  258.286245] wlp3s0f0: associate with <MAC address> (try 1/3)
[  258.294859] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  258.294929] wlp3s0f0: associated
[  258.401953] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  286.941987] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  292.203324] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  293.340948] wlp3s0f0: authenticate with <MAC address>
[  293.342799] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  293.344199] wlp3s0f0: authenticated
[  293.345749] wlp3s0f0: associate with <MAC address> (try 1/3)
[  293.349395] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  293.349468] wlp3s0f0: associated
[  293.448448] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  297.953595] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  308.083861] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  309.209433] wlp3s0f0: authenticate with <MAC address>
[  309.210951] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  309.213422] wlp3s0f0: authenticated
[  309.217386] wlp3s0f0: associate with <MAC address> (try 1/3)
[  309.221086] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  309.221163] wlp3s0f0: associated
[  309.319654] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  312.797443] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  318.060574] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  319.171508] wlp3s0f0: authenticate with <MAC address>
[  319.173192] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  319.174554] wlp3s0f0: authenticated
[  319.177254] wlp3s0f0: associate with <MAC address> (try 1/3)
[  319.180999] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  319.181075] wlp3s0f0: associated
[  319.280407] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  339.933175] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  344.938638] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  346.077903] wlp3s0f0: authenticate with <MAC address>
[  346.079600] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  346.080965] wlp3s0f0: authenticated
[  346.084971] wlp3s0f0: associate with <MAC address> (try 1/3)
[  346.088779] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  346.088902] wlp3s0f0: associated
[  346.188301] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  399.836692] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  405.103024] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  406.218488] wlp3s0f0: authenticate with <MAC address>
[  406.220189] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  406.221625] wlp3s0f0: authenticated
[  406.224446] wlp3s0f0: associate with <MAC address> (try 1/3)
[  406.228141] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  406.228252] wlp3s0f0: associated
[  406.329400] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  409.820840] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  415.084963] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  416.209311] wlp3s0f0: authenticate with <MAC address>
[  416.210991] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  416.212506] wlp3s0f0: authenticated
[  416.216470] wlp3s0f0: associate with <MAC address> (try 1/3)
[  416.220157] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  416.220245] wlp3s0f0: associated
[  416.319186] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  462.044254] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  467.054285] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[  468.187408] wlp3s0f0: authenticate with <MAC address>
[  468.189090] wlp3s0f0: send auth to <MAC address> (try 1/3)
[  468.190463] wlp3s0f0: authenticated
[  468.192104] wlp3s0f0: associate with <MAC address> (try 1/3)
[  468.195740] wlp3s0f0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=6)
[  468.195817] wlp3s0f0: associated
[  468.300046] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[  564.955291] wlp3s0f0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  569.964077] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)


########## wireless info END ############



```

---

### Post by jetsam on 2019-11-14
A few questions for you:  what causes it to become disabled?  Have you found work-arounds that enable you to re-enable your wi-fi and get back online when you want to?

I think we need more detail about when and how the problem happens before we have a hope of helping much.

Also, what's the basic architecture of the hardware (pc to usb wifi dongle, for example.)  Do you restart the system?  If so, when? Does the problem re-appear on restart or just at random times thereafter?

---

