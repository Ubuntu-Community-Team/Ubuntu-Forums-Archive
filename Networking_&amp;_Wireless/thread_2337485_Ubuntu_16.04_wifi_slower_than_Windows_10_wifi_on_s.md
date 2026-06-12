---
title: "Ubuntu 16.04 wifi slower than Windows 10 wifi on same hardware"
date: 2016-09-18
forum: Networking &amp; Wireless
---

### Post by flame2057 on 2016-09-18
I recently switched to Ubuntu 16.04 from Windows 10. I found that Ubuntu has significantly slower wifi that Windows 10, and when I ran a speed test from [http://www.speedtest.net/](http://www.speedtest.net/) on both OSes my theories were proven true; Ubuntu running on my desktop computer has less than a tenth the download speed as Windows 10 on the same computer. I've tried almost everything I could find on google relating to the issue, including the sticky threads, but I've had no luck.

Here is my wireless-info.txt:

```


########## wireless info START ##########


Report from: 18 Sep 2016 19:51 EDT -0400


Booted last: 18 Sep 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:f051]
    Kernel driver in use: rt2800pci


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2ada]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


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


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fd00:fc:8d08:8332:b812:d638:245f:a0a4/64 Scope:Global
          inet6 addr: fd00:fc:8d08:8332:6b40:55cc:49be:2201/64 Scope:Global
          inet6 addr: fe80::839a:f2d3:f1f1:8c27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4326882 (4.3 MB)  TX bytes:738416 (738.4 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0    no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:"GreenMagnolia"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'GreenMagnolia' [AC1]>   
          Bit Rate=27 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:110  Invalid misc:16   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
search hitronhub.home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       895     1  0 19:44 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     GreenMagnolia
GENERAL.CON-UUID:                       0c82d056-f206-4c4e-a60b-94dc290d3198
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0c82d056-f206-4c4e-a60b-94dc290d3198 | GreenMagnolia
IP4.ADDRESS[1]:                         192.168.0.18/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          hitronhub.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = owen-p7-1256c
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1474847065
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.18
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hitronhub.home
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 604800
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fd00:fc:8d08:8332:b812:d638:245f:a0a4/64
IP6.ADDRESS[2]:                         fd00:fc:8d08:8332:6b40:55cc:49be:2201/64
IP6.ADDRESS[3]:                         fe80::839a:f2d3:f1f1:8c27/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fc00::/7, nh = fe80::2fc:8dff:fe08:8332, mt = 600


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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/enp4s0
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


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
RogersB9358-guest  <MAC 'RogersB9358-guest' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --         no        
--                 <MAC '--' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
dlink-0B00         <MAC 'dlink-0B00' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
58 Moore Control4  <MAC '58 Moore Control4' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1       no        
GreenMagnolia      <MAC 'GreenMagnolia' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  yes     * 
GreenMagnolia      <MAC 'GreenMagnolia' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
Dartmouth          <MAC 'Dartmouth' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
--                 <MAC '--' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/GreenMagnolia]] (600 root)
[connection] id=GreenMagnolia | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=GreenMagnolia
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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


enp4s0    no frequency information.


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'GreenMagnolia' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"GreenMagnolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007b6b33023
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'GreenMagnolia' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"GreenMagnolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007be04e180
                    Extra: Last beacon: 2712ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'dlink-0B00' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"dlink-0B00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007bd10e84f
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'RogersB9358-guest' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"RogersB9358-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007bdfead7d
                    Extra: Last beacon: 3092ms ago
          Cell 05 - Address: <MAC '58 Moore Control4' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"58 Moore Control4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007cfbadbef
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/blacklist-rtl8192cu.conf]
blacklist rtl8192cu


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


[  116.405807] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  116.405841] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[  116.569500] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[  116.695894] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  116.698111] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[  116.849222] r8169 0000:04:00.0 enp4s0: link down
[  116.849277] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[  117.161383] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  118.275478] wlp3s0: authenticate with <MAC 'GreenMagnolia' [AC1]>
[  118.284073] wlp3s0: send auth to <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[  118.285526] wlp3s0: authenticated
[  118.287152] wlp3s0: associate with <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[  118.293350] wlp3s0: RX AssocResp from <MAC 'GreenMagnolia' [AC1]> (capab=0x411 status=0 aid=3)
[  118.293437] wlp3s0: associated
[  118.293468] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  309.583777] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 2 times)
[  415.042822] wlp3s0: authenticate with <MAC 'GreenMagnolia' [AC2]>
[  415.050879] wlp3s0: send auth to <MAC 'GreenMagnolia' [AC2]> (try 1/3)
[  415.052652] wlp3s0: authenticated
[  415.054370] wlp3s0: associate with <MAC 'GreenMagnolia' [AC2]> (try 1/3)
[  415.059115] wlp3s0: RX AssocResp from <MAC 'GreenMagnolia' [AC2]> (capab=0x431 status=0 aid=4)
[  415.059214] wlp3s0: associated
[  534.006573] wlp3s0: authenticate with <MAC 'GreenMagnolia' [AC1]>
[  534.014081] wlp3s0: send auth to <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[  534.023314] wlp3s0: authenticated
[  534.025681] wlp3s0: associate with <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[  534.029487] wlp3s0: RX AssocResp from <MAC 'GreenMagnolia' [AC1]> (capab=0x411 status=0 aid=3)
[  534.029657] wlp3s0: associated
[  573.592167] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 2 times)


########## wireless info END ############



```

---

### Post by Hadaka on 2016-09-18
Hi,from your wireless report I am seeing 3 or 4 possibilities for your slow
wifi.
1). Your wifi named GreenMagnolia has the parameter of TKIP please access your router
configuration and change to AES.
2). The dmesg report shows.."Queue 2 failed to flush " Please open a terminal..ctrl/alt/t and do..
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800pci.conf
```
3). You have no country code set and it is using 00 default, this does and can cause slowness..please copy and paste
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
4). The Rawlink 5390 wifi card has 2 physical connections for the antenna..windows can change via software
Ubuntu does not. If after doing the above changes you have no improvement, you "may" need to move the antenna connection
to the 5ghz terminal.
Please let us know your findings.
Thanks

---

### Post by flame2057 on 2016-09-19
I tried all that. Didn't work, Ubuntu still has significantly slower wifi speeds than Windows 10 on the same machine. I even reinstalled all of Ubuntu, but the issue persisted. So I decided to try Linux Mint, another OS I've heard good things about, in hopes it wouldn't have the same issue. It does. Hours of updating Linux Mint and still nothing. It could be all of Linux or something for me, I have no clue.


I went into Windows and found out I am using a 802.11n Wireless Lan Card. I followed a stack overflow post to install drivers for it in Linux Mint, but that didn't work either (what a surprise).


Anyway, here is my wireless-info.txt in mint, if it's worth anything. I appreciate your help so far, though. :)


```

