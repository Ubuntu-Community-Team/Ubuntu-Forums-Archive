---
title: "DNS_PROBE_FINISHED_NO_INTERNET occurs occasionally while using Google Chrome."
date: 2016-10-07
forum: Networking &amp; Wireless
---

### Post by natural2 on 2016-10-07
This started happens suddenly when I changed my OS to Ubuntu 16.04.

```


########## wireless info START ##########


Report from: 07 Oct 2016 22:01 CDT -0500


Booted last: 07 Oct 2016 00:00 CDT -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
	Subsystem: Acer Incorporated [ALI] AR8151 v1.0 Gigabit Ethernet [1025:040d]
	Kernel driver in use: atl1c


06:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Foxconn International, Inc. T77H047.31 802.11bgn Wireless Half-size Mini PCIe Card [AR9283] [105b:e01f]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  1 acer_wmi
video                  40960  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp6s0    Link encap:Ethernet  HWaddr <MAC 'wlp6s0' [IF2]>  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b01:f3f0:11f8:cedd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2610292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1449723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3293667237 (3.2 GB)  TX bytes:212966005 (212.9 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlp6s0    IEEE 802.11bgn  ESSID:"DDW365.51939A-2.4G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'DDW365.51939A-2.4G' [AC1]>   
          Bit Rate=117 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:155   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp6s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp6s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       729     1  0 Oct06 ?        00:00:37 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp6s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR928X Wireless Network Adapter (PCI-Express) (T77H047.31 802.11bgn Wireless Half-size Mini PCIe Card [AR9283])
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-38-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp6s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:06:00.0/net/wlp6s0
GENERAL.IP-IFACE:                       wlp6s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     DDW365.51939A-2.4G
GENERAL.CON-UUID:                       12f4225a-350b-43f1-bc4e-3cf92076bf3a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/17
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     117 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   12f4225a-350b-43f1-bc4e-3cf92076bf3a | DDW365.51939A-2.4G
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   c5bcfc8f-ff0d-4cd7-b93a-41990b589119 | DVW326.EC7642-2.4G
IP4.ADDRESS[1]:                         192.168.0.20/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             68.105.28.11
IP4.DNS[2]:                             68.105.29.11
IP4.DNS[3]:                             68.105.28.12
IP4.DNS[4]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 68.105.28.11 68.105.29.11 68.105.28.12
DHCP4.OPTION[5]:                        ip_address = 192.168.0.20
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1475898980
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::b01:f3f0:11f8:cedd/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8151 v1.0 Gigabit Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:03:00.0/net/enp3s0
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


SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
DDW365.51939A-2.4G  <MAC 'DDW365.51939A-2.4G' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
DVW326.EC7642-2.4G  <MAC 'DVW326.EC7642-2.4G' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        
ATT389              <MAC 'ATT389' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no        
ATT0493             <MAC 'ATT0493' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
Johnson             <MAC 'Johnson' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
10b208              <MAC '10b208' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
ATT9050             <MAC 'ATT9050' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA2       no        


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


[[/etc/NetworkManager/system-connections/DDW365.51939A-2.4G]] (600 root)
[connection] id=DDW365.51939A-2.4G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=DDW365.51939A-2.4G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DVW326.EC7642-2.4G]] (600 root)
[connection] id=DVW326.EC7642-2.4G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=DVW326.EC7642-2.4G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/KandyKustoms]] (600 root)
[connection] id=KandyKustoms | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=KandyKustoms
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


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


enp3s0    no frequency information.


wlp6s0    13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)


wlp6s0    Scan completed :
          Cell 01 - Address: <MAC 'DDW365.51939A-2.4G' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"DDW365.51939A-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000028a74c628
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DVW326.EC7642-2.4G' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"DVW326.EC7642-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002367dae5776
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT0493' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ATT0493"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002456f63d0f
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ATT389' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ATT389"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b91d2147c3
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Johnson' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Johnson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000217b7d9180
                    Extra: Last beacon: 1672ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     323EDC06388A3D0920FD7FC
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/iwlwifi-opt.conf]
options iwlwifi disable_11n=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[40612.278324] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[40612.298171] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready (repeated 3 times)
[40613.722121] wlp6s0: authenticate with <MAC 'DDW365.51939A-2.4G' [AC1]>
[40613.786585] wlp6s0: send auth to <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[40613.790035] wlp6s0: authenticated
[40613.792490] wlp6s0: associate with <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[40613.796538] wlp6s0: RX AssocResp from <MAC 'DDW365.51939A-2.4G' [AC1]> (capab=0x1411 status=0 aid=1)
[40613.796637] wlp6s0: associated
[40613.796810] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[57936.472974] wlp6s0: deauthenticating from <MAC 'DDW365.51939A-2.4G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[57938.030471] wlp6s0: authenticate with <MAC 'DDW365.51939A-2.4G' [AC1]>
[57938.140128] wlp6s0: send auth to <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[57938.145373] wlp6s0: authenticated
[57938.156046] wlp6s0: associate with <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[57938.159741] wlp6s0: RX AssocResp from <MAC 'DDW365.51939A-2.4G' [AC1]> (capab=0x1411 status=0 aid=1)
[57938.159842] wlp6s0: associated
[61566.750155] wlp6s0: deauthenticating from <MAC 'DDW365.51939A-2.4G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[61571.946412] wlp6s0: authenticate with <MAC 'DDW365.51939A-2.4G' [AC1]>
[61571.973559] wlp6s0: send auth to <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[61571.976176] wlp6s0: authenticated
[61571.980555] wlp6s0: associate with <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[61571.985134] wlp6s0: RX AssocResp from <MAC 'DDW365.51939A-2.4G' [AC1]> (capab=0x1411 status=0 aid=1)
[61571.985244] wlp6s0: associated
[68726.391111] wlp6s0: deauthenticating from <MAC 'DDW365.51939A-2.4G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[68728.856331] wlp6s0: authenticate with <MAC 'DDW365.51939A-2.4G' [AC1]>
[68728.880915] wlp6s0: send auth to <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[68728.883552] wlp6s0: authenticated
[68728.885320] wlp6s0: associate with <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[68728.890500] wlp6s0: RX AssocResp from <MAC 'DDW365.51939A-2.4G' [AC1]> (capab=0x1411 status=0 aid=1)
[68728.890604] wlp6s0: associated
[82030.753016] wlp6s0: deauthenticating from <MAC 'DDW365.51939A-2.4G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[82038.687870] wlp6s0: authenticate with <MAC 'DDW365.51939A-2.4G' [AC1]>
[82038.728238] wlp6s0: send auth to <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[82038.730714] wlp6s0: authenticated
[82038.738094] wlp6s0: associate with <MAC 'DDW365.51939A-2.4G' [AC1]> (try 1/3)
[82038.742365] wlp6s0: RX AssocResp from <MAC 'DDW365.51939A-2.4G' [AC1]> (capab=0x1411 status=0 aid=1)
[82038.742470] wlp6s0: associated


########## wireless info END ############



```

---

### Post by natural2 on 2016-10-11
Bump

---

### Post by natural2 on 2016-10-15
bump

---

