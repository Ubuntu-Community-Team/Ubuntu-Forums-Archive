---
title: "Wifi not connecting on 16.06"
date: 2019-05-29
forum: Networking &amp; Wireless
---

### Post by gamerwael on 2019-05-29
Ever since i installed ubuntu on my laptop the wifi doesnt seem to work. it displays available networks but doesnt connect. Similar problem is faced with bluetooth. My wifi chipset is Realtek RT3090. Pls help

```
########## wireless info START ##########

Report from: 29 May 2019 16:46 IST +0530

Booted last: 29 May 2019 00:00 IST +0530

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.15.0-50-generic #54~16.04.1-Ubuntu SMP Wed May 8 15:50:20 UTC 2019 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:143a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Hewlett-Packard Company RT3090 Wireless 802.11n 1T/1R PCIe [103c:1453]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 020: ID 148f:1000 Ralink Technology, Corp. Motorola BC4 Bluetooth 3.0+HS Adapter
Bus 001 Device 019: ID 5986:0149 Acer, Inc 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
8: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
13: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             110592  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              49152  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
eeprom_93cx6           16384  1 rt2800pci
ath10k_pci             45056  0
ath10k_core           323584  1 ath10k_pci
ath9k                 139264  0
ath9k_common           36864  1 ath9k
ath9k_hw              458752  2 ath9k,ath9k_common
ath                    24576  4 ath9k_hw,ath9k,ath10k_core,ath9k_common
b43                   397312  0
bcma                   57344  1 b43
ssb                    57344  1 b43
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
mac80211              684032  6 rt2800lib,rt2x00pci,b43,rt2x00lib,ath9k,ath10k_core
wmi_bmof               16384  0
cfg80211              540672  7 b43,rt2x00lib,mac80211,ath9k,ath,ath10k_core,ath9k_common
wmi                    20480  2 wmi_bmof,hp_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-essid TP-LINK_88E660
wpa-psk <WPA key removed>

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.0.108/24 brd 192.168.0.255 scope global dynamic enp2s0
       valid_lft 7197sec preferred_lft 7197sec
    inet6 fe80::a538:8336:4327:aa12/64 scope link 
       valid_lft forever preferred_lft forever
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC address> brd <MAC address>
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
5: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'virbr0-nic' [IF2]> brd <MAC address>
6: wlp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp3s0' [IF3]> brd <MAC address>

##### iwconfig ##########################

virbr0-nic  no wireless extensions.

virbr0    no wireless extensions.

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:Off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr;off   Fragment thr:Off
          Power Management:On
          

##### route #############################

default via 192.168.0.1 dev enp2s0  proto static  metric 100 
169.254.0.0/16 dev virbr0  scope link  metric 1000 linkdown 
192.168.0.0/24 dev enp2s0  proto kernel  scope link  src 192.168.0.108  metric 100 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 linkdown 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      7807     1  0 16:05 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         virbr0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/2
GENERAL.IP-IFACE:                       virbr0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     virbr0
GENERAL.CON-UUID:                       304f1812-0def-4a95-a944-109ecaf1ad75
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   304f1812-0def-4a95-a944-109ecaf1ad75 | virbr0
IP4.ADDRESS[1]:                         192.168.122.1/24
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
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
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       02c81a77-f64e-3029-b1fa-cd672f153c77
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   02c81a77-f64e-3029-b1fa-cd672f153c77 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.108/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1559135774
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.108
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::a538:8336:4327:aa12/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3090 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.15.0-50-generic
GENERAL.FIRMWARE-VERSION:               0.34
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlp3s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5,4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8de896c7-f026-48a5-b7be-28763a674ea7 | NETGEAR06
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   2dff45ae-e2bf-4ceb-a7dd-8876913dcc80 | Hotspot

GENERAL.DEVICE:                         virbr0-nic
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'virbr0-nic' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/3
GENERAL.IP-IFACE:                       virbr0-nic
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
NETGEAR06       <MAC 'NETGEAR06' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2       no        
Flat8           <MAC 'Flat8' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
TP-LINK_6DC42E  <MAC 'TP-LINK_6DC42E' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/HUAWEI-E5776-0904]] (600 root)
[connection] id=HUAWEI-E5776-0904 | type=wifi | permissions=user:gamerwael:;
[wifi] mac-address=<MAC 'wlp3s0' [IF3]> | mac-address-blacklist= | ssid=HUAWEI-E5776-0904
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF3]> | mac-address-blacklist= | ssid=gamerwael-HP-G62-Notebook-PC
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR06]] (600 root)
[connection] id=NETGEAR06 | type=wifi | permissions=user:gamerwael:;
[wifi] mac-address=<MAC 'wlp3s0' [IF3]> | mac-address-blacklist= | ssid=NETGEAR06
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_88E660]] (600 root)
[connection] id=TP-LINK_88E660 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF3]> | mac-address-blacklist= | ssid=TP-LINK_88E660
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/iPhone 6s+]] (600 root)
[connection] id=iPhone 6s+ | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF3]> | mac-address-blacklist= | ssid=iPhone 6s+
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tikona_Broadband]] (600 root)
[connection] id=Tikona_Broadband | type=wifi | permissions=user:gamerwael:;
[wifi] mac-address=<MAC 'wlp3s0' [IF3]> | mac-address-blacklist= | ssid=Tikona_Broadband
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

virbr0-nic  no frequency information.

virbr0    no frequency information.

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    14 channels in total; available frequencies :
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

virbr0-nic  Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_6DC42E' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:On
                    ESSID:"TP-LINK_6DC42E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004d846f3b4
                    Extra: Last beacon: 11648ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TP-LINK_57FC' [AC2]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_57FC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014a2ada180
                    Extra: Last beacon: 592ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     9B5C2765C235C863C24FDE0
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       4.15.0-50-generic SMP mod_unload 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     2AF67DBF566ACB443136786
depends:        rt2x00mmio,rt2x00lib,rt2800lib
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[rt2800lib]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     E3426613D56538B49359106
depends:        mac80211,rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[rt2x00pci]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     EF62F1ED5B94FD33F012351
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[rt2x00mmio]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     DE3F68ABAA885403D3E251A
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[rt2x00lib]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     4B1933EC31700CF6D6056ED
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[ath10k_pci]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-6.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     63EC35DB9BF9FC4074A002D
depends:        ath10k_core
retpoline:      Y
intree:         Y
name:           ath10k_pci
vermagic:       4.15.0-50-generic SMP mod_unload 686 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     165FDC1E16C9659545F5EBF
depends:        mac80211,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath10k_core
vermagic:       4.15.0-50-generic SMP mod_unload 686 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath9k]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F4328CE52BA6067DD4EDE7B
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       4.15.0-50-generic SMP mod_unload 686 
parm:           debugDebugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
parm:           use_msi:Use MSI instead of INTx if possible (int)

[ath9k_common]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     0340C3244B71A3EDEF1E37E
depends:        ath9k_hw,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[ath9k_hw]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D5984DFEF6457DDB060988E
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[ath]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A592EBDEEE43676A2F56015
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[b43]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode42.fw
firmware:       b43/ucode40.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode30_mimo.fw
firmware:       b43/ucode33_lcn40.fw
firmware:       b43/ucode29_mimo.fw
firmware:       b43/ucode26_mimo.fw
firmware:       b43/ucode25_mimo.fw
firmware:       b43/ucode25_lcn.fw
firmware:       b43/ucode24_lcn.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode16_lp.fw
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
srcversion:     9F0109CA3DBCBC74B77ACE8
depends:        mac80211,ssb,bcma,cfg80211
retpoline:      Y
intree:         Y
name:           b43
vermagic:       4.15.0-50-generic SMP mod_unload 686 
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

[bcma]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F4DB57748318105D28C557A
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[ssb]
filename:       /lib/modules/4.15.0-50-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     12D8BAB8F43573B88998E25
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       4.15.0-50-generic SMP mod_unload 686 

[mac80211]
filename:       /lib/modules/4.15.0-50-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     10B87D6D65DDD085D1326C9
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-50-generic SMP mod_unload 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-50-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C615A4309BFED95CEE6CECF
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-50-generic SMP mod_unload 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: Y

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0
use_msi: 0

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
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

ath9k

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[10282.067722] r8169 0000:02:00.0 enp2s0: link down
[10285.439225] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[10285.479532] r8169 0000:02:00.0 enp2s0: link down
[10285.479633] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[10285.482050] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[10343.291659] r8169 0000:02:00.0 enp2s0: link up
[10343.291673] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[10969.937755] r8169 0000:02:00.0 enp2s0: link down
[10971.449070] r8169 0000:02:00.0 enp2s0: link up
[11157.678748] wlp3s0: authenticate with <MAC address>
[11157.692296] wlp3s0: send auth to <MAC address> (try 1/3)
[11157.743567] wlp3s0: send auth to <MAC address> (try 2/3)
[11157.771691] wlp3s0: send auth to <MAC address> (try 3/3)
[11157.813093] wlp3s0: authentication with <MAC address> timed out
[11158.990695] wlp3s0: authenticate with <MAC address>
[11159.003479] wlp3s0: send auth to <MAC address> (try 1/3)
[11159.050940] wlp3s0: send auth to <MAC address> (try 2/3)
[11159.095020] wlp3s0: send auth to <MAC address> (try 3/3)
[11159.133974] wlp3s0: authentication with <MAC address> timed out
[11160.714441] wlp3s0: authenticate with <MAC address>
[11160.726727] wlp3s0: send auth to <MAC address> (try 1/3)
[11160.750955] wlp3s0: send auth to <MAC address> (try 2/3)
[11160.792018] wlp3s0: send auth to <MAC address> (try 3/3)
[11160.857408] wlp3s0: authentication with <MAC address> timed out
[11162.934256] wlp3s0: authenticate with <MAC address>
[11162.946890] wlp3s0: send auth to <MAC address> (try 1/3)
[11162.995549] wlp3s0: send auth to <MAC address> (try 2/3)
[11163.040004] wlp3s0: send auth to <MAC address> (try 3/3)
[11163.089392] wlp3s0: authentication with <MAC address> timed out
[11175.229309] wlp3s0: authenticate with <MAC address>
[11175.241937] wlp3s0: send auth to <MAC address> (try 1/3)
[11175.286342] wlp3s0: send auth to <MAC address> (try 2/3)
[11175.306338] wlp3s0: send auth to <MAC address> (try 3/3)
[11175.347128] wlp3s0: authentication with <MAC address> timed out
[11181.965665] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[11337.266472] r8169 0000:02:00.0 enp2s0: link down
[11338.902565] r8169 0000:02:00.0 enp2s0: link up

########## wireless info END ############
```

