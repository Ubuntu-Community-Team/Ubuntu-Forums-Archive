---
title: "Encore ENLWI-G2 slow connection speed, Ubuntu 16.04"
date: 2016-12-25
forum: Networking &amp; Wireless
---

### Post by sartonis on 2016-12-25
Hello

As the title says, im having very poor performance from this wireless card. 

With a wired connection i get a download seed up to 20 Mbps, but when i try the wireless connection goes to about 3/4 Mbps MAX

I tried a few fixes with no result.  



EDIT: Checked the status of UFW and its inactive.

[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]Haven't tried ndiswrapper fix. I prefer this as a last resort.




Here is the result of the Wireless info Script:


```

########## wireless info START ##########

Report from: 25 Dec 2016 20:56 ART -0300


Booted last: 25 Dec 2016 00:00 ART -0300


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185]
    Kernel driver in use: rtl818x_pci


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1532:0214 Razer USA, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0416:5020 Winbond Electronics Corp. 
Bus 004 Device 002: ID 1532:0043 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl818x_pci            53248  0
mac80211              737280  1 rtl818x_pci
cfg80211              565248  2 mac80211,rtl818x_pci
eeprom_93cx6           16384  1 rtl818x_pci
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:50467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66061012 (66.0 MB)  TX bytes:16447388 (16.4 MB)


wlp5s7    Link encap:Ethernet  HWaddr <MAC 'wlp5s7' [IF2]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7c41:2b7d:c47b:499a/64 Scope:Link
          inet6 addr: fd90:671c:86c6:8000:9188:6a19:4773:ec3f/64 Scope:Global
          inet6 addr: fd90:671c:86c6:8000:31fc:d26a:3931:4b0e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82517359 (82.5 MB)  TX bytes:18533575 (18.5 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlp5s7    IEEE 802.11bg  ESSID:"Valhalla"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'Valhalla' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:365  Invalid misc:7774   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp5s7
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s7


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       972     1  0 19:39 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s7
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
GENERAL.DRIVER:                         rtl818x_pci
GENERAL.DRIVER-VERSION:                 4.4.0-57-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp5s7' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:05:07.0/net/wlp5s7
GENERAL.IP-IFACE:                       wlp5s7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Valhalla
GENERAL.CON-UUID:                       433b7515-b9f4-4e39-a2e8-5164731bc772
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   433b7515-b9f4-4e39-a2e8-5164731bc772 | Valhalla
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1482792359
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.5
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fd90:671c:86c6:8000:9188:6a19:4773:ec3f/64
IP6.ADDRESS[2]:                         fd90:671c:86c6:8000:31fc:d26a:3931:4b0e/64
IP6.ADDRESS[3]:                         fe80::7c41:2b7d:c47b:499a/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0/net/enp3s0
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Fibertel WiFi836  <MAC 'Fibertel WiFi836' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Mustaine_Network  <MAC 'Mustaine_Network' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Valhalla          <MAC 'Valhalla' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 


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


[[/etc/NetworkManager/system-connections/Valhalla]] (600 root)
[connection] id=Valhalla | type=wifi | permissions=user:odin:;
[wifi] mac-address=<MAC 'wlp5s7' [IF2]> | mac-address-blacklist= | ssid=Valhalla
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Argentina/Buenos_Aires (based on set time zone)


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


wlp5s7    14 channels in total; available frequencies :
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
          Current Frequency:2.427 GHz (Channel 4)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlp5s7    Scan completed :
          Cell 01 - Address: <MAC 'Valhalla' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"Valhalla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000176f59794
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Mustaine_Network' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Mustaine_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015cd4e88db
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl818x_pci]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
license:        GPL
description:    RTL8180 / RTL8185 / RTL8187SE PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     718CDE48D1F626F7851C577
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   33.217601] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready (repeated 2 times)
[   37.440040] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   37.702116] r8169 0000:03:00.0 enp3s0: link down
[   37.702164] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   37.702175] r8169 0000:03:00.0 enp3s0: link down
[   38.248842] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready
[   40.031696] r8169 0000:03:00.0 enp3s0: link up
[   40.031706] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   88.905734] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[   89.033326] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[   89.035139] wlp5s7: authenticated
[   89.037330] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[   89.040601] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=2)
[   89.040638] wlp5s7: associated
[   89.040705] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s7: link becomes ready
[  129.570630] wlp5s7: deauthenticating from <MAC 'Valhalla' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  132.871617] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready (repeated 2 times)
[  136.783828] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  136.896217] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[  136.896280] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  136.940250] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready
[  138.389012] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[  138.494235] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[  138.495823] wlp5s7: authenticated
[  138.498098] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[  138.500614] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=2)
[  138.500650] wlp5s7: associated
[  138.500724] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s7: link becomes ready
[  139.163798] r8169 0000:03:00.0 enp3s0: link up
[  139.163815] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  174.324446] r8169 0000:03:00.0 enp3s0: link down
[  389.986796] wlp5s7: deauthenticating from <MAC 'Valhalla' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  391.487770] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[  391.615182] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[  391.623301] wlp5s7: authenticated
[  391.627069] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[  391.629895] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=2)
[  391.629935] wlp5s7: associated
[  846.974975] r8169 0000:03:00.0 enp3s0: link up
[  947.214418] r8169 0000:03:00.0 enp3s0: link down
[ 1552.123606] r8169 0000:03:00.0 enp3s0: link up
[ 1666.461420] r8169 0000:03:00.0 enp3s0: link down


########## wireless info END ############

```



