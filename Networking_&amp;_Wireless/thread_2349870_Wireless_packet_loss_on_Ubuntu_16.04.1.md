---
title: "Wireless packet loss on Ubuntu 16.04.1"
date: 2017-01-19
forum: Networking &amp; Wireless
---

### Post by crsftw on 2017-01-19
Hello,

I am having packet loss when communicating from my Ubuntu PC to the router.


**From PC->router:**
```

64 bytes from 192.168.1.1: icmp_seq=42 ttl=64 time=147 ms
64 bytes from 192.168.1.1: icmp_seq=43 ttl=64 time=106 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=64 time=108 ms
64 bytes from 192.168.1.1: icmp_seq=45 ttl=64 time=3.47 ms
^C
--- 192.168.1.1 ping statistics ---
45 packets transmitted, 40 received, 11% packet loss, time 44086ms
rtt min/avg/max/mdev = 0.969/12.012/147.158/31.411 ms
cristi@miner2:~$ 

```

**From other PC to Ubuntu:**
```

64 bytes from 192.168.1.171: icmp_seq=42 ttl=64 time=41.0 ms
64 bytes from 192.168.1.171: icmp_seq=43 ttl=64 time=121 ms
^C
--- 192.168.1.171 ping statistics ---
43 packets transmitted, 40 received, 6% packet loss, time 42080ms
rtt min/avg/max/mdev = 0.950/49.754/121.262/27.756 ms
cristi@x1:~$ 

```

Ubuntu is running from a USB stick, has enough RAM (4GB), CPU load is ok, no high traffic usage on the interface and I don't see high read/write on the USB stick (iotop).
I have tried with 2 different USB wireless cards, on multiple USB port (USB 2.0 and 3x).
I have updated the system multiple times, changed the wireless channel, changed the wireless authentication method from WPA-Personal to WPa-Auto-Personal.
Other wireless devices (laptop,smartphone,ipad) had no wireless issues at all.

Using the script I found out that I had power management on and I fixed that with:

```

sudo iwconfig wlx54e6fc921212 power off

```

```

cristi@miner2:~/wireless_troubleshooting$ grep -i power wireless-info.txt1
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Power Management:**on**
cristi@miner2:~/wireless_troubleshooting$ grep -i power wireless-info.txt
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Power Management:**off**
cristi@miner2:~/wireless_troubleshooting$ 

```

I also stopped acpid:

```
sudo /etc/init.d/acpid stop
```

And:
```
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

Also did router firmware update and reboot.

What am I missing ?
Any help if more than welcome.

Thank you.


```

cristi@miner2:~/wireless_troubleshooting$ cat wireless-info.txt


########## wireless info START ##########


Report from: 19 Jan 2017 13:50 EET +0200


Booted last: 19 Jan 2017 00:00 EET +0200


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


Cinnamon (from ~/.dmrc)


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:859e]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 003 Device 002: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              737280  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
wmi                    20480  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67654 errors:0 dropped:1 overruns:0 frame:0
          TX packets:64231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10462854 (10.4 MB)  TX bytes:53007337 (53.0 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"crs"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'crs' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:90  Invalid misc:9   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx<IF from MAC [IF2]>
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       964     1  0 00:23 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.4.0-59-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     mywireless
GENERAL.CON-UUID:                       9e222b73-f2e9-439e-80a8-c08bd214711e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9e222b73-f2e9-439e-80a8-c08bd214711e | crs
IP4.ADDRESS[1]:                         192.168.1.171/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             192.168.1.1
IP4.DNS[3]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 8.8.8.8 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.171
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1484911664
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = miner2
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
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


SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
DIGI221                      <MAC 'DIGI221' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
dd                               <MAC 'dd' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
DIGI4105                        <MAC 'DIGI4105' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
mywireless                              <MAC 'mywireless' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  yes     * 
Warning: Infected Network  <MAC 'Infected Network' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
DIGI8ED                        <MAC 'DIGI8ED' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
NAST                         <MAC 'NAST' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/mywireless]] (600 root)
[connection] id=mywireless | type=wifi | permissions=user:cri:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=crs
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/crs 1]] (600 root)
[connection] id=mywireless 1 | type=wifi | permissions=user:cri:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=mywireless
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Bucharest (based on set time zone)


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


enp3s0    no frequency information.


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
          Current Frequency:2.457 GHz (Channel 10)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'crs' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"mywireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004a9f041d
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIGI-105' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"DIGI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000105b8dcea47
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'DIGI-2' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"DIGI-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a35d8dc445
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Infected Network' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Infected Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004ec6c6ed072
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'DIGI-F' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"DIGI-F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002befb05aa
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CD175F3067617C23A4A79F3
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     FADD78F4B0B6C8F4DDFA8E5
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


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


##### module parameters #################


[rt2800usb]
nohwcrypt: N


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


