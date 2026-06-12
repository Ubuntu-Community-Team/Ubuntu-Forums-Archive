---
title: "Upgraded Ubuntu 17.04 to 17.10 now wifi does not work"
date: 2017-10-05
forum: Networking &amp; Wireless
---

### Post by kvisslav on 2017-10-05
Hi everybody,

Recently (two days ago) update Ubuntu 17.04 to 17.10 and got the problem that nether LAN, no WiFi works. Tried receipts from previous posts ([https://ubuntuforums.org/showthread.php?t=2358610&p=13633808#post13633808](https://ubuntuforums.org/showthread.php?t=2358610&p=13633808#post13633808)) - but it doesn't helps for me.
Below information from commands, asked to execute for tc
Did I something wrong? Thanks

[[IMG]http://i.piccy.info/i9/7b6eef7b20ae0ae2f31de5199378be5c/1507196457/43741/1185184/IMG_20171005_010022_500.jpg[/IMG]]("http://piccy.info/view3/11641274/346e4cd70ade96b4cd58bfc19c354340/")[[IMG]http://i.piccy.info/a3/2017-10-05-09-40/i9-11641274/472x354-r/i.gif[/IMG]]("http://i.piccy.info/a3c/2017-10-05-09-40/i9-11641274/472x354-r")
[[IMG]http://i.piccy.info/i9/7363a1a363358bbb8f0d64da7db9f522/1507196540/41500/1185184/IMG_20171005_010031_500.jpg[/IMG]]("http://piccy.info/view3/11641278/f54e1a824eabe807af6f96d11fb144c1/")[[IMG]http://i.piccy.info/a3/2017-10-05-09-42/i9-11641278/472x354-r/i.gif[/IMG]]("http://i.piccy.info/a3c/2017-10-05-09-42/i9-11641278/472x354-r")
[[IMG]http://i.piccy.info/i9/1ba8924c4489695418f399939e5556e5/1507196730/23203/1185184/IMG_20171005_010059_500.jpg[/IMG]]("http://piccy.info/view3/11641285/88f11bcc8534a59be754f40291614c3a/")[[IMG]http://i.piccy.info/a3/2017-10-05-09-45/i9-11641285/472x354-r/i.gif[/IMG]]("http://i.piccy.info/a3c/2017-10-05-09-45/i9-11641285/472x354-r")
[[IMG]http://i.piccy.info/i9/ee4484d1b75eff6d786e37952344b54c/1507196752/20312/1185184/IMG_20171005_010106_500.jpg[/IMG]]("http://piccy.info/view3/11641286/ac16cbab5185c6c57713f0e1d7b75dbe/")[[IMG]http://i.piccy.info/a3/2017-10-05-09-45/i9-11641286/472x354-r/i.gif[/IMG]]("http://i.piccy.info/a3c/2017-10-05-09-45/i9-11641286/472x354-r")

---

### Post by wildmanne39 on 2017-10-05
*Thread moved to **Ubuntu Development Version for a better fit**.*

You do know that you have installed a version of Ubuntu that is under development right which means it is not even ready for release yet.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, please do not post images of commands from the terminal.

Thanks

---

### Post by wildmanne39 on 2017-10-05
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by kvisslav on 2017-10-05
Thank you for clarification. Done. I did it from phone, hope that without new problems...

```

########## wireless info START ##########

Report from: 05 Oct 2017 21:40 EEST +0300

Booted last: 05 Oct 2017 00:00 EEST +0300

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu Artful Aardvark (development branch)
Release:	17.10
Codename:	artful

##### kernel ############################

Linux 4.13.0-12-generic #13-Ubuntu SMP Sat Sep 23 03:40:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

ubuntu

##### lspci #############################

04:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. AR9285 Wireless Network Adapter (PCI-Express) [105b:e016]
	Kernel driver in use: ath9k

05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Acer Incorporated [ALI] AR8132 Fast Ethernet [1025:0212]
	Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:000a A4Tech Co., Ltd. Optical Mouse Opto 510D / OP-620D
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2717:ff40  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              462848  2 ath9k,ath9k_common
acer_wmi               20480  0
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
sparse_keymap          16384  1 acer_wmi
mac80211              778240  1 ath9k
cfg80211              610304  4 mac80211,ath9k,ath,ath9k_common
mxm_wmi                16384  0
wmi                    24576  2 acer_wmi,mxm_wmi
video                  40960  2 acer_wmi,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::226:22ff:fe6b:ce8f  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 75  bytes 9220 (9.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 102  bytes 10986 (10.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 1  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 612  bytes 46516 (46.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 612  bytes 46516 (46.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.5  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::eee:e6ff:feb6:e71  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 133  bytes 10670 (10.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 86  bytes 11395 (11.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp5s0    no wireless extensions.

wlp4s0    IEEE 802.11  ESSID:"android"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'android' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:80   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    20100  0        0 enp5s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    20600  0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp5s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp5s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       567     1  0 21:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8132 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/enp5s0
GENERAL.IP-IFACE:                       enp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       77bea628-b6d3-3139-a69d-690f14df692a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   77bea628-b6d3-3139-a69d-690f14df692a | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1507315084
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.6
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::226:22ff:fe6b:ce8f/64
IP6.GATEWAY:                            --

GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.13.0-12-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlp4s0
GENERAL.IP-IFACE:                       wlp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     android
GENERAL.CON-UUID:                       2cfa5d86-bc6c-4b34-b0a4-851391d6050e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2cfa5d86-bc6c-4b34-b0a4-851391d6050e | android
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1507315087
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.5
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::eee:e6ff:feb6:e71/64
IP6.GATEWAY:                            --

SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
android       <MAC 'android' [AC1]>  Infra  7     2442 MHz  54 Mbit/s  76      &#9602;&#9604;&#9606;_  WPA1       yes     * 
VVF1          <MAC 'VVF1' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
TP-LINK_FA7E  <MAC 'TP-LINK_FA7E' [AC4]>  Infra  3     2422 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        
Natali        <MAC 'Natali' [AC3]>  Infra  2     2417 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
Home_Inet     <MAC 'Home_Inet' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
kiev          <MAC 'kiev' [AC5]>  Infra  9     2452 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2  no        
TAZIK         <MAC 'TAZIK' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/android]] (600 root)
[connection] id=android | type=wifi | permissions=
[wifi] bssid=<MAC 'android' [AC1]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=android
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Kiev (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp5s0    no frequency information.

wlp4s0    13 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp5s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)

wlp4s0    Scan completed :
          Cell 01 - Address: <MAC 'android' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"android"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000124f73dcbd
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'VVF1' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"VVF1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002907489d1
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Natali' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Natali"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003ea628f2180
                    Extra: Last beacon: 2760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'TP-LINK_FA7E' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_FA7E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001551baf546e
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'kiev' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"kiev"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000053010b93c
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.13.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     55EFCC9F539475103977285
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
name:           ath9k
vermagic:       4.13.0-12-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.13.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8A1D2C60031409F8A50F895
depends:        ath9k_hw,cfg80211,ath
intree:         Y
name:           ath9k_common
vermagic:       4.13.0-12-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_hw]
filename:       /lib/modules/4.13.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF13127B5F7FC2736913C0C
depends:        ath
intree:         Y
name:           ath9k_hw
vermagic:       4.13.0-12-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath]
filename:       /lib/modules/4.13.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
intree:         Y
name:           ath
vermagic:       4.13.0-12-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.13.0-12-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     66E288B8743878C5423A01E
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-12-generic SMP mod_unload 
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
filename:       /lib/modules/4.13.0-12-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A854863B536C70273DE73A5
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-12-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

[    8.487608] ath: phy0: Enable LNA combining
[    8.498255] ath: phy0: ASPM enabled: 0x43
[    8.498259] ath: EEPROM regdomain: 0x65
[    8.498260] ath: EEPROM indicates we should expect a direct regpair map
[    8.498262] ath: Country alpha2 being used: 00
[    8.498263] ath: Regpair used: 0x65
[   10.264533] ath9k 0000:04:00.0 wlp4s0: renamed from wlan0
[   10.413591] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready (repeated 3 times)
[   12.535669] wlp4s0: authenticate with <MAC 'android' [AC1]>
[   12.549942] wlp4s0: send auth to <MAC 'android' [AC1]> (try 1/3)
[   12.551728] wlp4s0: authenticated
[   12.554716] ath9k 0000:04:00.0 wlp4s0: disabling HT/VHT due to WEP/TKIP use
[   12.554720] ath9k 0000:04:00.0 wlp4s0: disabling HT as WMM/QoS is not supported by the AP
[   12.554722] ath9k 0000:04:00.0 wlp4s0: disabling VHT as WMM/QoS is not supported by the AP
[   12.556061] wlp4s0: associate with <MAC 'android' [AC1]> (try 1/3)
[   12.558496] wlp4s0: RX AssocResp from <MAC 'android' [AC1]> (capab=0x411 status=0 aid=4)
[   12.558674] wlp4s0: associated
[   12.558761] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready

########## wireless info END ############


 
```

---

### Post by wildmanne39 on 2017-10-05
It is connected but at 1mbs and if you have an ethernet/tethered connection it will override the wifi connection.

Change the settings in the router. WPA2-AES is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

We need to set your country code if you are in the Ukrane do:
```
sudo iw reg set UA
```
```
sudo sed -i 's/^REG.*=$/&UA/' /etc/default/crda
```
Reboot with all network connections uplugged.

---

### Post by kvisslav on 2017-10-05
Thanks a lot! Will check this in a couple of days and then return back.

---

### Post by kvisslav on 2017-10-19
Thank you. Unfortunately, I had need to have laptop 'to be online' ASAP, so I rolled back it to 17.04 that day and today upgrade to 17.10 'normally'. Everything works now. Thanks a lot for your time and advises

---

### Post by wildmanne39 on 2017-10-20
*Thread moved to **Networking & Wireless for better a better fit **.*

---