Thanks in advance!

---

### Post by Geoff_Lane on 2016-12-26
I've got a realtek wifi adapter and have virtually given up wifi as it is slow and unreliable.

Strangely my 12.04 was rock solid wifi but was with an older laptop and different wifi adapter.

Geffers

---

### Post by sartonis on 2016-12-26
> **Geoff_Lane said:**
> I've got a realtek wifi adapter and have virtually given up wifi as it is slow and unreliable.

Strangely my 12.04 was rock solid wifi but was with an older laptop and different wifi adapter.

Geffers


Thanks for your replay. 


In other situations i would go with the wired connection, but, in this case it´s not an option...


I really need a fix for this.

---

### Post by wildmanne39 on 2016-12-26
First unplug your wired connection so it will not override your wifi connection, because it is using the wrong driver and that makes it very slow.

Second go into network manager and set your settings to match the screenshots.

Go into your router and set the channel to 1, 6 or 11 and not auto then save.

Where do you live so we can make sure the Country code is correct?
Thanks

---

### Post by sartonis on 2016-12-26
> **wildmanne39 said:**
> First unplug your wired connection so it will not override your wifi connection, because it is using the wrong driver and that makes it very slow.

Second go into network manager and set your settings to match the screenshots.

Go into your router and set the channel to 1, 6 or 11 and not auto then save.

Where do you live so we can make sure the Country code is correct?
Thanks

I did unplug the ethernet cable to run tests, and used a wifi analyzer app from my phone to check the best channel to use. (will try again just to be sure) 

The Country code seems all right (i live in Argentina)

---

### Post by wildmanne39 on 2016-12-26
We need to change your Country code for better reliability. Please do:
```
sudo iw reg set AR
sudo sed -i 's/^REG.*=$/&AR/' /etc/default/crda
```
please post a fresh wireless file so we can make sure all the changes stuck.

---

### Post by sartonis on 2016-12-26
Ok, i run those codes with no result.

The output for this code:
```

sudo iw reg AR
```

gives me a bunch of option (phy and dev)

and this one:

```

sudo sed -i 's/^REG.*=$/&AR/' /etc/default/crda
```

reports nothing.

Here is the new wireless file:

```




########## wireless info START ##########


Report from: 26 Dec 2016 18:09 ART -0300


Booted last: 26 Dec 2016 00:00 ART -0300


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185]
	Kernel driver in use: rtl818x_pci


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1532:0214 Razer USA, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1532:0043 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl818x_pci            53248  0
mac80211              737280  1 rtl818x_pci
cfg80211              565248  2 mac80211,rtl818x_pci
eeprom_93cx6           16384  1 rtl818x_pci
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:455071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:609067176 (609.0 MB)  TX bytes:38479639 (38.4 MB)


wlp5s7    Link encap:Ethernet  HWaddr <MAC 'wlp5s7' [IF2]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7c41:2b7d:c47b:499a/64 Scope:Link
          inet6 addr: fd90:671c:86c6:8000:9188:6a19:4773:ec3f/64 Scope:Global
          inet6 addr: fd90:671c:86c6:8000:31fc:d26a:3931:4b0e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:314219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:397920042 (397.9 MB)  TX bytes:53198353 (53.1 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlp5s7    IEEE 802.11bg  ESSID:"Valhalla"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'Valhalla' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:145  Invalid misc:597   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp5s7
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s7


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       972     1  0 Dec25 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s7
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
GENERAL.DRIVER:                         rtl818x_pci
GENERAL.DRIVER-VERSION:                 4.4.0-57-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp5s7' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:05:07.0/net/wlp5s7
GENERAL.IP-IFACE:                       wlp5s7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Valhalla
GENERAL.CON-UUID:                       433b7515-b9f4-4e39-a2e8-5164731bc772
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   433b7515-b9f4-4e39-a2e8-5164731bc772 | Valhalla
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1482872280
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.5
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fd90:671c:86c6:8000:9188:6a19:4773:ec3f/64
IP6.ADDRESS[2]:                         fd90:671c:86c6:8000:31fc:d26a:3931:4b0e/64
IP6.ADDRESS[3]:                         fe80::7c41:2b7d:c47b:499a/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0/net/enp3s0
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Fibertel WiFi836    <MAC 'Fibertel WiFi836' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Mustaine_Network    <MAC 'Mustaine_Network' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Valhalla            <MAC 'Valhalla' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2       yes     * 
Fibertel Wifi 2015  <MAC 'Fibertel Wifi 2015' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1       no        


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


[[/etc/NetworkManager/system-connections/Valhalla]] (600 root)
[connection] id=Valhalla | type=wifi | permissions=user:odin:;
[wifi] mac-address=<MAC 'wlp5s7' [IF2]> | mac-address-blacklist= | ssid=Valhalla
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Argentina/Buenos_Aires (based on set time zone)


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


wlp5s7    14 channels in total; available frequencies :
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
          Current Frequency:2.427 GHz (Channel 4)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlp5s7    Scan completed :
          Cell 01 - Address: <MAC 'Valhalla' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"Valhalla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013417bc45b
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Fibertel WiFi836' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Fibertel WiFi836"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ddc45dd15e
                    Extra: Last beacon: 4828ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Fibertel Wifi 2015' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Fibertel Wifi 2015"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003eabae4621
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Mustaine_Network' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Mustaine_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000279793e116
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl818x_pci]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
license:        GPL
description:    RTL8180 / RTL8185 / RTL8187SE PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     718CDE48D1F626F7851C577
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   89.040638] wlp5s7: associated
[   89.040705] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s7: link becomes ready
[  129.570630] wlp5s7: deauthenticating from <MAC 'Valhalla' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  132.871617] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready (repeated 2 times)
[  136.783828] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  136.896217] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[  136.896280] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  136.940250] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready
[  138.389012] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[  138.494235] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[  138.495823] wlp5s7: authenticated
[  138.498098] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[  138.500614] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=2)
[  138.500650] wlp5s7: associated
[  138.500724] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s7: link becomes ready
[  139.163798] r8169 0000:03:00.0 enp3s0: link up
[  139.163815] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  174.324446] r8169 0000:03:00.0 enp3s0: link down
[  389.986796] wlp5s7: deauthenticating from <MAC 'Valhalla' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  391.487770] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[  391.615182] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[  391.623301] wlp5s7: authenticated
[  391.627069] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[  391.629895] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=2)
[  391.629935] wlp5s7: associated
[  846.974975] r8169 0000:03:00.0 enp3s0: link up
[  947.214418] r8169 0000:03:00.0 enp3s0: link down
[ 1552.123606] r8169 0000:03:00.0 enp3s0: link up
[ 1666.461420] r8169 0000:03:00.0 enp3s0: link down
[ 9902.431022] r8169 0000:03:00.0 enp3s0: link up
[ 9910.005855] wlp5s7: deauthenticating from <MAC 'Valhalla' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[80167.352543] r8169 0000:03:00.0 enp3s0: link down
[80308.917140] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready (repeated 2 times)
[80310.407117] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[80310.517062] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[80310.520936] wlp5s7: authenticated
[80310.525005] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[80310.530927] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=1)
[80310.530964] wlp5s7: associated
[80310.531055] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s7: link becomes ready


########## wireless info END ############





```

