---
title: "Alienware 17 R3 with Killer 1535 wireless adapter issue"
date: 2015-12-05
forum: Networking &amp; Wireless
---

### Post by jaime3 on 2015-12-05
Hi I need to get my wireless working I am using Ubuntu Gnome. I can't get it to work. Ubuntu doesn't detect it.

---

### Post by Hadaka on 2015-12-05
Hi, go here..
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
 post the wireless-info.txt file to help us find a possible solution.

---

### Post by jaime3 on 2015-12-05
########## wireless info START ##########


Report from: 05 Dec 2015 17:29 PST -0800


Booted last: 05 Dec 2015 00:00 PST -0800


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################




3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0a1] (rev 10)
	Subsystem: Device [0707:2400]
	Kernel driver in use: alx


3c:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Bigfoot Networks, Inc. Device [1a56:1535]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 002: ID 187c:0528 Alienware Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: dell-rbtn: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             40960  0
ath10k_core           278528  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              733184  1 ath10k_core
cfg80211              548864  3 ath,mac80211,ath10k_core
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau
video                  36864  3 i915,dell_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################

---

### Post by jaime3 on 2015-12-05
> **Hadaka said:**
> Hi, go here..
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
 post the wireless-info.txt file to help us find a possible solution.


########## wireless info START ##########


Report from: 05 Dec 2015 17:29 PST -0800


Booted last: 05 Dec 2015 00:00 PST -0800


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################




3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0a1] (rev 10)
    Subsystem: Device [0707:2400]
    Kernel driver in use: alx


3c:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1535]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 002: ID 187c:0528 Alienware Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath10k_pci             40960  0
ath10k_core           278528  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              733184  1 ath10k_core
cfg80211              548864  3 ath,mac80211,ath10k_core
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau
video                  36864  3 i915,dell_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################

---

### Post by Hadaka on 2015-12-05
Hi, both reports are incomplete, did you download
a backport for your wireless driver? do you have that link?
and please post the output of..
```
dmesg | grep ath
```
thanks.

---

### Post by jaime3 on 2015-12-06
Hello No actually. I did a fresh install then did all the update then clicked on additional drivers to install nvidia anyways ran the  
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info
Then dmesg | grep ath        

Now did you wanted me to fallow like the link u mention first? I tried it and didn't work. So what shall I do? Ty






########## wireless info START ##########

Report from: 05 Dec 2015 22:44 PST -0800

Booted last: 05 Dec 2015 00:00 PST -0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0a1] (rev 10)
    Subsystem: Device [0707:2400]
    Kernel driver in use: alx

3c:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1535]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 002: ID 187c:0528 Alienware Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ath10k_pci             40960  0
ath10k_core           278528  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              733184  1 ath10k_core
cfg80211              548864  3 ath,mac80211,ath10k_core
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0
wmi                    20480  2 dell_wmi,mxm_wmi
video                  36864  2 i915,dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp59s0   Link encap:Ethernet  HWaddr <MAC 'enp59s0' [IF]>  
          inet addr:192.168.0.29  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp59s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6704367 (6.7 MB)  TX bytes:582509 (582.5 KB)
          Interrupt:16 

wlp60s0   Link encap:Ethernet  HWaddr <MAC 'wlp60s0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp59s0   no wireless extensions.

wlp60s0   IEEE 802.11abgn  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thrff   Fragment thrff
          Power Managementf
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp59s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp59s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp59s0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ca.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       634     1  1 22:38 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp59s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Sunrise Point-H PCI Express Root Port
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp59s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:3b:00.0/net/enp59s0
GENERAL.IP-IFACE:                       enp59s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b4343b11-97e4-476b-9aec-9d0f251ab7d4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b4343b11-97e4-476b-9aec-9d0f251ab7d4 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.29/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ca.comcast.net.
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 192.168.0.29
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = hsd1.ca.comcast.net.
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1449470562
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp59s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp60s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.2.0-19-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00180-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp60s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:3c:00.0/net/wlp60s0
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

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

enp59s0   no frequency information.

wlp60s0   32 channels in total; available frequencies :
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

##### iwlist scan #######################

wlp60s0   Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp59s0   Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     5EB8A069F322875ED643860
depends:        ath10k_core
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     D76101C7C5BBFFDAA2F1098
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)

