---
title: "Wifi puzzle?"
date: 2017-07-30
forum: Networking &amp; Wireless
---

### Post by eezacque on 2017-07-30
Running Ubuntu 16.04 with broadcom driver 6.30.223.248+bdcom-0ubuntu8 on Asus Z97-PRO (wifi ac) motherboard.

Runs like a charm, but a few times per hour the network connection gets stuck, with no throughput at all. This always recovers by itself in a minute or so, or immediately, when I reconnect wifi. In this situation, wifi remains connected, and the windows laptop here doesn't have this issue, so I don't think the problem is in the router. There is nothing in the logs which helps me out, usually there is nothing posted in the logs when **** happens.

Could some please give me a pointer on how to approach this? 
Any logging in the broadcom driver I can switch on?
Help is greatly appreciated!

---

### Post by Hadaka on 2017-07-30
Hi, please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
~~Or Follow this guide..
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
Thanks.

---

### Post by eezacque on 2017-07-31
> **Hadaka said:**
> Hi, please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt

Adding wireless-info.txt in two parts

```


########## wireless info PART 1 ##########

Report from: 31 Jul 2017 11:30 CEST +0200

Booted last: 31 Jul 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, acpi_enforce_resources=lax, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    DeviceName:  Onboard LAN
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I218-V [1043:85c4]

05:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. BCM4352 802.11ac Wireless Network Adapter [1043:855c]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 003: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 004: ID 1bcf:0002 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
wl                   6365184  0
cfg80211              565248  1 wl
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback
auto tap0
iface tap0 inet manual 
pre-up ip tuntap add tap0 mode tap user izak
pre-up ip addr add 192.168.0.1/24 dev tap0
up ip link set dev tap0 up
post-up ip route del 192.168.0.1/24 dev tap0
post-up ip route add 192.168.0.121/32 dev tap0
post-down ip link del dev tap0

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:dfe00000-dfe20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:5710262 (5.7 MB)  TX bytes:5710262 (5.7 MB)

tap0      Link encap:Ethernet  HWaddr <MAC 'tap0' [IF2]>  
          inet addr:192.168.0.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'tap0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:375598 (375.5 KB)  TX bytes:511299 (511.2 KB)

virbr0    Link encap:Ethernet  HWaddr <MAC address>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0-nic Link encap:Ethernet  HWaddr <MAC 'virbr0-nic' [IF3]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF4]>  
          inet addr:192.168.178.15  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF4]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156130 errors:0 dropped:0 overruns:0 frame:89420
          TX packets:126691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169208203 (169.2 MB)  TX bytes:18059337 (18.0 MB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

virbr0    no wireless extensions.

tap0      no wireless extensions.

virbr0-nic  no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Ziggo701DC"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Ziggo701DC' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 tap0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
192.168.178.0   0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 208.67.222.222
nameserver 208.67.220.220

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1032     1  0 Jul30 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         virbr0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0
GENERAL.IP-IFACE:                       virbr0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     virbr0
GENERAL.CON-UUID:                       b6da22a9-5c45-47cc-9928-82c1e0bacabf
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b6da22a9-5c45-47cc-9928-82c1e0bacabf | virbr0
IP4.ADDRESS[1]:                         192.168.122.1/24
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4352 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF4]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:01.0/0000:05:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ziggo701DC
GENERAL.CON-UUID:                       007c7918-be73-4142-a7c3-1036a759cebc
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     52 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   007c7918-be73-4142-a7c3-1036a759cebc | Ziggo701DC
IP4.ADDRESS[1]:                         192.168.178.15/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.178.1
DHCP4.OPTION[10]:                       expiry = 1501524437
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.178.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.178.15
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = dynamic.ziggo.nl
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.178.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 36000
DHCP4.OPTION[23]:                       domain_name_servers = 89.101.251.228 89.101.251.229
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.178.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.178.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan0' [IF4]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
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

GENERAL.DEVICE:                         tap0
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'tap0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/tap0
GENERAL.IP-IFACE:                       tap0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.ADDRESS[1]:                         192.168.0.1/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::<IP6 'tap0' [IF2]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         virbr0-nic
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'virbr0-nic' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         41 (The device's existing connection was assumed)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0-nic
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Ziggo701DC        <MAC 'Ziggo701DC' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2         yes     * 
Rodermond         <MAC 'Rodermond' [AC4]>  Infra  3     2422 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2    no        
gast_netwerk      <MAC 'gast_netwerk' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2         no        
Sunshine          <MAC 'Sunshine' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1         no        
UniFi             <MAC 'UniFi' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        
Ubiquiti          <MAC 'Ubiquiti' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        
Omni20_Setup_80D  <MAC 'Omni20_Setup_80D' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
ZwarteHaAs        <MAC 'ZwarteHaAs' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2         no        
Ziggo             <MAC 'Ziggo' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA2 802.1X  no        
TP-LINK_69E8      <MAC 'TP-LINK_69E8' [AN10]>  Infra  2     2417 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2    no        
Ziggo17408        <MAC 'Ziggo17408' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
VFNL-ED9908       <MAC 'VFNL-ED9908' [AN12]>  Infra  4     2427 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2    no        
Ziggo             <MAC 'Ziggo' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Sitecom]] (600 root)
[connection] id=Sitecom | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF4]> | mac-address-blacklist= | ssid=Sitecom
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ziggo701DC]] (600 root)
[connection] id=Ziggo701DC | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF4]> | mac-address-blacklist= | ssid=Ziggo701DC
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/WRT54G-SAT]] (600 root)
[connection] id=WRT54G-SAT | type=802-11-wireless
[802-11-wireless] ssid=WRT54G-SAT | mac-address=<MAC 'wlan0' [IF4]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sitecom_3113f0]] (600 root)
[connection] id=Sitecom_3113f0 | type=wifi
[wifi] ssid=Sitecom_3113f0 | mac-address=<MAC 'wlan0' [IF4]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dd-wrt_vap]] (600 root)
[connection] id=dd-wrt_vap | type=wifi
[wifi] ssid=dd-wrt_vap | mac-address=<MAC 'wlan0' [IF4]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Amsterdam (based on set time zone)

country NL: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

virbr0    no frequency information.

tap0      no frequency information.

virbr0-nic  no frequency information.

eth0      no frequency information.



```

