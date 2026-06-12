---
title: "Cant install wifi adapter."
date: 2017-02-19
forum: Networking &amp; Wireless
---

### Post by rashhashan on 2017-02-19
I tried to follow [this ]("https://ubuntuforums.org/showthread.php?t=2235778") troubleshooting because its the same Netgear A6100 as mine, I get to the very end and i get this error.

monk@monk-desktop:~/Downloads/rtl8812AU_8821AU_linux-master$ sudo modprobe 8812au
modprobe: FATAL: Module 8812au not found in directory /lib/

---

### Post by howefield on 2017-02-19
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by wildmanne39 on 2017-02-19
That driver is from 2014, so unless you are using 14.04 then it is to old to work on a newer version of ubuntu.

Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

---

### Post by rashhashan on 2017-02-19
my computer is stuck in an applying changes loop right now >.<

---

### Post by wildmanne39 on 2017-02-19
Applying what changes? are  you trying to install updates?

---

### Post by rashhashan on 2017-02-19
> **wildmanne39 said:**
> Applying what changes? are  you trying to install updates?

Please ignore the other wireless adapter, I don't have a wired connection so I have to use a friends wireless adapter untill I can get mine to work. I have to give it back soon.

Bus 010 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
is what I need help with.

```


########## wireless info START ##########

Report from: 19 Feb 2017 19:14 CST -0600

Booted last: 19 Feb 2017 00:00 CST -0600

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

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:8505]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 002: ID 083a:4505 Accton Technology Corp. SMCWUSB-G 802.11bg
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 004 Device 002: ID 046d:c24a Logitech, Inc. G600 Gaming Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 002: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

mac80211              757760  1 zd1211rw
eeepc_wmi              16384  0
cfg80211              581632  2 mac80211,zd1211rw
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
mxm_wmi                16384  0
wmi                    16384  2 asus_wmi,mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 10356  bytes 764090 (764.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10356  bytes 764090 (764.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx0013f778e57c: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.198  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 2601:940:c100:c650::cd6b  prefixlen 128  scopeid 0x0<global>
        inet6 2601:940:c100:c650:e03e:7361:e42a:bc4a  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::8146:cf2e:70bd:a8da  prefixlen 64  scopeid 0x20<link>
        inet6 2601:940:c100:c650:edaf:f8f5:4af1:f19d  prefixlen 64  scopeid 0x0<global>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 11874  bytes 9421572 (9.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9511  bytes 1467162 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlx0013f778e57c  IEEE 802.11  ESSID:"HOME-C831-2.4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'HOME-C831-2.4' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/100  Signal level=60/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:202   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlx0013f778e57c
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlx0013f778e57c

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.al.comcast.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1030     1  0 19:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx0013f778e57c
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         SMC
GENERAL.PRODUCT:                        USB2.0 WLAN
GENERAL.DRIVER:                         zd1211rw
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.2/usb3/3-4/3-4:1.0/net/wlx0013f778e57c
GENERAL.IP-IFACE:                       wlx0013f778e57c
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     HOME-C831-2.4
GENERAL.CON-UUID:                       13ee50e9-b2fd-477a-b6c2-ac595db7d8ee
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   13ee50e9-b2fd-477a-b6c2-ac595db7d8ee | HOME-C831-2.4
IP4.ADDRESS[1]:                         10.0.0.198/24
IP4.GATEWAY:                            10.0.0.1
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.al.comcast.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 10.0.0.198
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 10.0.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 10.0.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 10.0.0.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.al.comcast.net
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1488157726
DHCP4.OPTION[21]:                       host_name = monk-desktop
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 10.0.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 604800
IP6.ADDRESS[1]:                         2601:940:c100:c650::cd6b/128
IP6.ADDRESS[2]:                         2601:940:c100:c650:edaf:f8f5:4af1:f19d/64
IP6.ADDRESS[3]:                         2601:940:c100:c650:e03e:7361:e42a:bc4a/64
IP6.ADDRESS[4]:                         fe80::8146:cf2e:70bd:a8da/64
IP6.GATEWAY:                            fe80::68ee:96ff:fe2e:c834
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:f6:c9:39:8e:4e:ac:88:82:83:40:c7:b8:4b:a8:44:61
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        rebind = 483840
DHCP6.OPTION[5]:                        max_life = 604800
DHCP6.OPTION[6]:                        preferred_life = 604800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1487549865
DHCP6.OPTION[10]:                       dhcp6_status_code = success All addresses were assigned.
DHCP6.OPTION[11]:                       ip6_address = 2601:940:c100:c650::cd6b
DHCP6.OPTION[12]:                       ip6_prefixlen = 64
DHCP6.OPTION[13]:                       renew = 302400
DHCP6.OPTION[14]:                       starts = 1487549865
DHCP6.OPTION[15]:                       iaid = f7:78:e5:7c
DHCP6.OPTION[16]:                       dhcp6_server_id = 0:1:0:1:20:34:70:d9:f6:40:19:7e:6f:91

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (P8 series motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/enp2s0
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

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
xfinitywifi    <MAC 'xfinitywifi' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  --         no        
--             <MAC '' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HOME-C831-2.4  <MAC 'HOME-C831-2.4' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
--             <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
--             <MAC '' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  38      &#9602;&#9604;__  --         no        
xfinitywifi    <MAC 'xfinitywifi' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  38      &#9602;&#9604;__  --         no        
--             <MAC '' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
HOME-8898-2.4  <MAC 'HOME-8898-2.4' [AC14]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
HOME-3675-2.4  <MAC 'HOME-3675-2.4' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
--             <MAC '' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
tony           <MAC 'tony' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
Sagittarius78  <MAC 'Sagittarius78' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  28      &#9602;___  WPA1 WPA2  no        
--             <MAC '' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  26      &#9602;___  WPA1 WPA2  no        
HOME-DE95-2.4  <MAC 'HOME-DE95-2.4' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  23      &#9602;___  WPA1 WPA2  no        
xfinitywifi    <MAC 'xfinitywifi' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  --         no        
xfinitywifi    <MAC 'xfinitywifi' [AN16]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  --         no        

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

[[/etc/NetworkManager/system-connections/HOME-C831-2.4]] (600 root)
[connection] id=HOME-C831-2.4 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HOME-C831-2.4
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

lo        no frequency information.

enp2s0    no frequency information.

wlx0013f778e57c  11 channels in total; available frequencies :
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

enp2s0    Interface doesn't support scanning.

Channel occupancy:

      7   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      5   APs on   Frequency:2.462 GHz (Channel 11)

wlx0013f778e57c  Scan completed :
          Cell 01 - Address: <MAC 'HOME-C831-2.4' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/100  Signal level=58/100  
                    Encryption key:on
                    ESSID:"HOME-C831-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000310d4db52f
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xfinitywifi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/100  Signal level=57/100  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000310d81e180
                    Extra: Last beacon: 148ms ago
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/100  Signal level=44/100  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000310d7ec140
                    Extra: Last beacon: 128ms ago
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/100  Signal level=59/100  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000310d81e180
                    Extra: Last beacon: 176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'tony' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/100  Signal level=30/100  
                    Encryption key:on
                    ESSID:"tony"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000304aa5671d1
                    Extra: Last beacon: 328ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/100  Signal level=30/100  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000304aa599b67
                    Extra: Last beacon: 120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/100  Signal level=38/100  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d7e7ea6b
                    Extra: Last beacon: 1364ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC '' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/100  Signal level=24/100  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ec08d180
                    Extra: Last beacon: 1996ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'xfinitywifi' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/100  Signal level=26/100  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ec08d180
                    Extra: Last beacon: 1972ms ago
          Cell 10 - Address: <MAC 'HOME-3675-2.4' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/100  Signal level=37/100  
                    Encryption key:on
                    ESSID:"HOME-3675-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f4d2b385b
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/100  Signal level=36/100  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000082bfc2580c
                    Extra: Last beacon: 408ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'xfinitywifi' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/100  Signal level=37/100  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000082bfc70b10
                    Extra: Last beacon: 76ms ago
          Cell 13 - Address: <MAC '' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/100  Signal level=36/100  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f4d2b5180
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'HOME-8898-2.4' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/100  Signal level=37/100  
                    Encryption key:on
                    ESSID:"HOME-8898-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000082bfc6f0d2
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

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

[   11.401661] zd1211rw 3-4:1.0 wlx0013f778e57c: renamed from wlan0
[   20.197955] IPv6: ADDRCONF(NETDEV_UP): wlx0013f778e57c: link is not ready
[   20.642016] zd1211rw 3-4:1.0: firmware version 4725
[   20.720295] IPv6: ADDRCONF(NETDEV_UP): wlx0013f778e57c: link is not ready (repeated 2 times)
[   23.054855] wlx0013f778e57c: authenticate with <MAC 'HOME-C831-2.4' [AC1]>
[   23.086078] wlx0013f778e57c: send auth to <MAC 'HOME-C831-2.4' [AC1]> (try 1/3)
[   23.290180] wlx0013f778e57c: send auth to <MAC 'HOME-C831-2.4' [AC1]> (try 2/3)
[   23.298929] wlx0013f778e57c: authenticated
[   23.302180] wlx0013f778e57c: associate with <MAC 'HOME-C831-2.4' [AC1]> (try 1/3)
[   23.311454] wlx0013f778e57c: RX AssocResp from <MAC 'HOME-C831-2.4' [AC1]> (capab=0x431 status=0 aid=5)
[   23.311794] wlx0013f778e57c: associated
[   23.311840] IPv6: ADDRCONF(NETDEV_CHANGE): wlx0013f778e57c: link becomes ready
[   27.351593] wlx0013f778e57c: disassociated from <MAC 'HOME-C831-2.4' [AC1]> (Reason: 2)
[   28.355169] wlx0013f778e57c: authenticate with <MAC 'HOME-C831-2.4' [AC1]>
[   28.386650] wlx0013f778e57c: send auth to <MAC 'HOME-C831-2.4' [AC1]> (try 1/3)
[   28.397254] wlx0013f778e57c: authenticated
[   28.398436] wlx0013f778e57c: associate with <MAC 'HOME-C831-2.4' [AC1]> (try 1/3)
[   28.401251] wlx0013f778e57c: RX AssocResp from <MAC 'HOME-C831-2.4' [AC1]> (capab=0x431 status=0 aid=5)
[   28.402385] wlx0013f778e57c: associated

########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-02-20
Please do the following after you make sure if you have secure boot that it is turned off in the bios:
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
sudo dpkg -i rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
```
Reboot

