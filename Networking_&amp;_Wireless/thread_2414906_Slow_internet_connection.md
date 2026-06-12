---
title: "Slow internet connection"
date: 2019-03-17
forum: Networking &amp; Wireless
---

### Post by c0ntr0lledcha0s on 2019-03-17
Hey team,

I've recently converted from a Win7 setup to Ubuntu 18.04.2 LTS, loving the clean layout but my issue is that my Wifi internet speeds are now really slow (2-3 mbps compared to 22-25mbps on any other device (NZ connection so that's pretty standard)).

I've spent the last few days learning terminal, looking at fixes and trying a range of solutions over multiple forums but nothing has worked. Hoping someone with more knowledge could take a crack at it.

```


########## wireless info START ##########

Report from: 17 Mar 2019 17:34 NZDT +1300

Booted last: 17 Mar 2019 00:00 NZDT +1300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.18.0-16-generic #17~18.04.1-Ubuntu SMP Tue Feb 12 13:35:51 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2a9c]
    Kernel driver in use: r8169

05:00.0 Network controller [0280]: Ralink corp. RT3092 Wireless 802.11n 2T/2R PCIe [1814:3092]
    Subsystem: Device [15a9:0015]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 004: ID 1058:1042 Western Digital Technologies, Inc. Elements SE Portable (WDBPCK)
Bus 002 Device 003: ID 0bc2:2320 Seagate RSS LLC USB 3.0 bridge [Portable Expansion Drive]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0461:4d7a Primax Electronics, Ltd 
Bus 001 Device 003: ID 04f2:1665 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
mac80211              802816  3 rt2x00pci,rt2x00lib,rt2800lib
cfg80211              667648  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: wlp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp5s0' [IF2]> brd <MAC address>
    inet 192.168.1.106/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp5s0
       valid_lft 84835sec preferred_lft 84835sec
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.26.10.6 peer 10.26.10.5/32 scope global tun0
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

tun0      no wireless extensions.

wlp5s0    IEEE 802.11  ESSID:"NETGEAR55"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'NETGEAR55' [AN1]>   
          Bit Rate=43.3 Mb/s   Tx-Power=30 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:73  Invalid misc:1036   Missed beacon:0

##### route #############################

0.0.0.0/1 via 10.26.10.5 dev tun0 
default via 192.168.1.1 dev wlp5s0 proto dhcp metric 20600 
10.26.10.1 via 10.26.10.5 dev tun0 
10.26.10.5 dev tun0 proto kernel scope link src 10.26.10.6 
128.0.0.0/1 via 10.26.10.5 dev tun0 
137.59.252.195 via 192.168.1.1 dev wlp5s0 
169.254.0.0/16 dev wlp5s0 scope link metric 1000 
192.168.1.0/24 dev wlp5s0 proto kernel scope link src 192.168.1.106 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1036     1  0 17:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3092 Wireless 802.11n 2T/2R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.18.0-16-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     NETGEAR55
GENERAL.CON-UUID:                       084da394-686e-4232-8ff3-ea216c744cd3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     43 Mb/s
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
IP4.ADDRESS[1]:                         192.168.1.106/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 20600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[4]:                           dst = 137.59.252.195/32, nh = 192.168.1.1, mt = 0
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        expiry = 1552882086
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[27]:                       ip_address = 192.168.1.106
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   084da394-686e-4232-8ff3-ea216c744cd3 | NETGEAR55

GENERAL.DEVICE:                         tun0
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/tun0
GENERAL.IP-IFACE:                       tun0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     tun0
GENERAL.CON-UUID:                       38302129-b421-42ea-9810-1c1c641f8fee
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
IP4.ADDRESS[1]:                         10.26.10.6/32
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 10.26.10.5/32, nh = 0.0.0.0, mt = 0
IP4.ROUTE[2]:                           dst = 0.0.0.0/1, nh = 10.26.10.5, mt = 0
IP4.ROUTE[3]:                           dst = 128.0.0.0/1, nh = 10.26.10.5, mt = 0
IP4.ROUTE[4]:                           dst = 10.26.10.1/32, nh = 10.26.10.5, mt = 0
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   38302129-b421-42ea-9810-1c1c641f8fee | tun0

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
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

SSID       BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
NETGEAR55  <MAC 'NETGEAR55' [AN1]>  Infra  13    2472 MHz  195 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2      yes     *      

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 2

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

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NETGEAR55]] (600 root)
[connection] id=NETGEAR55 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp5s0' [IF2]> | mac-address-blacklist= | ssid=NETGEAR55
[ipv4] method=auto
[ipv6] method=ignore

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

global
country NZ: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS, AUTO-BW
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

tun0      no frequency information.

wlp5s0    13 channels in total; available frequencies :
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
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

wlp5s0    Failed to read scan data : Resource temporarily unavailable

tun0      Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     99E7C626D61A874D884E3A2
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BB8B8955B8B201DFEB6191F
depends:        rt2x00mmio,rt2x00lib,rt2800lib
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2800lib]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     966CF51FCABF548A597F127
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00pci]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C5A0354349252C4888D0842
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00mmio]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4E56E599A263E22755195FD
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00lib]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E9726B139222EDB02105054
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.18.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.0-16-generic SMP mod_unload 
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
filename:       /lib/modules/4.18.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-16-generic SMP mod_unload 
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

[/etc/modprobe.d/ath9k.conf]
options ath9K nohwcrypt=1

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

[/etc/modprobe.d/network_drivers.conf]
install rt2860sta /sbin/modprobe --ignore-install rt2860sta $CMDLINE_OPTS; /bin/echo "1814 3092" > /sys/bus/usb/drivers/rt2860/new_id

[/etc/modprobe.d/rtl8192ce.conf]
options rtl8192ce swenc=1 ips=0 fwlps=0

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/network_drivers.rules]
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="1814", ATTR{idProduct}=="3092", RUN+="/sbin/modprobe -qba rt2860sta"

##### dmesg #############################

[    6.766609] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    6.864079] r8169 0000:02:00.0 enp2s0: link down
[    6.864160] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    6.868702] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[    6.868773] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[    6.869854] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.40
[    7.037532] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready (repeated 2 times)
[    7.801206] [<0000000027919fc2>] rt2800mmio_interrupt [rt2800mmio]
[    8.037983] wlp5s0: authenticate with <MAC 'NETGEAR55' [AN1]>
[    8.041465] wlp5s0: send auth to <MAC 'NETGEAR55' [AN1]> (try 1/3)
[    8.112139] wlp5s0: authenticated
[    8.120176] wlp5s0: associate with <MAC 'NETGEAR55' [AN1]> (try 1/3)
[    8.216102] wlp5s0: RX AssocResp from <MAC 'NETGEAR55' [AN1]> (capab=0x1411 status=0 aid=1)
[    8.216172] wlp5s0: associated
[    8.327260] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[ 1578.848813] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1579.456918] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1580.060742] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1580.660803] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1581.464810] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1582.068784] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1582.668775] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1583.272794] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1584.140774] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1584.744772] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1585.348722] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1585.952777] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1586.828755] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1587.440766] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1588.040635] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1588.644740] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1589.580734] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1590.180741] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1590.784696] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1591.392732] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1592.260741] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1592.864729] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1593.468617] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1594.068767] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1594.940779] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1595.556696] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

########## wireless info END ############

```

Any help would be appreciated

---