########## wireless info START ##########


Report from: 19 Sep 2016 20:53 EDT -0400


Booted last: 19 Sep 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    LinuxMint
Description:    Linux Mint 18 Sarah
Release:    18
Codename:    sarah


##### kernel ############################


Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:f051]
    Kernel driver in use: rt2800pci


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2ada]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


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


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fd00:fc:8d08:8332:394d:a4eb:4624:6420/64 Scope:Global
          inet6 addr: fd00:fc:8d08:8332:<IP6 'wlp3s0' [IF2]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlp3s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23502983 (23.5 MB)  TX bytes:2738366 (2.7 MB)


##### iwconfig ##########################


enp4s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:"GreenMagnolia"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'GreenMagnolia' [AC1]>   
          Bit Rate=27 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3340  Invalid misc:4766   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
search hitronhub.home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       856     1  0 20:43 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto GreenMagnolia
GENERAL.CON-UUID:                       57930ed1-055b-40d5-b71f-980473ee2c1d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     28 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   57930ed1-055b-40d5-b71f-980473ee2c1d | Auto GreenMagnolia
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   628bbb9d-b68c-43b5-8df3-5082bd24ccb6 | Auto 58 Moore Control4
IP4.ADDRESS[1]:                         192.168.0.18/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          hitronhub.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = owen-p7-1256c
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1474937004
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.18
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hitronhub.home
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 604800
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fd00:fc:8d08:8332:<IP6 'wlp3s0' [IF2]>/64
IP6.ADDRESS[2]:                         fd00:fc:8d08:8332:394d:a4eb:4624:6420/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlp3s0' [IF2]>/64
IP6.GATEWAY:                            


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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/enp4s0
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


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  *
RogersB9358-guest  <MAC 'RogersB9358-guest' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  --         no        
58 Moore Control4  <MAC '58 Moore Control4' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1       no        
dlink-0B00         <MAC 'dlink-0B00' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
GreenMagnolia      <MAC 'GreenMagnolia' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
--                 <MAC '' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
GreenMagnolia      <MAC 'GreenMagnolia' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  yes     *
--                 <MAC '' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
Dartmouth          <MAC 'Dartmouth' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
Princess-2G        <MAC 'Princess-2G' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  9       &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/Auto 58 Moore Control4]] (600 root)
[connection] id=Auto 58 Moore Control4 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=58 Moore Control4
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto GreenMagnolia]] (600 root)
[connection] id=Auto GreenMagnolia | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=GreenMagnolia
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