---

### Post by eezacque on 2017-07-31
```

########## wireless info PART 2 ##########

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
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Channel 108 : 5.54 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

tap0      Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Ziggo701DC' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Ziggo701DC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ZwarteHaAs' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ZwarteHaAs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC 'Ziggo' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Ziggo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'Rodermond' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Rodermond"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Ubiquiti' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Ubiquiti"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'UniFi' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UniFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'gast_netwerk' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"gast_netwerk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Sunshine' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Sunshine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-83-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-83-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     48C96882CCDC964173BE1D1
depends:        
intree:         Y
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

coretemp

coretemp

coretemp

coretemp

coretemp

coretemp

coretemp
nct6775

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF4]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[41089.134880] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41089.135892] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41110.188909] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=32311 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41208.404926] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=19842 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41215.085095] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41215.086098] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41223.726938] [iptables] IN=wlan0 OUT= MAC= SRC=192.168.178.15 DST=224.0.0.251 LEN=169 TOS=0x00 PREC=0x00 TTL=255 ID=26174 DF PROTO=UDP SPT=5353 DPT=5353 LEN=149 
[41305.733620] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=63627 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41341.136944] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41341.139062] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41402.240232] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=24586 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41467.088269] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41467.089829] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41500.665873] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=11313 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41593.139758] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41593.140852] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41597.439073] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=37296 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41663.784392] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=165 TOS=0x00 PREC=0x00 TTL=255 ID=60404 PROTO=UDP SPT=5353 DPT=5353 LEN=145 
[41663.885666] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=295 TOS=0x00 PREC=0x00 TTL=255 ID=65018 PROTO=UDP SPT=5353 DPT=5353 LEN=275 
[41719.090073] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41719.091165] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41762.149092] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=49981 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41845.142818] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41845.143807] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41859.557906] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=116 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41955.792294] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=1181 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[41971.093146] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[41971.094244] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42052.042504] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=63107 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42097.146880] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42097.147895] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42149.501052] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=13642 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42223.098148] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42223.099182] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42247.702685] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=22281 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42345.490218] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=57000 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42349.047650] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42349.048614] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42443.800304] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=37256 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42475.101225] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42475.102203] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42541.016381] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=6240 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42601.049416] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42601.052526] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42637.486411] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=25601 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42707.938944] [iptables] IN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=28085 PROTO=UDP SPT=137 DPT=137 LEN=58 
[42727.102054] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42727.103134] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42734.647546] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=37311 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42762.425475] [iptables] IN=tap0 OUT= MAC= SRC=192.168.0.1 DST=224.0.0.251 LEN=169 TOS=0x00 PREC=0x00 TTL=255 ID=42813 DF PROTO=UDP SPT=5353 DPT=5353 LEN=149 
[42762.425503] [iptables] IN=virbr0 OUT= MAC= SRC=192.168.122.1 DST=224.0.0.251 LEN=169 TOS=0x00 PREC=0x00 TTL=255 ID=29504 DF PROTO=UDP SPT=5353 DPT=5353 LEN=149 
[42853.052439] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42853.053524] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42859.212998] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=59087 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42873.346385] [iptables] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF4]>:68:94:23:e7:01:df:08:00 SRC=185.63.144.1 DST=192.168.178.15 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=0 DF PROTO=TCP SPT=443 DPT=60796 WINDOW=0 RES=0x00 RST URGP=0 
[42956.248292] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=32553 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[42979.105092] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[42979.106237] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43054.361650] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=22928 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43105.055417] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43105.056360] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43150.885250] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=9689 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43196.023421] [iptables] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF4]>:68:94:23:e7:01:df:08:00 SRC=192.229.163.180 DST=192.168.178.15 LEN=83 TOS=0x00 PREC=0x00 TTL=56 ID=31270 DF PROTO=TCP SPT=443 DPT=53670 WINDOW=300 RES=0x00 ACK PSH FIN URGP=0 
[43196.395224] [iptables] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF4]>:68:94:23:e7:01:df:08:00 SRC=192.229.163.180 DST=192.168.178.15 LEN=83 TOS=0x00 PREC=0x00 TTL=56 ID=56133 DF PROTO=TCP SPT=443 DPT=53668 WINDOW=296 RES=0x00 ACK PSH FIN URGP=0 
[43199.570269] [iptables] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF4]>:68:94:23:e7:01:df:08:00 SRC=192.229.163.180 DST=192.168.178.15 LEN=83 TOS=0x00 PREC=0x00 TTL=56 ID=24017 DF PROTO=TCP SPT=443 DPT=53672 WINDOW=306 RES=0x00 ACK PSH FIN URGP=0 
[43231.107962] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43231.108981] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43249.246145] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=48693 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43307.935878] [iptables] IN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=5921 PROTO=UDP SPT=137 DPT=137 LEN=58 
[43346.357312] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=4879 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43357.058361] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43444.515259] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=58527 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43483.110898] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43483.112053] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43542.505949] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=4837 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43609.061251] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43609.062246] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43640.566702] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=19828 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43701.036766] [iptables] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF4]>:68:94:23:e7:01:df:08:00 SRC=216.58.221.163 DST=192.168.178.15 LEN=355 TOS=0x00 PREC=0x00 TTL=48 ID=2619 PROTO=TCP SPT=443 DPT=34110 WINDOW=349 RES=0x00 ACK PSH URGP=0 
[43735.113873] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43735.114882] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43738.919892] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=6014 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43835.224424] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=33953 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43861.064257] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43861.065245] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43907.932803] [iptables] IN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=46840 PROTO=UDP SPT=137 DPT=137 LEN=58 
[43932.916146] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=38076 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[43987.116899] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[43987.117857] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[44030.282417] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=36979 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[44113.067172] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[44128.699786] [iptables] IN=tap0 OUT= MAC=01:00:5e:00:00:fb:00:aa:00:60:00:01:08:00 SRC=192.168.0.2 DST=224.0.0.251 LEN=204 TOS=0x00 PREC=0x00 TTL=255 ID=14848 PROTO=UDP SPT=5353 DPT=5353 LEN=184 
[44150.547642] [iptables] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF4]>:68:94:23:e7:01:df:08:00 SRC=31.13.91.2 DST=192.168.178.15 LEN=129 TOS=0x08 PREC=0x40 TTL=88 ID=62780 DF PROTO=TCP SPT=443 DPT=37750 WINDOW=647 RES=0x00 ACK PSH FIN URGP=0 
[44158.132063] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

### Post by johndough2 on 2017-07-31
Hi

Thoughts, rather than solutions.

Are you backing anything up over your network than could cause a slowdown?
Your lease times are long?

---

### Post by Hadaka on 2017-07-31
Hi, from your wireless report there are a few things being reported that may be causing you issues.
First and foremost is the wl driver for the broadcom card..
```
*broadcom driver 6.30.223.248+bdcom-0ubuntu8 on Asus Z97-PRO (wifi ac)*
```
Broadcom makes a great wifi card and it performs well with windows and apple boxes but no so much
with linux due to lack of manufacture support. You would do well to replace the wifi with a fully supported
intel or other fully linux supported card. Mean time, in your router configuration verify it is set for b/g/n
not just n only. While in the router configuration also set your ssid IPv4 settings to wpa2 aes ccmp...NO tkip.

Next is the output from ' iwconfig'..it is showing..#Power Management  on  Let's turn that off ..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

Lastly is IPv6..if you are not using it, or dont plan to in the near future..let's disable that.
#From your favorite editor add these 3 lines
#sudo gedit /etc/sysctl.conf
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
#Save and close
#From terminal
```
sudo sysctl -p
```
Then. as a test, turn your iptables and ufw off and see if these go away..
##### dmesg ############################
[41089.134880] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1
Thanks.

---

### Post by BenginM on 2017-08-01
Hiya 

Hadaka trying his best troubleshooting this , But if ["this answer"]("https://askubuntu.com/questions/718553/wi-fi-dropping-intermittently-on-dell-xps13-2015-cfg80211-dmesg-warning-and") doesn't convince you , i don't what will!

---

### Post by eezacque on 2017-08-01
> **johndough2 said:**
> Are you backing anything up over your network than could cause a slowdown?
Your lease times are long?

There are no backups, downloads or uploads going on.
The lease time is 36000s, and dhcp requests do not coincide with the problems reported.

Thanks for thinking along!

---

### Post by eezacque on 2017-08-01
> **Hadaka said:**
> Hi, from your wireless report there are a few things being reported that may be causing you issues.
First and foremost is the wl driver for the broadcom card..
```
*broadcom driver 6.30.223.248+bdcom-0ubuntu8 on Asus Z97-PRO (wifi ac)*
```
Broadcom makes a great wifi card and it performs well with windows and apple boxes but no so much
with linux due to lack of manufacture support. You would do well to replace the wifi with a fully supported
intel or other fully linux supported card. 


That is an option, but I will not switch hardware until I know hardware is the problem (the broadcom wifi is integrated in my mother board)

> 
Mean time, in your router configuration verify it is set for b/g/n
not just n only. While in the router configuration also set your ssid IPv4 settings to wpa2 aes ccmp...NO tkip.


The router is set to g/n; b/g/n is not supported.
WPA2 encryption was set to AES-TKIP, I will switch it to AES.

> 
Next is the output from ' iwconfig'..it is showing..#Power Management  on  Let's turn that off ..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```


