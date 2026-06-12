---
title: "NetGear WNDA3100v2 and Ubuntu 16.04.1 LTS: It just won't work."
date: 2017-01-30
forum: Networking &amp; Wireless
---

### Post by breaks2 on 2017-01-30
Hi everyone, I'm in need of a lot of help. I've been looking through many forums that seem to have become outdated because I can't get my NetGear WNDA3100v2 to work with any process that was posted many years ago.

Here is as much info as I can give you at the moment:

The NetGear device's ID is 0846:9011.
When I run lsb_release -a I get 16.04
I have already installed the NetGear's drivers from the older posts
And that's it, sorry. I'm totally new to this whole Linux thing.

Let me know if or how I need to give you more information to get this stuff working. I've been pulling my hair out all week.

---

### Post by wildmanne39 on 2017-01-30
Your device usually works with ndiswrapper. Please obtain a temporary internet connection then open a terminal and do:
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
find out if your system is 32- or 64-bit by running the following command then download the files in post #6 from the following link:
```
arch
```
[http://ubuntuforums.org/showthread.php?t=2052594](http://ubuntuforums.org/showthread.php?t=2052594)

Drag and drop the file to your desktop then right click and select extract here. 

Now install the driver:
```
cd ~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2
```
If your system is 32-bit (i686), install the 32-bit driver file:
```
sudo ndiswrapper -i bcmn43xx32.inf
```
If your system is a 64-bit (x86_64) system:
```
sudo ndiswrapper -i bcmn43xx64.inf
```
After you install the driver do:
```
sudo ndiswrapper -ma
sudo depmod -a
sudo modprobe ndiswrapper
```
Now your wifi should be working, if you installed other drivers you should remove them before installing this one.
Directions were found here:
[http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter](http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter)

---

### Post by breaks2 on 2017-01-30
> **wildmanne39 said:**
> Your device usually works with ndiswrapper. Please obtain a temporary internet connection then open a terminal and do:
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
find out if your system is 32- or 64-bit by running the following command then download the files in post #6 from the following link:
```
arch
```
[http://ubuntuforums.org/showthread.php?t=2052594](http://ubuntuforums.org/showthread.php?t=2052594)

Drag and drop the file to your desktop then right click and select extract here. 

Now install the driver:
```
cd ~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2
```
If your system is 32-bit (i686), install the 32-bit driver file:
```
sudo ndiswrapper -i bcmn43xx32.inf
```
If your system is a 64-bit (x86_64) system:
```
sudo ndiswrapper -i bcmn43xx64.inf
```
After you install the driver do:
```
sudo ndiswrapper -ma
sudo depmod -a
sudo modprobe ndiswrapper
```
Now your wifi should be working, if you installed other drivers you should remove them before installing this one.
Directions were found here:
[http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter](http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter)

I've tried to do this about a million times in the past week, and nothing has worked. I don't know why this is true, especially since there's been a few people who've figured out how to work around this and get it working while I'm still stuck in the dirt, having no clue why it's not working.

---

### Post by wildmanne39 on 2017-01-30
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags. 

If you just bought this device I would return it because it is the most difficult device to get to work, and many times it never works.

---

### Post by breaks2 on 2017-01-30
> **wildmanne39 said:**
> Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags. 

If you just bought this device I would return it because it is the most difficult device to get to work, and many times it never works.

Will do,

and I didn't just buy the device. I've had it for several years now and it's served me quite well on Windows, so I thought it'd be good on Ubuntu as well.

Also I'm not in a huge hurry to buy a new wireless adapter, either. I don't have the money for it.

I'll post the results from the script in a few min.

---

### Post by breaks2 on 2017-01-30
Update: Once I got Ubuntu started up again, my adapter is somehow working but it won't connect to my wifi? It detects all of the nearby networks but when I try to connect to one it does the infinite connection loop that everyone has had...

---

### Post by wildmanne39 on 2017-01-30
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.
That is good.

---

### Post by breaks2 on 2017-01-30
@wildmanne39

```

########## wireless info START ##########

Report from: 30 Jan 2017 16:22 EST -0500

Booted last: 30 Jan 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    DeviceName:  Onboard LAN
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2af3]

04:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:05e2]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 062: ID 413c:b11e Dell Computer Corp. 
Bus 003 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 003 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 008: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 003 Device 007: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller
Bus 003 Device 006: ID 0a5c:21f1 Broadcom Corp. HP Portable Bumble Bee
Bus 003 Device 005: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 003 Device 004: ID 1b1c:1b20 Corsair 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rndis_wlan             57344  0
rndis_host             16384  1 rndis_wlan
usbnet                 45056  3 rndis_host,rndis_wlan,cdc_ether
ndiswrapper           286720  0
b43                   417792  0
mac80211              737280  1 b43
cfg80211              565248  3 b43,mac80211,rndis_wlan
ssb                    65536  1 b43
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
bcma                   53248  1 b43
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp0s20u5 Link encap:Ethernet  HWaddr <MAC 'enp0s20u5' [IF2]>  
          inet addr:192.168.42.118  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::41fc:c9b2:cdf7:9771/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30876 (30.8 KB)  TX bytes:15923 (15.9 KB)

enx<IF from MAC [IF3]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF3]>' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135 (135.0 B)  TX bytes:135 (135.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

enp0s20u5  no wireless extensions.

enx<IF from MAC [IF3]>  IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20u5
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20u5
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20u5

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       914     1  0 16:12 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u5
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Android
GENERAL.PRODUCT:                        Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u5' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.0/net/enp0s20u5
GENERAL.IP-IFACE:                       enp0s20u5
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       8b82ac3b-4095-410b-937b-1c503a104d2d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8b82ac3b-4095-410b-937b-1c503a104d2d | Wired connection 1
IP4.ADDRESS[1]:                         192.168.42.118/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.118
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1485796848
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = breaks-800-060
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::41fc:c9b2:cdf7:9771/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enx<IF from MAC [IF3]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom
GENERAL.PRODUCT:                        Remote Download Wireless Adapter
GENERAL.DRIVER:                         ndiswrapper
GENERAL.DRIVER-VERSION:                 1.59+,08/26/2009, 5.10.79.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF3]>' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/net/enx<IF from MAC [IF3]>
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   db70e4cf-7e65-4d2c-99c4-9bcb7a35241e | WaltonsNet 2.4

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eno1
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

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
WaltonsNet 2.4  <MAC 'WaltonsNet 2.4' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
ATTbWhMdGs      <MAC 'ATTbWhMdGs' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WEP        no        
Theel           <MAC 'Theel' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WEP        no        
BHNTG1682G1A41  <MAC 'BHNTG1682G1A41' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/WaltonsNet 5]] (600 root)
[connection] id=WaltonsNet 5 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WaltonsNet 5
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WaltonsNet 2.4]] (600 root)
[connection] id=WaltonsNet 2.4 | type=wifi | permissions=user:breaks:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF3]>' [IF3]> | mac-address-blacklist= | ssid=WaltonsNet 2.4
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

eno1      no frequency information.

enp0s20u5  no frequency information.

enx<IF from MAC [IF3]>  14 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

enp0s20u5  Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

enx<IF from MAC [IF3]>  Scan completed :
          Cell 01 - Address: <MAC 'WaltonsNet 2.4' [AC1]>
                    ESSID:"WaltonsNet 2.4"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Theel' [AC2]>
                    ESSID:"Theel"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: <MAC 'ATTbWhMdGs' [AC3]>
                    ESSID:"ATTbWhMdGs"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: <MAC 'BHNTG1682G1A41' [AC4]>
                    ESSID:"BHNTG1682G1A41"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ndiswrapper]
filename:       /lib/modules/4.4.0-59-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     F409BC57C0CA7C84BD3C333
depends:        
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

[b43]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[bcma]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     B8F81D53A09CD1D43DDE810
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

##### module parameters #################

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  505.851917] rndis_host 3-5:1.0 enp0s20u5: renamed from usb0
[  505.873281] IPv6: ADDRCONF(NETDEV_UP): enp0s20u5: link is not ready

########## wireless info END ############

```

---

### Post by wildmanne39 on 2017-01-30
Before we continue you do not want to use your internal device it would probably work better and be easier to get working then the usb adapter using ndiswrapper.

---

### Post by breaks2 on 2017-01-30
> **wildmanne39 said:**
> Before we continue you do not want to use your internal device it would probably work better and be easier to get working then the usb adapter using ndiswrapper.

I can just remove it if I wanted to, but I don't think it matters so I'll just stick with it for now, okay?

I'm having issues with the usb adapter as well, so I can't even use it "using ndiswrapper".

---

### Post by wildmanne39 on 2017-01-30
You are going to keep using your internal card?

---

### Post by breaks2 on 2017-01-30
> **wildmanne39 said:**
> You are going to keep using your internal card?

Until I'm able to use my usb adapter, yes.

---

### Post by wildmanne39 on 2017-01-30
It is possible the driver from your internal device is conflicting with ndiswrapper, you really need chili555 or praseodym they have a lot more experience with this device then I do.

---

### Post by breaks2 on 2017-01-30
> **wildmanne39 said:**
> It is possible the driver from your internal device is conflicting with ndiswrapper, you really need chili555 or praseodym they have a lot more experience with this device then I do.

How do I get their attention pointed to this thread?

---

### Post by wildmanne39 on 2017-01-30
Hopefully one of them will pop in after seeing my post about them.

---

### Post by breaks2 on 2017-02-01
bump

---

### Post by wildmanne39 on 2017-02-03
I am sorry that you have not gotten anymore help to get your device to work, it is probably because it is almost impossible if not impossible to get it to work in the newer releases, I bought a new usb adapter from amazon for about 20.00 a few months ago that works great but I did have to install a new driver for it.

You did not even try to trouble shoot your internal device, you told me you would use it for now and I do not remember you saying it was not working properly, but I am pretty sure I told you that getting this device to work right with ndiswrapper is almost impossible.

> I'm tired of having Ubuntu on my computer wasting space because I can't use a sufficient internet connection without bringing my computer into another room all the time. 

I recommend starting a thread and asking which is the best usb device to buy for linux, because it is not just an ubuntu issue.

---

