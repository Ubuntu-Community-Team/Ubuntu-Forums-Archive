---
title: "1610 Yaketty - Wireless issues persist with Asus X555D Realtek RTL8812AE"
date: 2017-01-31
forum: Networking &amp; Wireless
---

### Post by dcheek2 on 2017-01-31
I have been experiencing similar issues as other users with this chipset. Wireless will drop at random, pings to 8.8.8.8 start at around 20-30ms, last packet ramped up to 200ms+. Pings to DG also drop consistent with packet loss to google public. I am dual-booting with windows 10, and not experiencing any wireless issues, same router.<br><br>I am somewhat of a linux noob and would love some help getting this working.<br><br>

---

### Post by wildmanne39 on 2017-01-31
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by dcheek2 on 2017-01-31
here you go:

```



########## wireless info START ##########


Report from: 31 Jan 2017 22:40 CST -0600


Booted last: 31 Jan 2017 00:00 CST -0600


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
    Kernel driver in use: rtl8821ae


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 004: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID b49a:04f2  
Bus 001 Device 007: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              757760  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              581632  2 mac80211,rtlwifi
wmi                    16384  1 asus_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.88.250  netmask 255.255.255.0  broadcast 192.168.88.255
        inet6 fe80::86bd:a30b:e58c:e41  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 179773  bytes 191204488 (191.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 53249  bytes 8942762 (8.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 218570  bytes 13216972 (13.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 218570  bytes 13216972 (13.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.88.13  netmask 255.255.255.0  broadcast 192.168.88.255
        inet6 fe80::8e76:a145:46c8:6a45  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 54504  bytes 7508642 (7.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3550  bytes 530100 (530.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"5G Tree House"  
          Mode:Managed  Frequency:5.3 GHz  Access Point: <MAC '5G Tree House' [AN4]>   
          Bit Rate=150 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.88.1    0.0.0.0         UG    100    0        0 enp2s0
0.0.0.0         192.168.88.1    0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.88.0    0.0.0.0         255.255.255.0   U     100    0        0 enp2s0
192.168.88.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       887     1  0 14:07 ?        00:00:48 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       417880c9-96d1-3bc7-b213-677cbf3a51f7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   417880c9-96d1-3bc7-b213-677cbf3a51f7 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.88.250/24
IP4.GATEWAY:                            192.168.88.1
IP4.DNS[1]:                             192.168.88.1
IP4.DNS[2]:                             75.75.75.75
IP4.DNS[3]:                             75.75.76.76
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.88.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.88.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       expiry = 1485927297
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       ip_address = 192.168.88.250
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       dhcp_message_type = 5
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       routers = 192.168.88.1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.88.1 75.75.75.75 75.75.76.76
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       ntp_servers = 192.168.88.1 204.11.201.12 216.229.0.179
DHCP4.OPTION[26]:                       network_number = 192.168.88.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.88.1
IP6.ADDRESS[1]:                         fe80::86bd:a30b:e58c:e41/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     5G Tree House
GENERAL.CON-UUID:                       bd61ef6d-f31b-4d91-a772-6b0316d2c27b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bd61ef6d-f31b-4d91-a772-6b0316d2c27b | 5G Tree House
IP4.ADDRESS[1]:                         192.168.88.13/24
IP4.GATEWAY:                            192.168.88.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.88.1
IP4.DNS[2]:                             75.75.75.75
IP4.DNS[3]:                             75.75.76.76
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.88.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.88.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       expiry = 1485927482
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       ip_address = 192.168.88.13
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       dhcp_message_type = 5
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       routers = 192.168.88.1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.88.1 75.75.75.75 75.75.76.76
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       ntp_servers = 192.168.88.1 204.11.201.12 216.229.0.179
DHCP4.OPTION[26]:                       network_number = 192.168.88.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.88.1
IP6.ADDRESS[1]:                         fe80::8e76:a145:46c8:6a45/64
IP6.GATEWAY:                            


SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
--                <MAC '--' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
Tree House        <MAC 'Tree House' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2         no        
--                <MAC '--' [AN3]>  Infra  161   5805 MHz  0 Mbit/s   100     &#9602;&#9604;&#9606;&#9608;  WEP          no        
5G Tree House     <MAC '5G Tree House' [AN4]>  Infra  60    5300 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2         yes     * 
abbe              <MAC 'abbe' [AN5]>  Infra  11    2462 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
HUARACHES-2.4     <MAC 'HUARACHES-2.4' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2    no        
XFINITY           <MAC 'XFINITY' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2 802.1X  no        
mingrong          <MAC 'mingrong' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2    no        
xfinitywifi       <MAC 'xfinitywifi' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
--                <MAC '--' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
ATT6D6w9u6        <MAC 'ATT6D6w9u6' [AN11]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
ATT4CCU9M8        <MAC 'ATT4CCU9M8' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2         no        
xfinitywifi       <MAC 'xfinitywifi' [AN13]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
--                <MAC '--' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
xfinitywifi       <MAC 'xfinitywifi' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
ATT776            <MAC 'ATT776' [AN16]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2    no        
Tads Guest        <MAC 'Tads Guest' [AN17]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
--                <MAC '--' [AN18]>  Infra  36    5180 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2    no        
mingrong          <MAC 'mingrong' [AN19]>  Infra  36    5180 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2    no        
--                <MAC '--' [AN20]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no        
HOME-2ED4-2.4     <MAC 'HOME-2ED4-2.4' [AN21]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no        
ATT5Zs8g3H        <MAC 'ATT5Zs8g3H' [AN22]>  Infra  9     2452 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2         no        
CopsWatching_Ext  <MAC 'CopsWatching_Ext' [AN23]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2         no        
xfinitywifi       <MAC 'xfinitywifi' [AN24]>  Infra  36    5180 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
xfinitywifi       <MAC 'xfinitywifi' [AN25]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
ddrake88          <MAC 'ddrake88' [AN26]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        
Tads Wi-Fi        <MAC 'Tads Wi-Fi' [AN27]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        


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


[[/etc/NetworkManager/system-connections/5G Tree House]] (600 root)
[connection] id=5G Tree House | type=wifi | permissions=user:daniel:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=5G Tree House
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


enp2s0    no frequency information.


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
          Current Frequency:5.3 GHz (Channel 60)


##### iwlist scan #######################


wlp1s0    Failed to read scan data : Resource temporarily unavailable


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     3205DD813E27A789613A4C3
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7AD0477B303BCC50CCDBB66
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     27201DE455FACC68E425C86
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
msi: Y
swenc: N
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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 9217.897723] wlp1s0: Connection to AP <MAC '5G Tree House' [AN4]> lost
[ 9229.487337] wlp1s0: authenticate with <MAC '5G Tree House' [AN4]>
[ 9229.490987] wlp1s0: send auth to <MAC '5G Tree House' [AN4]> (try 1/3)
[ 9229.492889] wlp1s0: authenticated
[ 9229.494041] wlp1s0: associate with <MAC '5G Tree House' [AN4]> (try 1/3)
[ 9229.496966] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN4]> (capab=0x401 status=0 aid=1)
[ 9229.561375] wlp1s0: associated
[ 9780.713663] wlp1s0: Connection to AP <MAC '5G Tree House' [AN4]> lost
[ 9792.496744] wlp1s0: authenticate with <MAC '5G Tree House' [AN4]>
[ 9792.503659] wlp1s0: send auth to <MAC '5G Tree House' [AN4]> (try 1/3)
[ 9792.506325] wlp1s0: authenticated
[ 9792.510089] wlp1s0: associate with <MAC '5G Tree House' [AN4]> (try 1/3)
[ 9792.514988] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN4]> (capab=0x401 status=0 aid=1)
[ 9792.605134] wlp1s0: associated
[13048.702329] wlp1s0: deauthenticated from <MAC '5G Tree House' [AN4]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[13048.801200] wlp1s0: authenticate with <MAC '5G Tree House' [AN4]>
[13048.806773] wlp1s0: send auth to <MAC '5G Tree House' [AN4]> (try 1/3)
[13048.810695] wlp1s0: authenticated
[13048.819189] wlp1s0: associate with <MAC '5G Tree House' [AN4]> (try 1/3)
[13048.824244] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN4]> (capab=0x401 status=0 aid=1)
[13048.959082] wlp1s0: associated
[17196.624279] wlp1s0: deauthenticated from <MAC '5G Tree House' [AN4]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[17199.960024] wlp1s0: authenticate with <MAC '5G Tree House' [AN4]>
[17199.963320] wlp1s0: send auth to <MAC '5G Tree House' [AN4]> (try 1/3)
[17199.967043] wlp1s0: authenticated
[17199.971503] wlp1s0: associate with <MAC '5G Tree House' [AN4]> (try 1/3)
[17199.979646] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN4]> (capab=0x401 status=0 aid=1)
[17200.084318] wlp1s0: associated
[25666.872568] wlp1s0: deauthenticated from <MAC '5G Tree House' [AN4]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[25666.976386] wlp1s0: authenticate with <MAC '5G Tree House' [AN4]>
[25666.983681] wlp1s0: send auth to <MAC '5G Tree House' [AN4]> (try 1/3)
[25666.985374] wlp1s0: authenticated
[25666.986467] wlp1s0: associate with <MAC '5G Tree House' [AN4]> (try 1/3)
[25666.992804] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN4]> (capab=0x401 status=0 aid=1)
[25667.132403] wlp1s0: associated
[28708.453470] wlp1s0: Connection to AP <MAC '5G Tree House' [AN4]> lost
[28720.049612] wlp1s0: authenticate with <MAC '5G Tree House' [AN4]>
[28720.058599] wlp1s0: send auth to <MAC '5G Tree House' [AN4]> (try 1/3)
[28720.060643] wlp1s0: authenticated
[28720.065909] wlp1s0: associate with <MAC '5G Tree House' [AN4]> (try 1/3)
[28720.072597] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN4]> (capab=0x401 status=0 aid=1)
[28720.179425] wlp1s0: associated
[29996.259632] wlp1s0: deauthenticated from <MAC '5G Tree House' [AN4]> (Reason: 16=GROUP_KEY_HANDSHAKE_TIMEOUT)
[30005.209033] wlp1s0: authenticate with <MAC '5G Tree House' [AN4]>
[30010.842944] wlp1s0: send auth to <MAC '5G Tree House' [AN4]> (try 1/3)
[30010.847045] wlp1s0: authenticated
[30010.850406] wlp1s0: associate with <MAC '5G Tree House' [AN4]> (try 1/3)
[30010.856526] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN4]> (capab=0x401 status=0 aid=1)
[30011.013416] wlp1s0: associated


########## wireless info END ############

```

