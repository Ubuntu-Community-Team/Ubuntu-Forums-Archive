---
title: "Wifi not working on Ubuntu 16.04"
date: 2017-02-02
forum: Networking &amp; Wireless
---

### Post by chipro12 on 2017-02-02
Hi , I just reinstalled my OS to the 64bit version of Ubuntu 16.04 and wifi seems not working . I had trouble before setting up this wifi for the 32bit Ubuntu when it had hardblocked problem. But for now, I have no idea what the problem is and how to fix :(

```


########## wireless info START ##########

Report from: 02 Feb 2017 17:36 EST -0500

Booted last: 02 Feb 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company MCP77 Ethernet [103c:360a]
    Kernel driver in use: forcedeth

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 002 Device 002: ID 13fe:3100 Kingston Technology Company Inc. 2/4 GB stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04d9:a070 Holtek Semiconductor, Inc. 
Bus 004 Device 002: ID 04d9:0141 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 147456  0
ath                    32768  1 ath5k
mac80211              737280  1 ath5k
cfg80211              565248  3 ath,ath5k,mac80211
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s10   Link encap:Ethernet  HWaddr <MAC 'enp0s10' [IF1]>  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9c5b:c6c5:3a60:92d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2714 (2.7 KB)  TX bytes:8855 (8.8 KB)

wlp7s0    Link encap:Ethernet  HWaddr <MAC 'wlp7s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s10   no wireless extensions.

wlp7s0    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp0s10
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s10
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s10

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       877     1  0 17:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s10
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP77 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s10' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0a.0/net/enp0s10
GENERAL.IP-IFACE:                       enp0s10
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       f9a54e32-0bc8-31e7-9f1b-34559d5d959e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f9a54e32-0bc8-31e7-9f1b-34559d5d959e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.114/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.114
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
DHCP4.OPTION[20]:                       expiry = 1486161314
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = luan-Compaq-Presario-CQ50-Notebook-PC
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::9c5b:c6c5:3a60:92d3/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express) (AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.4.0-62-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/0000:07:00.0/net/wlp7s0
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
WIFI-PROPERTIES.5GHZ:                   no
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

lo        no frequency information.

enp0s10   no frequency information.

wlp7s0    12 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s10   Interface doesn't support scanning.

wlp7s0    Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[ath5k]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     810B493FFA7764F2E3573E2
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: Y

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

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=Y
options ath5k no_hw_rfkill_switch=Y

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
blacklist hp-wmi

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

##### dmesg #############################

[   10.784628] ath5k 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.784807] ath5k 0000:07:00.0: registered as 'phy0'
[   11.415371] ath: EEPROM regdomain: 0x64
[   11.415378] ath: EEPROM indicates we should expect a direct regpair map
[   11.415383] ath: Country alpha2 being used: 00
[   11.415385] ath: Regpair used: 0x64
[   11.504207] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   15.401986] ath5k 0000:07:00.0 wlp7s0: renamed from wlan0
[   18.509827] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[   18.510545] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[   18.520498] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready (repeated 9 times)

########## wireless info END ############

```

---

### Post by wildmanne39 on 2017-02-02
Remove all your connections in network manager, also you need to uninstall network manager or wicd you can not have them both installed and working at the same time, reboot your router after it is back up perform the action above.
Thanks

---

### Post by chipro12 on 2017-02-02
Thanks a lot for quick reply. I uninstalled networkmanager, rebooted the router but things stay the same. 
```


########## wireless info START ##########

Report from: 02 Feb 2017 18:21 EST -0500

Booted last: 02 Feb 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company MCP77 Ethernet [103c:360a]
    Kernel driver in use: forcedeth

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 002 Device 002: ID 13fe:3100 Kingston Technology Company Inc. 2/4 GB stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04d9:a070 Holtek Semiconductor, Inc. 
Bus 004 Device 002: ID 04d9:0141 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 147456  0
ath                    32768  1 ath5k
mac80211              737280  1 ath5k
cfg80211              565248  3 ath,ath5k,mac80211
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s10   Link encap:Ethernet  HWaddr <MAC 'enp0s10' [IF1]>  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp0s10' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1653627 (1.6 MB)  TX bytes:188030 (188.0 KB)

wlp7s0    Link encap:Ethernet  HWaddr <MAC 'wlp7s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s10   no wireless extensions.

wlp7s0    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 enp0s10
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp0s10

##### resolv.conf #######################

nameserver 192.168.1.1

##### network managers ##################

Installed:

    Wicd

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

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

No NetworkManager profiles found.

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

enp0s10   no frequency information.

wlp7s0    12 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s10   Interface doesn't support scanning.

wlp7s0    No scan results

##### module infos ######################

[ath5k]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     810B493FFA7764F2E3573E2
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: Y

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

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=Y
options ath5k no_hw_rfkill_switch=Y

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
blacklist hp-wmi

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

##### dmesg #############################

[   11.181347] ath5k 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.181526] ath5k 0000:07:00.0: registered as 'phy0'
[   11.842302] ath: EEPROM regdomain: 0x64
[   11.842308] ath: EEPROM indicates we should expect a direct regpair map
[   11.842312] ath: Country alpha2 being used: 00
[   11.842313] ath: Regpair used: 0x64
[   13.378549] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   14.439058] ath5k 0000:07:00.0 wlp7s0: renamed from wlan0
[   21.461583] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   27.050128] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[   29.291361] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   29.583357] forcedeth 0000:00:0a.0 enp0s10: MSI enabled (repeated 2 times)

########## wireless info END ############

```

---

### Post by wildmanne39 on 2017-02-02
Did you reboot the computer after you removed all connections from wicd and network manager so wicd can find the connections when it booted back up? right now it says wicd is installed but not running so you may need to make wicd come on at boot.

---

### Post by chipro12 on 2017-02-02
Hi, I actually make wicd run via commandline (sudo wicd-client) but they seem to do nothing. here is the file

```


########## wireless info START ##########

Report from: 02 Feb 2017 19:20 EST -0500

Booted last: 02 Feb 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company MCP77 Ethernet [103c:360a]
    Kernel driver in use: forcedeth

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 002 Device 002: ID 13fe:3100 Kingston Technology Company Inc. 2/4 GB stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04d9:a070 Holtek Semiconductor, Inc. 
Bus 004 Device 002: ID 04d9:0141 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 147456  0
ath                    32768  1 ath5k
mac80211              737280  1 ath5k
cfg80211              565248  3 ath,ath5k,mac80211
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s10   Link encap:Ethernet  HWaddr <MAC 'enp0s10' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:849342 (849.3 KB)  TX bytes:155066 (155.0 KB)

wlp7s0    Link encap:Ethernet  HWaddr <MAC 'wlp7s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s10   no wireless extensions.

wlp7s0    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    Wicd

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

No NetworkManager profiles found.

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

enp0s10   no frequency information.

wlp7s0    12 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s10   Interface doesn't support scanning.

wlp7s0    No scan results

##### module infos ######################

[ath5k]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     810B493FFA7764F2E3573E2
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: Y

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

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=Y
options ath5k no_hw_rfkill_switch=Y

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
blacklist hp-wmi

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

##### dmesg #############################

[   11.105819] ath5k 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.105997] ath5k 0000:07:00.0: registered as 'phy0'
[   11.806005] ath: EEPROM regdomain: 0x64
[   11.806013] ath: EEPROM indicates we should expect a direct regpair map
[   11.806018] ath: Country alpha2 being used: 00
[   11.806020] ath: Regpair used: 0x64
[   11.970998] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   12.178678] ath5k 0000:07:00.0 wlp7s0: renamed from wlan0
[   23.637067] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   29.046745] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[   31.477296] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   31.851124] forcedeth 0000:00:0a.0 enp0s10: MSI enabled (repeated 2 times)
[   66.300524] forcedeth 0000:00:0a.0 enp0s10: link down
[   69.132751] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[   69.132986] forcedeth 0000:00:0a.0 enp0s10: no link during initialization
[   69.133348] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[   69.357854] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   69.615700] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[   69.615936] forcedeth 0000:00:0a.0 enp0s10: no link during initialization
[   69.616426] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[  101.140608] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[  229.533811] forcedeth 0000:00:0a.0 enp0s10: link up
[  229.534184] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s10: link becomes ready
[  237.052680] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[  237.329624] forcedeth 0000:00:0a.0 enp0s10: MSI enabled (repeated 2 times)
[  473.347960] forcedeth 0000:00:0a.0 enp0s10: link down
[  475.174217] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[  475.174460] forcedeth 0000:00:0a.0 enp0s10: no link during initialization
[  475.174815] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[  476.185764] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[  476.433727] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[  476.433969] forcedeth 0000:00:0a.0 enp0s10: no link during initialization
[  476.434347] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready

########## wireless info END ############


```

And here is the info when I uninstalled wicd and ran only network manager
```



########## wireless info START ##########

Report from: 02 Feb 2017 18:55 EST -0500

Booted last: 02 Feb 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company MCP77 Ethernet [103c:360a]
    Kernel driver in use: forcedeth

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 002 Device 002: ID 13fe:3100 Kingston Technology Company Inc. 2/4 GB stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04d9:a070 Holtek Semiconductor, Inc. 
Bus 004 Device 002: ID 04d9:0141 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 147456  0
ath                    32768  1 ath5k
mac80211              737280  1 ath5k
cfg80211              565248  3 ath,ath5k,mac80211
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s10   Link encap:Ethernet  HWaddr <MAC 'enp0s10' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp7s0    Link encap:Ethernet  HWaddr <MAC 'wlp7s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s10   no wireless extensions.

wlp7s0    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       909     1  0 18:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express) (AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.4.0-62-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/0000:07:00.0/net/wlp7s0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp0s10
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP77 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s10' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0a.0/net/enp0s10
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

lo        no frequency information.

enp0s10   no frequency information.

wlp7s0    12 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s10   Interface doesn't support scanning.

wlp7s0    No scan results

##### module infos ######################

[ath5k]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     810B493FFA7764F2E3573E2
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: Y

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

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=Y
options ath5k no_hw_rfkill_switch=Y

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
blacklist hp-wmi

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

##### dmesg #############################

[   11.292001] ath5k 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.292231] ath5k 0000:07:00.0: registered as 'phy0'
[   11.948200] ath: EEPROM regdomain: 0x64
[   11.948206] ath: EEPROM indicates we should expect a direct regpair map
[   11.948212] ath: Country alpha2 being used: 00
[   11.948213] ath: Regpair used: 0x64
[   12.461105] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   14.410366] ath5k 0000:07:00.0 wlp7s0: renamed from wlan0
[   20.232887] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready (repeated 2 times)
[   20.252892] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[   20.253757] forcedeth 0000:00:0a.0 enp0s10: MSI enabled
[   20.254035] forcedeth 0000:00:0a.0 enp0s10: no link during initialization
[   20.254359] IPv6: ADDRCONF(NETDEV_UP): enp0s10: link is not ready
[   20.660401] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready

########## wireless info END ############


```

---

### Post by wildmanne39 on 2017-02-02
Please use network manager and make sure networking and wireless are both enabled, and no wicd is not running at the time of the report.

Go into your router and make sure your wireless radio is turned on and broadcasting.

Then in network manager make sure your settings match the screenshots.
[ATTACH=CONFIG]273487[/ATTACH][ATTACH=CONFIG]273488[/ATTACH]
Now do
```
sudo systemctl restart NetworkManager.service
sudo dpkg-reconfigure resolvconf
```
Does wifi come on?

---

### Post by chipro12 on 2017-02-03
Thanks a lot for helping. So i figured out that my laptop wifi swich causes trouble. I have to add "rfkill unblock wifi" to rc.local and then at every single boot, I have to press the wifi switch on my laptop twice to get it turned on. i think this is a hardware problem for my case. Playting around with nohwcrypt and no_hw_rfkill_switch doesn't change. But now I get it working

---

### Post by wildmanne39 on 2017-02-05
Try it like this in the rc.local file:
```
sudo modprobe -r ath5k
rfkill unblock wifi
sudo modprobe ath5k
```
then you should not have to press the wifi button but may be the first time to get it in the right position.
Thanks

---