enp4s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'GreenMagnolia' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"GreenMagnolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cb0920976
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'dlink-0B00' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"dlink-0B00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cbd745638
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cb76f3180
                    Extra: Last beacon: 9764ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'GreenMagnolia' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"GreenMagnolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cb7d5f70f
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'RogersB9358-guest' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"RogersB9358-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cb7d5a1d9
                    Extra: Last beacon: 76ms ago
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cc2a3f180
                    Extra: Last beacon: 2112ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '58 Moore Control4' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"58 Moore Control4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cc99095ab
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Dartmouth' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Dartmouth"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cc244a180
                    Extra: Last beacon: 8312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Princess-2G' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Princess-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cbc07c68f
                    Extra: Last beacon: 1144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions


[rt2800lib]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions


[rt2x00pci]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions


[rt2x00mmio]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions


[rt2x00lib]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions


[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions
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


##### udev rules ########################


##### dmesg #############################


[   24.038280] rt2800pci 0000:03:00.0 wlp3s0: renamed from wlan0
[   33.120912] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   33.120946] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   33.192980] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   33.318353] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   33.321683] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   33.435643] r8169 0000:04:00.0 enp4s0: link down
[   33.435698] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   33.754014] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   34.837745] wlp3s0: authenticate with <MAC 'GreenMagnolia' [AC1]>
[   34.845548] wlp3s0: send auth to <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[   34.849602] wlp3s0: authenticated
[   34.852789] wlp3s0: associate with <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[   34.856512] wlp3s0: RX AssocResp from <MAC 'GreenMagnolia' [AC1]> (capab=0x411 status=0 aid=3)
[   34.856594] wlp3s0: associated
[   34.856630] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   37.587359] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 26 times)
[  569.958969] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 1 failed to flush
[  570.118887] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 2 times)
[  571.014447] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 1 failed to flush
[  571.174362] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 8 times)
[  574.876487] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 1 failed to flush
[  575.036416] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush


########## wireless info END ############



