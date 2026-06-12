---
title: "[Solved]Killer 1535 not working"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by Danny_Saba on 2016-04-26
Info about system, it's a self built desktop. Wifi works fine in WIndows.

I am unable to get my Killer 1535 wireless adapter to function. I am currently running 16.04 with kernel 4.5.2, from my understanding the driver should already be in this kernel. I see ath10k under lib with the board.bin file.


[http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian](http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian)

```
sudo lshw -C network
```

output

```
*-network DISABLED      
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 32
       serial: 9c:b6:d0:02:c6:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
```


The two ethernet adapters are enabled and function.


[COLOR=#242729][FONT=Consolas]```
lspci -vq | grep -i wireless -B 1 -A 5
```

Output: 

[/FONT][/COLOR]```
04:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 141
    Memory at dc200000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
```

---

### Post by jeremy31 on 2016-04-26
Likely missing firmware
```
sudo apt-get install git
git clone https://github.com/jeremyb31/ath10k-firmware.git
sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
```

Reboot

---

### Post by Danny_Saba on 2016-04-26
> **jeremy31 said:**
> Likely missing firmware
```
sudo apt-get install git
git clone https://github.com/jeremyb31/ath10k-firmware.git
sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
```

Reboot


Just tried and still disabled,  I thought that was going to work because I didn't add the firmware.


```
sudo ifconfig wlp4s0 up
```

Output

```
SIOCSIFFLAGS: Resource temporarily unavailable
```

---

### Post by jeremy31 on 2016-04-26
Danny please open terminal and enter ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

Then paste the contents of the wireless-info.**txt** file

Hopefully it is just a soft block causing your disabled status

Welcome to the forums

---

### Post by Danny_Saba on 2016-04-26
> **jeremy31 said:**
> Danny please open terminal and enter ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

Then paste the contents of the wireless-info.**txt** file

Hopefully it is just a soft block causing your disabled status

Welcome to the forums


Thanks!

Aww no blocks

```
########## wireless info START ##########


Report from: 26 Apr 2016 18:10 EDT -0400


Booted last: 26 Apr 2016 00:00 EDT -0400


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.5.2-040502-generic #201604200335 SMP Wed Apr 20 07:37:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection (2) I219-V [1458:e000]
    Kernel driver in use: e1000e


04:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:1535]
    Kernel driver in use: ath10k_pci


05:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller [1969:e0a1] (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Killer E2400 Gigabit Ethernet Controller [1458:e000]
    Kernel driver in use: alx


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 045b:0210 Hitachi, Ltd 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 004: ID 046a:00b5 Cherry GmbH 
Bus 001 Device 003: ID 046d:c24a Logitech, Inc. G600 Gaming Mouse
Bus 001 Device 006: ID 1b1c:0c09 Corsair 
Bus 001 Device 002: ID 045b:0209 Hitachi, Ltd 
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


mxm_wmi                16384  0
ath10k_pci             45056  0
ath10k_core           319488  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              741376  1 ath10k_core
cfg80211              577536  3 ath,mac80211,ath10k_core
wmi                    20480  1 mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:da100000-da120000 


enp5s0    Link encap:Ethernet  HWaddr <MAC 'enp5s0' [IF]>  
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f7b2:9f33:44e1:561d/64 Scope:Link
          inet6 addr: 2601:42:800:fb9e:1b89:1e15:8955:857b/64 Scope:Global
          inet6 addr: 2601:42:800:fb9e:ac3d:3efc:9812:f2f0/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12748012 (12.7 MB)  TX bytes:1278568 (1.2 MB)
          Interrupt:18 


wlp4s0    Link encap:Ethernet  HWaddr <MAC 'wlp4s0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp5s0    no wireless extensions.


enp0s31f6  no wireless extensions.


lo        no wireless extensions.


wlp4s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp5s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp5s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       783     1  0 17:42 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Killer E2400 Gigabit Ethernet Controller
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp5s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/enp5s0
GENERAL.IP-IFACE:                       enp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       ef20bd18-7fff-4457-aae6-2ebf75630036
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ef20bd18-7fff-4457-aae6-2ebf75630036 | Wired connection 2
IP4.ADDRESS[1]:                         192.168.1.40/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.40
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
DHCP4.OPTION[20]:                       expiry = 1461793339
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = Lian-Li
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         2601:42:800:fb9e:ac3d:3efc:9812:f2f0/64
IP6.ADDRESS[2]:                         2601:42:800:fb9e:1b89:1e15:8955:857b/64
IP6.ADDRESS[3]:                         fe80::f7b2:9f33:44e1:561d/64
IP6.GATEWAY:                            fe80::fa32:e4ff:fe53:7ec8
IP6.DNS[1]:                             2601:42:800:fb9e::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2601:42:800:fb9e::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:0:0:0:0:0:0
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_info_refresh_time = 600
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:67:ad:28:c0:7e:cf:1a:59:eb:93:a6:ae:4a:40:e6:77


GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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


GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.5.2-040502-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00180-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp4s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/wlp4s0
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


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


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


enp5s0    no frequency information.


enp0s31f6  no frequency information.


lo        no frequency information.


wlp4s0    32 channels in total; available frequencies :
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


##### iwlist scan #######################


wlp4s0    Interface doesn't support scanning : Network is down


enp5s0    Interface doesn't support scanning.


enp0s31f6  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
srcversion:     F411BB3F1A8E9CA7FB30C39
depends:        ath10k_core
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     304D8B128FFE6789A6CDD13
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.5.2-040502-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CC4EF0BEC141C8AE7D0A659
depends:        cfg80211
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.5.2-040502-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     CAB0052D4485B3B2226F1ED
depends:        
intree:         Y
vermagic:       4.5.2-040502-generic SMP mod_unload modversions 
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


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    4.132155] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/cal-pci-0000:04:00.0.bin failed with error -2
[    4.134577] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.134579] ath10k_pci 0000:04:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.142819] ath10k_pci 0000:04:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    4.142820] ath10k_pci 0000:04:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.143133] ath10k_pci 0000:04:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    4.205177] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    4.205891] ath10k_pci 0000:04:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    4.313725] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[    4.525340] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready (repeated 2 times)
[    4.526880] alx 0000:05:00.0 enp5s0: NIC Up: 1 Gbps Full
[    4.527125] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready
[    6.322907] ath10k_pci 0000:04:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    9.319538] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[    9.396159] ath: EEPROM regdomain: 0x69
[    9.396161] ath: EEPROM indicates we should expect a direct regpair map
[    9.396162] ath: Country alpha2 being used: 00
[    9.396163] ath: Regpair used: 0x69
[    9.399147] ath10k_pci 0000:04:00.0 wlp4s0: renamed from wlan0
[    9.417765] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[   14.655589] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[   20.655637] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[   25.975715] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[   31.975775] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[   37.291655] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[   43.291856] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[   59.226503] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[   65.222709] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[   70.536149] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[   76.533971] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[   92.215555] ath10k_pci 0000:04:00.0: failed to set tx-chainmask: -11, req 0x3
[   95.215387] ath10k_pci 0000:04:00.0: failed to set arp ac override parameter: -11
[  101.214825] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[  106.530813] ath10k_pci 0000:04:00.0: failed to set tx-chainmask: -11, req 0x3
[  109.530458] ath10k_pci 0000:04:00.0: failed to set arp ac override parameter: -11
[  115.530499] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[  131.213749] ath10k_pci 0000:04:00.0: failed to set tx-chainmask: -11, req 0x3
[  134.213895] ath10k_pci 0000:04:00.0: failed to set arp ac override parameter: -11
[  140.213576] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[  145.529655] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[  151.529675] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[  167.205405] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[  173.205545] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[  178.521319] ath10k_pci 0000:04:00.0: failed to enable dynamic BW: -11
[  184.521519] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[  200.213340] ath10k_pci 0000:04:00.0: failed to set rx-chainmask: -11, req 0x3
[  203.213358] ath10k_pci 0000:04:00.0: failed to set arp ac override parameter: -11
[  209.213530] ath10k_pci 0000:04:00.0: could not suspend target (-11)
[  214.521516] ath10k_pci 0000:04:00.0: failed to set rx-chainmask: -11, req 0x3
[  217.521339] ath10k_pci 0000:04:00.0: failed to set arp ac override parameter: -11
[  223.521337] ath10k_pci 0000:04:00.0: could not suspend target (-11)