Found here:
[https://ubuntuforums.org/showthread.php?t=2326038](https://ubuntuforums.org/showthread.php?t=2326038)

---

### Post by rashhashan on 2017-02-20
```
monk@monk-desktop:~$ sudo dpkg -i rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
[sudo] password for monk: 
Selecting previously unselected package rtl8812au-dkms.
(Reading database ... 203476 files and directories currently installed.)
Preparing to unpack rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb ...
Unpacking rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu2) ...
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu2) ...
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
First Installation: checking all kernels...
Building only for 4.8.0-37-generic
Building initial module for 4.8.0-37-generic
Error! Bad return status for module build on kernel: 4.8.0-37-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information.

```

Do I need to roll back to 16.04? If so how can I without a complete reinstall?

---

### Post by wildmanne39 on 2017-02-20
Please post what this log says:
```
Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information.
```
Thanks

---

### Post by rashhashan on 2017-02-20
> **wildmanne39 said:**
> Please post what this log says:
```
Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information.
```
Thanks

I don't know how to

---

### Post by wildmanne39 on 2017-02-20
I believe this should show the file:
```
cat /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log
```

---

### Post by rashhashan on 2017-02-20
> **wildmanne39 said:**
> I believe this should show the file:
```
cat /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log
```

the website won't let me post it, it says a security token is missing

> **wildmanne39 said:**
> I believe this should show the file:
```
cat /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log
```

this was at the bottom

```
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/ioctl_cfg80211.o' failed
make[2]: *** [/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/ioctl_cfg80211.o] Error 1
Makefile:1491: recipe for target '_module_/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build' failed
make[1]: *** [_module_/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-38-generic'
Makefile:1457: recipe for target 'modules' failed
make: *** [modules] Error 2

```

[http://pastebin.com/g4MGZDLm](http://pastebin.com/g4MGZDLm)

---

### Post by wildmanne39 on 2017-02-20
There are a lot of warnings, I will see if I can find another driver, please run the following command so we can make sure you have the needed packages installed to compile applications and drivers because this error.
```
make: *** [modules] Error 2
```
is often caused by missing required packages.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Thanks

---

### Post by rashhashan on 2017-02-20
> **wildmanne39 said:**
> There are a lot of warnings, I will see if I can find another driver, please run the following command so we can make sure you have the needed packages installed to compile applications and drivers because this error.
```
make: *** [modules] Error 2
```
is often caused by missing required packages.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Thanks
after running that command all went well till the bottom read 
```

ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtl8812au-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.8.0-38-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information

```

---

### Post by wildmanne39 on 2017-02-20
Sorry it took me so long to get back to you I have been researching trying to find a newer driver, I found one and it compile with no errors or warnings on my system.

Go here and download the 4.3.14 driver:
[https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU)

Before you run the commands please shutdown your computer unplug your other adapter and boot back up
.
Then drag it to your desktop and right click extract here then do:
```
cd Desktop/rtl8812AU-driver-4.3.14
make
sudo make install
sudo modprobe -v 8812au
```
Thanks

---

### Post by rashhashan on 2017-02-21
> **wildmanne39 said:**
> Sorry it took me so long to get back to you I have been researching trying to find a newer driver, I found one and it compile with no errors or warnings on my system.

Go here and download the 4.3.14 driver:
[https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU)

Before you run the commands please shutdown your computer unplug your other adapter and boot back up
.
Then drag it to your desktop and right click extract here then do:
```
cd Desktop/rtl8812AU-driver-4.3.14
make
sudo make install
sudo modprobe -v 8812au
```
Thanks

Success! You are the best! Thank you!

---

### Post by wildmanne39 on 2017-02-21
When there is a kernel upgrade I believe you will have to compile the driver again for the new kernel, there is a package that is made to automate the process but from the directions I did not believe you are ready just yet to edit driver files before compiling so I did not even attempt to include that method.

If it stops working after an upgrade do:

```
cd Desktop/rtl8812AU-driver-4.3.14
make clean
make
sudo make install
modprobe rtl8812AU
```
Glad it is working.
Enjoy!

---

### Post by ZorroCotroco on 2017-03-11
rtl8812au-dkms build fails on ubuntu 16.04.2   kernel 4.8.0-41
 
 
 wifi adapter: TP-LINK T4UH.
 
 
 You can install a patched for the 4.8 kernel driver from Yakkety this way:
 
 [HTML]
     wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu5_all.deb
     sudo dpkg -i rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu5_all.deb
[/HTML]
unplug/replug the usb device, reconnect and magic  ;). Enjoy

---