Ive also attached the gzip archive output by the script incase you need it.

---

### Post by wildmanne39 on 2017-02-01
Let's install a new driver, that should help and if needed we can set some parameters:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential git
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo modprobe -rv rtl8821ae
sudo modprobe -v rtl8821ae
```
Thanks

---

### Post by dcheek2 on 2017-02-01
Alright, new driver installed...seems to have helped a bit. still dropping connections and acting strange, packetloss followed by "ping: sendmsg: No buffer space available" and out of order packets as detailed below:

```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=30.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=30.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=27.5 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=46 time=31.0 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=46 time=28.8 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=46 time=30.5 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=46 time=32.8 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=46 time=29.5 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=46 time=28.6 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=46 time=35.7 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=46 time=30.5 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=46 time=28.7 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=46 time=56.4 ms
64 bytes from 8.8.8.8: icmp_seq=14 ttl=46 time=34.4 ms
64 bytes from 8.8.8.8: icmp_seq=15 ttl=46 time=90.7 ms
64 bytes from 8.8.8.8: icmp_seq=16 ttl=46 time=148 ms
64 bytes from 8.8.8.8: icmp_seq=17 ttl=46 time=27.9 ms
64 bytes from 8.8.8.8: icmp_seq=18 ttl=46 time=29.0 ms
64 bytes from 8.8.8.8: icmp_seq=19 ttl=46 time=163 ms
64 bytes from 8.8.8.8: icmp_seq=20 ttl=46 time=32.2 ms
64 bytes from 8.8.8.8: icmp_seq=21 ttl=46 time=153 ms
64 bytes from 8.8.8.8: icmp_seq=22 ttl=46 time=30.5 ms
64 bytes from 8.8.8.8: icmp_seq=23 ttl=46 time=149 ms
64 bytes from 8.8.8.8: icmp_seq=24 ttl=46 time=39.3 ms
64 bytes from 8.8.8.8: icmp_seq=25 ttl=46 time=28.3 ms
64 bytes from 8.8.8.8: icmp_seq=26 ttl=46 time=28.5 ms
64 bytes from 8.8.8.8: icmp_seq=27 ttl=46 time=27.3 ms
64 bytes from 8.8.8.8: icmp_seq=28 ttl=46 time=30.8 ms
64 bytes from 8.8.8.8: icmp_seq=29 ttl=46 time=31.2 ms
64 bytes from 8.8.8.8: icmp_seq=30 ttl=46 time=28.4 ms
64 bytes from 8.8.8.8: icmp_seq=31 ttl=46 time=29.7 ms
64 bytes from 8.8.8.8: icmp_seq=32 ttl=46 time=30.1 ms
64 bytes from 8.8.8.8: icmp_seq=33 ttl=46 time=27.6 ms
64 bytes from 8.8.8.8: icmp_seq=34 ttl=46 time=31.3 ms
64 bytes from 8.8.8.8: icmp_seq=35 ttl=46 time=36.7 ms
64 bytes from 8.8.8.8: icmp_seq=36 ttl=46 time=27.6 ms
64 bytes from 8.8.8.8: icmp_seq=37 ttl=46 time=37.8 ms
64 bytes from 8.8.8.8: icmp_seq=38 ttl=46 time=30.1 ms
64 bytes from 8.8.8.8: icmp_seq=39 ttl=46 time=28.6 ms
64 bytes from 8.8.8.8: icmp_seq=40 ttl=46 time=30.1 ms
64 bytes from 8.8.8.8: icmp_seq=41 ttl=46 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=42 ttl=46 time=27.3 ms
64 bytes from 8.8.8.8: icmp_seq=43 ttl=46 time=33.9 ms
64 bytes from 8.8.8.8: icmp_seq=44 ttl=46 time=30.2 ms
64 bytes from 8.8.8.8: icmp_seq=45 ttl=46 time=34.5 ms
64 bytes from 8.8.8.8: icmp_seq=46 ttl=46 time=33.5 ms
64 bytes from 8.8.8.8: icmp_seq=47 ttl=46 time=32.6 ms
64 bytes from 8.8.8.8: icmp_seq=48 ttl=46 time=31.1 ms
64 bytes from 8.8.8.8: icmp_seq=49 ttl=46 time=32.8 ms
64 bytes from 8.8.8.8: icmp_seq=50 ttl=46 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=51 ttl=46 time=28.7 ms
64 bytes from 8.8.8.8: icmp_seq=52 ttl=46 time=30.4 ms
64 bytes from 8.8.8.8: icmp_seq=53 ttl=46 time=28.6 ms
64 bytes from 8.8.8.8: icmp_seq=54 ttl=46 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=55 ttl=46 time=27.3 ms
64 bytes from 8.8.8.8: icmp_seq=56 ttl=46 time=28.8 ms
64 bytes from 8.8.8.8: icmp_seq=57 ttl=46 time=28.2 ms
64 bytes from 8.8.8.8: icmp_seq=58 ttl=46 time=47.7 ms
64 bytes from 8.8.8.8: icmp_seq=59 ttl=46 time=103 ms
64 bytes from 8.8.8.8: icmp_seq=60 ttl=46 time=165 ms
64 bytes from 8.8.8.8: icmp_seq=61 ttl=46 time=30.6 ms
64 bytes from 8.8.8.8: icmp_seq=62 ttl=46 time=112 ms
64 bytes from 8.8.8.8: icmp_seq=63 ttl=46 time=29.4 ms
64 bytes from 8.8.8.8: icmp_seq=64 ttl=46 time=121 ms
64 bytes from 8.8.8.8: icmp_seq=65 ttl=46 time=28.6 ms
64 bytes from 8.8.8.8: icmp_seq=66 ttl=46 time=126 ms
64 bytes from 8.8.8.8: icmp_seq=67 ttl=46 time=28.8 ms
64 bytes from 8.8.8.8: icmp_seq=68 ttl=46 time=28.0 ms
64 bytes from 8.8.8.8: icmp_seq=69 ttl=46 time=27.5 ms
64 bytes from 8.8.8.8: icmp_seq=70 ttl=46 time=29.0 ms
64 bytes from 8.8.8.8: icmp_seq=71 ttl=46 time=28.6 ms
64 bytes from 8.8.8.8: icmp_seq=72 ttl=46 time=27.5 ms
64 bytes from 8.8.8.8: icmp_seq=73 ttl=46 time=31.3 ms
64 bytes from 8.8.8.8: icmp_seq=74 ttl=46 time=32.9 ms
64 bytes from 8.8.8.8: icmp_seq=75 ttl=46 time=31.5 ms
64 bytes from 8.8.8.8: icmp_seq=76 ttl=46 time=29.7 ms
64 bytes from 8.8.8.8: icmp_seq=77 ttl=46 time=29.0 ms
64 bytes from 8.8.8.8: icmp_seq=78 ttl=46 time=29.4 ms
64 bytes from 8.8.8.8: icmp_seq=79 ttl=46 time=28.3 ms
64 bytes from 8.8.8.8: icmp_seq=80 ttl=46 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=81 ttl=46 time=29.2 ms
64 bytes from 8.8.8.8: icmp_seq=82 ttl=46 time=31.6 ms
64 bytes from 8.8.8.8: icmp_seq=83 ttl=46 time=30.3 ms
64 bytes from 8.8.8.8: icmp_seq=84 ttl=46 time=29.4 ms
64 bytes from 8.8.8.8: icmp_seq=85 ttl=46 time=42.9 ms
64 bytes from 8.8.8.8: icmp_seq=86 ttl=46 time=28.5 ms
64 bytes from 8.8.8.8: icmp_seq=87 ttl=46 time=32.2 ms
64 bytes from 8.8.8.8: icmp_seq=88 ttl=46 time=31.7 ms
64 bytes from 8.8.8.8: icmp_seq=89 ttl=46 time=34.5 ms
64 bytes from 8.8.8.8: icmp_seq=90 ttl=46 time=28.3 ms
64 bytes from 8.8.8.8: icmp_seq=91 ttl=46 time=28.4 ms
64 bytes from 8.8.8.8: icmp_seq=92 ttl=46 time=29.5 ms
64 bytes from 8.8.8.8: icmp_seq=93 ttl=46 time=36.8 ms
64 bytes from 8.8.8.8: icmp_seq=94 ttl=46 time=29.2 ms
64 bytes from 8.8.8.8: icmp_seq=95 ttl=46 time=31.2 ms
64 bytes from 8.8.8.8: icmp_seq=96 ttl=46 time=31.0 ms
64 bytes from 8.8.8.8: icmp_seq=97 ttl=46 time=29.0 ms
64 bytes from 8.8.8.8: icmp_seq=98 ttl=46 time=30.9 ms
64 bytes from 8.8.8.8: icmp_seq=99 ttl=46 time=28.2 ms
64 bytes from 8.8.8.8: icmp_seq=100 ttl=46 time=27.8 ms
64 bytes from 8.8.8.8: icmp_seq=101 ttl=46 time=36.0 ms
64 bytes from 8.8.8.8: icmp_seq=102 ttl=46 time=31.8 ms
64 bytes from 8.8.8.8: icmp_seq=103 ttl=46 time=30.6 ms
64 bytes from 8.8.8.8: icmp_seq=104 ttl=46 time=27.2 ms
64 bytes from 8.8.8.8: icmp_seq=105 ttl=46 time=28.5 ms
64 bytes from 8.8.8.8: icmp_seq=106 ttl=46 time=27.3 ms
64 bytes from 8.8.8.8: icmp_seq=107 ttl=46 time=28.2 ms
64 bytes from 8.8.8.8: icmp_seq=108 ttl=46 time=31.4 ms
64 bytes from 8.8.8.8: icmp_seq=109 ttl=46 time=29.7 ms
64 bytes from 8.8.8.8: icmp_seq=110 ttl=46 time=27.6 ms
64 bytes from 8.8.8.8: icmp_seq=111 ttl=46 time=27.5 ms
64 bytes from 8.8.8.8: icmp_seq=112 ttl=46 time=28.2 ms
64 bytes from 8.8.8.8: icmp_seq=113 ttl=46 time=31.8 ms
64 bytes from 8.8.8.8: icmp_seq=114 ttl=46 time=30.5 ms
64 bytes from 8.8.8.8: icmp_seq=115 ttl=46 time=36.2 ms
64 bytes from 8.8.8.8: icmp_seq=116 ttl=46 time=28.6 ms
64 bytes from 8.8.8.8: icmp_seq=117 ttl=46 time=28.5 ms
64 bytes from 8.8.8.8: icmp_seq=118 ttl=46 time=95.6 ms
64 bytes from 8.8.8.8: icmp_seq=119 ttl=46 time=152 ms
64 bytes from 8.8.8.8: icmp_seq=120 ttl=46 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=121 ttl=46 time=31.3 ms
64 bytes from 8.8.8.8: icmp_seq=122 ttl=46 time=27.6 ms
64 bytes from 8.8.8.8: icmp_seq=123 ttl=46 time=48.3 ms
64 bytes from 8.8.8.8: icmp_seq=124 ttl=46 time=181 ms
64 bytes from 8.8.8.8: icmp_seq=125 ttl=46 time=31.6 ms
64 bytes from 8.8.8.8: icmp_seq=126 ttl=46 time=180 ms
64 bytes from 8.8.8.8: icmp_seq=127 ttl=46 time=29.5 ms
64 bytes from 8.8.8.8: icmp_seq=128 ttl=46 time=174 ms
64 bytes from 8.8.8.8: icmp_seq=129 ttl=46 time=28.1 ms
64 bytes from 8.8.8.8: icmp_seq=130 ttl=46 time=76.8 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
64 bytes from 8.8.8.8: icmp_seq=131 ttl=46 time=33702 ms
64 bytes from 8.8.8.8: icmp_seq=134 ttl=46 time=30650 ms
64 bytes from 8.8.8.8: icmp_seq=136 ttl=46 time=28602 ms
64 bytes from 8.8.8.8: icmp_seq=137 ttl=46 time=27578 ms
64 bytes from 8.8.8.8: icmp_seq=132 ttl=46 time=32698 ms
64 bytes from 8.8.8.8: icmp_seq=133 ttl=46 time=31674 ms
64 bytes from 8.8.8.8: icmp_seq=135 ttl=46 time=29626 ms
64 bytes from 8.8.8.8: icmp_seq=146 ttl=46 time=28.9 ms
64 bytes from 8.8.8.8: icmp_seq=147 ttl=46 time=27.5 ms
64 bytes from 8.8.8.8: icmp_seq=148 ttl=46 time=28.7 ms
64 bytes from 8.8.8.8: icmp_seq=149 ttl=46 time=31.0 ms
64 bytes from 8.8.8.8: icmp_seq=150 ttl=46 time=29.5 ms
64 bytes from 8.8.8.8: icmp_seq=151 ttl=46 time=28.8 ms
64 bytes from 8.8.8.8: icmp_seq=152 ttl=46 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=153 ttl=46 time=27.3 ms
64 bytes from 8.8.8.8: icmp_seq=154 ttl=46 time=28.3 ms
64 bytes from 8.8.8.8: icmp_seq=155 ttl=46 time=32.1 ms
64 bytes from 8.8.8.8: icmp_seq=156 ttl=46 time=30.4 ms
64 bytes from 8.8.8.8: icmp_seq=157 ttl=46 time=28.4 ms
64 bytes from 8.8.8.8: icmp_seq=158 ttl=46 time=28.4 ms
64 bytes from 8.8.8.8: icmp_seq=159 ttl=46 time=29.1 ms
64 bytes from 8.8.8.8: icmp_seq=160 ttl=46 time=27.7 ms
64 bytes from 8.8.8.8: icmp_seq=161 ttl=46 time=32.2 ms
64 bytes from 8.8.8.8: icmp_seq=162 ttl=46 time=37.8 ms
64 bytes from 8.8.8.8: icmp_seq=163 ttl=46 time=29.2 ms
64 bytes from 8.8.8.8: icmp_seq=164 ttl=46 time=28.9 ms
64 bytes from 8.8.8.8: icmp_seq=165 ttl=46 time=28.2 ms
64 bytes from 8.8.8.8: icmp_seq=166 ttl=46 time=29.4 ms
64 bytes from 8.8.8.8: icmp_seq=167 ttl=46 time=31.7 ms
64 bytes from 8.8.8.8: icmp_seq=168 ttl=46 time=31.2 ms
64 bytes from 8.8.8.8: icmp_seq=169 ttl=46 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=170 ttl=46 time=30.4 ms
64 bytes from 8.8.8.8: icmp_seq=171 ttl=46 time=29.8 ms
64 bytes from 8.8.8.8: icmp_seq=172 ttl=46 time=28.7 ms
64 bytes from 8.8.8.8: icmp_seq=173 ttl=46 time=34.3 ms
64 bytes from 8.8.8.8: icmp_seq=174 ttl=46 time=30.8 ms
64 bytes from 8.8.8.8: icmp_seq=175 ttl=46 time=30.3 ms
64 bytes from 8.8.8.8: icmp_seq=176 ttl=46 time=27.7 ms
64 bytes from 8.8.8.8: icmp_seq=177 ttl=46 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=178 ttl=46 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=179 ttl=46 time=30.8 ms
64 bytes from 8.8.8.8: icmp_seq=180 ttl=46 time=32.5 ms
64 bytes from 8.8.8.8: icmp_seq=181 ttl=46 time=32.6 ms
64 bytes from 8.8.8.8: icmp_seq=182 ttl=46 time=78.4 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 8.8.8.8: icmp_seq=283 ttl=46 time=34.1 ms
64 bytes from 8.8.8.8: icmp_seq=284 ttl=46 time=30.3 ms
64 bytes from 8.8.8.8: icmp_seq=285 ttl=46 time=28.4 ms
64 bytes from 8.8.8.8: icmp_seq=286 ttl=46 time=27.5 ms
64 bytes from 8.8.8.8: icmp_seq=287 ttl=46 time=37.1 ms
64 bytes from 8.8.8.8: icmp_seq=288 ttl=46 time=30.7 ms
64 bytes from 8.8.8.8: icmp_seq=289 ttl=46 time=27.5 ms
64 bytes from 8.8.8.8: icmp_seq=290 ttl=46 time=33.7 ms
64 bytes from 8.8.8.8: icmp_seq=291 ttl=46 time=30.4 ms
64 bytes from 8.8.8.8: icmp_seq=292 ttl=46 time=29.0 ms
64 bytes from 8.8.8.8: icmp_seq=293 ttl=46 time=33.0 ms
64 bytes from 8.8.8.8: icmp_seq=294 ttl=46 time=31.3 ms
64 bytes from 8.8.8.8: icmp_seq=295 ttl=46 time=29.3 ms
^X64 bytes from 8.8.8.8: icmp_seq=296 ttl=46 time=30.4 ms
64 bytes from 8.8.8.8: icmp_seq=297 ttl=46 time=27.8 ms
^C
--- 8.8.8.8 ping statistics ---
297 packets transmitted, 189 received, 36% packet loss, time 336987ms
rtt min/avg/max/mdev = 27.255/1173.938/33702.787/5793.658 ms, pipe 15

