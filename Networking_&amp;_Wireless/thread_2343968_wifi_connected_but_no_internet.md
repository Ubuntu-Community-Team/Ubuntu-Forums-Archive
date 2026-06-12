---
title: "wifi connected but no internet"
date: 2016-11-21
forum: Networking &amp; Wireless
---

### Post by michaelporter on 2016-11-21
I bought a new laptop Asus X155LA with windows10 preinstalled. I installed Ubuntu 16.04 as dual-boot.
The install was successful except that I have no internet. Ubuntu announces at start up that I am connected to my router, but there is no internet.
Moving the laptop nearer to the router does no good. Internet is fine on Windows10. It was also fine on my old laptop with Ubuntu 13.04.
Any help greatly appreciated, thanks

---

### Post by TheFu on 2016-11-21
Can you ping the router by IP?
Can you ping 8.8.8.8?
Can you ping google.com?

Do each in that order and report where the failure happens, please.

There is also a **wireless-info** script mentioned all over the place in these forums. Get it. Run it. Post the link it can create so others can review the data.  Think it is on github, so look for it there with google.

---

### Post by wildmanne39 on 2016-11-21
*Thread moved to **Networking & Wireless**.*

Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by michaelporter on 2016-11-23
Thanks for the reply.
Here are the results

```

mike@mike-X555LAB:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.

```

terminal hangs (no prompt)

```

mike@mike-X555LAB:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

```

terminal hangs (no prompt)

```

mike@mike-X555LAB:~$ ping google.com
ping: unknown host google.com
mike@mike-X555LAB:~$

```

I also tried this:

```

mike@mike-X555LAB:~$ sudo modprobe rtl8821ae
[sudo] password for mike: 
mike@mike-X555LAB:~$ sudo modprobe rtl8821ae
mike@mike-X555LAB:~$ modinfo rtl8821ae
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     B9E24DCC76240A48AEEF94E
alias:          pci:v000010ECd00008821sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008812sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
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
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)
mike@mike-X555LAB:~$ 

```



```

########## wireless info START ##########

Report from: 23 Nov 2016 12:09 GMT +0000

Booted last: 23 Nov 2016 00:00 GMT +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
    Kernel driver in use: rtl8821ae

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID b49a:04f2  
Bus 001 Device 002: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 0781:5576 SanDisk Corp. Cruzer Facet
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################

rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  1 asus_wmi
video                  40960  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::77c7:525f:bba4:1fc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6204 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6235641 (6.2 MB)  TX bytes:914602 (914.6 KB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2244:1497:9d70:f51e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111884 (111.8 KB)  TX bytes:75478 (75.4 KB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:"PLUSNET-G7QZ"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'PLUSNET-G7QZ' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enp2s0
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       835     1  0 11:15 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       607ecdaf-d57d-38cd-b821-01aa2a8b08ec
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   607ecdaf-d57d-38cd-b821-01aa2a8b08ec | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.65/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = mike-X555LAB
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.254
DHCP4.OPTION[12]:                       expiry = 1479987715
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.254
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.65
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = lan
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::77c7:525f:bba4:1fc1/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-47-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     PLUSNET-G7QZ
GENERAL.CON-UUID:                       c97eca07-57b0-47b4-9835-25b0ad73a48d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c97eca07-57b0-47b4-9835-25b0ad73a48d | PLUSNET-G7QZ
IP4.ADDRESS[1]:                         192.168.1.67/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = mike-X555LAB
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.254
DHCP4.OPTION[12]:                       expiry = 1479987786
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.254
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.67
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = lan
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::2244:1497:9d70:f51e/64
IP6.GATEWAY:                            

SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
PLUSNET-G7QZ  <MAC 'PLUSNET-G7QZ' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2      yes     * 

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

[[/etc/NetworkManager/system-connections/PLUSNET-G7QZ]] (600 root)
[connection] id=PLUSNET-G7QZ | type=wifi | permissions=user:mike:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=PLUSNET-G7QZ
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'PLUSNET-G7QZ' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"PLUSNET-G7QZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008b17e6a586
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     B9E24DCC76240A48AEEF94E
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
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
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A96EBF28EBD4603749D5EC3
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     632F2E9C01BF2AC04D0F40A
depends:        mac80211,cfg80211
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

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 1195.312407] wlp3s0: authenticated
[ 1195.316487] wlp3s0: associate with <MAC address> (try 1/3)
[ 1195.317922] wlp3s0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[ 1195.318165] wlp3s0: associated
[ 1195.318209] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 1195.411127] wlp3s0: Limiting TX power to 17 (20 - 3) dBm as advertised by <MAC address>
[ 1419.189255] r8169 0000:02:00.0 enp2s0: link up
[ 1419.189273] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[ 1472.946878] wlp3s0: Connection to AP <MAC address> lost
[ 1473.151290] wlp3s0: authenticate with <MAC 'PLUSNET-G7QZ' [AC1]>
[ 1473.151792] wlp3s0: send auth to <MAC 'PLUSNET-G7QZ' [AC1]> (try 1/3)
[ 1473.155945] wlp3s0: authenticated
[ 1473.158827] wlp3s0: associate with <MAC 'PLUSNET-G7QZ' [AC1]> (try 1/3)
[ 1473.185744] wlp3s0: RX AssocResp from <MAC 'PLUSNET-G7QZ' [AC1]> (capab=0x431 status=0 aid=1)
[ 1473.185993] wlp3s0: associated
[ 1483.187969] wlp3s0: deauthenticating from <MAC 'PLUSNET-G7QZ' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1486.304717] wlp3s0: authenticate with <MAC address>
[ 1486.305224] wlp3s0: send auth to <MAC address> (try 1/3)
[ 1486.305841] wlp3s0: authenticated
[ 1486.307925] wlp3s0: associate with <MAC address> (try 1/3)
[ 1486.309389] wlp3s0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[ 1486.309642] wlp3s0: associated
[ 1488.181370] wlp3s0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1491.048519] wlp3s0: authenticate with <MAC address>
[ 1491.048956] wlp3s0: send auth to <MAC address> (try 1/3)
[ 1491.152025] wlp3s0: send auth to <MAC address> (try 2/3)
[ 1491.256011] wlp3s0: send auth to <MAC address> (try 3/3)
[ 1491.360074] wlp3s0: authentication with <MAC address> timed out
[ 1492.432497] wlp3s0: authenticate with <MAC 'PLUSNET-G7QZ' [AC1]>
[ 1492.433006] wlp3s0: send auth to <MAC 'PLUSNET-G7QZ' [AC1]> (try 1/3)
[ 1492.435361] wlp3s0: authenticated
[ 1492.436344] wlp3s0: associate with <MAC 'PLUSNET-G7QZ' [AC1]> (try 1/3)
[ 1492.540103] wlp3s0: associate with <MAC 'PLUSNET-G7QZ' [AC1]> (try 2/3)
[ 1492.546518] wlp3s0: RX AssocResp from <MAC 'PLUSNET-G7QZ' [AC1]> (capab=0x431 status=0 aid=1)
[ 1492.546828] wlp3s0: associated

########## wireless info END ############

```