---

### Post by gamerwael on 2019-05-29
[http://paste.ubuntu.com/p/PYhg9bFDFk/](http://paste.ubuntu.com/p/PYhg9bFDFk/)

---

### Post by praseodym on 2019-05-29
It loads a lot of other drivers:
```

sudo modprobe -rfv ath10k_pci b43 ath9k rt2800pci
sudo modprobe -v rt2800pci
```

---

### Post by gamerwael on 2019-06-04
Thanks for the reply.

The first command gives me:
rmmod ath9k
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211


And the second one gives me:
insmod /lib/modules/4.15.0-50-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.15.0-50-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko nohwcrypt=1 

Let me check and i'll let you know what happens.

---

### Post by gamerwael on 2019-06-04
Still not working. I click on my network after disconnecting from ethernet, it tries to connect for a few seconds..but then my network goes back to the list of available networks.

---

### Post by jeremy31 on 2019-06-04
Try disabling wifi power management
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot

---

### Post by gamerwael on 2019-06-09
I already have power management disabled. But i still ran your code.....no improvements.

---

### Post by plasmex on 2019-06-09
Have you tried the steps here?
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by gamerwael on 2019-06-10
My card's company isnt listed there:
 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

---

### Post by gamerwael on 2019-06-10
Wait...Found it...Checking

---

### Post by gamerwael on 2019-06-10
The instructions for my wifi card are unclear...
Im following this: [https://davidcortijo.wordpress.com/2012/05/07/ubuntu-12-04-how-to-solve-the-wifi-interface-using-ralink-rt3090-card/](https://davidcortijo.wordpress.com/2012/05/07/ubuntu-12-04-how-to-solve-the-wifi-interface-using-ralink-rt3090-card/)


[LIST=1]
[*]Check the wireless card status (*sudo iwlist scan*). You can see on the bottom the printed information on the terminal. For the sake of this tutorial, you must see any WIFI network. If you are not able to see any, maybe you should try another fix, out from this page ([here]("http://ubuntuforums.org/showthread.php?t=1849602") &#8211; post #71).
[*]Disable wireless energy management: *sudo iwconfig wlan0 power off*. You can also remain it disable after reboot as it is explained [here]("https://davidcortijo.wordpress.com/2012/01/23/ubuntu-11-10-avoid-wireless-network-energy-management/").
[*]From this step we will be able to see the different WIFI networks that we have around, We can try to connect through the upper toolbar, using the wireless network manager. The manager will ask the password, but the connection will not succeed.
[*]Using the same energy manager, we must click on the &#8220;Disconnect&#8221; menu option, and just followed connect again, and retry the connection with the WIFI network.
[/LIST]
[FONT=inherit]
What does the 4th step mean...energy manager?
And i dont understand anything in the [edit][/FONT]

---

### Post by him610 on 2019-06-10
gamerwael,
> What does the 4th step mean...energy manager?
Reread step 2.  'Disable wireless energy management....'
Substitute power for energy - you will figure what it means.

---

### Post by gamerwael on 2019-06-11
Still no help :(

---

### Post by praseodym on 2019-06-11
Why are there entries in the "interfaces" file? Back to normal via
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot

---

### Post by gamerwael on 2019-06-13
Done.. Im turning off now.. Ill get back tomorrow.

---

### Post by gamerwael on 2019-06-16
Still the same...

---

