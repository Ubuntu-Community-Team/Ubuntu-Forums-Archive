---
title: "Ubuntu 15.04 says the wifi connection is low - Qualcomm Atheros QCA9565"
date: 2015-10-19
forum: Networking &amp; Wireless
---

### Post by alef3 on 2015-10-19
I've recently reinstalled my ubuntu, but it can't connect properl to the router, i have to stand by the router, if a get a little far I lose the connection, i think the driver is outdated, but i can't seem to reinstall or update it. I've used the wireless script.

```


########## wireless info START ##########


Report from: 19 Oct 2015 14:17 BRST -0200


Booted last: 17 Oct 2015 18:54 BRT -0300


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 4.2.3-040203-generic #201510030832 SMP Sat Oct 3 12:34:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel driver in use: ath9k


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Dell Device [1028:05f3]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 036: ID 0bda:0177 Realtek Semiconductor Corp. 
Bus 003 Device 035: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 003 Device 003: ID 248a:8564  
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
ath9k                 143360  0 
ath9k_common           36864  1 ath9k
ath3k                  20480  0 
ath9k_hw              466944  2 ath9k_common,ath9k
dell_laptop            20480  0 
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              729088  1 ath9k
bluetooth             507904  26 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              536576  4 ath,ath9k_common,ath9k,mac80211
dcdbas                 16384  1 dell_laptop
snd_soc_rt5640        114688  0 
mxm_wmi                16384  1 nouveau
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               102400  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
video                  36864  4 i915,dell_wmi,nouveau,dell_laptop
wmi                    20480  4 dell_led,dell_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2710 (2.7 KB)  TX bytes:8792 (8.7 KB)


vboxnet0  Link encap:Ethernet  HWaddr <MAC 'vboxnet0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:125567 (125.5 KB)


vboxnet1  Link encap:Ethernet  HWaddr <MAC 'vboxnet1' [IF]>  
          inet addr:192.168.57.1  Bcast:192.168.57.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vboxnet1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:14635 (14.6 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3143787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2882340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2337841941 (2.3 GB)  TX bytes:2246114018 (2.2 GB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


vboxnet0  no wireless extensions.


vboxnet1  no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Descartes"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Descartes' [AC1]>   
          Bit Rate=135 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:265   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    400    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 vboxnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     400    0        0 wlan0
192.168.57.0    0.0.0.0         255.255.255.0   U     100    0        0 vboxnet1


##### resolv.conf #######################


nameserver 127.0.1.1


nameserver 8.8.8.8
nameserver 4.2.2.2


##### network managers ##################


Installed:


    NetworkManager
    Wicd


Running:


root       714     1  0 Oct17 ?        00:00:10 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         vboxnet1
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vboxnet1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vboxnet1
GENERAL.IP-IFACE:                       vboxnet1
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     vboxnet1
GENERAL.CON-UUID:                       ded97163-99cf-493a-a497-3177d123f0d4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/32
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9,8,7,10}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1712629c-d1da-4d9e-aeb1-4de53b7bf825 | vboxnet1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   d529fe13-8a98-4760-886e-3c0405b1727c | vboxnet1
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   d677c331-b420-44d6-88dc-872f3b87f89f | vboxnet1
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   ded97163-99cf-493a-a497-3177d123f0d4 | vboxnet1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.57.1/24, gw = 0.0.0.0
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'vboxnet1' [IF]>/64, gw = ::


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.2.3-040203-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Descartes
GENERAL.CON-UUID:                       ff0527b7-3f49-4b59-8e11-6adfebee60d3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/33
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ff0527b7-3f49-4b59-8e11-6adfebee60d3 | Descartes
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.0.102/24, gw = 192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1445275716
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_lease_time = 7200
DHCP4.OPTION[15]:                       ip_address = 192.168.0.102
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_interface_mtu = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_netbios_scope = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


GENERAL.DEVICE:                         vboxnet0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vboxnet0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vboxnet0
GENERAL.IP-IFACE:                       vboxnet0
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               on


SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
REDE SAT      <MAC 'REDE SAT' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
oi velox      <MAC 'oi velox' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA2       no        
MJNet2        <MAC 'MJNet2' [AN3]>  Infra  2     2417 MHz  11 Mbit/s  72      &#9602;&#9604;&#9606;_  --         no        
Descartes     <MAC 'Descartes' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  96      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
gabriel       <MAC 'gabriel' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  10      &#9602;___  WPA1       no        
Grum_leonane  <MAC 'Grum_leonane' [AN6]>  Infra  11    2462 MHz  11 Mbit/s  27      &#9602;___  WEP        no        


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


[[/etc/NetworkManager/system-connections/Descartes]] (600 root)
[connection] id=Descartes | type=802-11-wireless
[802-11-wireless] ssid=Descartes | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Elias GOX]] (600 root)
[connection] id=Elias GOX | type=802-11-wireless
[802-11-wireless] ssid=Elias GOX | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Alunos]] (600 root)
[connection] id=Alunos | type=802-11-wireless
[802-11-wireless] ssid=Alunos | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


country BR: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


vboxnet0  no frequency information.


vboxnet1  no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


vboxnet0  Interface doesn't support scanning.


vboxnet1  Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Descartes' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Descartes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011ca82f06a
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'oi velox' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"oi velox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e3ecbebfbe
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'JARDEL' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"JARDEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000017be2183
                    Extra: Last beacon: 496ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'gabriel' [AC4]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"gabriel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000005418edc9
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'REDE SAT' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"REDE SAT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000118f65e183
                    Extra: Last beacon: 736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'JOSIEL' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"JOSIEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ea51418f9
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E5B6C8C8DD5FD6F7AEB5C66
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[ath3k]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     BC24BEB84AA8FE42E66C237
depends:        bluetooth
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.3-040203-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.3-040203-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[85136.543308] wlan0: authenticate with <MAC 'Descartes' [AC1]>
[85136.559692] wlan0: send auth to <MAC 'Descartes' [AC1]> (try 1/3)
[85136.562040] wlan0: authenticated
[85136.565973] wlan0: associate with <MAC 'Descartes' [AC1]> (try 1/3)
[85136.570157] wlan0: RX AssocResp from <MAC 'Descartes' [AC1]> (capab=0x431 status=0 aid=1)
[85136.570222] wlan0: associated
[85136.572667] ath: EEPROM regdomain: 0x804c
[85136.572671] ath: EEPROM indicates we should expect a country code
[85136.572673] ath: doing EEPROM country->regdmn map search
[85136.572674] ath: country maps to regdmn code: 0x3b
[85136.572676] ath: Country alpha2 being used: BR
[85136.572677] ath: Regpair used: 0x3b
[85136.572679] ath: regdomain 0x804c dynamically updated by country IE
[87373.111960] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[87374.135172] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)


########## wireless info END ############



```