```

at around seq 255, I disconnected the wireless and waited for it to reconnect at around seq 283

---

### Post by wildmanne39 on 2017-02-01
Please set your settings in network manager to match the screenshots.
[ATTACH=CONFIG]273465[/ATTACH][ATTACH=CONFIG]273466[/ATTACH]
Thanks

---

### Post by dcheek2 on 2017-02-01
No improvement... not sure how disabling IP6 stack and forcing DNS would have changed anything, but Im willing to try anything...any more ideas?

---

### Post by wildmanne39 on 2017-02-01
I will pick this back up tomorrow it is getting late here. please leave those settings as they are it does make a big difference.

We will try driver parameters and change the country code when I get back unless someone helps you first which is okay.

---

### Post by dcheek2 on 2017-02-01
Alright, so I changed countrycode and regdomain in /etc/environment and /etc/defaults/crda to US. 

I also created rtl8821ae.conf in /etc/modprobe.d/ with the following line (presumably to disable firmware power management):

```

options rtl8821ae ips=0 fwlps=0

```

after a reboot, I checked the connection and it had not improved, if anything it is getting worse.

---

### Post by wildmanne39 on 2017-02-01
Please run the wireless script again and post the results so we can make sure the changes have taken effect and I want to see if the error message that was there with the old driver if it is there with the new driver.
Thanks

---

### Post by dcheek2 on 2017-02-02
here you go:

```