---

### Post by wildmanne39 on 2016-12-26
None of the changes are showing in the file posted, did you do what was in the screenshots? I edited the first command in the other post, when I copied and pasted it to the forum I missed a part of it, so run them both again.

---

### Post by sartonis on 2016-12-26
> **wildmanne39 said:**
> None of the changes are showing in the file posted, did you do what was in the screenshots? I edited the first command in the other post, when I copied and pasted it to the forum I missed a part of it, so run them both again.


[FONT=courier new]Yes,I did what you told me. In Connection Manager y put as &#8220;ignore&#8221;and added  Google DNS&#8217;s

I ran both codes again.

The first one just ask for SUDO pass and the other one did the same as before.

Here is the Wireless file again. 



[/FONT]
```


########## wireless info START ##########


Report from: 26 Dec 2016 18:33 ART -0300


Booted last: 26 Dec 2016 00:00 ART -0300


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185]
    Kernel driver in use: rtl818x_pci


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1532:0214 Razer USA, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1532:0043 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl818x_pci            53248  0
mac80211              737280  1 rtl818x_pci
cfg80211              565248  2 mac80211,rtl818x_pci
eeprom_93cx6           16384  1 rtl818x_pci
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:455071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:609067176 (609.0 MB)  TX bytes:38479639 (38.4 MB)


wlp5s7    Link encap:Ethernet  HWaddr <MAC 'wlp5s7' [IF2]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7c41:2b7d:c47b:499a/64 Scope:Link
          inet6 addr: fd90:671c:86c6:8000:9188:6a19:4773:ec3f/64 Scope:Global
          inet6 addr: fd90:671c:86c6:8000:31fc:d26a:3931:4b0e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:324449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:406550803 (406.5 MB)  TX bytes:58620399 (58.6 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlp5s7    IEEE 802.11bg  ESSID:"Valhalla"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'Valhalla' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:264  Invalid misc:502   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp5s7
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s7


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       972     1  0 Dec25 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s7
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
GENERAL.DRIVER:                         rtl818x_pci
GENERAL.DRIVER-VERSION:                 4.4.0-57-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp5s7' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:05:07.0/net/wlp5s7
GENERAL.IP-IFACE:                       wlp5s7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Valhalla
GENERAL.CON-UUID:                       433b7515-b9f4-4e39-a2e8-5164731bc772
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     48 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   433b7515-b9f4-4e39-a2e8-5164731bc772 | Valhalla
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1482872280
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.5
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fd90:671c:86c6:8000:9188:6a19:4773:ec3f/64
IP6.ADDRESS[2]:                         fd90:671c:86c6:8000:31fc:d26a:3931:4b0e/64
IP6.ADDRESS[3]:                         fe80::7c41:2b7d:c47b:499a/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0/net/enp3s0
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Valhalla            <MAC 'Valhalla' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
Fibertel WiFi836    <MAC 'Fibertel WiFi836' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Mustaine_Network    <MAC 'Mustaine_Network' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Fibertel Wifi 2015  <MAC 'Fibertel Wifi 2015' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1       no        


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


[[/etc/NetworkManager/system-connections/Valhalla]] (600 root)
[connection] id=Valhalla | type=wifi | permissions=user:odin:;
[wifi] mac-address=<MAC 'wlp5s7' [IF2]> | mac-address-blacklist= | ssid=Valhalla
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Argentina/Buenos_Aires (based on set time zone)


country AR: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp3s0    no frequency information.


wlp5s7    13 channels in total; available frequencies :
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
          Current Frequency:2.427 GHz (Channel 4)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlp5s7    Scan completed :
          Cell 01 - Address: <MAC 'Valhalla' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"Valhalla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000042ea3709
                    Extra: Last beacon: 152ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Mustaine_Network' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Mustaine_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027ece15eb7
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Fibertel Wifi 2015' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Fibertel Wifi 2015"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f0094827a
                    Extra: Last beacon: 6752ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Fibertel WiFi836' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Fibertel WiFi836"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000de1a997030
                    Extra: Last beacon: 4224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl818x_pci]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
license:        GPL
description:    RTL8180 / RTL8185 / RTL8187SE PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     718CDE48D1F626F7851C577
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 1666.461420] r8169 0000:03:00.0 enp3s0: link down
[ 9902.431022] r8169 0000:03:00.0 enp3s0: link up
[ 9910.005855] wlp5s7: deauthenticating from <MAC 'Valhalla' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[80167.352543] r8169 0000:03:00.0 enp3s0: link down
[80308.917140] IPv6: ADDRCONF(NETDEV_UP): wlp5s7: link is not ready (repeated 2 times)
[80310.407117] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[80310.517062] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[80310.520936] wlp5s7: authenticated
[80310.525005] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[80310.530927] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=1)
[80310.530964] wlp5s7: associated
[80310.531055] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s7: link becomes ready
[81245.592733] ieee80211 phy0: wlp5s7: No probe response from AP <MAC 'Valhalla' [AC1]> after 500ms, disconnecting.
[81247.213093] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[81247.344722] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[81247.548577] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 2/3)
[81247.752581] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 3/3)
[81247.956561] wlp5s7: authentication with <MAC 'Valhalla' [AC1]> timed out
[81249.977705] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[81250.104564] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[81250.308463] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 2/3)
[81250.512491] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 3/3)
[81250.515220] wlp5s7: authenticated
[81250.516544] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[81250.720555] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 2/3)
[81250.726970] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=1)
[81250.727009] wlp5s7: associated
[81313.562371] ieee80211 phy0: wlp5s7: No probe response from AP <MAC 'Valhalla' [AC1]> after 500ms, disconnecting.
[81315.214844] wlp5s7: authenticate with <MAC 'Valhalla' [AC1]>
[81315.350312] wlp5s7: send auth to <MAC 'Valhalla' [AC1]> (try 1/3)
[81315.352268] wlp5s7: authenticated
[81315.354247] wlp5s7: associate with <MAC 'Valhalla' [AC1]> (try 1/3)
[81315.356862] wlp5s7: RX AssocResp from <MAC 'Valhalla' [AC1]> (capab=0x411 status=0 aid=1)
[81315.356898] wlp5s7: associated


########## wireless info END ############



```