Done.

> 
Lastly is IPv6..if you are not using it, or dont plan to in the near future..let's disable that.
#From your favorite editor add these 3 lines
#sudo gedit /etc/sysctl.conf
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
#Save and close
#From terminal
```
sudo sysctl -p
```


I disabled IPv6 through 'Edit connections' but I followed your suggestion to be sure.
Done.

> 
Then. as a test, turn your iptables and ufw off and see if these go away..
##### dmesg ############################
[41089.134880] [iptables] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:94:23:e7:01:df:08:00 SRC=192.168.178.1


These do go away.

I will let you know whether your suggestions make a difference.

---

### Post by eezacque on 2017-08-01
> **BenginM said:**
> Hadaka trying his best troubleshooting this , But if ["this answer"]("https://askubuntu.com/questions/718553/wi-fi-dropping-intermittently-on-dell-xps13-2015-cfg80211-dmesg-warning-and") doesn't convince you , i don't what will!

Your quote refers to wifi drops accompanied by dmesg warnings.
This does not apply to my case.

---

### Post by BenginM on 2017-08-01
> **eezacque said:**
> Your quote refers to wifi drops accompanied by dmesg warnings.
This does not apply to my case.

well *If you don't get the picture* then *readjust the frame*! I can show you many Broadcom upstream bugs in Windows,MacOSX , and GNU/linux , but i'll let you go on with the puzzle .. !

---

### Post by wildmanne39 on 2017-08-01
I have been working with wireless issues for six years now here in the forum and I have seen many issues with broadcom but almost none are unfixable and once fixed broadcom are usually very reliable devices, while intel is a good device there is probably no reason to have to replace his broadcom device unless it is defective, I have owned 3 over the years and one did go out after 6 years of use and I replaced it with an usb adapter.

I will take a better look later when I can if chili555 or another broadcom expert does not stop by, just from a quick look I think the driver version you are using has been troublesome in the past and always needed upgrading but that is just from memory.

---

### Post by eezacque on 2017-08-03
> **Hadaka said:**
> Hi, from your wireless report there are a few things being reported that may be causing you issues.


The problem hasn't puzzled me since I applied your fixes.
Cannot tell whether it was Power Management or TKIP that hampered wifi; when I'm in the mood, I'll do some more experiments.

Thanks a lot!!!

---

### Post by Hadaka on 2017-08-03
That is great ! Glad that helped.
Thank you for marking your thread solved.

---

