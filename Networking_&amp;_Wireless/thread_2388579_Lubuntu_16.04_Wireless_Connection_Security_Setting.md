---
title: "Lubuntu 16.04 Wireless Connection Security Settings Issue"
date: 2018-04-04
forum: Networking &amp; Wireless
---

### Post by captionopen2 on 2018-04-04
I was having problems connecting to my wireless router using either WEP, WPA & WPA2 set security passwords.
However, when I remove the security password, I'm able to connect. Is there any reason why I shouldn't be 
able to connect using a password vs. unsecured network? As soon as I change the security settings, it
disconnects me, and then I have to hardwire to get back to the settings... Even though I have the password
set to the right security setting & have the password correctly entered.


```
########## wireless info START ##########

Report from: 04 Apr 2018 21:35 EDT -0400

Booted last: 04 Apr 2018 00:00 EDT -0400

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:22:43 UTC 2018 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:0a.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
    Subsystem: Netgear WG311v3 802.11g Wireless PCI Adapter [1385:6b00]
    Kernel driver in use: ndiswrapper

02:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Sony Corporation RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [104d:80ea]
    Kernel driver in use: 8139too

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:8307 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

cfg80211              499712  0
ndiswrapper           200704  0
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:13402 (13.4 KB)  TX bytes:13402 (13.4 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.254.23  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14794627 (14.7 MB)  TX bytes:988573 (988.5 KB)
          Interrupt:9 Memory:ed000000-ed010000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Wise"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Wise' [AC2]>   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    303    0        0 wlan0
192.168.254.0   0.0.0.0         255.255.255.0   U     303    0        0 wlan0

##### resolv.conf #######################

nameserver 192.168.254.254
nameserver 127.0.1.1
search netgear.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       788     1  0 21:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88w8335 [Libertas] 802.11b/g Wireless (WG311v3 802.11g Wireless PCI Adapter)
GENERAL.DRIVER:                         ndiswrapper
GENERAL.DRIVER-VERSION:                 1.60+NETGEAR,02/22/2005,3.1.1.7
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0a.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wise 1
GENERAL.CON-UUID:                       6c7f6f53-0b5d-424e-aed2-1c22fa37b466
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6c7f6f53-0b5d-424e-aed2-1c22fa37b466 | Wise 1
IP4.ADDRESS[1]:                         192.168.254.23/24
IP4.GATEWAY:                            192.168.254.254
IP4.DNS[1]:                             192.168.254.254
IP4.DOMAIN[1]:                          netgear.com
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.254.254
DHCP4.OPTION[5]:                        ip_address = 192.168.254.23
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.254.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.254.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.254.254
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = netgear.com
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1522977795
DHCP4.OPTION[21]:                       host_name = sony
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.254.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.254.254
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan0' [IF2]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /virtual/device/placeholder/1
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

SSID  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Wise  <MAC 'Wise' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  --        yes     * 
Wise  <MAC 'Wise' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  17      &#9602;___  WPA2      no        

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

[[/etc/NetworkManager/system-connections/Wise 1]] (600 root)
[connection] id=Wise 1 | type=wifi | permissions=user:sony:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Wise
[ipv4] method=auto
[ipv6] method=ignore

##### Netplan config ####################

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

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Wise' [AC1]>
                    ESSID:"Wise"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Wise' [AC2]>
                    ESSID:"Wise"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-116-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D2A8E57424453F0D1BE1DBE
depends:        
intree:         Y
vermagic:       4.4.0-116-generic SMP mod_unload modversions 686 retpoline 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/4.4.0-116-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     A19B5DA6C416B748A70FAAC
depends:        
vermagic:       4.4.0-116-generic SMP mod_unload modversions 686 retpoline 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

lp

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
blacklist mrv8k

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000011ABd00001FAAsv00006B00sd00001385bc*sc*i* ndiswrapper
alias pci:v000011ABd00001FAAsv*sd*bc*sc*i* ndiswrapper
alias pci:v000011ABd00001FABsv*sd*bc*sc*i* ndiswrapper

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

grep: /etc/pm/config.d/.config.swo: Permission denied

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x11ab:0x1faa (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    6.925073] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   15.893098] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   15.902586] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[   16.588610] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[   16.592415] ndiswrapper: using IRQ 9
[   16.852560] wlan0: ethernet device <MAC 'wlan0' [IF2]> using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   16.852591] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   28.846005] 8139too 0000:02:0d.0 eth0: link down
[   28.846109] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.846477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.540595] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.342638] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   68.676142] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  658.131901] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=496 TOS=0x00 PREC=0x00 TTL=128 ID=5761 PROTO=UDP SPT=58217 DPT=161 LEN=476 
[  661.236491] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=496 TOS=0x00 PREC=0x00 TTL=128 ID=5799 PROTO=UDP SPT=60882 DPT=161 LEN=476 
[  697.640102] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=74 TOS=0x00 PREC=0x00 TTL=128 ID=7298 PROTO=UDP SPT=61525 DPT=161 LEN=54 
[  699.641151] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=74 TOS=0x00 PREC=0x00 TTL=128 ID=7314 PROTO=UDP SPT=61526 DPT=161 LEN=54 
[  701.641324] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=516 TOS=0x00 PREC=0x00 TTL=128 ID=7318 PROTO=UDP SPT=59736 DPT=161 LEN=496 
[  704.664422] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=516 TOS=0x00 PREC=0x00 TTL=128 ID=7347 PROTO=UDP SPT=54260 DPT=161 LEN=496 
[  726.697835] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=74 TOS=0x00 PREC=0x00 TTL=128 ID=8437 PROTO=UDP SPT=50854 DPT=161 LEN=54 
[  729.385968] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=74 TOS=0x00 PREC=0x00 TTL=128 ID=8720 PROTO=UDP SPT=50855 DPT=161 LEN=54 
[  731.331022] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=516 TOS=0x00 PREC=0x00 TTL=128 ID=8896 PROTO=UDP SPT=50856 DPT=161 LEN=496 
[  733.752983] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=516 TOS=0x00 PREC=0x00 TTL=128 ID=9117 PROTO=UDP SPT=52725 DPT=161 LEN=496 
[  800.179628] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=74 TOS=0x00 PREC=0x00 TTL=128 ID=11188 PROTO=UDP SPT=60716 DPT=161 LEN=54 
[  800.929062] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=516 TOS=0x00 PREC=0x00 TTL=128 ID=11249 PROTO=UDP SPT=60717 DPT=161 LEN=496 
[  803.868751] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:44:ed:57:00:0b:cd:08:00 SRC=192.168.254.26 DST=192.168.254.23 LEN=516 TOS=0x00 PREC=0x00 TTL=128 ID=11315 PROTO=UDP SPT=52735 DPT=161 LEN=496 

########## wireless info END ############
```

---

### Post by praseodym on 2018-04-06
The problem is, this chipset is not supporting WPA/WPA2 correctly, so no surprise WEP/unencrypted works. I strongly recommend buying a wifi USB for 10 bucks or so.

The scan shows the network twice, using a repeater?! If so, add the MAC address of the stronger AP into the BSSID field of the network manager profile

---

