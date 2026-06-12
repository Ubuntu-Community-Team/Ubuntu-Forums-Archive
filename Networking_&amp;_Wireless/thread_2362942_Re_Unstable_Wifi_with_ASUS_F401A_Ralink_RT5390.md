---
title: "Re: Unstable Wifi with ASUS F401A/ Ralink RT5390"
date: 2017-06-04
forum: Networking &amp; Wireless
---

### Post by dcingram on 2017-06-04
Help. I have just installed UBUNTU as my OS overwriting all others (I was sick of Windows) only to find that the WIFI is really bad with my laptop / WIFI card set up. The WIFI was fine on Windows. I have searched the forums here and have tried dabbling in adding some code here and there - not really knowing what I was doing - but have had no success. Any help would be greatly appreciated but would be being offered to someone with the computing skills of a flowering plant. Here is what the terminal said when I proudly typed in lshw -C network:

```
 *-network               
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 84:4b:f5:70:5e:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.8.0-53-generic firmware=0.34 ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f7d00000-f7d0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: enp3s0f2
       version: 0a
       serial: 50:46:5d:4b:7e:99
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:27 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

This is the wireless report

```
########## wireless info START ##########


Report from: 04 Jun 2017 21:47 AEST +1000


Booted last: 04 Jun 2017 00:00 AEST +1000


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.8.0-53-generic #56~16.04.1-Ubuntu SMP Tue May 16 01:18:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe [105b:e054]
	Kernel driver in use: rt2800pci


03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:14f7]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5165 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              57344  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              761856  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              581632  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    16384  1 asus_wmi
video                  40960  2 asus_wmi,i915


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f2  Link encap:Ethernet  HWaddr <MAC 'enp3s0f2' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:36056 (36.0 KB)  TX bytes:36056 (36.0 KB)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::510b:9aad:ceba:699e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2663 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1643562 (1.6 MB)  TX bytes:414026 (414.0 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0f2  no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:"TP-LINK_49F0"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'TP-LINK_49F0' [AC1]>   
          Bit Rate=120 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:69   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       730     1  0 21:43 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.8.0-53-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TP-LINK_49F0
GENERAL.CON-UUID:                       0014b0e4-9b3c-4d0d-a58e-3a5c16667050
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     121 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0014b0e4-9b3c-4d0d-a58e-3a5c16667050 | TP-LINK_49F0
IP4.ADDRESS[1]:                         192.168.0.102/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
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
DHCP4.OPTION[10]:                       expiry = 1496583809
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.102
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
IP6.ADDRESS[1]:                         fe80::510b:9aad:ceba:699e/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
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


SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
TP-LINK_49F0  <MAC 'TP-LINK_49F0' [AC1]>  Infra  9     2452 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2      yes     * 
NETGEAR22     <MAC 'NETGEAR22' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2      no        


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


[[/etc/NetworkManager/system-connections/Telstra48BABD]] (600 root)
[connection] id=Telstra48BABD | type=wifi | permissions=user:dcingram:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Telstra48BABD
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_49F0]] (600 root)
[connection] id=TP-LINK_49F0 | type=wifi | permissions=user:dcingram:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=TP-LINK_49F0
[ipv4] method=auto
[ipv6] method=auto

continued...

##### iw reg get ########################


Region: Australia/Brisbane (based on set time zone)


country AU: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
	(5490 - 5710 @ 160), (N/A, 24), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp3s0f2  no frequency information.


wlp2s0    13 channels in total; available frequencies :
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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0f2  Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.452 GHz (Channel 9)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_49F0' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_49F0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d68f5347f5
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TelstraD323F3' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"TelstraD323F3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d68d9dd185
                    Extra: Last beacon: 3880ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'NETGEAR22' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d68cf7a8b7
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     4D2CAAE95D28B3DF4F72A52
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     DBE617B0243C0FEB62786D4
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     D84965563CC7530CFFD2269
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     02CA9DA77FC2C7FCCC58176
depends:        rt2x00lib
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     CF930122B7900096FC259FA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    2.312461] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f01)
[   10.491521] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   10.495653] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   11.815230] rt2800pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   23.858948] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   23.858994] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   24.455956] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   24.611232] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   24.615933] IPv6: ADDRCONF(NETDEV_UP): enp3s0f2: link is not ready
[   24.729653] r8169 0000:03:00.2 enp3s0f2: link down
[   24.729711] IPv6: ADDRCONF(NETDEV_UP): enp3s0f2: link is not ready
[   25.410281] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   26.514885] wlp2s0: authenticate with <MAC 'TP-LINK_49F0' [AC1]>
[   26.527705] wlp2s0: send auth to <MAC 'TP-LINK_49F0' [AC1]> (try 1/3)
[   26.529614] wlp2s0: authenticated
[   26.530708] wlp2s0: associate with <MAC 'TP-LINK_49F0' [AC1]> (try 1/3)
[   26.534347] wlp2s0: RX AssocResp from <MAC 'TP-LINK_49F0' [AC1]> (capab=0x431 status=0 aid=1)
[   26.534493] wlp2s0: associated
[   26.534532] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready


########## wireless info END ############
```

---

### Post by wildmanne39 on 2017-06-04
Hello and welcome to the forum, we are going to set a driver parameter that is almost always needed with the driver you are using, please do:
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Now go into network manager and set your settings to match the screenshots.
Then do:
```
sudo systemctl restart NetworkManager.service
```
It will be best if you set your channel in your router to a fixed channel 1, 6, or 11 is best most of the time.

---

### Post by dcingram on 2017-06-05
Hi wildmanne39,

Thank you very much for your help. I have applied the changes that you suggested. So far, touch wood, the wifi connection hasn't dropped like it was constantly doing previously. But I will continue to monitor this and get back, as it is early days. On speed tests, the internet speed still registers as slow at 7mpbs down 5 mpbs up (the up speed is about the same as I was getting on windows, but the download speed is about one third). I don't know if I should expect more than this, or there is something else to do to address the speed situation?

Thanks again

---

### Post by wildmanne39 on 2017-06-05
I do not know how much signal strength and link quality has improved since the changes, but if you made all the changes then the only thing that I know could help is to have a signal extender, the stronger the signal the faster the connection.  Not much more can be done then what we have already done to stop the disconnects, but I am pretty sure the changes you made did that.

---

### Post by liquid.linux on 2018-05-13
Hello.

I have a similar issue with an Asus X54C.

I followed the steps on this guide, I'll be testing and report of any issues. 

Thank for the help.

---

### Post by trf000 on 2018-09-25
I have the same issue, but after rebooting it resets and I'm back to slow speeds

---

