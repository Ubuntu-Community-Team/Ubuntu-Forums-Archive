---
title: "TP-LINK TL-WN823N Network adapter"
date: 2018-03-02
forum: Networking &amp; Wireless
---

### Post by djwadds on 2018-03-02
I'm using TP-LINK TL-WN823N Network adapter and Ubuntu 17.10.1 but the internet keeps dropping out. Has anyone had a problem like this with a wireless adapter? 

Any advice would be greatly appreciated.

---

### Post by jeremy31 on 2018-03-02
Please post results from terminal for ```
sudo update-usbids; lsusb
```
There are at least 2 different versions

---

### Post by djwadds on 2018-03-02
Sorry should have said mine is version 1

Will post when I get back home tonight

---

### Post by holiday on 2018-03-02
I have a TP-LINK Wn725N, another TPLink USB wifi-adapter. It was unreliable until I took Network Manager out of the picture. It is quite possible to live without NM but there is not much support for that option.

---

### Post by djwadds on 2018-03-02
Can anyone suggest a better more Linux friendly USB

---

### Post by jeremy31 on 2018-03-02
Just post the info I asked for please and we can see what can be done with the wireless device you already have

---

### Post by djwadds on 2018-03-02
djwadds@djwadds-All-Series:~$ sudo update-usbids; lsusb
[sudo] password for djwadds: 
--2018-03-02 22:04:15--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
Resolving [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org](www.linux-usb.org))... 216.105.38.10
Connecting to [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org)|216.105.38.10|:80](www.linux-usb.org)|216.105.38.10|:80)... ^C
djwadds@djwadds-All-Series:~$

---

### Post by djwadds on 2018-03-02
Then Times out

---

### Post by jeremy31 on 2018-03-02
Just post results for ```
lsusb
```

---

### Post by djwadds on 2018-03-02
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1532:0202 Razer USA, Ltd 
Bus 003 Device 003: ID 0781:5581 SanDisk Corp. Ultra
Bus 003 Device 002: ID 1532:0053 Razer USA, Ltd 
Bus 003 Device 005: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2018-03-02
In terminal, I would do
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl8192cu.conf
```

The first command will disable wifi power management as it causes issues and the seconds command prevents one of the modules from loading and may resolve some conflicts

---

### Post by djwadds on 2018-03-02
Second Command Returned
blacklist rtl8192cu

---

### Post by djwadds on 2018-03-02
Hasn't worked yet, WIFI just disconnected again

---

### Post by jeremy31 on 2018-03-02
See the wireless script link in my signature and post results

---

### Post by djwadds on 2018-03-02
```
########## wireless info START ##########

Report from: 02 Mar 2018 22:50 GMT +0000

Booted last: 02 Mar 2018 00:00 GMT +0000

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful

##### kernel ############################

Linux 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection I217-V [1043:859f]
	Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1532:0202 Razer USA, Ltd 
Bus 003 Device 003: ID 0781:5581 SanDisk Corp. Ultra
Bus 003 Device 002: ID 1532:0053 Razer USA, Ltd 
Bus 003 Device 005: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8xxxu              126976  0
mac80211              782336  1 rtl8xxxu
cfg80211              614400  1 mac80211
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
mxm_wmi                16384  1 nouveau
wmi                    24576  4 asus_wmi,wmi_bmof,mxm_wmi,nouveau
video                  40960  2 asus_wmi,nouveau

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
3: wlx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 192.168.0.13/24 brd 192.168.0.255 scope global dynamic wlx<IF from MAC [IF2]>
       valid_lft 86214sec preferred_lft 86214sec
    inet6 2a02:c7f:9213:8100:21bd:3af0:3b74:903f/64 scope global temporary dynamic 
       valid_lft 2525sec preferred_lft 2525sec
    inet6 2a02:c7f:9213:8100:7ea1:6712:bd64:a2d2/64 scope global mngtmpaddr noprefixroute dynamic 
       valid_lft 2525sec preferred_lft 2525sec
    inet6 fd53:8939:b1b9:0:21bd:3af0:3b74:903f/64 scope global temporary dynamic 
       valid_lft 604616sec preferred_lft 85865sec
    inet6 fd53:8939:b1b9:0:15e6:cc87:2cc5:3414/64 scope global mngtmpaddr noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::1386:f415:c284:a5f1/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:"SKYE8271"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'SKYE8271' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:0

##### route #############################

default via 192.168.0.1 dev wlx<IF from MAC [IF2]> proto static metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF2]> scope link metric 1000 
192.168.0.0/24 dev wlx<IF from MAC [IF2]> proto kernel scope link src 192.168.0.13 metric 600 

##### resolv.conf #######################