########## wireless info START ##########


Report from: 02 Feb 2017 09:00 CST -0600


Booted last: 02 Feb 2017 00:00 CST -0600


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
    Kernel driver in use: rtl8821ae


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 005: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID b49a:04f2  
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             225280  0
btcoexist             167936  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi               102400  3 rtl_pci,btcoexist,rtl8821ae
mac80211              757760  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              581632  2 mac80211,rtlwifi
wmi                    16384  1 asus_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.88.250  netmask 255.255.255.0  broadcast 192.168.88.255
        inet6 fe80::86bd:a30b:e58c:e41  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 87418  bytes 82727376 (82.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 42730  bytes 6965281 (6.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 100964  bytes 6123540 (6.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 100964  bytes 6123540 (6.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.88.13  netmask 255.255.255.0  broadcast 192.168.88.255
        inet6 fe80::b2c0:90ff:fea5:e195  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 34675  bytes 4723912 (4.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1672  bytes 257348 (257.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"5G Tree House"  
          Mode:Managed  Frequency:5.3 GHz  Access Point: <MAC '5G Tree House' [AN5]>   
          Bit Rate=150 Mb/s   Tx-Power=23 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.88.1    0.0.0.0         UG    100    0        0 enp2s0
0.0.0.0         192.168.88.1    0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.88.0    0.0.0.0         255.255.255.0   U     100    0        0 enp2s0
192.168.88.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       931     1  0 Feb01 ?        00:00:19 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       417880c9-96d1-3bc7-b213-677cbf3a51f7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   417880c9-96d1-3bc7-b213-677cbf3a51f7 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.88.250/24
IP4.GATEWAY:                            192.168.88.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.88.1
IP4.DNS[2]:                             75.75.75.75
IP4.DNS[3]:                             75.75.76.76
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.88.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.88.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       expiry = 1486051099
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       ip_address = 192.168.88.250
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       dhcp_message_type = 5
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       routers = 192.168.88.1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.88.1 75.75.75.75 75.75.76.76
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       ntp_servers = 192.168.88.1 204.11.201.12 216.229.0.179
DHCP4.OPTION[26]:                       network_number = 192.168.88.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.88.1
IP6.ADDRESS[1]:                         fe80::86bd:a30b:e58c:e41/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     5G Tree House
GENERAL.CON-UUID:                       bd61ef6d-f31b-4d91-a772-6b0316d2c27b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bd61ef6d-f31b-4d91-a772-6b0316d2c27b | 5G Tree House
IP4.ADDRESS[1]:                         192.168.88.13/24
IP4.GATEWAY:                            192.168.88.1
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.88.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.88.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       expiry = 1486051099
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       ip_address = 192.168.88.13
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       dhcp_message_type = 5
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       routers = 192.168.88.1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.88.1 75.75.75.75 75.75.76.76
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       ntp_servers = 192.168.88.1 204.11.201.12 216.229.0.179
DHCP4.OPTION[26]:                       network_number = 192.168.88.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.88.1
IP6.ADDRESS[1]:                         fe80::b2c0:90ff:fea5:e195/64
IP6.GATEWAY:                            


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Tree House     <MAC 'Tree House' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2         no        
--             <MAC '--' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
abbe           <MAC 'abbe' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
--             <MAC '--' [AN4]>  Infra  161   5805 MHz  0 Mbit/s   77      &#9602;&#9604;&#9606;_  WEP          no        
5G Tree House  <MAC '5G Tree House' [AN5]>  Infra  60    5300 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2         yes     * 
xfinitywifi    <MAC 'xfinitywifi' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
XFINITY        <MAC 'XFINITY' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
--             <MAC '--' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2    no        
ATT776         <MAC 'ATT776' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2    no        
HUARACHES-2.4  <MAC 'HUARACHES-2.4' [AN10]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2    no        
--             <MAC '--' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2    no        
--             <MAC '--' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
xfinitywifi    <MAC 'xfinitywifi' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
mingrong       <MAC 'mingrong' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
HOME-2ED4-2.4  <MAC 'HOME-2ED4-2.4' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
ATT4CCU9M8     <MAC 'ATT4CCU9M8' [AN16]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
xfinitywifi    <MAC 'xfinitywifi' [AN17]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
XFINITY        <MAC 'XFINITY' [AN18]>  Infra  153   5765 MHz  54 Mbit/s  20      &#9602;___  WPA2 802.1X  no        


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


[[/etc/NetworkManager/system-connections/5G Tree House]] (600 root)
[connection] id=5G Tree House | type=wifi | permissions=user:daniel:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=5G Tree House
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


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
          Current Frequency:5.3 GHz (Channel 60)


##### iwlist scan #######################


wlp1s0    Interface doesn't support scanning : Device or resource busy


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     B435D5267F2688C985B95CB
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B833496EC3F52F9539F912E
depends:        mac80211,rtlwifi
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8A2D93AA4A1D6F5C8F09EB7
depends:        mac80211,cfg80211
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae swenc=1 ips=0 fwlps=0


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[18347.470644] rtlwifi: rtlwifi: wireless switch is on
[18351.001045] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[18357.338266] wlp1s0: authenticate with <MAC '5G Tree House' [AN5]>
[18357.341305] wlp1s0: send auth to <MAC '5G Tree House' [AN5]> (try 1/3)
[18357.342613] wlp1s0: authenticated
[18357.348323] wlp1s0: associate with <MAC '5G Tree House' [AN5]> (try 1/3)
[18357.353141] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN5]> (capab=0x401 status=0 aid=1)
[18357.355391] wlp1s0: associated
[18357.355670] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready


########## wireless info END ############

```

---

### Post by wildmanne39 on 2017-02-02
Two things before we try something else:

1. Your ethernet connection is plugged in and it will override your wifi be default so please unplug it then test download speeds, and this connection is using the wrong driver so it will be very slow.

2. I may help to take the spaces out of your network name that use to be an issue for ubuntu I am not sure it still is.
Thanks

---

### Post by dcheek2 on 2017-02-02
alright, so I re-ran the test with the ethernet cable disconnected, pings are still stopping after about 30s:
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=3405 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=1365 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=46 time=342 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=2390 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=46 time=46.8 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=46 time=32.8 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=46 time=32.9 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=46 time=53.1 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=46 time=32.9 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=46 time=30.6 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=46 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=46 time=104 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=46 time=28.7 ms
64 bytes from 8.8.8.8: icmp_seq=14 ttl=46 time=30.5 ms
64 bytes from 8.8.8.8: icmp_seq=15 ttl=46 time=29.0 ms
64 bytes from 8.8.8.8: icmp_seq=16 ttl=46 time=27.4 ms
64 bytes from 8.8.8.8: icmp_seq=17 ttl=46 time=50.0 ms
64 bytes from 8.8.8.8: icmp_seq=18 ttl=46 time=46.5 ms
64 bytes from 8.8.8.8: icmp_seq=19 ttl=46 time=36.9 ms
64 bytes from 8.8.8.8: icmp_seq=20 ttl=46 time=33.6 ms
64 bytes from 8.8.8.8: icmp_seq=21 ttl=46 time=30.7 ms
64 bytes from 8.8.8.8: icmp_seq=22 ttl=46 time=28.4 ms
64 bytes from 8.8.8.8: icmp_seq=23 ttl=46 time=44.1 ms
64 bytes from 8.8.8.8: icmp_seq=24 ttl=46 time=31.4 ms
64 bytes from 8.8.8.8: icmp_seq=25 ttl=46 time=27.9 ms
64 bytes from 8.8.8.8: icmp_seq=26 ttl=46 time=31.7 ms
64 bytes from 8.8.8.8: icmp_seq=27 ttl=46 time=30.9 ms
64 bytes from 8.8.8.8: icmp_seq=28 ttl=46 time=29.9 ms
64 bytes from 8.8.8.8: icmp_seq=29 ttl=46 time=51.8 ms
64 bytes from 8.8.8.8: icmp_seq=30 ttl=46 time=31.8 ms
64 bytes from 8.8.8.8: icmp_seq=31 ttl=46 time=48.4 ms
64 bytes from 8.8.8.8: icmp_seq=32 ttl=46 time=32.0 ms
64 bytes from 8.8.8.8: icmp_seq=33 ttl=46 time=34.6 ms
64 bytes from 8.8.8.8: icmp_seq=34 ttl=46 time=31.2 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
From 192.168.88.13 icmp_seq=53 Destination Host Unreachable
From 192.168.88.13 icmp_seq=54 Destination Host Unreachable
From 192.168.88.13 icmp_seq=55 Destination Host Unreachable
From 192.168.88.13 icmp_seq=56 Destination Host Unreachable
From 192.168.88.13 icmp_seq=57 Destination Host Unreachable
From 192.168.88.13 icmp_seq=58 Destination Host Unreachable
From 192.168.88.13 icmp_seq=59 Destination Host Unreachable
From 192.168.88.13 icmp_seq=60 Destination Host Unreachable
From 192.168.88.13 icmp_seq=61 Destination Host Unreachable
From 192.168.88.13 icmp_seq=62 Destination Host Unreachable
From 192.168.88.13 icmp_seq=66 Destination Host Unreachable
From 192.168.88.13 icmp_seq=67 Destination Host Unreachable
From 192.168.88.13 icmp_seq=68 Destination Host Unreachable
From 192.168.88.13 icmp_seq=69 Destination Host Unreachable
From 192.168.88.13 icmp_seq=70 Destination Host Unreachable
From 192.168.88.13 icmp_seq=71 Destination Host Unreachable
From 192.168.88.13 icmp_seq=72 Destination Host Unreachable
From 192.168.88.13 icmp_seq=75 Destination Host Unreachable
From 192.168.88.13 icmp_seq=76 Destination Host Unreachable
From 192.168.88.13 icmp_seq=77 Destination Host Unreachable
From 192.168.88.13 icmp_seq=78 Destination Host Unreachable
From 192.168.88.13 icmp_seq=79 Destination Host Unreachable
^C
--- 8.8.8.8 ping statistics ---
81 packets transmitted, 34 received, +22 errors, 58% packet loss, time 109180ms
rtt min/avg/max/mdev = 27.452/253.985/3405.163/710.190 ms, pipe 4

```

here is the output of the script with wired disconnected:
```



########## wireless info START ##########


Report from: 02 Feb 2017 11:12 CST -0600


Booted last: 02 Feb 2017 00:00 CST -0600


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.10
Release:	16.10
Codename:	yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
	Kernel driver in use: rtl8821ae


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 005: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID b49a:04f2  
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             225280  0
btcoexist             167936  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi               102400  3 rtl_pci,btcoexist,rtl8821ae
mac80211              757760  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              581632  2 mac80211,rtlwifi
wmi                    16384  1 asus_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 212232  bytes 235641542 (235.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 103427  bytes 15786015 (15.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 166013  bytes 10080112 (10.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 166013  bytes 10080112 (10.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.88.13  netmask 255.255.255.0  broadcast 192.168.88.255
        inet6 fe80::e1e5:8b87:b012:b193  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 49724  bytes 6832885 (6.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2993  bytes 471002 (471.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"5G Tree House"  
          Mode:Managed  Frequency:5.3 GHz  Access Point: <MAC '5G Tree House' [AN3]>   
          Bit Rate=150 Mb/s   Tx-Power=23 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.88.1    0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.88.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       931     1  0 Feb01 ?        00:00:26 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     5G Tree House
GENERAL.CON-UUID:                       67dfdc18-0aa7-41a5-9d6f-d3696abd19d8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   67dfdc18-0aa7-41a5-9d6f-d3696abd19d8 | 5G Tree House
IP4.ADDRESS[1]:                         192.168.88.13/24
IP4.GATEWAY:                            192.168.88.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.88.1
IP4.DNS[2]:                             75.75.75.75
IP4.DNS[3]:                             75.75.76.76
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.88.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.88.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       expiry = 1486059037
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       ip_address = 192.168.88.13
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       dhcp_message_type = 5
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       routers = 192.168.88.1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.88.1 75.75.75.75 75.75.76.76
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       ntp_servers = 192.168.88.1 204.11.201.12 216.229.0.179
DHCP4.OPTION[26]:                       network_number = 192.168.88.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.88.1
IP6.ADDRESS[1]:                         fe80::e1e5:8b87:b012:b193/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/enp2s0
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Tree House     <MAC 'Tree House' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2         no        
--             <MAC '--' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
5G Tree House  <MAC '5G Tree House' [AN3]>  Infra  60    5300 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2         yes     * 
abbe           <MAC 'abbe' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
XFINITY        <MAC 'XFINITY' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
xfinitywifi    <MAC 'xfinitywifi' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  --           no        
HUARACHES-2.4  <MAC 'HUARACHES-2.4' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
mingrong       <MAC 'mingrong' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
xfinitywifi    <MAC 'xfinitywifi' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
--             <MAC '--' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
Tads Guest     <MAC 'Tads Guest' [AN11]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2         no        
--             <MAC '--' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2    no        
ATT776         <MAC 'ATT776' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2    no        
xfinitywifi    <MAC 'xfinitywifi' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
Tads Wi-Fi     <MAC 'Tads Wi-Fi' [AN15]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2         no        


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


[[/etc/NetworkManager/system-connections/5G Tree House]] (600 root)
[connection] id=5G Tree House | type=wifi | permissions=user:daniel:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=5G Tree House
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


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
          Current Frequency:5.3 GHz (Channel 60)


##### iwlist scan #######################


wlp1s0    Interface doesn't support scanning : Device or resource busy


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B435D5267F2688C985B95CB
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B833496EC3F52F9539F912E
depends:        mac80211,rtlwifi
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8A2D93AA4A1D6F5C8F09EB7
depends:        mac80211,cfg80211
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae swenc=1 ips=0 fwlps=0


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[18347.470644] rtlwifi: rtlwifi: wireless switch is on
[18351.001045] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[18357.338266] wlp1s0: authenticate with <MAC '5G Tree House' [AN3]>
[18357.341305] wlp1s0: send auth to <MAC '5G Tree House' [AN3]> (try 1/3)
[18357.342613] wlp1s0: authenticated
[18357.348323] wlp1s0: associate with <MAC '5G Tree House' [AN3]> (try 1/3)
[18357.353141] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN3]> (capab=0x401 status=0 aid=1)
[18357.355391] wlp1s0: associated
[18357.355670] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[26241.940573] wlp1s0: deauthenticating from <MAC '5G Tree House' [AN3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[26294.151918] wlp1s0: authenticate with <MAC '5G Tree House' [AN3]>
[26294.156625] wlp1s0: send auth to <MAC '5G Tree House' [AN3]> (try 1/3)
[26294.159864] wlp1s0: authenticated
[26294.163046] wlp1s0: associate with <MAC '5G Tree House' [AN3]> (try 1/3)
[26294.168326] wlp1s0: RX AssocResp from <MAC '5G Tree House' [AN3]> (capab=0x401 status=0 aid=1)
[26294.169555] wlp1s0: associated


########## wireless info END ############

```

as far as the SSID goes, I have another laptop with an intel chipset that works just fine with ubuntu 16.10, so I doubt the spaces are an issue.

---

### Post by wildmanne39 on 2017-02-02
Please run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Reboot does that help?

You are having issues because of a bug so I hope upgrading will help.

---

### Post by dcheek2 on 2017-02-03
Unfortunately no, it did not help. Do you think this will be fixed in 17.04?

---

### Post by wildmanne39 on 2017-02-03
I have no way of knowing but it is not likely, tomorrow I will go through all the information I can find on the bug and we can try some of the work arounds to see if it will help your issue.

---

### Post by dcheek2 on 2017-02-04
what information do you have on this bug?

---

### Post by wildmanne39 on 2017-02-04
First suggestion is to go into your router and the setting to 802.11g only (not 802.11n) then save the settings and router should reboot.

---

### Post by dcheek2 on 2017-02-04
I have a mikrotik router, there is no easy way to change wireless standard from one to another, is there a particular feature of N that causes problems? channel-width or mutiplexing maybe?

---

### Post by wildmanne39 on 2017-02-04
The N feature itself cases issues sometime's with certain drivers, how hard is it to change that setting just to see if it helps? There should be a drop down menu if that option is available.

From one of the bug reports:
> Forcing the router into 802.11g mode does, at least at a cursory glance, seem to mitigate the halting problem, but speeds remain abysmal.


---

### Post by dcheek2 on 2017-02-04
I changed it, and it seemed to recover faster when it did start to drop. Still coming back out of order and stopping for tacos on the way.

---

### Post by wildmanne39 on 2017-02-04
I am still researching the bug reports to see what else we can try.

---

### Post by wildmanne39 on 2017-02-04
You can also research the error by googling:
> ping: sendmsg: Network is unreachable+ubuntu

---

### Post by dcheek2 on 2017-02-04
is there a particular bug report that is of interest?

seems to me that this is a driver issue, specifically something causing the wireless card to stop responding. One thing I haven't checked is whether the wireless card is still passing Layer 2 before it drops.

---

### Post by dcheek2 on 2017-02-04
> **dcheek2 said:**
> One thing I haven't checked is whether the wireless card is still passing Layer 2 before it drops.

It does appear to be dropping its MAC address after about 30 sec.

I checked the router log and found LOTs of DEAUTH requests from the wireless card, like it is going to sleep but doesnt want to reconnect.

---

### Post by dcheek2 on 2017-02-14
bump...any more ideas?

---

### Post by dcheek2 on 2017-03-15
SUCCESS!!!

after reinstalling the latest rtlwifi module, I installed WICD, removed network-manager, rebooted and everything works!

I ran a ping for over 1 hour to my router and didn't drop a single packet.

---