[/etc/modprobe.d/blacklist-radeon.conf]
blacklist radeon


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


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[  100.076876] wlx<IF from MAC [IF2]>: authenticated
[  100.080284] wlx<IF from MAC [IF2]>: associate with <MAC 'mywireless' [AC1]> (try 1/3)
[  100.083402] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'mywireless' [AC1]> (capab=0x411 status=0 aid=1)
[  100.086313] wlx<IF from MAC [IF2]>: associated
[  100.086354] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[ 6013.106774] wlx<IF from MAC [IF2]>: authenticate with <MAC 'mywireless' [AC1]>
[ 6013.141657] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 1/3)
[ 6013.143286] wlx<IF from MAC [IF2]>: authenticated
[ 6013.143608] wlx<IF from MAC [IF2]>: associate with <MAC 'mywireless' [AC1]> (try 1/3)
[ 6013.146885] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'mywireless' [AC1]> (capab=0x411 status=0 aid=1)
[ 6013.149744] wlx<IF from MAC [IF2]>: associated
[ 7374.123634] wlx<IF from MAC [IF2]>: authenticate with <MAC 'mywireless' [AC1]>
[ 7374.158692] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 1/3)
[ 7374.276419] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 2/3)
[ 7374.295643] wlx<IF from MAC [IF2]>: authenticated
[ 7374.296483] wlx<IF from MAC [IF2]>: associate with <MAC 'mywireless' [AC1]> (try 1/3)
[ 7374.382608] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'mywireless' [AC1]> (capab=0x411 status=0 aid=1)
[ 7374.385357] wlx<IF from MAC [IF2]>: associated
[47125.821238] wlx<IF from MAC [IF2]>: authenticate with <MAC 'mywireless' [AC1]>
[47125.856147] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 1/3)
[47125.857711] wlx<IF from MAC [IF2]>: authenticated
[47125.858107] wlx<IF from MAC [IF2]>: associate with <MAC 'mywireless' [AC1]> (try 1/3)
[47125.861208] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'mywireless' [AC1]> (capab=0x411 status=0 aid=2)
[47125.864046] wlx<IF from MAC [IF2]>: associated
[47136.589000] wlx<IF from MAC [IF2]>: authenticate with <MAC 'mywireless' [AC1]>
[47136.628141] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 1/3)
[47136.687651] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 2/3)
[47136.740794] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 3/3)
[47136.781103] wlx<IF from MAC [IF2]>: authentication with <MAC 'mywireless' [AC1]> timed out
[47150.431424] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[47177.592594] wlx<IF from MAC [IF2]>: authenticate with <MAC 'mywireless' [AC1]>
[47177.610923] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 1/3)
[47177.612407] wlx<IF from MAC [IF2]>: authenticated
[47177.612779] wlx<IF from MAC [IF2]>: associate with <MAC 'mywireless' [AC1]> (try 1/3)
[47177.615905] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'mywireless' [AC1]> (capab=0x411 status=0 aid=1)
[47177.619165] wlx<IF from MAC [IF2]>: associated
[47177.619202] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[47320.382885] wlx<IF from MAC [IF2]>: deauthenticated from <MAC 'mywireless' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[47320.470320] wlx<IF from MAC [IF2]>: authenticate with <MAC 'mywireless' [AC1]>
[47320.491740] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 1/3)
[47320.493227] wlx<IF from MAC [IF2]>: authenticated
[47320.493563] wlx<IF from MAC [IF2]>: associate with <MAC 'mywireless' [AC1]> (try 1/3)
[47320.498405] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'crs' [AC1]> (capab=0x411 status=0 aid=1)
[47320.501461] wlx<IF from MAC [IF2]>: associated


########## wireless info END ############


cristi@miner2:~/wireless_troubleshooting$ 



```

---

### Post by Hadaka on 2017-01-19
Hi,please do if Region is correct.
# REGION = Europe/Bucharest
```
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```
Boot and test wireless and please post a new wireless
diagnostic report if you are still having issues.

*Running the OS from usb is going to be slower and have
have less performance. Especially with the RT2800 driver.
Thanks.

---

### Post by crsftw on 2017-01-19
Thank you for the suggestion, but that did not work.
In the script I see this line:
```
Tx excessive retries:87  Invalid misc:67
```
Not sure if that is relevant...

Here's the output again:
```



########## wireless info START ##########




Report from: 19 Jan 2017 17:25 EET +0200


Booted last: 19 Jan 2017 00:00 EET +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon (from ~/.dmrc)


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:859e]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 003 Device 002: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              737280  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
wmi                    20480  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23583 (23.5 KB)  TX bytes:27832 (27.8 KB)


wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87994 (87.9 KB)  TX bytes:83929 (83.9 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"mywireless"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'mywireless' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:87  Invalid misc:67   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx<IF from MAC [IF2]>
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       906     1  0 17:17 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.4.0-59-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     mywireless
GENERAL.CON-UUID:                       9e222b73-f2e9-439e-80a8-c08bd214711e
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9e222b73-f2e9-439e-80a8-c08bd214711e | mywireless
IP4.ADDRESS[1]:                         192.168.1.171/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             192.168.1.1
IP4.DNS[3]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 8.8.8.8 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.171
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1484925440
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = miner2
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)


GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 