---

### Post by wildmanne39 on 2016-11-23
Hello, go to the link below and download the new driver zip file to your desktop then right click on the file and click extract here.
[https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex](https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex)

Make sure secure boot is turned off in the bios before you try to install the driver if you have secure boot and it must stay off, otherwise just install the driver.
```
cd rtlwifi_new-rock.new_btcoex
make
sudo make install
sudo modprobe -rv rtl8723ae
sudo modprobe -v rtl8723ae ant_sel=2
```
We may have to change a parameter or two, it looks like you have done a couple on your own.
Thanks

---

### Post by michaelporter on 2016-11-24
Thankyou Wildemann, that worked a treat.
Should I re-enable secure boot? (I don't know what secure boot is??!!)

Thanks once again.

---

### Post by wildmanne39 on 2016-11-24
> **michaelporter said:**
> Thankyou Wildemann, that worked a treat.
Should I re-enable secure boot? (I don't know what secure boot is??!!)

Thanks once again.No, if you re-enable secure boot the driver will stop loading.

---

### Post by michaelporter on 2016-12-01
Unfortunately the same problem occurs after updating.

---

### Post by TheFu on 2016-12-01
If the driver file was replaced, then the driver you downloaded could be gone.  Get it from github again and install.  If that fixes it, great!

May want to blacklist/freeze that specific package so it doesn't get updated.  However, that means when it is fixed finally, you won't get those too.  I'd check every month whether the packaged version is newer than the github version that you have installed.  A reoccurring reminder in a calendar, perhaps?

OTOH, if that doesn't fix it ... probably rerun the wireless-info script and post here again. I dunno.

---

### Post by wildmanne39 on 2016-12-01
Whenever Update Manager installs a newer kernel version, you must recompile the driver:
```
cd rtlwifi_new-rock.new_btcoex
make clean
make
sudo make install
```
reboot then your should have wifi again.
I am sorry I should have included this part of the directions I must have gotten distracted by something.

---

### Post by michaelporter on 2016-12-02
OK that worked thanks

---

### Post by wildmanne39 on 2016-12-02
Your welcome!
Enjoy!

---

