---
title: "acer aspire 6550g wireless not working"
date: 2015-06-24
forum: Networking &amp; Wireless
---

### Post by michal-trojanovic on 2015-06-24
Hi, yesterday i have installed ubuntu 15.04 and my wifi is not working. I can see networks but when i try to connect it is just loading and never connects.

Here is output of a script i have found on the forums.

Thank you for your help.

```


########## wireless info START ##########


Report from: 24 Jun 2015 08:53 CEST +0200


Booted last: 24 Jun 2015 08:46 CEST +0200


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:31:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0605]
    Kernel driver in use: tg3


03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:d20c Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


b43                   421888  0 
bcma                   57344  1 b43
ssb                    65536  1 b43
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              724992  2 b43,ath9k
cfg80211              540672  5 b43,ath,ath9k_common,ath9k,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226a:8aff:fe4f:3c81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:982299 (982.2 KB)  TX bytes:283335 (283.3 KB)
          Interrupt:11 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::ceaf:78ff:fe7e:2bc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144756 (144.7 KB)  TX bytes:46661 (46.6 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"NOaCO"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'NOaCO' [AC6]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:16  Invalid misc:2   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetLink BCM57785 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       88cc2f06-982c-45c7-aef5-dda5fa0b60ff
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   88cc2f06-982c-45c7-aef5-dda5fa0b60ff | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.17/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             195.168.1.2
IP4.DNS[2]:                             195.168.1.4
IP4.DNS[3]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1435214950
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       ip_address = 192.168.1.17
DHCP4.OPTION[15]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       routers = 192.168.1.1
DHCP4.OPTION[18]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[19]:                       domain_name_servers = 195.168.1.2 195.168.1.4 192.168.1.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       requested_host_name = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::226a:8aff:fe4f:3c81/64, gw = ::


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9287 Wireless Network Adapter (PCI-Express) (T77H167.00)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 3.19.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          70 (connecting (getting IP configuration))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:06.0/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     NOaCO
GENERAL.CON-UUID:                       6e75b7b3-d2f4-44f1-8114-d7d8064a7abe
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6e75b7b3-d2f4-44f1-8114-d7d8064a7abe | NOaCO
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes


SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
4TV          <MAC '4TV' [AC3]>  Infra  7     2442 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
misis        <MAC 'misis' [AC2]>  Infra  4     2427 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
mivejama     <MAC 'mivejama' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
Blaguss      <MAC 'Blaguss' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
apli         <MAC 'apli' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
NOaCO-guest  <MAC 'NOaCO-guest' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  --         no        
NOaCO        <MAC 'NOaCO' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Blaguss      <MAC 'Blaguss' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/meress]] (600 root)
[connection] id=meress | type=wifi
[wifi] ssid=meress | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NOaCO]] (600 root)
[connection] id=NOaCO | type=wifi
[wifi] ssid=NOaCO | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Bratislava (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR


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


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NOaCO-guest' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"NOaCO-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000071124803f
                    Extra: Last beacon: 824ms ago
          Cell 02 - Address: <MAC 'misis' [AC2]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"misis"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009f1c641d102
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '4TV' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"4TV"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000f61ceba650e
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Blaguss' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Blaguss"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000069413ac75
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'mivejama' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"mivejama"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006024204add5
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'NOaCO' [AC6]>
                    Channel:1
                    Frequenlo        Interface doesn't support scanning.


cy:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"NOaCO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000071124719b
                    Extra: Last beacon: 824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Blaguss' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Blaguss"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003147833808
                    Extra: Last beacon: 10972ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[b43]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     25A88E97301A6821E663814
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
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


[bcma]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512


[ssb]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     CBEA66963CF96C070BE11E6
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     88CC41451370601B0D885E4
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


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


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
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


[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS


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
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  377.664398] wlan0: RX AssocResp from <MAC 'NOaCO' [AC6]> (capab=0x411 status=0 aid=2)
[  377.664499] wlan0: associated
[  383.269053] wlan0: authenticate with <MAC 'NOaCO' [AC6]>
[  383.292940] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 1/3)
[  383.804238] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 2/3)
[  384.300457] wlan0: authenticated
[  384.340094] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 1/3)
[  385.792092] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 2/3)
[  386.344554] wlan0: RX AssocResp from <MAC 'NOaCO' [AC6]> (capab=0x411 status=0 aid=2)
[  386.344687] wlan0: associated
[  392.260895] wlan0: authenticate with <MAC 'NOaCO' [AC6]>
[  392.285313] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 1/3)
[  392.804035] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 2/3)
[  393.292535] wlan0: authenticated
[  393.340063] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 1/3)
[  394.804060] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 2/3)
[  395.344493] wlan0: RX AssocResp from <MAC 'NOaCO' [AC6]> (capab=0x411 status=0 aid=2)
[  395.344591] wlan0: associated
[  405.424590] wlan0: deauthenticated from <MAC 'NOaCO' [AC6]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  406.401095] wlan0: authenticate with <MAC 'NOaCO' [AC6]>
[  406.425181] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 1/3)
[  407.432518] wlan0: authenticated
[  407.468087] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 1/3)
[  408.780096] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 2/3)
[  409.472473] wlan0: RX AssocResp from <MAC 'NOaCO' [AC6]> (capab=0x411 status=0 aid=2)
[  409.472570] wlan0: associated
[  419.552661] wlan0: deauthenticated from <MAC 'NOaCO' [AC6]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  420.541046] wlan0: authenticate with <MAC 'NOaCO' [AC6]>
[  420.565260] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 1/3)
[  421.572356] wlan0: authenticated
[  421.620260] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 1/3)
[  422.816091] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 2/3)
[  423.624662] wlan0: RX AssocResp from <MAC 'NOaCO' [AC6]> (capab=0x411 status=0 aid=2)
[  423.624774] wlan0: associated
[  433.704567] wlan0: deauthenticated from <MAC 'NOaCO' [AC6]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  434.697076] wlan0: authenticate with <MAC 'NOaCO' [AC6]>
[  434.721216] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 1/3)
[  435.728553] wlan0: authenticated
[  435.764300] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 1/3)
[  436.816099] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 2/3)
[  437.768628] wlan0: RX AssocResp from <MAC 'NOaCO' [AC6]> (capab=0x411 status=0 aid=2)
[  437.768726] wlan0: associated
[  443.268962] wlan0: authenticate with <MAC 'NOaCO' [AC6]>
[  443.293168] wlan0: send auth to <MAC 'NOaCO' [AC6]> (try 1/3)
[  444.904412] wlan0: authenticated
[  444.948096] wlan0: associate with <MAC 'NOaCO' [AC6]> (try 1/3)


########## wireless info END ############



```

---

