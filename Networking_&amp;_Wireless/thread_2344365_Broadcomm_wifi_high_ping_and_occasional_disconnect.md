---
title: "Broadcomm wifi high ping and occasional disconnects"
date: 2016-11-24
forum: Networking &amp; Wireless
---

### Post by bkbkbkbk on 2016-11-24
Hello,
i've recently installed ubuntu 16.10 on my desktop PC with asus z97 motherboard that has integrated wifi. I've followed a few forum threads to install and update Broadcomm drivers however still experiencing major issues with wifi connectivity. Namely on a random occasion pings get high and lead to host disconnected. Everything works finely for a while if I disconnect/connect to wifi again.

Would anyone please point me to a possible solution?

Details follow:
```
Linux desktop 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:03:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Drivers version:
```
Package: bcmwl-kernel-sourceStatus: install ok installed
Priority: optional
Section: admin
Installed-Size: 7829
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu11
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d00004311sv*sd*bc02sc80i*, pci:v000014E4d00004312sv*sd*bc02sc80i*, pci:v000014E4d00004313sv*sd*bc02sc80i*, pci:v000014E4d00004315sv*sd*bc02sc80i*, pci:v000014E4d00004727sv*sd*bc02sc80i*, pci:v000014E4d00004328sv*sd*bc02sc80i*, pci:v000014E4d00004328sv*sd*bc02sc80i*, pci:v000014E4d00004329sv*sd*bc02sc80i*, pci:v000014E4d0000432asv*sd*bc02sc80i*, pci:v000014E4d0000432bsv*sd*bc02sc80i*, pci:v000014E4d0000432csv*sd*bc02sc80i*, pci:v000014E4d0000432dsv*sd*bc02sc80i*, pci:v000014E4d00004365sv*sd*bc02sc80i*, pci:v000014E4d00004353sv*sd*bc02sc80i*, pci:v000014E4d00004357sv*sd*bc02sc80i*, pci:v000014E4d00004358sv*sd*bc02sc80i*, pci:v000014E4d00004359sv*sd*bc02sc80i*, pci:v000014E4d00004331sv*sd*bc02sc80i*, pci:v000014E4d000043a0sv*sd*bc02sc80i*, pci:v000014E4d000043B1sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
```

wireless-info:
```


########## wireless info START ##########


Report from: 25 Nov 2016 00:00 +03 +0300


Booted last: 25 Nov 2016 00:00 +03 +0300


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:03:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    DeviceName:  Onboard LAN
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I218-V [1043:85c4]


05:00.0 Network controller [0280]: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. BCM4352 802.11ac Wireless Network Adapter [1043:855c]
    Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 005 Device 002: ID 046d:0a1f Logitech, Inc. G930
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1058:10a8 Western Digital Technologies, Inc. Elements Portable (WDBUZG)
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 004: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 003 Device 012: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 003 Device 011: ID 046d:081b Logitech, Inc. Webcam C310
Bus 003 Device 010: ID 0835:8502 Action Star Enterprise Co., Ltd 
Bus 003 Device 009: ID 0835:8500 Action Star Enterprise Co., Ltd 
Bus 003 Device 008: ID 046d:c531 Logitech, Inc. C-U0007 [Unifying Receiver]
Bus 003 Device 007: ID 046d:c07c Logitech, Inc. M-R0017 [G700s Rechargeable Gaming Mouse]
Bus 003 Device 006: ID 046d:c24d Logitech, Inc. G710 Gaming Keyboard
Bus 003 Device 005: ID 0835:8501 Action Star Enterprise Co., Ltd 
Bus 003 Device 003: ID 0835:8500 Action Star Enterprise Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
wl                   6447104  0
cfg80211              581632  1 wl
snd_soc_rt5640        118784  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          233472  2 snd_soc_ssm4567,snd_soc_rt5640
snd_pcm               110592  8 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
mxm_wmi                16384  0
wmi                    16384  2 asus_wmi,mxm_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xdff00000-dff20000  


eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1  (Local Loopback)
        RX packets 28655  bytes 1474605 (1.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 28655  bytes 1474605 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.12  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::d683:4107:9a97:935f  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 137251  bytes 191680802 (191.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 6875
        TX packets 78480  bytes 9454194 (9.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  


##### iwconfig ##########################


eno1      no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.


wlp5s0    IEEE 802.11  ESSID:"Tech_D0031611"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Tech_D0031611' [AC1]>   
          Bit Rate=144 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp5s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s0


##### resolv.conf #######################


nameserver 213.184.238.6
nameserver 213.184.238.45
nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root       916     1  0 Nov24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4352 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:01.0/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Tech_D0031611 3
GENERAL.CON-UUID:                       068120ae-589d-4546-bc79-44564d5d1ceb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     144 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   068120ae-589d-4546-bc79-44564d5d1ceb | Tech_D0031611 3
IP4.ADDRESS[1]:                         192.168.0.12/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             213.184.238.6
IP4.DNS[2]:                             213.184.238.45
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1480625067
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.12
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 604800
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 213.184.238.6 213.184.238.45
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         fe80::d683:4107:9a97:935f/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
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


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Apple Inc.
GENERAL.PRODUCT:                        iPhone
GENERAL.DRIVER:                         ipheth
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.5/3-10.5.5/3-10.5.5:4.2/net/eth0
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
Tech_D0031611  <MAC 'Tech_D0031611' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
WiFi           <MAC 'WiFi' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
--             <MAC '' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  --         no        
Zahar_1992     <MAC 'Zahar_1992' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Tech_D0031611]] (600 root)
[connection] id=Tech_D0031611 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tech_D0031611
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tech_D0031611 3]] (600 root)
[connection] id=Tech_D0031611 3 | type=wifi | permissions=user:andrew:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tech_D0031611
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Minsk (based on set time zone)


country BY: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS


##### iwlist channels ###################


eno1      no frequency information.


lo        no frequency information.


eth0      no frequency information.


wlp5s0    32 channels in total; available frequencies :
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


eno1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.462 GHz (Channel 11)


wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'Tech_D0031611' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Tech_D0031611"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WiFi' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Zahar_1992' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Zahar_1992"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'TP-LINK_CEAC' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_CEAC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'vba4wifi' [AC5]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"vba4wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ZTE15/40' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ZTE15/40"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 52ms ago


##### module infos ######################


[wl]
filename:       /lib/modules/4.8.0-27-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
license:        MIXED/Proprietary
srcversion:     51DB051EE5EC6BAE4C1C879
depends:        cfg80211
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/4.8.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/xboxdrv.conf]
blacklist xpad


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


[/etc/pm/power.d/wifi_pwr_off] (755 root)
/sbin/iwconfig wlp5s0 power off


[/etc/pm/sleep.d/xboxdrv] (755 root)
case $1 in
     suspend|suspend_hybrid|hibernate)
    systemctl stop xboxdrv || :
        ;;
     resume|thaw)
    systemctl start xboxdrv || :
        ;;
esac


##### udev rules ########################


##### dmesg #############################


[    5.125105] wl: loading out-of-tree module taints kernel.
[    5.125107] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.126740] wl: module verification failed: signature and/or required key missing - tainting kernel
[    5.196135] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    5.198100] wl 0000:05:00.0 wlp5s0: renamed from wlan0
[    6.261878] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[    6.678919] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0b05-17cf.hcd failed with error -2
[    6.678921] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0b05-17cf.hcd not found
[  914.468047] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)


########## wireless info END ############



```

---

### Post by Hadaka on 2016-11-24
hi, your diagnostic wireless reports dmesg reports..
```
wl: module verification failed: signature and/or required key missing
```
Please access bios and disable your secure boot...UEFI to correct.
your AC1..access point..router indicates TKIP in your wifi configuration.
please access your router configurations and change to wpa2 aes NO TKIP
boot and test wireless
thanks.

---

