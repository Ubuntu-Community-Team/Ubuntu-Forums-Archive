---
title: "Wifi dropping after light use [Ubuntu 15.04] [Realtek  RTL8723BE]"
date: 2015-12-18
forum: Networking &amp; Wireless
---

### Post by Tzhaarevoke on 2015-12-18
I've used Ubuntu for a couple years without a problem, so please forgive me I'm not very knowledgeable haha. After installing Ubuntu 15.04 on my Laptop I noticed that the wifi will drop after light use (more than a couple tabs open, watching a video... etc.) I can fix it by disconnecting and reconnecting to the network, but a more permanent fix would be great. I have the most updated drivers so that shouldn't be a problem. 

Any help would be awesome! :D

Here is what the wireless info script returns 

```
 

########## wireless info START ##########


Report from: 30 Oct 2015 22:28 MDT -0600


Booted last: 29 Oct 2015 20:15 MDT -0600


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################




01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:808b]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f2:b45e Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1004:633e LG Electronics, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              94208  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              724992  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              540672  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr 3c:a8:2a:a5:ef:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr d8:5d:e2:22:08:83  
          inet addr:192.168.0.179  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::da5d:e2ff:fe22:883/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:131466473 (131.4 MB)  TX bytes:22604856 (22.6 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"CoxUp 2.4GHz"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E8:CC:18:F7:96:88   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35   Missed beacon:0




##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    400    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     400    0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search mh.shawcable.net


##### network managers ##################


Installed:


    NetworkManager


Running:


root       732     1  0 Oct27 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 3.19.0-30-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         D8:5D:E2:22:08:83
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     CoxUp 2.4GHz
GENERAL.CON-UUID:                       24b5e803-58f8-4694-a800-67e7f295c65a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/12
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   24b5e803-58f8-4694-a800-67e7f295c65a | CoxUp 2.4GHz
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.0.179/24, gw = 192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          mh.shawcable.net
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1446869387
DHCP4.OPTION[9]:                        domain_name = mh.shawcable.net
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 604800
DHCP4.OPTION[16]:                       ip_address = 192.168.0.179
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         ip = fe80::da5d:e2ff:fe22:883/64, gw = ::


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8106e-1_0.0.1 06/29/12
GENERAL.HWADDR:                         3C:A8:2A:A5:EF:D5
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off




SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
HP-Print-D2-ENVY 4500 series  28:80:23:F1:33:D2  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
SHAW-2FA73B                   74:85:2A:61:23:78  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
TELUS2317                     20:76:00:C1:5E:D8  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HP-Print-E2-Photosmart 7520   74:46:A0:DC:E7:E2  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  --         no        
HP-Print-5C-Officejet 6700    A0:1D:48:C4:D2:5C  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        
CoxUp 2.4GHz                  E8:CC:18:F7:96:88  Infra  11    2462 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 


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



```

---

### Post by jeremy31 on 2015-12-19
The script result is incomplete but if you can change the settings on the wifi router, change encryption to WPA2 only and put it on channel 9 instead of auto or channel 11 where it is now.
And usually with rtl8723be it works better after ```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
``` and a reboot to disable power management

---

