---
title: "USB Wifi Driver"
date: 2016-11-08
forum: Networking &amp; Wireless
---

### Post by calimer on 2016-11-08
I've recently been using Linux for my students and they gave me a USB Wifi Adapter for my computer that is TL WN722N TP LINK
[https://www.amazon.com/TP-Link-Wireless-External-Supports-TL-WN722N/dp/B002SZEOLG](https://www.amazon.com/TP-Link-Wireless-External-Supports-TL-WN722N/dp/B002SZEOLG)

I sometimes have internet drops and I think a lot of it has to do with poor internet at the school but I'd like to get the best driver possible for it.  I'm not exactly sure how to make sure I get the proper driver for it and also make sure the old one doesn't conflict or have problems.  I don't have a lot of time to test it and so if I screw it up it won't be easy for me to fix fast so any help would be super greatly appreciated.  Any insight would be greatly appreciated, thank you for your time!
-Mike

EDIT I am using Lubuntu 16.04

---

### Post by slickymaster on 2016-11-08
*Thread moved to **Networking & Wireless**.*

Please have a read at this [sticky]("https://ubuntuforums.org/showthread.php?t=370108") and do what's requested there

---

### Post by calimer on 2016-11-08
Thank you so much, I will run all that tomorrow!  I should be up to date and I check for updates often but I'll be sure to try the dist-upgrades command. I'll post my wifi text too wee :)

---

### Post by chili555 on 2016-11-09
I believe the driver is ath9k_htc. Verify:```
lsmod | grep ath
```If that is the case, I have the exact same device. There is no alternate driver or, as importantly, firmware file as far as I've been able to find.

If there is an internal wireless device in your machine, you should blacklist it. I'd also check the usual things. Set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

We will know more and we may have other suggestions when we see your wireless script results.

---

### Post by calimer on 2016-11-09
lsmod | grep ath results in:
ath9k_htc              77824  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              466944  2 ath9k_common,ath9k_htc
ath                    32768  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              737280  1 ath9k_htc
cfg80211              565248  4 ath,ath9k_common,mac80211,ath9k_htc


Here is my wirefless info:

```


########## wireless info START ##########

Report from: 09 Nov 2016 12:58 EST -0500

Booted last: 09 Nov 2016 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit Network Connection [8086:10de] (rev 02)
	Subsystem: Dell 82567LM-3 Gigabit Network Connection [1028:027f]
	Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 008 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

ath9k_htc              77824  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              466944  2 ath9k_common,ath9k_htc
ath                    32768  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              737280  1 ath9k_htc
cfg80211              565248  4 ath,ath9k_common,mac80211,ath9k_htc
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
video                  40960  1 dell_wmi
wmi                    20480  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:f7fe0000-f8000000 

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2e5:3bec:3600:6dc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2274101 (2.2 MB)  TX bytes:536473 (536.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s25   no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"ORMS-Main"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ORMS-Main' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:29  Invalid misc:34   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>

##### resolv.conf #######################

nameserver 127.0.1.1
search localdomain

##### network managers ##################

Installed:

	NetworkManager

Running:

root       618     1  0 12:52 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         ATHEROS
GENERAL.PRODUCT:                        USB2.0 WLAN
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 4.4.0-47-generic
GENERAL.FIRMWARE-VERSION:               1.4
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     ORMS-Main
GENERAL.CON-UUID:                       db33742b-3b25-4170-98ab-de25ba77af88
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   db33742b-3b25-4170-98ab-de25ba77af88 | ORMS-Main
IP4.ADDRESS[1]:                         192.168.1.64/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1478721161
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.64
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = localdomain
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 7200
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::f2e5:3bec:3600:6dc3/64
IP6.GATEWAY:                            fe80::1:1
IP6.ROUTE[1]:                           dst = fe80::1:1/128, nh = ::, mt = 600
IP6.DOMAIN[1]:                          localdomain

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82567LM-3 Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.5-3
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
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

SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ORMS-Main           <MAC 'ORMS-Main' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA2       yes     * 
ORMS-Main           <MAC 'ORMS-Main' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
ORMS-Main           <MAC 'ORMS-Main' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
DBC130              <MAC 'DBC130' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
DDW365.CC438C-2.4G  <MAC 'DDW365.CC438C-2.4G' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
belkin.00b          <MAC 'belkin.00b' [AC7]>  Infra  10    2457 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
D835AB              <MAC 'D835AB' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/ORMS-Main]] (600 root)
[connection] id=ORMS-Main | type=wifi | permissions=user:m:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=ORMS-Main
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

lo        no frequency information.

enp0s25   no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'ORMS-Main' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"ORMS-Main"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002e94de9e3
                    Extra: Last beacon: 228ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'D835AB' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"D835AB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000055ce9712196
                    Extra: Last beacon: 5820ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ORMS-Main' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"ORMS-Main"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002e9351cc5
                    Extra: Last beacon: 5328ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'DDW365.CC438C-2.4G' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"DDW365.CC438C-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003984aa796c
                    Extra: Last beacon: 5312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'DBC130' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"DBC130"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000498a40a135
                    Extra: Last beacon: 272ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ORMS-Main' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ORMS-Main"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002e6fcf88b
                    Extra: Last beacon: 600ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'belkin.00b' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"belkin.00b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000362d423818
                    Extra: Last beacon: 1044ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       ath9k_htc/htc_9271-1.4.0.fw
firmware:       ath9k_htc/htc_7010-1.4.0.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     D97AA41EF63133F707BAA44
depends:        mac80211,ath9k_hw,ath9k_common,ath,cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_dev_fw:Use development FW version (int)
parm:           blink:Enable LED blink on activity (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     FA7ECFBA5761A5B3ED96BB2
depends:        ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
blink: 1
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_dev_fw: 0

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   19.288369] usb 1-2: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[   19.288415] usbcore: registered new interface driver ath9k_htc
[   20.619156] usb 1-2: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[   20.871650] ath9k_htc 1-2:1.0: ath9k_htc: HTC initialized with 33 credits
[   21.137905] ath9k_htc 1-2:1.0: ath9k_htc: FW Version: 1.4
[   21.137909] ath9k_htc 1-2:1.0: FW RMW support: On
[   21.137911] ath: EEPROM regdomain: 0x809c
[   21.137912] ath: EEPROM indicates we should expect a country code
[   21.137914] ath: doing EEPROM country->regdmn map search
[   21.137916] ath: country maps to regdmn code: 0x52
[   21.137918] ath: Country alpha2 being used: CN
[   21.137919] ath: Regpair used: 0x52
[   21.382982] ath9k_htc 1-2:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   36.547730] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 2 times)
[   36.734696] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[   37.885584] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[   50.448437] wlx<IF from MAC [IF2]>: authenticate with <MAC 'ORMS-Main' [AC3]>
[   50.707332] wlx<IF from MAC [IF2]>: send auth to <MAC 'ORMS-Main' [AC3]> (try 1/3)
[   50.709428] wlx<IF from MAC [IF2]>: authenticated
[   50.712035] wlx<IF from MAC [IF2]>: associate with <MAC 'ORMS-Main' [AC3]> (try 1/3)
[   50.718432] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'ORMS-Main' [AC3]> (capab=0x431 status=0 aid=16)
[   50.727182] wlx<IF from MAC [IF2]>: associated
[   50.727195] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[  112.961217] wlx<IF from MAC [IF2]>: authenticate with <MAC 'ORMS-Main' [AC1]>
[  113.132865] wlx<IF from MAC [IF2]>: send auth to <MAC 'ORMS-Main' [AC1]> (try 1/3)
[  113.136115] wlx<IF from MAC [IF2]>: authenticated
[  113.140095] wlx<IF from MAC [IF2]>: associate with <MAC 'ORMS-Main' [AC1]> (try 1/3)
[  113.144955] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'ORMS-Main' [AC1]> (capab=0x431 status=0 aid=16)
[  113.153703] wlx<IF from MAC [IF2]>: associated

########## wireless info END ############


```

---

### Post by chili555 on 2016-11-09
> ath: Country alpha2 being used: CNChina?? Did you set the country code already?

We see three networks with the same name, ORMS-Main, and, as expected, your wireless is attempting to roam from among them, always looking for a better connection. Reminds me of an old girlfriend!!!

You might try binding to the strongest and nearest like this: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by calimer on 2016-11-09
I have not intentionally set it to China, maybe the wifi adapter is from China?  Thanks for the heads up on the link!  I'll check it out.  Unfortunately I'm not given much time to work on things, and even typing in here is a rush.  Thanks so much for your help!!

EDIT I tried sudo iwlist wlan0 scan but it says wlan0     Interface doesn't support scanning.

I did edit the gksudo gedit /etc/default/crda and changed it to US but I have the kiddos on the server so I can test it yet, I imagine I have to restart for the effects to take effect.

---

### Post by calimer on 2016-12-09
I'm still having a lot of drops.  I know that our internet is not but it seems to drop a bit more than the windows computer does.  Any insight would be greatly appreciated!!!  Thank you :)

---