DI-105                         <MAC 'DI-105' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Rla                           <MAC 'Rla' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
DI-F8ED                        <MAC 'DI-F8ED' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
mywireless                              <MAC 'mywireless' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  51      &#9602;&#9604;__  WPA1 WPA2  yes     * 
NAST                         <MAC 'NAST' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
Infected Network  <MAC 'Infected Network' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
In                             <MAC 'In' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
ASUS_Guest1                      <MAC 'ASUS_Guest1' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
ASUS_Guest3                      <MAC 'ASUS_Guest3' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
ASUS_Guest2                      <MAC 'ASUS_Guest2' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        


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


[[/etc/NetworkManager/system-connections/mywireless]] (600 root)
[connection] id=mywireless | type=wifi | permissions=user:cristi:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=mywireless
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/mywireless 1]] (600 root)
[connection] id=mywireless 1 | type=wifi | permissions=user:cristi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=mywireless
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Bucharest (based on set time zone)


country RO: DFS-ETSI


	(2402 - 2482 @ 40), (N/A, 20), (N/A)


	(5170 - 5250 @ 80), (N/A, 20), (N/A)
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS


	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp3s0    no frequency information.


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


          Current Frequency:2.457 GHz (Channel 10)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'mywireless' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"mywireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master


                    Extra:tsf=000000034aec64f5
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Rla' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)


                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on


                    ESSID:"Rla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master


                    Extra:tsf=00000011a40f6c07
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'DI-105' [AC3]>


                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on


                    ESSID:"DI-105"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master


                    Extra:tsf=00000108b931a8a7
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NAST' [AC4]>


                    Channel:1
                    Frequency:2.412 GHz (Channel 1)


                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on


                    ESSID:"NAST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026b02199e7
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'In' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"In"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master


                    Extra:tsf=0000015580478a18
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


          Cell 06 - Address: <MAC 'ASUS_Guest1' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ASUS_Guest1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001558047989d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ASUS_Guest2' [AC7]>


                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on


                    ESSID:"ASUS_Guest2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master


                    Extra:tsf=000001558047ab8e
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


          Cell 08 - Address: <MAC 'ASUS_Guest3' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ASUS_Guest3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001558047d435
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'DI-F8ED' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on








                    ESSID:"DI-F8ED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master


                    Extra:tsf=00000005bf4e3667
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1




                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Infected Network' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Infected Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004ef6cc119f4
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CD175F3067617C23A4A79F3
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     FADD78F4B0B6C8F4DDFA8E5
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


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


##### module parameters #################


[rt2800usb]
nohwcrypt: N


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


[/etc/modprobe.d/blacklist-radeon.conf]
blacklist radeon


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


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    8.797702] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[    8.807549] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[    9.237517] rt2800usb 3-3:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   97.224529] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[   97.224560] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   97.232698] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   97.415861] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[   97.419389] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   97.483563] r8169 0000:03:00.0 enp3s0: link down
[   97.483613] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   97.677397] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[   98.647443] wlx<IF from MAC [IF2]>: authenticate with <MAC 'mywireless' [AC1]>
[   98.672107] wlx<IF from MAC [IF2]>: send auth to <MAC 'mywireless' [AC1]> (try 1/3)
[   98.673547] wlx<IF from MAC [IF2]>: authenticated
[   98.677106] wlx<IF from MAC [IF2]>: associate with <MAC 'mywireless' [AC1]> (try 1/3)
[   98.682093] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'mywireless' [AC1]> (capab=0x411 status=0 aid=1)
[   98.684689] wlx<IF from MAC [IF2]>: associated
[   98.684714] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[  272.713287] r8169 0000:03:00.0 enp3s0: link up
[  272.713302] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  396.720070] r8169 0000:03:00.0 enp3s0: link down


########## wireless info END ############



```

Any other suggestions ?
If I update the drivers, would that make a change?
Any advice on how to update the driver?

---

### Post by praseodym on 2017-01-19
Add the mtu-value of your ISP as a number instead of "Automatic" in the network profíle. Reconnect.

---

### Post by jeremy31 on 2017-01-19
Prevent power management from enabling itself with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Reboot

---

### Post by crsftw on 2017-01-19
Tried both solutions, but no change:

wlx3c330072f715 Link encap:Ethernet  HWaddr 3c:33:00:72:f7:15
          inet addr:192.168.1.130  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::14a4:424:7270:1d74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  **MTU:1492**  Metric:1

I used 2 wireless NICs.
One is supported (TP-Link TL-WN727N) in [https://wireless.wiki.kernel.org/en/users/drivers/rt2800usb/](https://wireless.wiki.kernel.org/en/users/drivers/rt2800usb/)  and the other is not (Alfa_Network AWUS036NH)

After the MTU change i issued:
```

sudo service network-manager restart

```

This should be enough, right ?
Any other ideas ?

Thank you.

---

### Post by crsftw on 2017-01-22
Ok, so it seems that the problem is somehow related to kernel.
Using Linux 4.4.0-59-generic I had the inital problems I reported above.
Using Linux 4.4.0-31-generic I have packet loss of "only" 1%.

---