```

---

### Post by Hadaka on 2016-09-20
Hi, you have the 'EXACT' problems with LinuxMint..and will continue to do so untill you make corrections.
windows is obviously runing the 5GHz connection. Linux is using the 2.4GHz connection.

```
GreenMagnolia <MAC 'GreenMagnolia' [AC1]>Infra 1  [COLOR=#ff0000]2412 MHZ[/COLOR]  54 Mbit/s 42 WPA1 WPA2  yes *
```
Power Management needs to be OFF **[COLOR=#ff0000]<--[/COLOR]**
```
wlp3s0    IEEE 802.11bgn  ESSID:"GreenMagnolia"  
          Mode:Managed  Frequency:[COLOR=#ff0000]2.412 GHz[/COLOR]  Access Point: <MAC 'GreenMagnolia' [AC1]>   
          Bit Rate=27 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:[COLOR=#ff0000]on[/COLOR]
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3340  Invalid misc:4766   Missed beacon:0
```
AES only no TKIP **[COLOR=#ff0000]<--[/COLOR]**
```
wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'GreenMagnolia' [AC1]>
                    Channel:1
                    Frequency:[COLOR=#ff0000]2.412 GHz[/COLOR] (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"GreenMagnolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cb0920976
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : [COLOR=#ff0000]TKIP[/COLOR] CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : [COLOR=#ff0000]TKIP[/COLOR] CCMP
                        Authentication Suites (1) : PSK
```

##### iw reg get ########################
Region: America/New_York (based on set time zone)
country [COLOR=#ff0000]00[/COLOR]: DFS-UNSET
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```


##### dmesg #############################
[   34.837745] wlp3s0: authenticate with <MAC 'GreenMagnolia' [AC1]>
[   34.845548] wlp3s0: send auth to <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[   34.849602] wlp3s0: authenticated
[   34.852789] wlp3s0: associate with <MAC 'GreenMagnolia' [AC1]> (try 1/3)
[   37.587359] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 26 times)
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800pci.conf
```

---

### Post by filipkloucek on 2017-07-02
Hi, i have similar problem with my ThinkPad T470. When i boot notebook in win10, wifi is fast and i have avg 50-60 mbit/sec. But when i boot notebbok with Ubuntu 16.04, my speed is avg 10-15mbit/sec. My internet speed from my provider is 60mbit/sec.

Thanx for help.

My wireless test is [http://paste.ubuntu.com/25005122/](http://paste.ubuntu.com/25005122/)

```

[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
518
519
520
521
522
523
524
525
526
527
528
529
530
531
532
533
534
535
536
537
538
539
540
541
542
543
544
545
546
547
548
549
550
551
552
553
554
555
556
557
558
559
560
561
562
563
564
565
566
567
568
569
570
571
572
573
574
575
576
577
578
579
580
581
582
583
584
585
586
587
588
589
590
591
592
593
594
595
596
597
598
599
600
601
602
603
604
605
606
607
608
609
610
611
612
613
614
615
616
617
618
619
620
621
622
623
624
625
626
627
628
629
630
631
632
633
634
635
636
637
638
639
640
641
642
643
644
645
646
647
648
649
650
651
652
653
654
655
656
657
658
659
660
661
662
663
664
665
666
667
668
669
670
671
672
673
674
675
676
677
678
679
680
681
682
683
684
685
686
687
688
689
690
691
692
693
694
695
696
697
698
699
700
701
702
703
704
705
706
707
708
709
710
711
712
713
714
715
716
717
718
719
720
721
722
723
724
725
726
727
728
729
730
731
732
733
734
735
736
737
738
739
740
741
742
743
744
745
746
747
748
749
750
751
752
753
754
755
756
757
758
759
760
761
762
763
764
765
766
767
768
769
770
771
772
773
774
775
776
777
778
779
780
781
782
783
784
785
786
787
788
789
790
791
792
793
794
795
796
797
798
799
800
801
802
803
804
805
806
807
808
809
810
811
812
813
814
815
816
817
818
819
820
821
822
823
824
825
826
827
828
829
830
831
832
833
834
835
836
837
838
839
840
841
842
843
844
845
846
847
848
849
850
851
852
853
854
855
856
857
858
859
860
861
862
863
864
865
866
867
868
869
870
871
872
873
874
875
876
877
878
879
880
881
882
883
884
885
886
887
888
889
890
891[/TD]
[TD="class: code"][COLOR=#000000]########## wireless info START ##########

Report from: 02 Jul 2017 19:02 CEST +0200

Booted last: 02 Jul 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-58-generic #63~16.04.1-Ubuntu SMP Mon Jun 26 18:08:51 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, rootflags=subvol=@, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-LM [8086:15d7] (rev 21)
    Subsystem: Lenovo Ethernet Connection (4) I219-LM [17aa:2245]
    Kernel driver in use: e1000e

04:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:0010]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 0bda:0316 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 138a:0097 Validity Sensors, Inc. 
Bus 001 Device 006: ID 5986:111c Acer, Inc 
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 004: ID 062a:410c Creative Labs 
Bus 001 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                360448  0
mac80211              761856  1 iwlmvm
iwlwifi               229376  1 iwlmvm
cfg80211              581632  3 iwlmvm,iwlwifi,mac80211
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

br-0f898c00ba2e Link encap:Ethernet  HWaddr <MAC 'br-0f898c00ba2e' [IF1]>  
          inet addr:172.18.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br-622f29e67ec1 Link encap:Ethernet  HWaddr <MAC 'br-622f29e67ec1' [IF2]>  
          inet addr:172.19.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br-e95162042459 Link encap:Ethernet  HWaddr <MAC 'br-e95162042459' [IF3]>  
          inet addr:172.20.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF4]>  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF5]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:ec200000-ec220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:67125 (67.1 KB)  TX bytes:67125 (67.1 KB)

wlp4s0    Link encap:Ethernet  HWaddr <MAC 'wlp4s0' [IF6]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25151803 (25.1 MB)  TX bytes:8196910 (8.1 MB)

##### iwconfig ##########################

br-0f898c00ba2e  no wireless extensions.

enp0s31f6  no wireless extensions.

br-e95162042459  no wireless extensions.

br-622f29e67ec1  no wireless extensions.

lo        no wireless extensions.

docker0   no wireless extensions.

wlp4s0    IEEE 802.11  ESSID:"TF"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'TF' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:383   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-0f898c00ba2e
172.19.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-622f29e67ec1
172.20.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-e95162042459
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       851     1  0 18:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         br-0f898c00ba2e
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'br-0f898c00ba2e' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/br-0f898c00ba2e
GENERAL.IP-IFACE:                       br-0f898c00ba2e
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     br-0f898c00ba2e
GENERAL.CON-UUID:                       28a3b580-103c-4e9e-b6ab-023d34597ea1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{10}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   28a3b580-103c-4e9e-b6ab-023d34597ea1 | br-0f898c00ba2e
IP4.ADDRESS[1]:                         172.18.0.1/16
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         br-622f29e67ec1
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'br-622f29e67ec1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/br-622f29e67ec1
GENERAL.IP-IFACE:                       br-622f29e67ec1
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     br-622f29e67ec1
GENERAL.CON-UUID:                       b56f66e8-e151-4294-a184-8444fa399a2e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{8}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b56f66e8-e151-4294-a184-8444fa399a2e | br-622f29e67ec1
IP4.ADDRESS[1]:                         172.19.0.1/16
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         br-e95162042459
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'br-e95162042459' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/br-e95162042459
GENERAL.IP-IFACE:                       br-e95162042459
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     br-e95162042459
GENERAL.CON-UUID:                       c23ec711-4e9f-4b5e-a3fa-6b89da5e09e3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c23ec711-4e9f-4b5e-a3fa-6b89da5e09e3 | br-e95162042459
IP4.ADDRESS[1]:                         172.20.0.1/16
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF4]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       1adf0e2f-b153-4b0c-a1f8-bea2f4f87113
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1adf0e2f-b153-4b0c-a1f8-bea2f4f87113 | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.8.0-58-generic
GENERAL.FIRMWARE-VERSION:               22.391740.0
GENERAL.HWADDR:                         <MAC 'wlp4s0' [IF6]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:04:00.0/net/wlp4s0
GENERAL.IP-IFACE:                       wlp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TF
GENERAL.CON-UUID:                       1a80a3d7-0cc1-4b67-a4a5-5ba34704e6c5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1a80a3d7-0cc1-4b67-a4a5-5ba34704e6c5 | TF
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             93.190.56.17
IP4.DNS[2]:                             93.190.56.41
IP4.DNS[3]:                             8.8.8.8
IP4.DNS[4]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1499021638
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.7
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 93.190.56.17 93.190.56.41 8.8.8.8 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (4) I219-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF5]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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

SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TF            <MAC 'TF' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
Wifi_BART     <MAC 'Wifi_BART' [AC5]>  Infra  10    2457 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
VomoWIFI      <MAC 'VomoWIFI' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
barbora_wifi  <MAC 'barbora_wifi' [AC4]>  Infra  10    2457 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
FP_AC_5Ghz    <MAC 'FP_AC_5Ghz' [AC6]>  Infra  40    5200 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
TLAPNET       <MAC 'TLAPNET' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2       no        

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

[[/etc/NetworkManager/system-connections/srrvz]] (600 root)
[connection] id=srrvz | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF6]> | mac-address-blacklist= | ssid=srrvz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Digital_Staff]] (600 root)
[connection] id=Digital_Staff | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF6]> | mac-address-blacklist= | ssid=Digital_Staff
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPCDCCE664]] (600 root)
[connection] id=UPCDCCE664 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF6]> | mac-address-blacklist= | ssid=UPCDCCE664
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CZFree.Net.anenska_spravedlnost]] (600 root)
[connection] id=CZFree.Net.anenska_spravedlnost | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF6]> | mac-address-blacklist= | ssid=CZFree.Net.anenska_spravedlnost
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF6]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TF]] (600 root)
[connection] id=TF | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF6]> | mac-address-blacklist= | ssid=TF
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Prague (based on set time zone)

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

