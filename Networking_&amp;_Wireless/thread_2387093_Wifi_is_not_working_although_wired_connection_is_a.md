---
title: "Wifi is not working although wired connection is alive on Ubuntu16.04"
date: 2018-03-14
forum: Networking &amp; Wireless
---

### Post by ksn0215 on 2018-03-14
Hi everyone,

I can use wired connection, but I can not use Wifi on my Ubuntu 16.04.4 laptop for a few days.

I read these threads below after inspecting into log messages, but I could not fix.

[https://ubuntuforums.org/showthread.php?t=2222374](https://ubuntuforums.org/showthread.php?t=2222374)

[https://ubuntuforums.org/showthread.php?t=2338757](https://ubuntuforums.org/showthread.php?t=2338757)

I am not sure this is relevant but load average is always very high (over 200).

I think the information below is useful to diagnose.
File wireless-info.txt (output from "wireless_script" follows):
```

########## wireless info START ##########

Report from: 15 Mar 2018 03:33 JST +0900

Booted last: 15 Mar 2018 00:00 JST +0900

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Subsystem: Lenovo 82566MM Gigabit Network Connection [17aa:20de]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 003: ID 0781:5583 SanDisk Corp. 
Bus 002 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. BCM2045B (BDC-2) [Bluetooth Controller]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                73728  0
iwlegacy               98304  1 iwl3945
mac80211              782336  2 iwlegacy,iwl3945
cfg80211              614400  3 mac80211,iwlegacy,iwl3945

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

br-26a53f06fd17 Link encap:Ethernet  HWaddr <MAC 'br-26a53f06fd17' [IF1]>  
          inet addr:172.18.0.1  Bcast:172.18.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF2]>  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF3]>  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::718d:5c3d:9b36:2902/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48294507 (48.2 MB)  TX bytes:2640129 (2.6 MB)
          Interrupt:20 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67689 (67.6 KB)  TX bytes:67689 (67.6 KB)

##### iwconfig ##########################

docker0   no wireless extensions.

br-26a53f06fd17  no wireless extensions.

lo        no wireless extensions.

enp0s25   no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp0s25
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br-26a53f06fd17
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-26a53f06fd17
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s25

##### resolv.conf #######################

nameserver 192.168.0.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      7238     1  0 03:00 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         br-26a53f06fd17
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'br-26a53f06fd17' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/1
GENERAL.IP-IFACE:                       br-26a53f06fd17
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     br-26a53f06fd17
GENERAL.CON-UUID:                       16c63465-6aff-4668-a40f-c8ac046c6a16
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{38}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   16c63465-6aff-4668-a40f-c8ac046c6a16 | br-26a53f06fd17
IP4.ADDRESS[1]:                         172.18.0.1/16
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            

GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       d3de18fc-349a-412e-8e5b-296f07f6f431
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{37}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d3de18fc-349a-412e-8e5b-296f07f6f431 | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82566MM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.3-0
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/2
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     &#33258;&#21205; Ethernet
GENERAL.CON-UUID:                       fd421c80-de36-46d8-aa3a-8d5eeb8a53ea
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   fd421c80-de36-46d8-aa3a-8d5eeb8a53ea | &#33258;&#21205; Ethernet
IP4.ADDRESS[1]:                         192.168.0.4/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       expiry = 1521136805
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.4
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::718d:5c3d:9b36:2902/64
IP6.GATEWAY:                            

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

[[/etc/NetworkManager/system-connections/WARPSTAR-A59B67 2]] (600 root)
[connection] id=WARPSTAR-A59B67 2 | type=wifi | permissions=user:ksn:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WARPSTAR-A59B67
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WARPSTAR-A59B67]] (600 root)
[connection] id=WARPSTAR-A59B67 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WARPSTAR-A59B67
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/aterm-404c09-g]] (600 root)
[connection] id=aterm-404c09-g | type=wifi | permissions=user:ksn:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=aterm-404c09-g
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/29B80B63394B10573A8A872933B40F10]] (600 root)
[connection] id=29B80B63394B10573A8A872933B40F10 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=29B80B63394B10573A8A872933B40F10
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################

##### iw reg get ########################

Region: Asia/Tokyo (based on set time zone)

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

docker0   no frequency information.

br-26a53f06fd17  no frequency information.

lo        no frequency information.

enp0s25   no frequency information.

##### iwlist scan #######################

docker0   Interface doesn't support scanning.

br-26a53f06fd17  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

##### module infos ######################

[iwl3945]
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     44DE0EFB756B1D09C774503
depends:        iwlegacy,mac80211,cfg80211
intree:         Y
name:           iwl3945
vermagic:       4.13.0-32-generic SMP mod_unload 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     3A3AB842DE90A78596C496F
depends:        mac80211,cfg80211
intree:         Y
name:           iwlegacy
vermagic:       4.13.0-32-generic SMP mod_unload 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/4.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-32-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-32-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

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

[/etc/pm/config.d/config.copy] (644 root)
SUSPEND_MODULES="iwl3945 wls3" 

[/etc/pm/config.d/.config.swp] (644 root)
Binary file /etc/pm/config.d/.config.swp matches

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############

```

Any help will be much appreciated.

Thank you in advance.

---

### Post by praseodym on 2018-03-14
The card does not show up, a wifi driver is though. Try resetting your BIOS to default settings

---

### Post by ksn0215 on 2018-03-14
Thank you very much for your reply.

I tried to reset BIOS to default settings, but still cannot use Wifi through networkmanager.

---

### Post by ksn0215 on 2018-03-14
<del>(Note)The link below might be broken so I am adding a text file</del> I gave a part of result rather than upload a file.

Thank you for your cooperation.

I am not sure but this information might be useful:

$ dmesg
```

[  472.048704] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.061276] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.133412] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.145981] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.218187] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.230765] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.302960] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.315529] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.387717] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.400247] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.472430] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.484999] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.557197] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.570795] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.642975] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.655553] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.727678] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.764545] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.836352] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.849684] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  472.921842] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  472.934402] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.006586] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.019206] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.091376] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.103963] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.176152] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.188715] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.260873] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.273466] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.345643] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.358216] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.430363] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.442972] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.515126] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.527736] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.599882] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.612462] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.684685] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.697234] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.769445] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.781985] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.854181] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.866743] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  473.938946] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  473.976143] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.047599] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.060905] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.133072] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.145656] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.217853] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.230418] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.302601] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.315169] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.387348] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.399924] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.472098] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.484157] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  474.484199] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484231] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484259] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484286] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484315] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484342] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484370] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484401] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484428] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484455] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484482] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484511] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484539] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484569] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484597] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  474.484622] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.556867] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.569436] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.641622] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.654189] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.726350] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.738941] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.811068] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.823673] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.895893] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.908406] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  474.980620] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  474.993184] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.065386] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.077970] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.150126] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.187367] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.258760] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.272110] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.344314] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.356815] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.429050] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.441570] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.513818] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.526364] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.598578] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.611116] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.683333] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.695892] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.768050] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.780599] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.852774] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.865350] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  475.937539] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  475.950102] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.022284] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.034853] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.107041] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.119643] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.191797] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.204367] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.276550] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.289118] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.361305] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.398545] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.469962] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.483272] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.555494] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.568054] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.640206] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.652799] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.724964] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.737570] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.809743] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.822285] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.894499] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.907045] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  476.979289] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  476.991833] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.064026] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.076596] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.148787] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.161315] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.233564] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.246085] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.318276] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.330858] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.403046] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.415599] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.487802] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.500383] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.572511] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.609788] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.681168] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.694481] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.766661] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.779237] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.851420] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.863993] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  477.936172] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  477.948744] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.020921] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.033505] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.052136] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  478.105681] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.118277] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.190440] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.203010] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.275203] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.287762] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.359948] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.372517] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.444702] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.457273] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.529457] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.542060] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.614251] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.626806] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.698964] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.711566] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.783734] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.820976] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.892365] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.905690] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  478.977871] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  478.990445] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.062630] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.075196] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.147385] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.159955] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.232162] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.244713] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.316896] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.329464] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.401696] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.414256] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.486458] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.499025] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.571186] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.583763] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.655913] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.668486] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.740669] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.753244] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.825426] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.837988] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.910188] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  479.922760] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  479.994932] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.032177] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.103573] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.116892] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.189080] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.201668] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.273835] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.286446] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.358593] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.371178] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.443411] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.455918] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.528113] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.540675] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.612855] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.625433] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.697613] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.710180] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.782365] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.794938] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.867119] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.879695] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  480.951876] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  480.964460] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.036633] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.049201] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.121429] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.133997] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.206162] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.243399] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.314837] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.328154] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.400353] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.412910] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.485110] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.497669] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.569861] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.582422] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.592118] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  481.654559] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.667166] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.739357] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.751930] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.824078] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.836675] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.908874] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  481.921441] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  481.993629] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.006176] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.078337] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.090950] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.163124] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.175705] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.247892] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.260458] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.332649] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.345196] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.417404] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.429972] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.502157] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.514724] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.586909] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.599480] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.671631] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.684211] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.756420] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.793635] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.865064] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.878376] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  482.950570] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  482.963137] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.035301] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.047894] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.120083] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.132651] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.204841] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.217405] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.289595] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.302160] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.374340] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.386885] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.459046] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.472654] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.544826] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.557357] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.629603] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.642113] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.714361] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.726865] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.799111] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.811674] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.883807] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.896416] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  483.968567] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  483.981137] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.053360] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.065894] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.138078] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.150647] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.222832] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.235448] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.307648] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.320154] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.392402] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.404961] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.477142] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.489714] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.561904] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.574471] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.646661] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.659195] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.731381] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.743966] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.816151] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.828681] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.900921] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.913492] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  484.985621] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  484.998240] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  485.070419] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  485.082980] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  485.112171] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  485.155187] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  485.167758] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  485.239885] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  485.277068] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  485.348550] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  485.361880] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  485.389175] pciehp 0000:00:1c.1:pcie004: Slot(3): Link Up
[  485.500237] pci 0000:03:00.0: [8086:4227] type 00 class 0x028000
[  485.500352] pci 0000:03:00.0: reg 0x10: [mem 0x00000000-0x00000fff]
[  485.500847] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[  485.516194] pci 0000:03:00.0: BAR 0: assigned [mem 0xdc100000-0xdc100fff]
[  485.516212] pcieport 0000:00:1c.1: PCI bridge to [bus 03]
[  485.516218] pcieport 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[  485.516228] pcieport 0000:00:1c.1:   bridge window [mem 0xdc100000-0xdfcfffff]
[  485.516235] pcieport 0000:00:1c.1:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
[  485.516414] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[  485.516431] iwl3945 0000:03:00.0: enabling device (0000 -> 0002)
[  485.572164] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 12 802.11a channels
[  485.572169] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  485.579547] ieee80211 phy71: Selected rate control algorithm 'iwl-3945-rs'
[  485.760211] pci 0000:03:00.0: [8086:4227] type 00 class 0x028000
[  485.760338] pci 0000:03:00.0: reg 0x10: [mem 0xdc100000-0xdc100fff]
[  485.760908] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[  485.772198] pci 0000:03:00.0: BAR 0: assigned [mem 0xdc100000-0xdc100fff]
[  485.772215] pcieport 0000:00:1c.1: PCI bridge to [bus 03]
[  485.772221] pcieport 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[  485.772229] pcieport 0000:00:1c.1:   bridge window [mem 0xdc100000-0xdfcfffff]
[  485.772236] pcieport 0000:00:1c.1:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
[  485.772395] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[  485.812913] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 12 802.11a channels
[  485.812916] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  485.813578] ieee80211 phy72: Selected rate control algorithm 'iwl-3945-rs'
[  486.000207] pci 0000:03:00.0: [8086:4227] type 00 class 0x028000
[  486.000333] pci 0000:03:00.0: reg 0x10: [mem 0xdc100000-0xdc100fff]
[  486.000902] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[  486.012222] pci 0000:03:00.0: BAR 0: assigned [mem 0xdc100000-0xdc100fff]
[  486.012240] pcieport 0000:00:1c.1: PCI bridge to [bus 03]
[  486.012246] pcieport 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[  486.012255] pcieport 0000:00:1c.1:   bridge window [mem 0xdc100000-0xdfcfffff]
[  486.012262] pcieport 0000:00:1c.1:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
[  486.012438] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[  486.053717] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 12 802.11a channels
[  486.053723] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  486.054765] ieee80211 phy73: Selected rate control algorithm 'iwl-3945-rs'
[  486.220207] pci 0000:03:00.0: [8086:4227] type 00 class 0x028000
[  486.220332] pci 0000:03:00.0: reg 0x10: [mem 0xdc100000-0xdc100fff]
[  486.220955] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[  486.232248] pci 0000:03:00.0: BAR 0: assigned [mem 0xdc100000-0xdc100fff]
[  486.232266] pcieport 0000:00:1c.1: PCI bridge to [bus 03]
[  486.232272] pcieport 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[  486.232282] pcieport 0000:00:1c.1:   bridge window [mem 0xdc100000-0xdfcfffff]
[  486.232289] pcieport 0000:00:1c.1:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
[  486.232468] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[  486.273629] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 12 802.11a channels
[  486.273635] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  486.275944] ieee80211 phy74: Selected rate control algorithm 'iwl-3945-rs'
[  486.448207] pci 0000:03:00.0: [8086:4227] type 00 class 0x028000
[  486.448335] pci 0000:03:00.0: reg 0x10: [mem 0xdc100000-0xdc100fff]
[  486.448902] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[  486.460255] pci 0000:03:00.0: BAR 0: assigned [mem 0xdc100000-0xdc100fff]
[  486.460276] pcieport 0000:00:1c.1: PCI bridge to [bus 03]
[  486.460285] pcieport 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[  486.460298] pcieport 0000:00:1c.1:   bridge window [mem 0xdc100000-0xdfcfffff]
[  486.460308] pcieport 0000:00:1c.1:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
[  486.460545] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[  486.501836] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 12 802.11a channels
[  486.501843] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  486.504247] ieee80211 phy75: Selected rate control algorithm 'iwl-3945-rs'
[  486.779304] pciehp 0000:00:1c.1:pcie004: Slot(3): Link Down
[  486.791869] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  486.864083] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  486.876653] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  486.948840] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  486.961414] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.033596] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.046164] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.118326] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.130918] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.203105] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.215675] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.287866] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.300428] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.372619] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.385185] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.457355] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.469942] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.542134] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.554698] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.626880] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.639448] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.711636] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.748813] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.820291] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.833542] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.905786] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  487.918334] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  487.990534] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.003110] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.075295] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.087864] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.148126] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  488.160052] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.172618] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.244810] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.257349] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.329555] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.342128] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.414261] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.426829] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.499076] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.511637] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.583822] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.596373] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.668582] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.705738] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.777194] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.790542] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.862730] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.875297] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  488.947485] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  488.960052] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.032181] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.044806] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.116993] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.129563] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.201751] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.214318] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.286508] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.299073] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.371237] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.383812] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.456016] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.468535] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.540719] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.553289] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.625473] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.662676] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.734150] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.747493] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.819658] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.832227] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.904419] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  489.916992] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  489.989141] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.001739] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.073891] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.086511] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.158674] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.171208] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.243420] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.256017] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.328203] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.340771] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.412958] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.425524] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.497658] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.510239] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.582439] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.619632] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.691074] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.704411] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.776601] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.789162] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.861350] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.873886] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  490.946142] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  490.958702] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.030884] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.043426] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.115625] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.128150] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.200373] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.212962] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.285110] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.297663] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.369904] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.382454] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.454599] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.467171] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.539409] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.576549] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.648056] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.661373] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.668180] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  491.733564] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.746087] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.818314] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.830885] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.903011] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  491.915640] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  491.987824] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.000342] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.072578] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.085151] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.157339] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.169905] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.242072] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.254661] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.326852] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.339397] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.411567] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.424161] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.496359] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.533497] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.604988] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.618265] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.690475] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.703024] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.775216] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.787800] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.859956] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.872529] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  492.944716] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  492.957324] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.029512] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.042094] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.114278] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.126847] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.199034] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.211606] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.283791] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.296359] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.368551] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.381114] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.453303] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.490128] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.561948] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.575261] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.647429] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.660015] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.732150] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.744717] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.816967] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.829510] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.901718] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.914280] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  493.986449] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  493.999042] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.071228] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.083775] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.155977] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.168529] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.240687] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.277921] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.349401] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.362697] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.434885] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.447435] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.519621] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.532171] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.604389] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.616959] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.689150] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.701713] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.773908] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.786455] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.858665] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.871227] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  494.943416] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  494.955982] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.028179] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.040734] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.112922] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.125437] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.184146] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  495.197678] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.234483] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.306309] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.319640] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.391823] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.404396] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.476567] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.489150] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.561336] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.573858] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.646090] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.658661] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.730854] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.743419] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.815567] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.828135] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.900357] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  495.912926] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  495.985112] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.022287] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.093761] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.107065] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.179255] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.191827] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.264015] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.276570] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.348768] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.361340] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.433469] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.446095] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.518275] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.530850] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.603034] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.615587] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.687794] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.700360] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.772532] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.809696] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.881207] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.894491] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  496.966689] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  496.979263] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.051453] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.064020] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.136146] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.148772] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.220902] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.233511] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.305720] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.318234] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.390471] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.404038] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.476158] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.488725] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.560972] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.573521] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.645719] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.658287] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.730483] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.767300] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.839118] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.852429] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  497.924608] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  497.937192] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.009375] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.021955] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.094076] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.106651] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.178877] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.191444] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.263632] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.276171] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.348399] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.360969] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.433153] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.445723] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.517909] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.530457] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.602671] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.615180] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.687424] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.720135] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  498.720180] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720210] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720239] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720268] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720297] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720325] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720353] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720381] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720409] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720436] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720466] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720495] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720526] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720556] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720586] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720615] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720650] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720680] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720712] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720742] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720770] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720801] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720830] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720860] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720890] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720921] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720951] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.720982] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721012] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721043] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721072] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721104] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721133] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721165] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721194] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721224] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721253] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721284] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721313] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721344] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721374] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721403] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721433] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721462] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721491] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721520] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721546] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721575] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721604] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721633] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721662] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721693] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721722] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721753] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721782] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721811] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721841] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721869] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721897] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721928] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721957] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.721995] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722027] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722063] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722094] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722123] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722152] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722183] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722216] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722244] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722272] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722299] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722327] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722354] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722385] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722412] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722440] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722468] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722495] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722522] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722550] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722578] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722605] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722632] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722659] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722689] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722719] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722746] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722774] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722801] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722829] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722858] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722885] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722913] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722941] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722968] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.722996] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723023] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723050] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723080] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723110] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723148] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723180] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723209] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723241] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723804] pciehp 0000:00:1c.1:pcie004: Slot(3): No adapter
[  498.723830] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.724441] pciehp 0000:00:1c.1:pcie004: Slot(3): Link Up event ignored; already powering on
[  498.724447] pciehp 0000:00:1c.1:pcie004: Slot(3): Link Down event queued; currently getting powered on
[  498.796055] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.809380] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.881551] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.894139] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  498.966322] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  498.978891] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.051083] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.063630] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.135830] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.148341] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.220564] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.233161] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.305315] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.317920] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.390106] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.402671] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.474855] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.511677] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.583490] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.596803] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.668985] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.681557] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.753705] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.766272] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.838505] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.851066] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  499.923255] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  499.935822] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.008008] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.020573] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.092779] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.105297] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.177516] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.190087] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.262274] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.274857] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.347036] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.359595] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.431800] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.468956] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.540373] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.553704] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.625933] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.638465] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.710653] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.723220] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.795405] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.808019] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.880166] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.892784] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  500.964965] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  500.977530] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.049718] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.062295] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.134475] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.147000] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.219236] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.256062] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.327883] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.341166] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.413364] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.425892] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.498107] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.510688] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.582885] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.595459] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.667629] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.680169] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.752406] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.764971] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.837165] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.849670] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  501.921911] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  501.934482] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.006613] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.019183] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.091408] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.103988] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.176123] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.213311] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.256138] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  502.284798] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.298085] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.370323] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.382895] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.455083] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.467633] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.539832] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.552404] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.624578] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.637101] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.709330] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.721865] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.794099] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.806649] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.878832] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.891406] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  502.963605] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  502.976149] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.048371] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.060937] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.133106] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.170263] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.241761] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.255085] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.327216] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.339827] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.412009] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.424596] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.496775] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.509292] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.581476] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.594052] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.666276] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.678800] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.751033] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.763595] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.835802] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.848375] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  503.920533] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  503.933109] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.005275] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.017885] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.090047] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.102637] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.174766] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.187329] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.259558] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.296719] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.368222] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.381538] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.453704] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.466290] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.538481] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.551048] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.623234] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.635802] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.707933] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.720522] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.792730] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.805311] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.877469] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.890031] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  504.962256] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  504.974823] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.047011] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.059576] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.131749] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.144336] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.216519] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.229043] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.301259] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.313825] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.386031] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.423186] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.494662] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.507992] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.580151] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.592729] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.664937] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.677480] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.749659] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.762204] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.784106] pciehp 0000:00:1c.1:pcie004: Failed to check link status
[  505.834388] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.846995] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  505.919202] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  505.931738] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.003961] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.016520] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.088693] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.101280] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.173460] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.186033] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.258227] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.270770] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.342976] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.355543] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.427706] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.440297] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.512483] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.549634] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.621083] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.634420] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.706634] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.719203] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.791393] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.803957] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.876122] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.888652] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  506.960882] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  506.973459] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.045657] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.058222] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.130405] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.142975] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.215160] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.227687] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.299921] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.312489] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.384615] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.397192] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.469438] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.506560] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.578037] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.591393] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.663563] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.676155] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.748339] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.760899] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.833092] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.845657] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  507.917827] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  507.930411] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.002595] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.015165] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.087355] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.099920] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.172107] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.184677] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.256869] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.269432] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.341620] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.354187] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.426374] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.438939] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.511129] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.523698] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.595889] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.632332] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.704520] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.717829] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.790033] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.802598] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.874776] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.887356] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  508.959549] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  508.972087] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  509.044240] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  509.056834] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  509.129058] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  509.141622] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  509.213783] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  509.226362] pciehp 0000:00:1c.1:pcie004: Slot(3): Card present
[  509.298568] pciehp 0000:00:1c.1:pcie004: Slot(3): Card not present
[  509.304168] pciehp 0000:00:1c.1:pcie004: Failed to check link status

```

I looked for any hints on the web and tried some ways but still I cannot fix.

Any help will be appreciated.

---

### Post by ksn0215 on 2018-03-18
I could fix by myself!

In my case, this did the trick:

/etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
#auto lo                            # I commented out this line
#iface lo inet loopback             # I commented out this line

auto wlan0                         # I added  this line
iface wlan0 inet dhcp              # I added  this line

```

I am not sure why this works because I could not find wlan0 in the result of "sudo lshw -C network". Also, now I can find wls3 instead of wlan0 (This might be much easier to understand).

(NOTE) I upgraded my ubuntu from 16.04 to 17.10 but nothing on this issue changed. Upgrading was not solution.

Anyway, thank you for your help. I will close this issue.:D

(PS) I am not sure but the issue on the result of dmesg would be caused by setting loosely the network adapter on my laptop, to the judge from my diagnosis. Screws at the bottom were loose. I fixed it tightly, then network became stable and no error messages are shown now.

---

