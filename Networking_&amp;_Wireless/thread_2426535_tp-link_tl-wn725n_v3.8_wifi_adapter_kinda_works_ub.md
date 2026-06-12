---
title: "tp-link tl-wn725n v3.8 wifi adapter kinda works ubuntu 19.4"
date: 2019-09-10
forum: Networking &amp; Wireless
---

### Post by geoiii on 2019-09-10
[LEFT][COLOR=#242729][FONT=Arial]this adapter has great strong fast connection.
I am having 2 issues.
On Fresh boot I have to unplug, replug and it connects instantly but then I get this message 
"Network service discovery disabled. Your current network has a .local domain, which is not recommended and incompatible with the avahi network service discovery. The service has been disabled."
I still have good internet connection. Does anyone know what is going on?
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Thanks in advance
:guitar:
[/FONT][/COLOR][/LEFT]

---

### Post by overdrank on 2019-09-10
Hi and welcome, I may not be able to help much, but if you post the results of this _[link]("https://ubuntuforums.org/showthread.php?t=370108")_. Then I can at least bump you to the top of the page to be seen. :D

---

### Post by geoiii on 2019-09-13
hope i did this right


```
########## wireless info START ##########

Report from: 13 Sep 2019 10:45 CDT -0500

Booted last: 13 Sep 2019 00:00 CDT -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco

##### kernel ############################

Linux 5.0.0-27-generic #28-Ubuntu SMP Tue Aug 20 19:53:07 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company MCP61 Ethernet [103c:2a99]
    Kernel driver in use: forcedeth

##### lsusb #############################

Bus 001 Device 008: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 006: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 001 Device 005: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 004: ID 14cd:6600 Super Top M110E PATA bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

r8188eu               430080  0
lib80211               16384  1 r8188eu
cfg80211              671744  1 r8188eu
mxm_wmi                16384  1 nouveau
wmi                    28672  2 mxm_wmi,nouveau

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s7: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp0s7' [IF1]> brd <MAC address>
4: wlx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 192.168.1.139/24 brd 192.168.1.255 scope global dynamic noprefixroute wlx<IF from MAC [IF2]>
       valid_lft 84876sec preferred_lft 84876sec
    inet6 2600:1700:6830:e970::45/128 scope global dynamic noprefixroute 
       valid_lft 2590479sec preferred_lft 603279sec
    inet6 2600:1700:6830:e970:dc8f:8162:9892:cac3/64 scope global temporary dynamic 
       valid_lft 3574sec preferred_lft 3574sec
    inet6 2600:1700:6830:e970:13d6:bbc7:8a79:886/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3574sec preferred_lft 3574sec
    inet6 fe80::8c2d:de70:c1ce:8606/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp0s7    no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"ATT9244gDS"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ATT9244gDS' [AC1]>   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry ff   RTS thr ff   Fragment thr ff
          Encryption key:****-****-****-****-****-****-****-****   Security mode pen
          Power Management ff
          Link Quality=94/100  Signal level=62/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

default via 192.168.1.254 dev wlx<IF from MAC [IF2]> proto dhcp metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF2]> scope link metric 1000 
192.168.1.0/24 dev wlx<IF from MAC [IF2]> proto kernel scope link src 192.168.1.139 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']

nameserver 127.0.0.53
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       826     1  0 10:16 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8188EUS 802.11n Wireless Network Adapter
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4.4/1-4.4:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     ATT9244gDS
GENERAL.CON-UUID:                       3bccaa51-261b-48ff-a1a2-41a2a5acd2e5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.1.139/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.254, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[2]:                        dad_wait_time = 0
DHCP4.OPTION[3]:                        dhcp_lease_time = 86400
DHCP4.OPTION[4]:                        dhcp_message_type = 5
DHCP4.OPTION[5]:                        dhcp_rebinding_time = 75600
DHCP4.OPTION[6]:                        dhcp_renewal_time = 43200
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[8]:                        domain_name = attlocal.net
DHCP4.OPTION[9]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[10]:                       expiry = 1568474397
DHCP4.OPTION[11]:                       ip_address = 192.168.1.139
DHCP4.OPTION[12]:                       network_number = 192.168.1.0
DHCP4.OPTION[13]:                       next_server = 0.0.0.0
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       requested_domain_search = 1
DHCP4.OPTION[18]:                       requested_host_name = 1
DHCP4.OPTION[19]:                       requested_interface_mtu = 1
DHCP4.OPTION[20]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_root_path = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
DHCP4.OPTION[28]:                       requested_subnet_mask = 1
DHCP4.OPTION[29]:                       requested_time_offset = 1
DHCP4.OPTION[30]:                       requested_wpad = 1
DHCP4.OPTION[31]:                       routers = 192.168.1.254
DHCP4.OPTION[32]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[33]:                       time_offset = -18000
DHCP4.OPTION[34]:                       vendor_unknown_3561 = 4:6:30:30:31:45:34:36:5:f:32:37:37:34:32:37:35:37:37:33:32:33:30:30:38:6:6:4e:56:47:35:39:39
DHCP4.OPTION[35]:                       vivso = 0:0:d:e9:21:4:6:30:30:31:45:34:36:5:f:32:37:37:34:32:37:35:37:37:33:32:33:30:30:38:6:6:4e:56:47:35:39:39
IP6.ADDRESS[1]:                         2600:1700:6830:e970::45/128
IP6.ADDRESS[2]:                         2600:1700:6830:e970:dc8f:8162:9892:cac3/64
IP6.ADDRESS[3]:                         2600:1700:6830:e970:13d6:bbc7:8a79:886/64
IP6.ADDRESS[4]:                         fe80::8c2d:de70:c1ce:8606/64
IP6.GATEWAY:                            fe80::fe51:a4ff:fe32:7e00
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = 2600:1700:6830:e970::/60, nh = fe80::fe51:a4ff:fe32:7e00, mt = 600
IP6.ROUTE[3]:                           dst = 2600:1700:6830:e970::/64, nh = ::, mt = 600
IP6.ROUTE[4]:                           dst = ::/0, nh = fe80::fe51:a4ff:fe32:7e00, mt = 20600
IP6.ROUTE[5]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[6]:                           dst = 2600:1700:6830:e970::45/128, nh = ::, mt = 600
IP6.DNS[1]:                             2600:1700:6830:e970::1
DHCP6.OPTION[1]:                        dad_wait_time = 0
DHCP6.OPTION[2]:                        dhcp6_client_id = 0:4:48:6f:2c:8:ff:8a:0:e5:91:94:1b:b7:89:ab:13:57
DHCP6.OPTION[3]:                        dhcp6_domain_search = attlocal.net.
DHCP6.OPTION[4]:                        dhcp6_name_servers = 2600:1700:6830:e970::1
DHCP6.OPTION[5]:                        dhcp6_server_id = 0:1:0:1:23:ee:3:32:fc:51:a4:32:7e:0
DHCP6.OPTION[6]:                        iaid = 94:8a:d5:9b
DHCP6.OPTION[7]:                        ip6_address = 2600:1700:6830:e970::45
DHCP6.OPTION[8]:                        ip6_prefixlen = 128
DHCP6.OPTION[9]:                        life_starts = 1568117961
DHCP6.OPTION[10]:                       max_life = 2592000
DHCP6.OPTION[11]:                       preferred_life = 604800
DHCP6.OPTION[12]:                       rebind = 483840
DHCP6.OPTION[13]:                       renew = 302400
DHCP6.OPTION[14]:                       requested_dhcp6_client_id = 1
DHCP6.OPTION[15]:                       requested_dhcp6_domain_search = 1
DHCP6.OPTION[16]:                       requested_dhcp6_name_servers = 1
DHCP6.OPTION[17]:                       starts = 1568117961
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3bccaa51-261b-48ff-a1a2-41a2a5acd2e5 | ATT9244gDS

GENERAL.DEVICE:                         enp0s7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP61 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp0s7' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               3 (limited)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/net/enp0s7
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
ATT9244gDS     <MAC 'ATT9244gDS' [AC1]>  Infra  1     2412 MHz  16 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     *      
tlbadba        <MAC 'tlbadba' [AC3]>  Infra  1     2412 MHz  16 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2       no             
--             <MAC '' [AC7]>  Infra  6     2437 MHz  44 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2       no             
CGNM-CD28      <MAC 'CGNM-CD28' [AC2]>  Infra  1     2412 MHz  16 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no             
CGNM-8F88      <MAC 'CGNM-8F88' [AC5]>  Infra  6     2437 MHz  16 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no             
CGNM-5228      <MAC 'CGNM-5228' [AC6]>  Infra  6     2437 MHz  16 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no             
--             <MAC '' [AC4]>  Infra  1     2412 MHz  44 Mbit/s  23      &#9602;___  --         no             
Matt's Router  <MAC 'Matt's Router' [AC8]>  Infra  11    2462 MHz  16 Mbit/s  23      &#9602;___  WPA2       no             

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
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ATT9244gDS.nmconnection]] (600 root)
[connection] id=ATT9244gDS | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=ATT9244gDS
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s7    no frequency information.

wlx<IF from MAC [IF2]>  11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s7    Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'ATT9244gDS' [AC1]>
                    ESSID:"ATT9244gDS"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key n
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=88/100  Signal level=62/100  
          Cell 02 - Address: <MAC 'CGNM-CD28' [AC2]>
                    ESSID:"CGNM-CD28"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key n
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=46/100  
          Cell 03 - Address: <MAC 'tlbadba' [AC3]>
                    ESSID:"tlbadba"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key n
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=74/100  
          Cell 04 - Address: <MAC '' [AC4]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key ff
                    Bit Rates:108 Mb/s
                    Quality=0/100  Signal level=23/100  
          Cell 05 - Address: <MAC 'CGNM-8F88' [AC5]>
                    ESSID:"CGNM-8F88"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key n
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=43/100  
          Cell 06 - Address: <MAC 'CGNM-5228' [AC6]>
                    ESSID:"CGNM-5228"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key n
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=42/100  
          Cell 07 - Address: <MAC '' [AC7]>
                    ESSID:""
                    Protocol:IEEE 802.11gn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key n
                    Bit Rates:108 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=56/100  
          Cell 08 - Address: <MAC 'Matt's Router' [AC8]>
                    ESSID:"Matt's Router"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key n
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=23/100  
          Cell 09 - Address: <MAC 'tl79c0c4' [AC9]>
                    ESSID:"tl79c0c4"
                    Protocol:IEEE 802.11gn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key n
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=26/100  

##### module infos ######################

[r8188eu]
filename:       /lib/modules/5.0.0-27-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     D9CAC39C699DBD238A62CAA
depends:        cfg80211,lib80211
staging:        Y
retpoline:      Y
intree:         Y
name:           r8188eu
vermagic:       5.0.0-27-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:12:1A:1E:
        64:1F:2A:03:9B:20:12:38:E0:CA:9F:8F:4A:6F:3F:6D:95:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:97:54:AF:4E:9C6:0D:29:18:A1:BD:
        053:EA:AB:F8:F3:75:F1:6F7:65:04:12:06:2E:2D4:9C:2A:AE:
        31:138:47:42:02:62:4B:43:96:80:86:BC:BD:C1:82:89:A9:7A:5E:
        2A:7C:8D:14:91:21:6A1:938:AD:9E:B4:32:ADE:6A:C1:00:57:
        2B:3E:B9:B9:80:A4:25:AA:09:07:B5:23:A2:2A4:8B:78:9E:F2:59:
        9A:482:03:5D:55:C5:2C:A3:EE:CF:4D:A2:8D:9B:3E:4A:AA:12:F8:
        B7:12:AB:1B:3CA:44:1A:28D:2F:60:A6:CB:C3:2A:40:08:37:08:
        71:73:6E:6E:F5:77:B6:3B:17:6C:24:2C:BA:1D:73:CC:32:1D:E9:76:
        C7:BC:70:12:52:EC:E3:1DD:A4:72:6F:EF:00:EF:6A:9A:B4:5C:B8:
        02:5C:AD:2B0:4F:0C:88:E1:BB:CA6:39:7B:20:A5:57:8C:4D:6B:
        03:2F:4E:6E:EB:47:B0:55:7E:36:37:3D:06:8B:39:5C:BF:39:39:51:
        75:B2:C6:B3:45:C5:74:3C:7F:24:9C:92:AF:1D:2B:61:92:52:40:70:
        BF:3B1:A3:CD:E7:73:17:C5:E6:73:5F:88:28:F5:62:18:46:06:FA:
        17:29:B5:B6:A8:F9:69:A2:49:720:73:3E:B8:64:65:8A:5C:87:56:
        2B:F9:60:56:54:7C:97:8C4:67:17:69:A3:99:99:23:11:02:4F:A6:
        BB:C9:49:E9:6B:32:EF:42:40:97:E9:FC:97:E6:B6:75:83:56:0F:EE:
        11:11:1A:A1:1A:E2:F3:AE:65:FE:7F:FC:33:F1:1C:B1:B6:A7:43:44:
        36:28:CF:0B:8E:AE:E2:29:55:6E:9B:79:0A:F0:6E:A1:17:7A:3A:F8:
        47:C7:5F:1E:C7:8B:11:3D6:28:EC:44:B3:96:40:E5:9C:5A:35:CA:
        59:38:16:2F:34:C7:7B:50:69:87B:04:A3:BB:5C:1D:64:F5:C4:8B:
        A1:9E:33:19:7B:5D:C5:0D:42:52:ED:06:E2:4E:6F:A5:E4:20:9B:43:
        908:29:85:07:88:5B:B9:6B:84:CC:5D2:7E:1A:A7:F7:51:8B:84:
        361:97:46E:82:C3:22:3A:F5:85:65:14:41:09:37:20:C6D:0E:
        03:9D:7C:82:1A:85:EA:2A:A4:64:07:235:34:AF:FC2:41:3B:13:
        91:8C:41:22:C9:CA:3A:EA:19:20:8E:F7:2F:E0:3D:74A:E2:60:51:
        F5:FD:E9:80:5C:F3:5E:01:129:B1:A0:95:99:34:28:30:89:53:A8:
        81
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0isable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)
parm:           monitor_enable:Enable monitor interface (default: false) (bool)

[cfg80211]
filename:       /lib/modules/5.0.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8F0CAF5346FF71FCE9CB198
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-27-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:12:1A:1E:
        64:1F:2A:03:9B:20:12:38:E0:CA:9F:8F:4A:6F:3F:6D:95:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:15:61:112:54:64:1E:67:7F:50A:
        FC:4C:75:70:50:E8:26:9B0:A9C:B6:03:93:52:88:42:F2:6A:16:
        50:85:45:E6:C1:AD:74:E7:3F:67:2B:C8:3D:07:8E:9C:87:7A:C3:1C:
        94:76:E7:5B:BD:17:A5:2B:59:15D:56:23:C5:F2:7E:9E:32:79:FD:
        6E:CE:15:BF:5E:0C:F55D:0C:741:0F:45:04:A7:EF:AE:0A:11:
        09:FD:6B:8C:84:751:2A:40:5A:07:41:A3:A3:11:49:00:24:A7:E2:
        AC:5E:EE:E5:47:EE:B5:ACF:3A:96:03:74:EC:0C:0D:39:E2:96:4B:
        CE:84:1BC:C0:38:86:8A:92:1BE:59:49:AF:A6:B8:45:30F:13:
        EE:B3:E96:CE:9D:03:A0:2D:2C:77:82A:FD:C4:45:AB:0E:8C:9C:
        0F:6A:77:3B:1A:86:4D:0E:AA:B8:87:37:57:3D:FD:FB:BA:00:24:76:
        5F:9A:21:E4:6D:93:67:13:53:CA:81:59:C7:0D:29:71:CBC:A9:8C:
        02:F7:7D:86:3D:1E:FC:F7:92:B5:45:2F:CF:C2:02:7B:F09:84:6B:
        68:22:67:A9:3E:97:23B:F9:97:05:4B:CE:10:A6:B8:EE:C7:6A:EE:
        80:28:15:E8:68:EF:B68:EE:13:5A:4E:42:85:56:5A:B1:90:98:22:
        9B:05:C8E:43:AF:85:B8:90:C5:7AE:AA:60:01:E8:82:0E:61:9F:
        269:98:26:C2:A8:FA:B3:81:B4:88:EC:BF:65:8E:7D:100:50:1F:
        6E:BC:25:A9:91:A4:B3:F7:B1:85:67:E6:E1:A74:AF:E7:C3:23:33:
        E1:FE:19:03:B4:84:4B:91:9A:7F:C9:6A:63:33:94:BB:75:86:2C:66:
        AA:C8:4D:B6:80:E8:7C:8E:8E:1F0:5E:1F:A8:98:56:33:69:08:9F:
        9A:F7:56:53:16:3F:B1:90:C7:1F:76:04:B9D:A1:F4:8B:A1:64:31:
        AC:72:4D:EF:66:1B:C5:51:08:E8:0D:19:8A:C4:5E:59:4A:BB:1D:2E:
        E5:12:A8:7E:5B:BD:14:11:C4:06:93:3C:27:27:18:7E:7C:9E:66D:
        19:329:929:F7:FD:AC:779:0C:E9:FA:5D:AE:244:9E:C4:BB:
        88:EE:767:71:86:83:7B:B23:7A:31:B4:3A:E6DF:52:85:63:
        5F:F4:93:BB:5B:76:30:40:3F:33:E0:AA:3F:61:FD:62:7D:329:77:
        73:AF:47:3D:95:9F:B8:4CF:AF:66:75:A2:C4:1E:B5:4B:24:FD:90:
        FC
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
monitor_enable: N
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   38.956863] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[   38.956869] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found
[   41.850180] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[   43.213449] r8188eu 1-4.4:1.0 wlx00e04c818802: renamed from wlan0
[   82.978860] forcedeth 0000:00:07.0 enp0s7: MSI enabled
[   82.979119] forcedeth 0000:00:07.0 enp0s7: no link during initialization
[  257.311834] r8188eu 1-4.4:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[  260.826198] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############
```

---

### Post by Yellow Pasque on 2019-09-14
For error message, try reading: [https://ubuntuforums.org/showthread.php?t=2353783](https://ubuntuforums.org/showthread.php?t=2353783)

---