br-0f898c00ba2e  no frequency information.

enp0s31f6  no frequency information.

br-e95162042459  no frequency information.

br-622f29e67ec1  no frequency information.

lo        no frequency information.

docker0   no frequency information.

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
          Current Frequency:2.417 GHz (Channel 2)

##### iwlist scan #######################

br-0f898c00ba2e  Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

br-e95162042459  Interface doesn't support scanning.

br-622f29e67ec1  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

docker0   Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:5.2 GHz (Channel 40)

wlp4s0    Scan completed :
          Cell 01 - Address: <MAC 'TF' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"TF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000052495eb907
                    Extra: Last beacon: 4612ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Lochman' [AC2]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Lochman"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000247eb63a97e
                    Extra: Last beacon: 4516ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TLAPNET' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"TLAPNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b1ef963a4
                    Extra: Last beacon: 4528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'barbora_wifi' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"barbora_wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000039a30490d
                    Extra: Last beacon: 3004ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Wifi_BART' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Wifi_BART"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb88639a54
                    Extra: Last beacon: 3008ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FP_AC_5Ghz' [AC6]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"FP_AC_5Ghz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002041c6635a
                    Extra: Last beacon: 1324ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     8CB024DCE8CBAD06752D324
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-58-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.8.0-58-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-58-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-IWL6000G2B_UCODE_API_MAX.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-24.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-24.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-24.ucode
firmware:       iwlwifi-8000C--24.ucode
firmware:       iwlwifi-9260-th-a0-lc-a0--24.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--24.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--24.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--24.ucode
srcversion:     E7651FD3D9AF45F96CD8B2E
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-58-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
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
filename:       /lib/modules/4.8.0-58-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-58-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 1
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

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

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/r8168-dkms.conf]
alias    pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*    r8168
alias    pci:v000010ECd00008168sv*sd*bc*sc*i*            r8168

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    6.422086] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    6.563704] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.671918] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
[    7.346869] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[    7.349152] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    7.534379] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[    7.537464] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[    7.901852] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[   12.128695] wlp4s0: authenticate with <MAC 'TF' [AC1]>
[   12.137816] wlp4s0: send auth to <MAC 'TF' [AC1]> (try 1/3)
[   12.143513] wlp4s0: authenticated
[   12.147645] wlp4s0: associate with <MAC 'TF' [AC1]> (try 1/3)
[   12.155288] wlp4s0: RX AssocResp from <MAC 'TF' [AC1]> (capab=0x411 status=0 aid=4)
[   12.159877] wlp4s0: associated
[   12.159897] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready

########## wireless info END ############[/COLOR][/TD]
[/TR]
[/TABLE]

```

---

### Post by johndough2 on 2017-07-04
Hi

I think you missed the point made earlier.

There are 2 Green Magnolia WiFi networks, one goes at 54Mbs and the other at 18mbs
ESSID:"GreenMagnolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
ESSID:"GreenMagnolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s

So if Ubuntu will only connect to 1 then it should be the 1st one, this will 54 of a possible 72 Mb/s, rather than the other option of 18 of 72Mb/s.

---

### Post by chili555 on 2017-07-04
I own and have used, over the years, three Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

I also suggest that you install the latest firmware package:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot and let us hear your report.

---

