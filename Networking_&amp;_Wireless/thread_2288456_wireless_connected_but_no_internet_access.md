---
title: "wireless connected but no internet access"
date: 2015-07-27
forum: Networking &amp; Wireless
---

### Post by truongkechun on 2015-07-27
Hi, i'm using ubuntu 15.04 vivid, I'm connected to the wifi but when I open Firefox, it said "Server not found", I open Software Updater it said Failed to download, basically no internet access.
But I've used ubuntu 14 before and I could use the wifi normally without any error.
Also my windows and phones work without any error too.
I've clean reinstall several time and I have the same problem.

Here is some information about my situation:

My wifi device is: Huawei HG8045A

```
$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr a4:ba:db:d7:88:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:563292 (563.2 KB)  TX bytes:563292 (563.2 KB)

wlan0     Link encap:Ethernet  HWaddr c4:46:19:0f:ee:bf  
          inet addr:192.168.100.9  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::c646:19ff:fe0f:eebf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32258604 (32.2 MB)  TX bytes:2616017 (2.6 MB)
```

```
$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0
sf@SFLap:~$ ping -c3 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_seq=1 ttl=53 time=423 ms
64 bytes from 91.189.94.12: icmp_seq=2 ttl=53 time=422 ms
64 bytes from 91.189.94.12: icmp_seq=3 ttl=53 time=421 ms

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 421.879/422.802/423.965/0.868 ms
```

```
$ ping -c3 ubuntuforums.org

ping: unknown host ubuntuforums.org


```

Here is some code from some bro's script:
```

########## wireless info START ##########

Report from: 27 Jul 2015 22:12 ICT +0700

Booted last: 28 Jul 2015 04:42 ICT +0700

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:31:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl

13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0447]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 014: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 002 Device 011: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 010: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 009: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 013: ID 0951:1665 Kingston Technology 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6461 Microdia 
Bus 001 Device 003: ID 2635:0601  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6369280  0 
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
cfg80211              540672  1 wl
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
wmi                    20480  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.100.9  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55703 errors:0 dropped:0 overruns:0 frame:18398
          TX packets:47028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60247797 (60.2 MB)  TX bytes:4920972 (4.9 MB)
          Interrupt:17 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"DinhMoc"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'DinhMoc' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       662     1  0 21:43 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter (Inspiron M5010 / XPS 8300)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:12:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     DinhMoc
GENERAL.CON-UUID:                       83386bbf-439a-4e3a-af79-1d490216c8cf
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   83386bbf-439a-4e3a-af79-1d490216c8cf | DinhMoc
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.100.9/24, gw = 192.168.100.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1438268643
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 259200
DHCP4.OPTION[14]:                       ip_address = 192.168.100.9
DHCP4.OPTION[15]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       routers = 192.168.100.1
DHCP4.OPTION[18]:                       broadcast_address = 192.168.100.255
DHCP4.OPTION[19]:                       domain_name_servers = 8.8.8.8 8.8.4.4
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       requested_host_name = 1
DHCP4.OPTION[26]:                       network_number = 192.168.100.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.100.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = fe80::1
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:c7:92:bc:95:8:e8:4f:2d:fe:10
DHCP6.OPTION[4]:                        requested_dhcp6_server_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:53:f0:f9:49:84:c4:33:23:9c:3e:c1:69:6a:d2:6e:d2

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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:13:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Nothing         <MAC 'Nothing' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1       no        
Comtrend        <MAC 'Comtrend' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
Free            <MAC 'Free' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
TP-LINK_883BA0  <MAC 'TP-LINK_883BA0' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
LeChung         <MAC 'LeChung' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  WPA1       no        
DinhMoc         <MAC 'DinhMoc' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/DinhMoc]] (600 root)
[connection] id=DinhMoc | type=wifi
[wifi] ssid=DinhMoc | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vananh]] (600 root)
[connection] id=vananh | type=wifi
[wifi] ssid=vananh | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Ho_Chi_Minh (based on set time zone)

country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 40), (N/A, 20), (N/A)
    (5250 - 5330 @ 40), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 40), (N/A, 27), (0 ms), DFS
    (57240 - 65880 @ 2160), (N/A, 40), (N/A), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'DinhMoc' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-11 dBm  
                    Encryption key:on
                    ESSID:"DinhMoc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Comtrend' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Comtrend"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'LeChung' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"LeChung"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'TP-LINK_883BA0' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_883BA0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Nothing' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Nothing"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-21-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

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

[cfg80211]
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  991.453754] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  999.714122] CPU: 1 PID: 378 Comm: wl_event_handle Tainted: P           OE  3.19.0-21-generic #21-Ubuntu
[  999.714251]  [<ffffffffc08809fb>] wl_notify_roaming_status+0xcb/0x150 [wl]
[  999.714318]  [<ffffffffc087d75a>] wl_event_handler+0x6a/0x230 [wl]
[  999.714417]  [<ffffffffc087d6f0>] ? wl_free_wdev.isra.23+0x80/0x80 [wl]
[ 1535.378159] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

I don't understand but sometime I refresh the page in firefox and it work but very short, about a minute and it said "server not found" again.

If you need any information please tell me, I will provide asap.
Big thanks in advance.

---

### Post by Bucky Ball on 2015-07-27
Welcome. Click on Network Manager> Click 'Edit' and edit the wireless connection> Click the IPv6 tab> set IPv6 to ignore> click OK> Reboot.

Any different?

---

### Post by praseodym on 2015-07-27
Change the encryption mode to pure WPA2-AES (CCMP) in your router and to a fixed channel. Check the router manual for that

---

### Post by yannis2 on 2015-07-27
another tip is to change the name of wireless

---

### Post by truongkechun on 2015-07-28
@[[COLOR=#000000]praseodym[/COLOR]]("http://ubuntuforums.org/member.php?u=1411497") did you mean change these?
change encryption mode to AES

[IMG]http://i.imgur.com/A5rHd8L.png[/IMG]


Here change channel to what? I see it list from 1 to 13


[IMG]http://i.imgur.com/HRr24Zk.png[/IMG]

---

### Post by Bucky Ball on 2015-07-28
Change the second screenshot to channel 6 and the encryption mode in the first screen shot to WPA2-AES.

For future reference, please attach large screenshots rather than insert them in the body of you post. 'Go Advanced' or 'Adv Reply' and use the paperclip icon in the toolbar. Thanks.

---

### Post by truongkechun on 2015-07-28
YES, i did as @Bucky Ball said and it's WORKEDDDDDD!!! The solution in #2. But why IPv6 messing my wifi here?
p.s: yes big thanks for the attachment tip.

---