nameserver 127.0.0.53

search Home

##### network managers ##################

Installed:

	NetworkManager

Running:

root       749     1  0 22:47 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         802.11n
GENERAL.PRODUCT:                        USB WLAN
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.13.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     SKYE8271
GENERAL.CON-UUID:                       e6820b1a-3d77-48a3-8cf5-7654a6e09007
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e6820b1a-3d77-48a3-8cf5-7654a6e09007 | SKYE8271
IP4.ADDRESS[1]:                         192.168.0.13/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1520117241
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.13
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         2a02:c7f:9213:8100:21bd:3af0:3b74:903f/64
IP6.ADDRESS[2]:                         fd53:8939:b1b9:0:21bd:3af0:3b74:903f/64
IP6.ADDRESS[3]:                         2a02:c7f:9213:8100:7ea1:6712:bd64:a2d2/64
IP6.ADDRESS[4]:                         fd53:8939:b1b9:0:15e6:cc87:2cc5:3414/64
IP6.ADDRESS[5]:                         fe80::1386:f415:c284:a5f1/64
IP6.GATEWAY:                            fe80::7250:afff:fe5a:2401
IP6.ROUTE[1]:                           dst = 2a02:c7f:9213:8100::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = fd53:8939:b1b9::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fd53:8939:b1b9:0:7250:afff:fe5a:2400
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:e2:5b:1f:96:c7:e7:3e:49:76:ef:9e:bf:9e:61:c4:16
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd53:8939:b1b9:0:7250:afff:fe5a:2400
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        dhcp6_unknown_15 = 0:1d:37:30:35:30:61:66:35:61:32:34:30:30:40:73:6b:79:64:73:6c:7c:36:33:38:38:36:61:36:33:0
DHCP6.OPTION[5]:                        dhcp6_unknown_16 = 0:0:d:e9:0:25:32:2e:30:36:2e:32:31:38:38:2e:52:7c:30:30:31:7c:45:52:31:31:30:7c:41:43:34:32:31:37:32:43:30:30:38:33:33:36:0
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:70:50:af:5a:24:1

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
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

SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
SKYE8271  <MAC 'SKYE8271' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  67      â&#8211;&#8218;â&#8211;&#8222;â&#8211;&#8224;_  WPA2      yes     * 
SKYE8271  <MAC 'SKYE8271' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  37      â&#8211;&#8218;â&#8211;&#8222;__  WPA2      no        
SKYE8271  <MAC 'SKYE8271' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  24      â&#8211;&#8218;___  WPA2      no        
SKYE8271  <MAC 'SKYE8271' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  17      â&#8211;&#8218;___  WPA2      no        

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

[[/etc/NetworkManager/system-connections/SKYE8271]] (600 root)
[connection] id=SKYE8271 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=SKYE8271
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

eno1      no frequency information.

wlx<IF from MAC [IF2]>  14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'SKYE8271' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"SKYE8271"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e4d13e2f4
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SKYE8271' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SKYE8271"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e49ad6d2d
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SKYE8271' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SKYE8271"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000152f2f29113
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'SKYE8271' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"SKYE8271"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000152f7e53f02
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.13.0-36-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@gmail.com>
srcversion:     5384B78EEE469EF94AB3F21
depends:        mac80211
intree:         Y
name:           rtl8xxxu
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[mac80211]
filename:       /lib/modules/4.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-36-generic SMP mod_unload 
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
filename:       /lib/modules/4.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8192cu.conf]
blacklist rtl8192cu

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.378330] usb 3-10: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[    4.378347] usb 3-10: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    4.852585] rtl8xxxu 3-10:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[    5.136255] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[    5.323395] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[    7.536376] wlx<IF from MAC [IF2]>: authenticate with <MAC 'SKYE8271' [AC1]>
[    7.542812] wlx<IF from MAC [IF2]>: send auth to <MAC 'SKYE8271' [AC1]> (try 1/3)
[    7.545680] wlx<IF from MAC [IF2]>: authenticated
[    7.547967] wlx<IF from MAC [IF2]>: associate with <MAC 'SKYE8271' [AC1]> (try 1/3)
[    7.554834] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'SKYE8271' [AC1]> (capab=0x411 status=0 aid=1)
[    7.555378] usb 3-10: rtl8xxxu_bss_info_changed: HT supported
[    7.555981] wlx<IF from MAC [IF2]>: associated
[    7.556024] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2018-03-03
The next time the internet disconnects run ```
./wireless-info
```
After you reboot/reconnect run ```
cat wireless-info.txt | nc termbin.com 9999
```
Post URL from terminal.  I think it might be trying to roam to one of the other access points with the same name

---

