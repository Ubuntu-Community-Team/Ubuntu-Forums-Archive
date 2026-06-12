---
title: "WiFi Does Not Transfer Data"
date: 2016-02-07
forum: Networking &amp; Wireless
---

### Post by &amp;*@Fth&amp;% on 2016-02-07
I can connect to WiFi networks, and ethernet works just fine, but WiFi does not transfer data. The same thing happens with Bluetooth as well (using my phone's Bluetooth network) and no data is transferred. How should I go about fixing this?

---

### Post by Vladlenin5000 on 2016-02-07
Here's the result of your script in a human readable form (I don't know what you did but extracting it was a 2-step job that many wouldn't be able / wouldn't have cared to do):

```

########## wireless info START ##########

Report from: 07 Feb 2016 21:52 EST -0500

Booted last: 07 Feb 2016 00:00 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, recovery, nomodeset

##### desktop ###########################

Plasma

##### lspci #############################

03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASRock Incorporation Device [1849:10a1]
    Kernel driver in use: alx

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Kernel driver in use: rtl8821ae

##### lsusb #############################

Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 25a7:2433  
Bus 001 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              733184  3 rtl_pci,rtlwifi,rtl8821ae
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
cfg80211              548864  2 mac80211,rtlwifi
snd_pcm               106496  9 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7054565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2315808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10320454919 (10.3 GB)  TX bytes:196195396 (196.1 MB)
          Interrupt:18 

vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp4s0    Link encap:Ethernet  HWaddr <MAC 'wlp4s0' [IF]>  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp4s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20866460 (20.8 MB)  TX bytes:1271963 (1.2 MB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

lo        no wireless extensions.

wlp4s0    IEEE 802.11abgn  ESSID:"OWD24"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'OWD24' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0

##### resolv.conf #######################

search home
nameserver 192.168.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      7405     1  0 18:28 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8171 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       1acd681d-a775-4d46-9712-0e6c71fa2ef3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/13
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1acd681d-a775-4d46-9712-0e6c71fa2ef3 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_netbios_scope = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        host_name = Bens-PC
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        expiry = 1454975872
DHCP4.OPTION[10]:                       domain_name = home
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       requested_subnet_mask = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       ip_address = 192.168.1.7
DHCP4.OPTION[20]:                       dhcp_lease_time = 86400
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       network_number = 192.168.1.0
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.2.0-27-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp4s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:04:00.0/net/wlp4s0
GENERAL.IP-IFACE:                       wlp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     OWD24
GENERAL.CON-UUID:                       84c9122b-3a23-4451-a901-ea7317a70ac9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/14
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   84c9122b-3a23-4451-a901-ea7317a70ac9 | OWD24
IP4.ADDRESS[1]:                         192.168.1.8/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_netbios_scope = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        host_name = new-host
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        expiry = 1454984270
DHCP4.OPTION[10]:                       domain_name = home
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       requested_subnet_mask = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       ip_address = 192.168.1.8
DHCP4.OPTION[20]:                       dhcp_lease_time = 86400
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       network_number = 192.168.1.0
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp4s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_50_55_27_9D_EE_41
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{8}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ebef6813-1ca0-440c-8e77-1ba2292525be | Tablet Network

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_64_89_9A_B9_69_05
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f14b21b4-d30b-4a4c-a391-2542c9caf777 | Ben's phone Network

GENERAL.DEVICE:                         vmnet1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vmnet1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vmnet1
GENERAL.IP-IFACE:                       vmnet1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         vmnet8
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vmnet8' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vmnet8
GENERAL.IP-IFACE:                       vmnet8
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
OWD24        <MAC 'OWD24' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WEP        yes     * 
HIGHLANDER2  <MAC 'HIGHLANDER2' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WEP        no        
Kensington   <MAC 'Kensington' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/OWD24]] (600 root)
[connection] id=OWD24 | type=wifi | permissions=user:ben:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=OWD24
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ubnt-276797bb-43ee-4abe-80dd-31f6dde6cb52]] (600 root)
[connection] id=ubnt | type=wifi | permissions=user:ben:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ubnt
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Verizon VS985 4G 9554]] (600 root)
[connection] id=Verizon VS985 4G 9554 | type=wifi | autoconnect=false | permissions=user:ben:;
[wifi] mac-address=<MAC 'wlp4s0' [IF]> | mac-address-blacklist= | ssid=Verizon VS985 4G 9554
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ben's WiFi]] (600 root)
[connection] id=Ben's WiFi | type=wifi | autoconnect=false | permissions=user:ben:;
[wifi] mac-address=<MAC 'wlp4s0' [IF]> | mac-address-blacklist= | ssid=Ben's WiFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ubnt]] (600 root)
[connection] id=ubnt | type=wifi | permissions=user:kubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ubnt
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TripMate-7BE2]] (600 root)
[connection] id=TripMate-7BE2 | type=wifi | permissions=user:ben:;
[wifi] mac-address=<MAC 'wlp4s0' [IF]> | mac-address-blacklist= | ssid=TripMate-7BE2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/OWD24-84c9122b-3a23-4451-a901-ea7317a70ac9]] (600 root)
[connection] id=OWD24 | type=wifi | permissions=user:ben:;
[wifi] mac-address=<MAC 'wlp4s0' [IF]> | mac-address-blacklist= | ssid=OWD24
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: US/Eastern (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

vmnet1    no frequency information.

vmnet8    no frequency information.

lo        no frequency information.

wlp4s0    24 channels in total; available frequencies :
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
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlp4s0    Scan completed :
          Cell 01 - Address: <MAC 'OWD24' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"OWD24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032b9824e82
                    Extra: Last beacon: 84ms ago
          Cell 02 - Address: <MAC 'RKK6L' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"RKK6L"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e437971180
                    Extra: Last beacon: 7048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HIGHLANDER2' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HIGHLANDER2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000012f7cd4c4
                    Extra: Last beacon: 84ms ago

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     BB713075FA2F842D6685836
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 1 to disable interrupt clear before set (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A888EFDC516033207A503FA
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F4CACC5FCAEBE7C22930A24
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FBF6EA073A00B4F3836226E
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
msi: Y
swenc: N
swlps: N

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  835.745053] NetworkManager[1043]: segfault at 168 ip 00000000004c39cd sp 00007fff123357d0 error 4 in NetworkManager (deleted)[400000+1bf000]
[  836.039385] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready (repeated 3 times)
[ 2069.241784] wlp4s0: authenticate with <MAC 'OWD24' [AC1]>
[ 2069.393892] wlp4s0: send auth to <MAC 'OWD24' [AC1]> (try 1/3)
[ 2069.395298] wlp4s0: authenticated
[ 2069.395416] rtl8821ae 0000:04:00.0 wlp4s0: disabling HT/VHT due to WEP/TKIP use
[ 2069.396892] wlp4s0: associate with <MAC 'OWD24' [AC1]> (try 1/3)
[ 2069.401290] wlp4s0: RX AssocResp from <MAC 'OWD24' [AC1]> (capab=0x431 status=0 aid=7)
[ 2069.401564] wlp4s0: associated
[ 2069.401601] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
[ 2072.965371] bridge-enp3s0: disabling the bridge
[ 2072.977810] bridge-enp3s0: down
[ 2072.977814] bridge-enp3s0: detached
[ 2072.977887] bridge-wlp4s0: device is wireless, enabling SMAC
[ 2072.977889] bridge-wlp4s0: up
[ 2072.977891] bridge-wlp4s0: attached
[ 2570.055622] wlp4s0: deauthenticating from <MAC 'OWD24' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2585.672200] bridge-wlp4s0: disabling the bridge
[ 2585.743826] bridge-wlp4s0: down
[ 2585.743831] bridge-wlp4s0: detached
[ 2585.743867] bridge-enp3s0: up
[ 2585.743870] bridge-enp3s0: attached
[10976.400040] wlp4s0: authenticate with <MAC 'OWD24' [AC1]>
[10976.400465] wlp4s0: send auth to <MAC 'OWD24' [AC1]> (try 1/3)
[10976.402019] wlp4s0: authenticated
[10976.402099] rtl8821ae 0000:04:00.0 wlp4s0: disabling HT/VHT due to WEP/TKIP use
[10976.403752] wlp4s0: associate with <MAC 'OWD24' [AC1]> (try 1/3)
[10976.406472] wlp4s0: RX AssocResp from <MAC 'OWD24' [AC1]> (capab=0x431 status=0 aid=2)
[10976.406632] wlp4s0: associated
[10976.453269] bridge-enp3s0: disabling the bridge
[10976.467758] bridge-enp3s0: down
[10976.467762] bridge-enp3s0: detached
[10976.467806] bridge-wlp4s0: device is wireless, enabling SMAC
[10976.467807] bridge-wlp4s0: up
[10976.467810] bridge-wlp4s0: attached

########## wireless info END ############


```

