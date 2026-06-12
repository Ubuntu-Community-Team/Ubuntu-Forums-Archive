---
title: "Wifi problem with the wpa_supplicant 2.4 on Ubuntu 17.10"
date: 2018-01-21
forum: Networking &amp; Wireless
---

### Post by l.gosh on 2018-01-21
The Wifi in my ASUS x552C was working fine at home on the Ubuntu  17.10, but as soon as I came to the university and connected to their  Wifi by following some procedures, with the last procedure of having run  this file that I downloaded from the university's netstart page. When I turn on the laptop, the wifi works for 1 minute extremely slowly, and then disconnects. Then I have to do the
  ```
sudo service network-manager restart

```

 in order to get it working, but then it disconnects again in 1 minute and the same thing happens over and over again.

Here is the wireless script output that I found on this forum: 

```


########## wireless info START ##########

Report from: 22 Jan 2018 20:47 +04 +0400

Booted last: 22 Jan 2018 00:00 +04 +0400

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, irqpoll, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e074]
    Kernel driver in use: mt7630e

04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8168

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0e8d:763f MediaTek Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
mac80211              778240  1 mt7630e
cfg80211              610304  2 mac80211,mt7630e
mxm_wmi                16384  1 nouveau
wmi                    24576  4 asus_wmi,wmi_bmof,mxm_wmi,nouveau
video                  40960  3 asus_wmi,nouveau,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp4s0f2: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 25  base 0x5000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3171  bytes 243461 (243.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3171  bytes 243461 (243.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0f0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.253.113.2  netmask 255.252.0.0  broadcast 10.255.255.255
        inet6 fe80::5635:30ff:fe14:2b27  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 23672  bytes 4510826 (4.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3872  bytes 521037 (521.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp4s0f2  no wireless extensions.

wlp3s0f0  IEEE 802.11  ESSID:"AUBGSTUDENTS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'AUBGSTUDENTS' [AN1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-190 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:4   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.252.1.1      0.0.0.0         UG    600    0        0 wlp3s0f0
10.252.0.0      0.0.0.0         255.252.0.0     U     600    0        0 wlp3s0f0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0f0

##### resolv.conf #######################

nameserver 127.0.0.53

search ppc.aubg.bg

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2880     1  6 20:47 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0f0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MEDIATEK Corp.
GENERAL.PRODUCT:                        MT7630e 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         mt7630e
GENERAL.DRIVER-VERSION:                 4.13.0-25-generic
GENERAL.FIRMWARE-VERSION:               112.3
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0f0
GENERAL.IP-IFACE:                       wlp3s0f0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     AUBGSTUDENTS
GENERAL.CON-UUID:                       4bb60789-d209-41ef-8c7c-e635af5460cb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     6 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4,3,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c8c4560e-64bd-413f-9bb6-f026febef726 | AUBGSTUDENTS
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   4bb60789-d209-41ef-8c7c-e635af5460cb | AUBGSTUDENTS
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   db2a5840-265b-4c6c-b83e-87fd5883f7ef | AUBGSetUpPPC
IP4.ADDRESS[1]:                         10.253.113.2/14
IP4.GATEWAY:                            10.252.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.252.3.1
IP4.DNS[2]:                             10.252.2.1
IP4.DOMAIN[1]:                          ppc.aubg.bg
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 7200
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = studin-lng140-2
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 0.0.0.0
DHCP4.OPTION[12]:                       expiry = 1516661233
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 10.252.1.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 10.253.113.2
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = ppc.aubg.bg
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 10.255.255.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 21600
DHCP4.OPTION[25]:                       domain_name_servers = 10.252.3.1 10.252.2.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.252.0.0
DHCP4.OPTION[28]:                       network_number = 10.252.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 10.252.3.1
IP6.ADDRESS[1]:                         fe80::5635:30ff:fe14:2b27/64
IP6.GATEWAY:                            --

GENERAL.DEVICE:                         enp4s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8168
GENERAL.DRIVER-VERSION:                 8.044.02-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.2/net/enp4s0f2
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

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X  yes     * 
AUBGLABS        <MAC 'AUBGLABS' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGGuests      <MAC 'AUBGGuests' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WEP          no        
AUBGOCC         <MAC 'AUBGOCC' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGGuests      <MAC 'AUBGGuests' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WEP          no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2         no        
AUBGFIN         <MAC 'AUBGFIN' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2         no        
AUBGSetUpPPC    <MAC 'AUBGSetUpPPC' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WEP          no        
AUBGGuests      <MAC 'AUBGGuests' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WEP          no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN16]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGLABS        <MAC 'AUBGLABS' [AN17]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN18]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN19]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSetUpPPC    <MAC 'AUBGSetUpPPC' [AN20]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WEP          no        
AUBGLABS        <MAC 'AUBGLABS' [AN21]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN22]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN23]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2         no        
AUBGFIN         <MAC 'AUBGFIN' [AN24]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN25]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN26]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN27]>  Infra  6     2437 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN28]>  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN29]>  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGGuests      <MAC 'AUBGGuests' [AN30]>  Infra  1     2412 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WEP          no        
AUBGGuests      <MAC 'AUBGGuests' [AN31]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WEP          no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN32]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN33]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGLABS        <MAC 'AUBGLABS' [AN34]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN35]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN36]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN37]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN38]>  Infra  11    2462 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN39]>  Infra  11    2462 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN40]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2         no        
AUBGGuests      <MAC 'AUBGGuests' [AN41]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WEP          no        
AUBGGuests      <MAC 'AUBGGuests' [AN42]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WEP          no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN43]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN44]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN45]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN46]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN47]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN48]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN49]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGLABS        <MAC 'AUBGLABS' [AN50]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGLABS        <MAC 'AUBGLABS' [AN51]>  Infra  6     2437 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN52]>  Infra  6     2437 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN53]>  Infra  6     2437 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN54]>  Infra  11    2462 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN55]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGLABS        <MAC 'AUBGLABS' [AN56]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFS          <MAC 'AUBGFS' [AN57]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN58]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN59]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSetUpPPC    <MAC 'AUBGSetUpPPC' [AN60]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WEP          no        
AUBGFS          <MAC 'AUBGFS' [AN61]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN62]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGGuests      <MAC 'AUBGGuests' [AN63]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WEP          no        
AUBGSetUpPPC    <MAC 'AUBGSetUpPPC' [AN64]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WEP          no        
AUBGGuests      <MAC 'AUBGGuests' [AN65]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WEP          no        
AUBGGuests      <MAC 'AUBGGuests' [AN66]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WEP          no        
AUBGSetUpPPC    <MAC 'AUBGSetUpPPC' [AN67]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WEP          no        
AUBGSTUDENTS    <MAC 'AUBGSTUDENTS' [AN68]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN69]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN70]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2         no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN71]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2         no        
AUBGFS          <MAC 'AUBGFS' [AN72]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGFIN         <MAC 'AUBGFIN' [AN73]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN74]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN75]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2         no        
AUBGPrivPC      <MAC 'AUBGPrivPC' [AN76]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGLABS        <MAC 'AUBGLABS' [AN77]>  Infra  11    2462 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGLABS        <MAC 'AUBGLABS' [AN78]>  Infra  11    2462 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN79]>  Infra  11    2462 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGOCC         <MAC 'AUBGOCC' [AN80]>  Infra  11    2462 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AUBGSetUpPPC    <MAC 'AUBGSetUpPPC' [AN81]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  WEP          no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN82]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2         no        
AUBGSetUpPPC    <MAC 'AUBGSetUpPPC' [AN83]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WEP          no        
AUBGServiceOCC  <MAC 'AUBGServiceOCC' [AN84]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2         no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AUBGSetUpPPC]] (600 root)
[connection] id=AUBGSetUpPPC | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AUBGSetUpPPC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AUBGSTUDENTS]] (600 root)
[connection] id=AUBGSTUDENTS | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=AUBGSTUDENTS
[802-1x] system-ca-certs=false
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NATIA]] (600 root)
[connection] id=NATIA | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NATIA
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AUBGSTUDENTS.save]] (600 root)
[connection] id=AUBGSTUDENTS | type=wifi | permissions=
[wifi] bssid=<MAC 'AUBGSTUDENTS' [AN33]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=AUBGSTUDENTS
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Asia/Tbilisi (based on set time zone)

global
country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp4s0f2  no frequency information.

wlp3s0f0  13 channels in total; available frequencies :
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

wlp3s0f0  Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

enp4s0f2  Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.13.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-25-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-25-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
bss_entries_limit: 1000
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
blacklist r8169

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
options iwlwifi 11n_disable=1 wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/r8168-dkms.conf]
alias    pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*    r8168
alias    pci:v000010ECd00008168sv*sd*bc*sc*i*            r8168

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 1133.820262] wlp3s0f0: associated
[ 1133.820278] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready
[ 1140.563076] wlp3s0f0: disconnect from AP <MAC 'AUBGSTUDENTS' [AN1]> for new auth to <MAC 'AUBGSTUDENTS' [AN39]>
[ 1140.564465] ===>rt2800_sta_remove:MT7630
[ 1140.569456] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0 (repeated 2 times)
[ 1140.596287] wlp3s0f0: authenticate with <MAC 'AUBGSTUDENTS' [AN39]>
[ 1140.608315] wlp3s0f0: send auth to <MAC 'AUBGSTUDENTS' [AN39]> (try 1/3)
[ 1140.616827] wlp3s0f0: authenticated
[ 1140.620224] wlp3s0f0: associate with <MAC 'AUBGSTUDENTS' [AN39]> (try 1/3)
[ 1140.708038] wlp3s0f0: associate with <MAC 'AUBGSTUDENTS' [AN39]> (try 2/3)
[ 1140.713503] wlp3s0f0: RX AssocResp from <MAC 'AUBGSTUDENTS' [AN39]> (capab=0x411 status=0 aid=2)
[ 1140.713518] ===>rt2800_sta_add:MT7630
[ 1140.713548] ===>rt2800_sta_add:MT7630   wcid=33
[ 1140.731751] wlp3s0f0: associated
[ 1146.920407] ===>rt2800_sta_remove:MT7630
[ 1146.925416] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0 (repeated 2 times)
[ 1147.289431] wlp3s0f0: authenticate with <MAC 'AUBGSTUDENTS' [AN1]>
[ 1147.300298] wlp3s0f0: send auth to <MAC 'AUBGSTUDENTS' [AN1]> (try 1/3)
[ 1147.310248] wlp3s0f0: authenticated
[ 1147.312391] wlp3s0f0: associate with <MAC 'AUBGSTUDENTS' [AN1]> (try 1/3)
[ 1147.318582] wlp3s0f0: RX AssocResp from <MAC 'AUBGSTUDENTS' [AN1]> (capab=0x411 status=0 aid=1)
[ 1147.318594] ===>rt2800_sta_add:MT7630
[ 1147.318624] ===>rt2800_sta_add:MT7630   wcid=33
[ 1147.329215] wlp3s0f0: associated

########## wireless info END ############


```

  Here are the logs that I think are connected to wifi:

  > **ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0**

  **nl80211: Unexpected encryption algorithm 5**

  **dbus: Failed to construct signal**

  **dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none**

  **((src/devices/nm-device.c:1452)): assertion '' failed**

  For 3 days already, I have been searching all over the web for the answer, and found out that it might be because of the  "wpasupplicant 2.4" not accepting weak certificates or something like  that... Since I am a rookie to the ubuntu, as well as this forum so I'm  sorry if I won't be as specific as needed, but I will add more  information as soon as someone suggests it.


  The output of the dpkg -l network-manager:
  ```
$ dpkg -l network-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-==============================================================
ii  network-manager              1.8.4-1ubuntu3      amd64               network management framework (daemon and userspace tools)

```

 The output of the dpkg -l wpasupplicant:

  ```
~$ dpkg -l wpasupplicant
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-==============================================================
ii  wpasupplicant                2.4-0ubuntu10       amd64               client support for WPA and WPA2 (IEEE 802.11i)

```

 The version of the wpasupplicant shows up as 2.4 even though last  night I tried upgrading to 2.6 by downloading the 2.6 .tar file from the  [internet]("https://w1.fi/wpa_supplicant/"), and following the instructions for **Compilation & Installation** from [this]("https://thangamaniarun.wordpress.com/2014/03/16/how-to-compile-wpa_supplicant-wit-wi-fi-direct-support-on-ubuntu-android/")  website. However, I was getting errors while doing that, so I had to  search internet for more and more stuff, and eventually when I did the **make && make install**,  it ran without an error, so that made me think that the installation  was successful. But, the version still shows up the same in Synaptic and  in dpkg. 

  Any thoughts, leads, information would be EXTREMELY appreciated,  because I have not slept normally for 3 days, because the university  starts tomorrow and I wanted to have my laptop prepared... 


  lspci output about network adapters:

  ```
03:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)

```

 The /etc/NetworkManager/system-connections/-=SSID=- file:
  ```
[connection]
id=-=ID=-
uuid=-=UUID=-
type=wifi
autoconnect-priority=20
permissions=

[wifi]
mac-address-blacklist=
mode=infrastructure
ssid=-=SSID=-

[wifi-security]
auth-alg=open
key-mgmt=wpa-eap

[802-1x]
eap=peap;
identity=-=myAcc@Xxx.Xxx.Xxx=-
password=-=myPassword=-
phase2-auth=mschapv2

[ipv4]
dns-search=
method=auto

[ipv6]
dns-search=
method=auto

```
 (I didn't want to go back to Windows, since I really loved Ubuntu  after the first day of install, even though I had weeks worth of error  fixing and even though I am a newbie.).

The  source of the file (SecureW2_JoinNow.run) that I downloaded from the university's website is:
  ```
#!/bin/sh

die () {
    [ ! -z "$1" ] && echo "Fatal: $1"
    [ ! -z "$tmpdir" -a -d "$tmpdir" ] && ${RM} -Rf "$tmpdir"
    exit 1
}

missing () {
    echo 'Executable `'$1'` seems to be missing, not executable or cannot be located with `which`.'
    echo ''
    echo 'Please install this program using your distribution-specific package manager (e.g. `apt-get` or `yum`).'
    echo 'If this does not solve the issue, you can try editing this script by hand to provide the proper'
    echo 'executable locations, or request your network administrator to contact SecureW2 Support.'
    die
}

findutil () {
    for u in "$@"; do \
        p="$("${WHICH}" "$u" 2> /dev/null)"
        [ ! -z "$p" ] && break
    done
    [ -z "$p" ] && missing "$1"
    return 0
}

which --skip-alias which > /dev/null 2>&1
if [ $? -eq 0 ]; then \
    WHICH="$(which --skip-alias which)"
else
    WHICH="$(which which)"
fi

[ ! -x "${WHICH}" ] && missing which

findutil mkdir      && MKDIR="$p"
findutil rm         && RM="$p"
findutil tar        && TAR="$p"
findutil gzip       && GZIP="$p"
findutil pwd        && PWD="$p"
findutil sed        && SED="$p"
findutil readlink   && READLINK="$p"
findutil python \
         python2 \
         python3    && PYTHON="$p"

tmpdir="/tmp/securew2-joinnow-$$.tmp"
archive="$(${READLINK} -f "$0")"

${MKDIR} -p "$tmpdir" || die "Error creating temporary directory $tmpdir"
cd $tmpdir || die "Error switching working directory to $tmpdir"
${SED} '0,/^#ARCHIVE#$/d' "$archive" | ${GZIP} -d | ${TAR} x || die "Error extracting embedded archive"
${PYTHON} main.py "$@"
retval=$?
${RM} -Rf "$tmpdir"
exit $retval

#ARCHIVE#
And tons of numbers and symbols...

```

  

  THANK YOU!

---

