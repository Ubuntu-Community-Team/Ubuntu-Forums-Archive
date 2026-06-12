---
title: "Internet is appears as if it is connected, but I have no internet."
date: 2017-07-27
forum: Networking &amp; Wireless
---

### Post by polisflatt on 2017-07-27
Hello guys, I have recently migrated from Windows 7 to Ubuntu 16, and I have been experiencing very tricky WiFi problems.

The first thing I noticed when I installed Ubuntu to my HDD is that it did not find any WiFi access points, so I resorted to googling the problem. I saw that I had to plug in my Ethernet cable and goto the Software and Updates program and let it download a few things, then proceed to goto the Additional Drivers tab and finally enable the "Broadband" option. I rebooted, and I could connect to my WiFi access point. However, I went to Firefox just to see it returned a "Server not found" error. I further looked online and have come across solutions in which involve things like updating Ubuntu, changing DNS, disabling IPv6, and other things related to that. None of those solutions worked for me, and I'm really frustrated.

Can you guys help me fix my problem?

Thanks.

---

### Post by BenginM on 2017-07-27
Hiya , welcome to the forums. 

 follow the sticky thread :

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

and post the wireless info script here inside a [CODE] tags .. thanks.

---

### Post by polisflatt on 2017-07-27
You mean this?

```

########## wireless info START ##########

Report from: 27 Jul 2017 21:17 CDT -0500

Booted last: 27 Jul 2017 00:00 CDT -0500

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell NetXtreme BCM5755M Gigabit Ethernet PCI Express [1028:01fe]
    Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
dell_laptop            20480  0
sparse_keymap          16384  1 dell_wmi
dell_smbios            16384  2 dell_wmi,dell_laptop
wl                   6447104  0
cfg80211              581632  1 wl
wmi                    16384  1 dell_wmi
video                  40960  2 dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp9s0    Link encap:Ethernet  HWaddr <MAC 'enp9s0' [IF1]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2605:a000:b886:6800:d4ed:f4b0:d068:23ae/64 Scope:Global
          inet6 addr: 2605:a000:b886:6800:80f2:7b36:5ccf:5d86/64 Scope:Global
          inet6 addr: fe80::6d8e:ebe3:3c01:9cbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120775 errors:0 dropped:1 overruns:0 frame:0
          TX packets:71671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144533893 (144.5 MB)  TX bytes:7420620 (7.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1355468 (1.3 MB)  TX bytes:1355468 (1.3 MB)

wlp12s0   Link encap:Ethernet  HWaddr <MAC 'wlp12s0' [IF2]>  
          inet6 addr: 2605:a000:b886:6800:7563:fb33:d4a6:e15/64 Scope:Global
          inet6 addr: 2605:a000:b886:6800:fd57:9a29:f499:4498/64 Scope:Global
          inet6 addr: fe80::ba60:4345:a493:71c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1803 errors:0 dropped:0 overruns:0 frame:4774
          TX packets:513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205822 (205.8 KB)  TX bytes:91597 (91.5 KB)
          Interrupt:17 Base address:0xc000 

##### iwconfig ##########################

lo        no wireless extensions.

enp9s0    no wireless extensions.

wlp12s0   IEEE 802.11  ESSID:"Test"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: <MAC 'Test' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp9s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp9s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp9s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       820     1  0 19:51 ?        00:00:14 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5755M Gigabit Ethernet PCI Express
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5755m-v3.29
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/enp9s0
GENERAL.IP-IFACE:                       enp9s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       bbe06f54-1350-32a6-89a8-6b0292a48065
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/11
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bbe06f54-1350-32a6-89a8-6b0292a48065 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.10/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.18.47.61
IP4.DNS[2]:                             209.18.47.62
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = dell-Latitude-D830
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1501211478
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.10
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 209.18.47.61 209.18.47.62
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         2605:a000:b886:6800:80f2:7b36:5ccf:5d86/64
IP6.ADDRESS[2]:                         2605:a000:b886:6800:d4ed:f4b0:d068:23ae/64
IP6.ADDRESS[3]:                         fe80::6d8e:ebe3:3c01:9cbe/64
IP6.GATEWAY:                            fe80::5665:deff:fe16:a857

GENERAL.DEVICE:                         wlp12s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4321 802.11a/b/g/n (Wireless 1500 Draft 802.11n WLAN Mini-card)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp12s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlp12s0
GENERAL.IP-IFACE:                       wlp12s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Test
GENERAL.CON-UUID:                       69e620c2-0878-420e-967f-d81a614a6a9d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/10
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     270 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0,4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ba568793-da58-42b7-a6f2-dea61000757d | 2WIRE676
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   83e395ef-3762-4515-a934-60965390a643 | Ashley
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   69e620c2-0878-420e-967f-d81a614a6a9d | Test
IP6.ADDRESS[1]:                         2605:a000:b886:6800:7563:fb33:d4a6:e15/64
IP6.ADDRESS[2]:                         2605:a000:b886:6800:fd57:9a29:f499:4498/64
IP6.ADDRESS[3]:                         fe80::ba60:4345:a493:71c8/64
IP6.GATEWAY:                            fe80::5665:deff:fe16:a857

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Ashley     <MAC 'Ashley' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Test       <MAC 'Test' [AC1]>  Infra  40    5200 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
GORDON     <MAC 'GORDON' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
TC8717TA1  <MAC 'TC8717TA1' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
2WIRE676   <MAC '2WIRE676' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  14      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/Test]] (600 root)
[connection] id=Test | type=wifi | permissions=user:dell:;
[wifi] mac-address=<MAC 'wlp12s0' [IF2]> | mac-address-blacklist= | ssid=Test
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ashley]] (600 root)
[connection] id=Ashley | type=wifi | permissions=user:dell:;
[wifi] mac-address=<MAC 'wlp12s0' [IF2]> | mac-address-blacklist= | ssid=Ashley
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/2WIRE676]] (600 root)
[connection] id=2WIRE676 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp12s0' [IF2]> | mac-address-blacklist= | ssid=2WIRE676
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATT9Cnu7eG]] (600 root)
[connection] id=ATT9Cnu7eG | type=wifi | permissions=user:dell:;
[wifi] mac-address=<MAC 'wlp12s0' [IF2]> | mac-address-blacklist= | ssid=ATT9Cnu7eG
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

enp9s0    no frequency information.

wlp12s0   32 channels in total; available frequencies :
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
          Channel 110 : 5.55 GHz
          Channel 112 : 5.56 GHz
          Current Frequency:5.2 GHz (Channel 40)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.2 GHz (Channel 40)

wlp12s0   Scan completed :
          Cell 01 - Address: <MAC 'Test' [AC1]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=70/70  Signal level=-15 dBm  
                    Encryption key:on
                    ESSID:"Test"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Ashley' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"Ashley"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'GORDON' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"GORDON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '2WIRE676' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"2WIRE676"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.8.0-36-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     0ADAE750C888A523D63D8B5
depends:        cfg80211
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

##### dmesg #############################

[   10.299008] wl: module verification failed: signature and/or required key missing - tainting kernel
[   10.482032] wlan0: Broadcom BCM4328 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   13.803484] wl 0000:0c:00.0 wlp12s0: renamed from wlan0
[   25.733927] IPv6: ADDRCONF(NETDEV_UP): wlp12s0: link is not ready
[   25.741186] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready (repeated 2 times)
[  279.976336] CPU: 1 PID: 362 Comm: wl_event_handle Tainted: P           OE   4.8.0-36-generic #36~16.04.1-Ubuntu
[  279.976485]  [<ffffffffc06d30f5>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  279.976554]  [<ffffffffc06d2740>] wl_event_handler+0x60/0x1e0 [wl]
[  279.976623]  [<ffffffffc06d26e0>] ? wl_notify_scan_status+0x330/0x330 [wl]
[  386.305184] tg3 0000:09:00.0 enp9s0: Link is up at 1000 Mbps, full duplex
[  386.305213] tg3 0000:09:00.0 enp9s0: Flow control is on for TX and on for RX
[  386.306238] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready
[ 3599.930534] tg3 0000:09:00.0 enp9s0: Link is down
[ 3603.849493] tg3 0000:09:00.0 enp9s0: Link is up at 1000 Mbps, full duplex
[ 3603.849511] tg3 0000:09:00.0 enp9s0: Flow control is on for TX and on for RX
[ 3918.048006] tg3 0000:09:00.0 enp9s0: Link is down
[ 4171.586881] tg3 0000:09:00.0 enp9s0: Link is up at 1000 Mbps, full duplex
[ 4171.586900] tg3 0000:09:00.0 enp9s0: Flow control is on for TX and on for RX
[ 4712.591122] tg3 0000:09:00.0 enp9s0: Link is down
[ 4827.496349] tg3 0000:09:00.0 enp9s0: Link is up at 1000 Mbps, full duplex
[ 4827.496373] tg3 0000:09:00.0 enp9s0: Flow control is on for TX and on for RX
[ 5220.776845] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

---

### Post by wildmanne39 on 2017-07-27
Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer

```
Reboot

---

### Post by polisflatt on 2017-07-27
> **wildmanne39 said:**
> Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer

```
Reboot

Thank-you, this worked!

---

### Post by wildmanne39 on 2017-07-27
Your welcome!
Enjoy!:)

---

### Post by BenginM on 2017-07-27
the [https://wireless.wiki.kernel.org/en/users/drivers/b43](https://wireless.wiki.kernel.org/en/users/drivers/b43) page reports it is partially supported by the b43 module and bcmwl wl works.

I suggest installing the LTS stack kernel base which should give you the kernel 4.8.0.-59

 [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by BenginM on 2017-07-27
well, i was late .. glad it's workin'..

---