[ath]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9D:EE:C2:96:8B:FCA:67:407:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9D:EE:C2:96:8B:FCA:67:407:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9D:EE:C2:96:8B:FCA:67:407:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
debug_mask: 0
skip_otp: N
uart_print: N

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   12.050864] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready (repeated 2 times)
[   12.052038] alx 0000:3b:00.0 enp59s0: NIC Up: 1 Gbps Full
[   12.052249] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready
[   12.384146] ath: EEPROM regdomain: 0x69
[   12.384148] ath: EEPROM indicates we should expect a direct regpair map
[   12.384149] ath: Country alpha2 being used: 00
[   12.384150] ath: Regpair used: 0x69
[   12.404881] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[   12.428336] IPv6: ADDRCONF(NETDEV_UP): wlp60s0: link is not ready
[   17.643567] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   20.643080] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   28.925711] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   31.925233] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   40.203913] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   43.203476] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   52.298014] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[   55.297542] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   63.580216] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   66.579732] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   74.898405] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   77.897851] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   86.180549] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   89.180139] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   97.466741] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  100.466325] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  108.748997] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  111.748519] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  120.035175] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  123.034697] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  131.317377] ath10k_pci 0000:3c:00.0: failed to enable adaptive qcs: -11
[  134.316902] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  142.599552] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  145.599100] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  153.881774] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  156.881217] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  165.163947] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  168.163478] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  176.450153] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  179.449675] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  187.740352] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[  190.739853] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  199.026539] ath10k_pci 0000:3c:00.0: failed to enable ani by default: -11
[  202.026051] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  210.360721] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  213.360168] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  221.646916] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  224.646379] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  232.941106] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  235.940579] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  244.227300] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  247.226834] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  257.005243] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[  260.004747] ath10k_pci 0000:3c:00.0: could not suspend target (-11)

########## wireless info END ############




















-Alienware-17-R3:~$ dmesg | grep ath
[    5.380927] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[    5.385383] ath10k_pci 0000:3c:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    5.633474] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-0000:3c:00.0.bin failed with error -2
[    5.634650] ath10k_pci 0000:3c:00.0: Direct firmware load for  ath10k/QCA6174/hw3.0/board-pci-168c:003e:1a56:1535.bin failed with error  -2
[    5.634652] ath10k_pci 0000:3c:00.0: failed to load spec board file, falling back to generic: -2
[    5.755380] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    5.755383] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    8.319314] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 (0x05030000,  0x00340aff, 168c:003e:1a56:1535 fallback) fw  WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 htt 3.26 wmi 4 cal otp max_sta 32
[    8.319317] ath10k_pci 0000:3c:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    9.316897] ath10k_pci 0000:3c:00.0: suspend timed out - target pause event never came
[   12.384146] ath: EEPROM regdomain: 0x69
[   12.384148] ath: EEPROM indicates we should expect a direct regpair map
[   12.384149] ath: Country alpha2 being used: 00
[   12.384150] ath: Regpair used: 0x69
[   12.404881] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[   17.643567] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   20.643080] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   28.925711] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   31.925233] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   40.203913] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   43.203476] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   52.298014] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[   55.297542] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   63.580216] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   66.579732] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   74.898405] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   77.897851] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   86.180549] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   89.180139] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   92.257745] audit: type=1400 audit(1449384002.987:23):  apparmor="DENIED" operation="open"  profile="/usr/lib/telepathy/mission-control-5"  name="/usr/share/dconf/profile/gdm" pid=1285 comm="mission-control"  requested_mask="r" denied_mask="r" fsuid=120 ouid=0
[   97.466741] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  100.466325] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  108.748997] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  111.748519] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  120.035175] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  123.034697] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  131.317377] ath10k_pci 0000:3c:00.0: failed to enable adaptive qcs: -11
[  134.316902] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  142.599552] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  145.599100] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  153.881774] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  156.881217] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  165.163947] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  168.163478] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  176.450153] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  179.449675] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  187.740352] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[  190.739853] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  199.026539] ath10k_pci 0000:3c:00.0: failed to enable ani by default: -11
[  202.026051] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  210.360721] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  213.360168] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  221.646916] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  224.646379] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  232.941106] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  235.940579] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  244.227300] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  247.226834] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  257.005243] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[  260.004747] ath10k_pci 0000:3c:00.0: could not suspend target (-11)

---

