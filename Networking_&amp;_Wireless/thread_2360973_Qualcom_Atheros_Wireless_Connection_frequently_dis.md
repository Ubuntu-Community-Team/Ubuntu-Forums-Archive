---
title: "Qualcom Atheros Wireless Connection frequently disconnects"
date: 2017-05-10
forum: Networking &amp; Wireless
---

### Post by sonicking on 2017-05-10
Hi,

I have an Acer E15 laptop and it comes with Qualcom Atheros wireless card.  A number of people have posted about its driver issue with Linux. The helpful users like chili555 , Jeremy31 have provided suggestions and links to newer drivers.  But even following their help, my computer is still experiencing issue.  In particular, the wireless connection frequently disconnects itself!  I have to reconnect it manually.  It happens so often that it has become a pain.

Running [COLOR=#111111][FONT=Consolas]lspci -nnk | grep -iA2 net; dmesg | grep ath10k
[/FONT][/COLOR]
```
02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
    Kernel driver in use: ath10k_pci
--
03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
    Kernel driver in use: r8169
    Kernel modules: r8169
[   11.771604] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   13.307020] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   15.619585] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 11ad:0806) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   15.619589] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   15.815175] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   36.286763] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  498.306143] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  498.408627] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  498.409242] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  498.511030] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  527.375799] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  565.306543] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  578.317394] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  578.428412] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  739.466968] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  739.467212] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  739.580752] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  771.400556] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  791.582248] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!

```[COLOR=#111111][FONT=Consolas]

[/FONT][/COLOR]It shows there is still an error.  I can't help but wonder if that's what causes my disconnect issue.  Can someone make some suggestions?  Thanks!

---

### Post by jeremy31 on 2017-05-10
Has wifi power management been disabled?  Check ```
iwconfig
```

---

### Post by sonicking on 2017-05-10
Yes. Power Management has been disabled.

---

### Post by jeremy31 on 2017-05-10
See the wireless script link in my signature and post results

---

### Post by sonicking on 2017-05-10
```


########## wireless info START ##########


Report from: 10 May 2017 12:07 EDT -0400


Booted last: 10 May 2017 00:00 EDT -0400


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-77-generic #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, pci=acpi, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
	Subsystem: Lite-On Communications Inc Device [11ad:0806]
	Kernel driver in use: ath10k_pci


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b573 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0461:4e22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
wmi                    20480  1 acer_wmi
video                  40960  2 i915_bpo,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f1  Link encap:Ethernet  HWaddr <MAC 'enp3s0f1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3878654 (3.8 MB)  TX bytes:781958 (781.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:760221 (760.2 KB)  TX bytes:760221 (760.2 KB)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::307a:32db:165c:db96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91649396 (91.6 MB)  TX bytes:24926909 (24.9 MB)


##### iwconfig ##########################


enp3s0f1  no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"FiOS-P0HBK"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'FiOS-P0HBK' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:78   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search fios-router.home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       843     1  0 11:12 ?        00:00:06 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-77-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FiOS-P0HBK
GENERAL.CON-UUID:                       66249d45-0f9d-4730-aab3-ec140f62365c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/21
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,3,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   eb335e55-9cec-4a0d-ae58-89549c65b3d2 | FiOS-3HCE1-5G
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   66249d45-0f9d-4730-aab3-ec140f62365c | FiOS-P0HBK
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   756e566e-1741-4233-8d82-264c3edb04c6 | FiOS-P0HBK-5G 1
IP4.ADDRESS[1]:                         192.168.1.159/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          fios-router.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.159
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1494518733
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = fios-router.home
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       domain_search = fios-router.home.
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       routers = 192.168.1.1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::307a:32db:165c:db96/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.3/0000:03:00.1/net/enp3s0f1
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
FiOS-P0HBK     <MAC 'FiOS-P0HBK' [AC1]>  Infra  9     2452 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2              yes     * 
--             <MAC '--' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
HOME-9A41-2.4  <MAC 'HOME-9A41-2.4' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2         no        
xfinitywifi    <MAC 'xfinitywifi' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  --                no        
--             <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC7]>  Infra  157   5785 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2              no        
FiOS-P0HBK-5G  <MAC 'FiOS-P0HBK-5G' [AC6]>  Infra  157   5785 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2              no        
--             <MAC '--' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  --                no        
--             <MAC '--' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2         no        
FiOS-3HCE1-5G  <MAC 'FiOS-3HCE1-5G' [AC2]>  Infra  40    5200 MHz  54 Mbit/s  29      &#9602;___  WPA2              no        
--             <MAC '--' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2              no        
--             <MAC '--' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2         no        
Lauren         <MAC 'Lauren' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2         no        
--             <MAC '--' [AN13]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA2              no        
HOME-AB68      <MAC 'HOME-AB68' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2         no        
HOME-9A41-5    <MAC 'HOME-9A41-5' [AC3]>  Infra  149   5745 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2         no        
--             <MAC '--' [AN16]>  Infra  149   5745 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2 802.1X  no        
--             <MAC '' [AC4]>  Infra  149   5745 MHz  54 Mbit/s  17      &#9602;___  --                no        
xfinitywifi    <MAC 'xfinitywifi' [AC5]>  Infra  149   5745 MHz  54 Mbit/s  17      &#9602;___  --                no        


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


[[/etc/NetworkManager/system-connections/FiOS-P0HBK]] (600 root)
[connection] id=FiOS-P0HBK | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-3HCE1-5G]] (600 root)
[connection] id=FiOS-3HCE1-5G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-3HCE1-5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AsusWifi]] (600 root)
[connection] id=AsusWifi | type=wifi | permissions=user:aaron:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=AsusWifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-P0HBK-5G 1]] (600 root)
[connection] id=FiOS-P0HBK-5G 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK-5G
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp3s0f1  no frequency information.


lo        no frequency information.


wlp2s0    32 channels in total; available frequencies :
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
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


enp3s0f1  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:5.2 GHz (Channel 40)
      3   APs on   Frequency:5.745 GHz (Channel 149)
      2   APs on   Frequency:5.785 GHz


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'FiOS-P0HBK' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"FiOS-P0HBK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000906b32d98b
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FiOS-3HCE1-5G' [AC2]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"FiOS-3HCE1-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009028c77038
                    Extra: Last beacon: 4800ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME-9A41-5' [AC3]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"HOME-9A41-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036e112803b
                    Extra: Last beacon: 988ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036e112822c
                    Extra: Last beacon: 988ms ago
          Cell 05 - Address: <MAC 'xfinitywifi' [AC5]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036e1128557
                    Extra: Last beacon: 988ms ago
          Cell 06 - Address: <MAC 'FiOS-P0HBK-5G' [AC6]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"FiOS-P0HBK-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000906ad02044
                    Extra: Last beacon: 608ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC7]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000906ad0225b
                    Extra: Last beacon: 608ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.4.0-77-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-77-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.4.0-77-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2270F04573C68C47B0DF2B4
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-77-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.4.0-77-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-77-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-77-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0EDE2F31518E91FFBB1E4EC
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-77-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-77-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     48C96882CCDC964173BE1D1
depends:        
intree:         Y
vermagic:       4.4.0-77-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


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


[ 3119.007659] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[ 3123.700068] wlp2s0: authenticate with <MAC 'FiOS-P0HBK-5G' [AC6]>
[ 3123.727978] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC6]> (try 1/3)
[ 3123.729043] wlp2s0: authenticated
[ 3123.733140] wlp2s0: associate with <MAC 'FiOS-P0HBK-5G' [AC6]> (try 1/3)
[ 3123.735957] wlp2s0: RX AssocResp from <MAC 'FiOS-P0HBK-5G' [AC6]> (capab=0x11 status=0 aid=1)
[ 3123.738522] wlp2s0: associated
[ 3123.743140] ath: EEPROM regdomain: 0x8348
[ 3123.743144] ath: EEPROM indicates we should expect a country code
[ 3123.743147] ath: doing EEPROM country->regdmn map search
[ 3123.743149] ath: country maps to regdmn code: 0x3a
[ 3123.743151] ath: Country alpha2 being used: US
[ 3123.743153] ath: Regpair used: 0x3a
[ 3123.743155] ath: regdomain 0x8348 dynamically updated by country IE
[ 3123.822778] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'FiOS-P0HBK-5G' [AC6]>
[ 3165.984578] wlp2s0: deauthenticating from <MAC 'FiOS-P0HBK-5G' [AC6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3166.030889] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[ 3170.710394] wlp2s0: authenticate with <MAC 'FiOS-P0HBK-5G' [AC6]>
[ 3170.738262] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC6]> (try 1/3)
[ 3170.739079] wlp2s0: authenticated
[ 3170.742062] wlp2s0: associate with <MAC 'FiOS-P0HBK-5G' [AC6]> (try 1/3)
[ 3170.744775] wlp2s0: RX AssocResp from <MAC 'FiOS-P0HBK-5G' [AC6]> (capab=0x11 status=0 aid=1)
[ 3170.747731] wlp2s0: associated
[ 3170.751265] ath: EEPROM regdomain: 0x8348
[ 3170.751269] ath: EEPROM indicates we should expect a country code
[ 3170.751271] ath: doing EEPROM country->regdmn map search
[ 3170.751273] ath: country maps to regdmn code: 0x3a
[ 3170.751274] ath: Country alpha2 being used: US
[ 3170.751276] ath: Regpair used: 0x3a
[ 3170.751278] ath: regdomain 0x8348 dynamically updated by country IE
[ 3170.846265] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'FiOS-P0HBK-5G' [AC6]>
[ 3187.146062] wlp2s0: deauthenticating from <MAC 'FiOS-P0HBK-5G' [AC6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3187.237438] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[ 3191.897847] wlp2s0: authenticate with <MAC 'FiOS-P0HBK' [AC1]>
[ 3191.934270] wlp2s0: send auth to <MAC 'FiOS-P0HBK' [AC1]> (try 1/3)
[ 3191.935870] wlp2s0: authenticated
[ 3191.939538] wlp2s0: associate with <MAC 'FiOS-P0HBK' [AC1]> (try 1/3)
[ 3191.942909] wlp2s0: RX AssocResp from <MAC 'FiOS-P0HBK' [AC1]> (capab=0x431 status=0 aid=4)
[ 3191.944666] wlp2s0: associated
[ 3191.947426] ath: EEPROM regdomain: 0x8348
[ 3191.947428] ath: EEPROM indicates we should expect a country code
[ 3191.947429] ath: doing EEPROM country->regdmn map search
[ 3191.947431] ath: country maps to regdmn code: 0x3a
[ 3191.947432] ath: Country alpha2 being used: US
[ 3191.947433] ath: Regpair used: 0x3a
[ 3191.947434] ath: regdomain 0x8348 dynamically updated by country IE


########## wireless info END ############



```

---

### Post by sonicking on 2017-05-10
I must add that when the connection is working, it is great and I get fast speed.  The problem is that it disconnects frequently!  I cannot go to any website.  It keeps saying "resolving host" on the corner.  I have to manually reconnect.

---

### Post by jeremy31 on 2017-05-10
Do you see any big swings in the signal level with
```
watch -n 1 cat /proc/net/wireless
```
When connected to the router

---

### Post by sonicking on 2017-05-10
Hi, I see that under "Quality" - link and level are changing. Link is between 32-60; level is between 48-73.   But this is when the connection is working.  I want to check again when "Resolving Host" is flashing.

---

### Post by sonicking on 2017-05-10
Ok. So the ranges are pretty much what I wrote.  Do they look strange or normal?

---

### Post by jeremy31 on 2017-05-10
They shouldn't vary that much.  Please file a bug report, see [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)
I would file against package linux.  I saw a similar issue with disconnects using 5Ghz using a USB Edimax adapter but I figured it was because of either using tethering on my cell phone or an issue with the source code I got from github.
I imagine using 2.4 Ghz has no issues with the signal strength

---

