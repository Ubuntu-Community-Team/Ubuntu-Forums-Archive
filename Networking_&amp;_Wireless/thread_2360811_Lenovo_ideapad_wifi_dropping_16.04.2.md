---
title: "Lenovo ideapad wifi dropping 16.04.2"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by milram on 2017-05-08
I reformatted windows and installed 16.0.4.2. Wifi work but drops intermittently.
I updated the drivers following [COLOR=#006621][FONT=Roboto]https://github.com/lwfinger/rtlwifi_new
[/FONT][/COLOR]I still get intermittant loss of internet connectivity

```



########## wireless info START ##########


Report from: 08 May 2017 19:40 EDT -0400


Booted last: 08 May 2017 00:00 EDT -0400


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.8.0-51-generic #54~16.04.1-Ubuntu SMP Wed Apr 26 16:00:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel driver in use: rtl8821ae


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:381e]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 004: ID 5986:06b3 Acer, Inc 
Bus 002 Device 003: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


wl                   6447104  0
rtl8821ae             229376  0
btcoexist             167936  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi               102400  3 rtl_pci,btcoexist,rtl8821ae
mac80211              761856  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              581632  3 wl,mac80211,rtlwifi
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    16384  1 ideapad_laptop
video                  40960  1 ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF1]>  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6686094 (6.6 MB)  TX bytes:1336149 (1.3 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:327379 (327.3 KB)  TX bytes:327379 (327.3 KB)


wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF3]>  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp1s0' [IF3]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28381958 (28.3 MB)  TX bytes:2957278 (2.9 MB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


docker0   no wireless extensions.


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"Ramnet"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'Ramnet' [AN8]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 docker0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       951     1  0 19:07 ?        00:00:12 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF1]>
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
GENERAL.CON-UUID:                       eed60d81-ffdb-4992-827d-5ac7792070c1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   eed60d81-ffdb-4992-827d-5ac7792070c1 | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.8.0-51-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ramnet
GENERAL.CON-UUID:                       61137618-eaee-4307-8736-6ab29e0480d6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   61137618-eaee-4307-8736-6ab29e0480d6 | Ramnet
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   bf711bb7-863c-4463-8e09-e9f8c54fe6e9 | Ramnet01
IP4.ADDRESS[1]:                         192.168.1.31/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = linuxmobile
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       expiry = 1494372856
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.31
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp1s0' [IF3]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/enp2s0
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


SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
--                   <MAC '--' [AN1]>  Infra  4     2427 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2              no        
--                   <MAC '--' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --                no        
--                   <MAC '--' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 802.1X  no        
--                   <MAC '--' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2         no        
--                   <MAC '--' [AN5]>  Infra  4     2427 MHz  54 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA2              no        
xfinitywifi          <MAC 'xfinitywifi' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  --                no        
Peace.Net            <MAC 'Peace.Net' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2         no        
Ramnet               <MAC 'Ramnet' [AN8]>  Infra  4     2427 MHz  54 Mbit/s  86      &#9602;&#9604;&#9606;&#9608;  WPA2              yes     * 
Ramnet01             <MAC 'Ramnet01' [AN9]>  Infra  36    5180 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2              no        
KVK83                <MAC 'KVK83' [AN10]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WEP               no        
--                   <MAC '--' [AN11]>  Infra  11    2462 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2              no        
The Lloyd Family     <MAC 'The Lloyd Family' [AN12]>  Infra  11    2462 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2              no        
ngHub_319442NR00518  <MAC 'ngHub_319442NR00518' [AN13]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2              no        
FiOS-0AQBU           <MAC 'FiOS-0AQBU' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2              no        
xfinitywifi          <MAC 'xfinitywifi' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  --                no        
HOME-155F-2.4        <MAC 'HOME-155F-2.4' [AN16]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
HOME-C566-2.4        <MAC 'HOME-C566-2.4' [AN17]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2         no        
--                   <MAC '--' [AN18]>  Infra  132   5660 MHz  54 Mbit/s  30      &#9602;___  WPA2              no        
The Lloyd Family     <MAC 'The Lloyd Family' [AN19]>  Infra  132   5660 MHz  54 Mbit/s  29      &#9602;___  WPA2              no        


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


[[/etc/NetworkManager/system-connections/Ramnet]] (600 root)
[connection] id=Ramnet | type=wifi | permissions=user:jramsey:;
[wifi] mac-address=<MAC 'wlp1s0' [IF3]> | mac-address-blacklist= | ssid=Ramnet
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Ramnet01]] (600 root)
[connection] id=Ramnet01 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF3]> | mac-address-blacklist= | ssid=Ramnet01
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


docker0   no frequency information.


lo        no frequency information.


wlp1s0    32 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.427 GHz (Channel 4)


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


docker0   Interface doesn't support scanning.


wlp1s0    Interface doesn't support scanning : Device or resource busy


lo        Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/4.8.0-51-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     0ADAE750C888A523D63D8B5
depends:        cfg80211
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[rtl8821ae]
filename:       /lib/modules/4.8.0-51-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     6CA5F147BB6BDA3D20D84FF
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.8.0-51-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B833496EC3F52F9539F912E
depends:        mac80211,rtlwifi
vermagic:       4.8.0-51-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.8.0-51-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     0BB42E4C7EBEC81FFE99621
depends:        mac80211,cfg80211
vermagic:       4.8.0-51-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: N
int_clear: Y
ips: N
msi: Y
swenc: Y
swlps: N


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


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae swenc=1 ips=0 fwlps=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   16.166604] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   16.166608] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   16.516399] rtlwifi: loading out-of-tree module taints kernel.
[   16.516528] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   16.692935] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_29.bin
[   16.692944] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   16.700867] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.701668] rtlwifi: rtlwifi: wireless switch is on
[   17.470923] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.653457] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[   26.967110] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[   27.259223] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   28.853239] r8169 0000:02:00.0 enp2s0: link down
[   28.853329] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   29.788701] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   34.617475] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready
[   36.030782] wlp1s0: authenticate with <MAC 'Ramnet01' [AN9]>
[   36.033556] wlp1s0: No basic rates, using min rate instead
[   36.033973] wlp1s0: send auth to <MAC 'Ramnet01' [AN9]> (try 1/3)
[   36.035515] wlp1s0: authenticated
[   36.040058] wlp1s0: associate with <MAC 'Ramnet01' [AN9]> (try 1/3)
[   36.041625] wlp1s0: RX AssocResp from <MAC 'Ramnet01' [AN9]> (capab=0x811 status=0 aid=1)
[   36.043192] wlp1s0: associated
[   36.043250] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  108.204852] r8169 0000:02:00.0 enp2s0: link up
[  108.204875] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[  156.857548] r8169 0000:02:00.0 enp2s0: link down
[  914.006589] r8169 0000:02:00.0 enp2s0: link up
[ 1526.989615] r8169 0000:02:00.0 enp2s0: link down
[ 1649.240385] wlp1s0: deauthenticating from <MAC 'Ramnet01' [AN9]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1652.413935] wlp1s0: authenticate with <MAC 'Ramnet' [AN8]>
[ 1652.416935] wlp1s0: send auth to <MAC 'Ramnet' [AN8]> (try 1/3)
[ 1652.420404] wlp1s0: authenticated
[ 1652.424070] wlp1s0: associate with <MAC 'Ramnet' [AN8]> (try 1/3)
[ 1652.428794] wlp1s0: RX AssocResp from <MAC 'Ramnet' [AN8]> (capab=0xc11 status=0 aid=11)
[ 1652.431452] wlp1s0: associated


########## wireless info END ############




```


[http://paste.ubuntu.com/24539715/](http://paste.ubuntu.com/24539715/)

---