[FONT=courier new]Please correct me if im wrong, but, doesnt show in this part that the area code is correct?

[/FONT]```
##### iw reg get ########################


Region: America/Argentina/Buenos_Aires (based on set time zone)


country AR: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
```


Find attached  screenshoots of my connection
[FONT=courier new]
[/FONT]

---

### Post by wildmanne39 on 2016-12-26
> Please correct me if im wrong, but, doesnt show in this part that the area code is correct?Yes it does now but it did not in the last report you posted.
The screenshot that shows the dns severs is not completely correct please put the numbers all in the dns line instead of using the second line. 

It should look like this 8.8.8.8,8.8.4.4 the comma is important.

The codes should not have had have returned a message unless there was an error, so not seeing a message means the command did what was supposed to do.

---

### Post by sartonis on 2016-12-26
ok, i corrected the dns's. 

Unfortunately the problem still persist. 

I will try a reboot.

---

### Post by sartonis on 2016-12-26
Now the dns are ok. 
 
I tried with a reboot but nothing changed.

The speed still is very low.

---

### Post by wildmanne39 on 2016-12-26
Let us know if the reboot helped, the settings change in network manager needed a reboot since I did not have you run the command to restart it.

I still believe it will work better with the channel on 1,6,or 11.

---

### Post by sartonis on 2016-12-26
i will try with those channels.

The reboot didn't work

---

### Post by sartonis on 2016-12-27
Hi again.

Well, Yesterday i tried to change channels to see if i can get a better performance. 

Now, i dont have wireless connection at all. It´s says that the wifi is out of range.

---

### Post by wildmanne39 on 2016-12-27
That is strange, you have one on 4 and one on 11, so any of the other channels should be okay, the channels you can use are between 1 and 14. Just change the channel back to 4 or something else.

---

### Post by sartonis on 2016-12-27
I have to move the pc so i can use the Ethernet cable. 

Will post the result later.

---