---

### Post by Hadaka on 2015-10-19
Hi, you have 2 network managers loaded..
```
##### network managers ##################
  Installed:       NetworkManager     Wicd
```
decide on one.

---

### Post by alef3 on 2015-10-20
I had read some threads and then ran some scripts, that's how I came to have two managers, I've deleted networkmanager, I'm using only Wicd, it's better now, really thanks for your help ^^

---

### Post by Hadaka on 2015-10-20
Great !

---

### Post by alef3 on 2015-10-21
Wicd was also having weak signal, and it wasnt showing its icon on the system tray icon, then i uninstalled wicd and reinstalled neworkmanager, but now it wont work at all

```


########## wireless info START ##########


Report from: 21 Oct 2015 14:10 BRST -0200


Booted last: 20 Oct 2015 18:25 BRST -0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 4.2.3-040203-generic #201510030832 SMP Sat Oct 3 12:34:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel driver in use: ath9k


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Dell Device [1028:05f3]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 052: ID 0bda:0177 Realtek Semiconductor Corp. 
Bus 003 Device 058: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 003 Device 003: ID 248a:8564  
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
9: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath3k                  20480  0 
bluetooth             507904  26 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
ath9k                 143360  0 
snd_soc_rt5640        114688  0 
ath9k_common           36864  1 ath9k
snd_soc_rl6231         16384  1 snd_soc_rt5640
dell_laptop            20480  0 
ath9k_hw              466944  2 ath9k_common,ath9k
snd_soc_core          196608  1 snd_soc_rt5640
dcdbas                 16384  1 dell_laptop
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              729088  1 ath9k
snd_pcm               102400  9 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
cfg80211              536576  4 ath,ath9k_common,ath9k,mac80211
mxm_wmi                16384  1 nouveau
video                  36864  4 i915,dell_wmi,nouveau,dell_laptop
wmi                    20480  4 dell_led,dell_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7406076 (7.4 MB)  TX bytes:489151 (489.1 KB)


vboxnet0  Link encap:Ethernet  HWaddr <MAC 'vboxnet0' [IF]>  
          inet6 addr: fe80::<IP6 'vboxnet0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:177760 (177.7 KB)


vboxnet1  Link encap:Ethernet  HWaddr <MAC 'vboxnet1' [IF]>  
          inet addr:192.168.57.1  Bcast:192.168.57.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vboxnet1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:69639 (69.6 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:238355 errors:0 dropped:2 overruns:0 frame:0
          TX packets:181588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:230234568 (230.2 MB)  TX bytes:31290295 (31.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


vboxnet0  no wireless extensions.


vboxnet1  no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Descartes"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Descartes' [AC1]>   
          Bit Rate=90 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 vboxnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0
192.168.57.0    0.0.0.0         255.255.255.0   U     100    0        0 vboxnet1


##### resolv.conf #######################


nameserver 192.168.0.1
nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root     30407  1139  0 14:04 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       3ec02d54-84ee-439b-ab8c-0e365835cebe
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3ec02d54-84ee-439b-ab8c-0e365835cebe | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.0.100/24, gw = 192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1445450772
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       ip_address = 192.168.0.100
DHCP4.OPTION[15]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       requested_host_name = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::


GENERAL.DEVICE:                         vboxnet0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vboxnet0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vboxnet0
GENERAL.IP-IFACE:                       vboxnet0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     vboxnet0
GENERAL.CON-UUID:                       35b951d0-14a4-4b2b-80d5-0ab7f4f9b7ba
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   35b951d0-14a4-4b2b-80d5-0ab7f4f9b7ba | vboxnet0
WIRED-PROPERTIES.CARRIER:               on
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'vboxnet0' [IF]>/64, gw = ::


GENERAL.DEVICE:                         vboxnet1
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vboxnet1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vboxnet1
GENERAL.IP-IFACE:                       vboxnet1
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     vboxnet1
GENERAL.CON-UUID:                       4cdc5db0-0665-47b7-8210-2b7466fe36d7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4cdc5db0-0665-47b7-8210-2b7466fe36d7 | vboxnet1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.57.1/24, gw = 0.0.0.0
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'vboxnet1' [IF]>/64, gw = ::


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.2.3-040203-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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


[[/etc/NetworkManager/system-connections/Descartes]] (600 root)
[connection] id=Descartes | type=802-11-wireless
[802-11-wireless] ssid=Descartes | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Elias GOX]] (600 root)
[connection] id=Elias GOX | type=802-11-wireless
[802-11-wireless] ssid=Elias GOX | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Alunos]] (600 root)
[connection] id=Alunos | type=802-11-wireless
[802-11-wireless] ssid=Alunos | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


country BR: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


vboxnet0  no frequency information.


vboxnet1  no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


vboxnet0  Interface doesn't support scanning.


vboxnet1  Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Descartes' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Descartes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000039edb4f937
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath3k]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     BC24BEB84AA8FE42E66C237
depends:        bluetooth
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E5B6C8C8DD5FD6F7AEB5C66
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/4.2.3-040203-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.3-040203-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.3-040203-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.3-040203-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CE:E6:5B:C1:E3:07:7F:6F:F5:58:77:52:AC:20:3F:9D:65:F7:05:DA
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v0000168Cd00000013sv00000017sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000025sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001731bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000035sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000036sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000406sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000407sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000408sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00000417sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001012sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001203sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001204sd00001259bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001234sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001235sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00001236sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002030sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002031sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002041sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002042sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002051sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00002053sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003070sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003202sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003203sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A07sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A12sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A13sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A14sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A17sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A18sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A63sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A73sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003A74sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004610sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00004F00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005A00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005B00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005D00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00005E00sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007064sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007065sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007084sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv00007088sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000A527sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E801sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E811sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E814sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E911sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv0000E912sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000013sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000053sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000418sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000420sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00000426sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00001054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002052sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00002054sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003071sd000002FAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A15sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A16sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Csd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A1Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A23sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003A24sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00003B08sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000700Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv0000701Dsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007094sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007101sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007114sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv00007115sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000043sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00000044sd00001737bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001329sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000134Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001602sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00001603sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00002065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003000sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A19sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00003A22sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005000sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005001sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005301sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00005401sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv00007092sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv0000E901sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000034sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000035sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000100sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000112sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000200sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000202sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B0sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002B1sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv000002D6sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000422sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000423sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000425sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000427sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00000428sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000042Asd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001020sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001025sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001026sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001033sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001034sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001060sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000137Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001385sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001386sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000139Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000142Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00001604sd0000196Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002108sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00002A97sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003061sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003062sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003063sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003064sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003065sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003067sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00003164sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00004105sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006303sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006313sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006323sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006333sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006353sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007096sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007106sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007108sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007111sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007112sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007116sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007128sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007130sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007131sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv00007519sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000A601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000C601sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E000sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E002sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E008sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Bsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E00Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E913sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E917sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv0000E918sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00001055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv00002055sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000720Bsd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv0000B203sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000001Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00001072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000147Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002071sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00002072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A09sd000007D1bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A69sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Dsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A6Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00003A76sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008001sd000018CBbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv00008011sd00001799bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv0000E914sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000023sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000032sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000033sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000384sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000429sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000430sd00001468bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00000502sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001022sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001024sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00001026sd000010E9bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv000013C0sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002072sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00002A5Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003072sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A6Fsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00003A70sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007122sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007125sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00007132sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv00009000sd00001385bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E815sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E915sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv0000E916sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000024sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00002098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A78sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A79sd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Asd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00003A7Bsd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv00009223sd00001ACEbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv0000D05Bsd000010FCbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000029sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000034sd00001B0Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000036sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000008Fsd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000504sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00000507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001000sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001001sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001067sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001071sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001081sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001090sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001130sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001381sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001382sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Csd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000147Dsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001536sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001A67sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00001C71sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00002000sd00001071bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003041sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003042sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003091sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003092sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003093sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003094sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003095sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003096sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003097sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003098sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00003099sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Asd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Dsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000309Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv000030A3sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004301sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004303sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004306sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00004507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006502sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006507sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006512sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006522sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006532sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006542sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006552sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006600sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006610sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006620sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00006642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007136sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007137sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007138sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007139sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007140sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007141sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007154sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007156sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007157sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007158sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007161sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007163sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv00007168sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000A822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000B822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000C823sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000D822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E004sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E006sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E007sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E009sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E00Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E010sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E012sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E013sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E015sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E019sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E01Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E622sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000E919sd00001458bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv0000F822sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Asv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000023sd00001931bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000037sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000204sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000205sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000410sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000411sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000464sd00001028bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C02sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C05sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C10sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00000C11sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001000sd00001B14bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001089sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001106sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001461sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001537sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001619sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001A89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00001D89sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002036sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002300sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002A37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00002C37sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000303Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003040sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A2sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ABsd00001895bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030ADsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AEsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030AFsd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030B2sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000031A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00003B00sd00001106bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004101sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004102sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004103sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004104sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004114sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00004305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006623sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007159sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007164sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007167sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007173sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007178sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007182sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007183sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007187sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00007194sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00008305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv00009811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A011sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A305sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A500sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A501sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A502sd00003485bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A831sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000A842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000BA91sd0000167Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000D811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E014sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E016sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E017sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E01Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E022sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E023sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E025sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E031sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E032sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E033sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E035sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E036sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E037sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E03Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E048sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E049sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E070sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000E811sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000EE32sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv0000F611sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001112sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv00001A12sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv000030A7sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv0000E029sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Csv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000300sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00000301sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv00002099sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Dsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00000802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001121sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001462sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000158Fsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001626sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00001A21sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00002309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B0sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B3sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000030B4sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv000031A4sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00004309sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006603sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00006613sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv00007189sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E030sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv0000E034sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Esv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000009Asd0000106Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00000508sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001173sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001627sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001628sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv000016A8sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001800sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001801sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00001802sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002000sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00002001sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003112sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003113sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003114sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003116sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003A7Esd00001186bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00003ABEsd00001948bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004107sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004108sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00004109sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000410Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006503sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006513sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00006523sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv00007188sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv0000E04Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000030sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001186sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000118Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001237sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000126Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001785sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000179Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001838sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000191Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001C01sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F86sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002000sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002001sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002086sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002097sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000209Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002126sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002152sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002187sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002B32sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002B33sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002B87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002C97sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00002F87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003118sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003122sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000312Fsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003218sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00003219sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004001sd00001C56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004105sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004106sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000410Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004115sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004116sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004117sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00004318sd00001A32bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006607sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006608sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006627sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006628sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006647sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00006657sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007192sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007193sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00007197sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000850Dsd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008601sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv00008631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000A118sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B841sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000B842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C680sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C706sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000C708sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E044sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E047sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Esd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E04Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E051sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E062sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E063sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E075sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000E080sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv0000F842sd00001113bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000032sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000033sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000063sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000064sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000081sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000088sd000014CDbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000091sd00001969bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000802sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000812sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000822sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00000862sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001783sd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000180Esd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00001864sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv000018CDsd000010CFbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002003sd00001A56bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002110sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002116sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Esd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000211Fsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002185sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002208sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002234sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C00sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C03sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002C04sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00002F85sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003114sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000104Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003117sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00003214sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004110sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004111sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004112sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004113sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000411Fsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00004120sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006611sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006621sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006631sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006641sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006651sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006661sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv00007055sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000802Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000812Asd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000850Esd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E6sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0E8sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000C0F9sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E052sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E058sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E059sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E064sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E07Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E085sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E086sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E087sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv0000E08Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000034sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000612sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000622sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000632sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000642sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000652sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000662sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000672sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000682sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000692sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006A2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000006B2sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000803sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000813sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00000842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001832sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00001842sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000018E3sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002005sd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002130sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000213Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002176sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000217Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002182sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Bsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000218Dsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002810sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002811sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002812sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002813sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A1sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A2sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A3sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000028A4sd00001B9Abc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F82sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00002F8Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003025sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003027sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00003028sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Bsd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000302Csd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00004026sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Bsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Csd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Dsd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000411Esd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00004129sd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000412Asd0000144Dbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00006671sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv00007202sd0000144Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv000085F2sd00001043bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A119sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000A120sd0000185Fbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E068sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E069sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E07Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E08Fsd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E091sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv0000E099sd0000105Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000036sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001195sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00001F95sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00002100sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00003118sd0000168Cbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006617sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006618sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv00006637sd000011ADbc*sc*i* ndiswrapper
alias pci:v0000168Cd00000037sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000057Esd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv00000589sd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv0000058Asd00001014bc*sc*i* ndiswrapper
alias pci:v0000168Cd00001014sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv00000000sd00000000bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000ABCDsv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FE30sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000FF19sv*sd*bc*sc*i* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[29873.230145] VBoxNetFlt: attached to 'vboxnet1' / <MAC 'vboxnet1' [IF]>
[29873.230194] device vboxnet1 entered promiscuous mode
[30747.929207] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30748.954254] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30770.885266] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30771.910040] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30778.981305] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30779.903185] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30800.912524] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30801.936919] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30879.004058] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30883.000872] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30915.077886] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30916.000527] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30920.099476] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30923.071541] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30961.091941] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30963.039598] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30977.079722] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30979.129360] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30986.098161] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30987.122494] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30991.119742] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30992.144589] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30994.091788] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30995.117118] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[30997.063253] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[30998.088265] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31009.156686] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31011.103851] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31012.128675] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31013.153061] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31021.147060] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31022.171958] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31088.170582] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31089.194925] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31091.142568] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31093.191881] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31130.188326] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31131.213149] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31134.185156] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31136.235433] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31277.454961] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31278.377307] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31280.324946] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31283.296472] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31315.373893] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31316.398896] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31321.420454] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31322.342247] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[31325.417243] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[31326.339552] wlan0: AP <MAC 'Descartes' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[32016.912686] r8169 0000:07:00.0 eth0: link down
[32059.738961] wlan0: deauthenticating from <MAC 'Descartes' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[32069.832127] wlan0: authenticate with <MAC 'Descartes' [AC1]>
[32069.849747] wlan0: send auth to <MAC 'Descartes' [AC1]> (try 1/3)
[32069.852103] wlan0: authenticated
[32069.855982] wlan0: associate with <MAC 'Descartes' [AC1]> (try 1/3)
[32069.860349] wlan0: RX AssocResp from <MAC 'Descartes' [AC1]> (capab=0x31 status=0 aid=1)
[32069.860405] wlan0: associated
[32069.862714] ath: EEPROM regdomain: 0x804c
[32069.862717] ath: EEPROM indicates we should expect a country code
[32069.862718] ath: doing EEPROM country->regdmn map search
[32069.862719] ath: country maps to regdmn code: 0x3b
[32069.862720] ath: Country alpha2 being used: BR
[32069.862721] ath: Regpair used: 0x3b
[32069.862722] ath: regdomain 0x804c dynamically updated by country IE
[32087.912314] r8169 0000:07:00.0 eth0: link up


########## wireless info END ############



```

---