---

### Post by Vladlenin5000 on 2016-02-08
For the moment the only advice is the set your WiFi router with WPA2 only with AES. Everything shown in the available hotspots - WEP or WPA/WPA2 (mixed mode) - is known to have problems (and WEP in particular is highly insecure). Remove (delete) the current WiFi profile (in Kubuntu), reconnect and test.If the symptom persists then you may benefit from a new driver but let's not go there yet.

---

### Post by &amp;*@Fth&amp;% on 2016-02-08
Tried that. I just tried reinstalling the network manager and it seems like it worked, but I can't be sure until Wednesday. I'll see about upgrading to WEP2 on my router.

---

### Post by &amp;*@Fth&amp;% on 2016-02-14
It seems to only happen with some networks apparently.

---

### Post by &amp;*@Fth&amp;% on 2016-02-15
I can also connect to the router and adjust settings, but I can't use the internet. This makes no sense >:(

---

### Post by &amp;*@Fth&amp;% on 2016-02-16
Edit: sorry, wrong thread! Not sure how that happenned...

---

### Post by &amp;*@Fth&amp;% on 2016-03-02
I can connect to one of my routers, but not the other, nor my phone's wifi hotspot.

---

### Post by &amp;*@Fth&amp;% on 2016-03-11
Bump

---

### Post by &amp;*@Fth&amp;% on 2016-03-20
Bump

---

### Post by jeremy31 on 2016-03-20
If you can ```
ping -c3 8.8.8.8
``` and get an error with ```
ping -c3 ubuntuforums.org
```

Then do
```
sudo sed -i 's/nameserver 192.168.1.1/nameserver 127.0.1.1/' /etc/resolv.conf
```

If the nameserver isn't set correctly it can't resolve host names

---

### Post by &amp;*@Fth&amp;% on 2016-03-20
Nope, I can't ping a website nor a URL. I can open up the router's configuration interface, and ping the router itself, but I literally cannot do ANYTHING else.

---

### Post by jeremy31 on 2016-03-20
Did the ping to 8.8.8.8 do anything?

---

### Post by &amp;*@Fth&amp;% on 2016-03-20
I can't test it right now, but from what I remember it spat out an error saying it couldn't connect or something like that.

---

### Post by &amp;*@Fth&amp;% on 2016-03-23
Thanks Jeremy! That kast command fixed everything! For those wondering, the ping 8.8.8.8 worked, but the ubuntuforums one just hung out and returned nothing.

---