########## wireless info END ############
```

Seems like the firmware can't load. Sorry I am new at this.

```
[    4.132155] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/cal-pci-0000:04:00.0.bin failed with error -2
[    4.134577] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.134579] ath10k_pci 0000:04:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.142819] ath10k_pci 0000:04:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    4.142820] ath10k_pci 0000:04:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.143133] ath10k_pci 0000:04:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    4.205177] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    4.205891] ath10k_pci 0000:04:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    4.313725] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[    4.525340] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready (repeated 2 times)
[    4.526880] alx 0000:05:00.0 enp5s0: NIC Up: 1 Gbps Full
[    4.527125] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready
[    6.322907] ath10k_pci 0000:04:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
```

---

### Post by jeremy31 on 2016-04-26
I think this is an issue with board files
```
sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/board*.bin
cd /lib/firmware/ath10k/QCA6174/hw3.0
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board.bin
```

Reboot and if it still doesn't work post ```
dmesg | grep ath10k
```

---

### Post by Danny_Saba on 2016-04-26
> **jeremy31 said:**
> I think this is an issue with board files
```
sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/board*.bin
cd /lib/firmware/ath10k/QCA6174/hw3.0
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board.bin
```

Reboot and if it still doesn't work post ```
dmesg | grep ath10k
```

The WiFI options disappeared. It no longer shows disabled.  Not sure if this might help: [http://askubuntu.com/questions/607707/ath10k-installation](http://askubuntu.com/questions/607707/ath10k-installation)


```
[    3.885341] ath10k_pci 0000:04:00.0: enabling device (0000 -> 0002)[    3.885571] ath10k_pci 0000:04:00.0: pci irq msi interrupts 1 irq_mode 0 reset_mode 0
[    4.125541] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/cal-pci-0000:04:00.0.bin failed with error -2
[    4.125798] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.125800] ath10k_pci 0000:04:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.130794] ath10k_pci 0000:04:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    4.130796] ath10k_pci 0000:04:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.131113] ath10k_pci 0000:04:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    4.195521] ath10k_pci 0000:04:00.0: found invalid board magic
[    4.197340] ath10k_pci 0000:04:00.0: board_file api 1 bmi_id N/A crc32 41f6f40c
[   11.295968] ath10k_pci 0000:04:00.0: wmi unified ready event not received
[   14.334379] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[   17.354338] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[   17.354340] ath10k_pci 0000:04:00.0: failed to wait for target init: -110
[   17.354654] ath10k_pci 0000:04:00.0: could not init core (-110)
[   17.354672] ath10k_pci 0000:04:00.0: could not probe fw (-110)

```

---

### Post by jeremy31 on 2016-04-26
Ignore the link you posted, I wrote the answer and 16.04 supports the wifi but doesn't have the correct firmware in linux-firmware package

The instructions in the description of this bug report may help [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343)

---

### Post by Danny_Saba on 2016-04-26
> **jeremy31 said:**
> Ignore the link you posted, I wrote the answer and 16.04 supports the wifi but doesn't have the correct firmware in linux-firmware package

The instructions in the description of this bug report may help [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343)


Thank you very much! That worked perfectly.

---

### Post by jeremy31 on 2016-04-26
Good to hear Danny

---

