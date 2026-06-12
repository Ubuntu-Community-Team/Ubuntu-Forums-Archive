---
title: "wi-fi does not work on Ubuntu 18.04"
date: 2018-08-28
forum: Networking &amp; Wireless
---

### Post by joaoricardolo on 2018-08-28
Hi, I'm having trouble wi-fi. I think it was after I updated Ubuntu to 18.04. I've already tried this README  and at first it worked, except that after I rebooted I think it did not work anymore. Then I tried the ndisgtk, taking the drivers from windows (I used only a .inf in case, despite having more driver files), but tb did not work. I saw in the forum itself that it has a wireless-info script, which takes snapshots of the situation of our wi-fi, and I executed it. I know my board is RealTek, rtl8188ee. I'll try to post the script result here. I'm sorry about the text, but I'm using Google Translate, to translate from Portuguese to English. 


Here's the wireless-info.txt output:




```
########## wireless info START ##########


Report from: 28 Aug 2018 16:17 -03 -0300


Booted last: 28 Aug 2018 00:00 -03 -0300


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: AzureWave RTL8188EE Wireless Network Adapter [1a3b:1f38]
    Kernel modules: ndiswrapper


02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1297:2033]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 1ea7:0064  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b351 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


ndiswrapper           282624  0
wmi                    24576  0


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0f2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.9  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::dd68:b44f:eaba:b226  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 6657  bytes 3991169 (3.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5278  bytes 1105228 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2117  bytes 151844 (151.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2117  bytes 151844 (151.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp2s0f2  no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f2
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f2


##### resolv.conf #######################


nameserver 127.0.0.53
search Home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       697     1  0 15:48 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.2/net/enp2s0f2
GENERAL.IP-IFACE:                       enp2s0f2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexão cabeada 1
GENERAL.CON-UUID:                       071dda87-922a-392a-a73a-19e8b88cb87b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.9/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        domain_name = Home
DHCP4.OPTION[8]:                        expiry = 1535568766
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       ip_address = 192.168.1.9
DHCP4.OPTION[15]:                       requested_wpad = 1
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_netbios_scope = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       routers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       dhcp_message_type = 5
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[28]:                       domain_name_servers = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::dd68:b44f:eaba:b226/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   071dda87-922a-392a-a73a-19e8b88cb87b | Conexão cabeada 1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Familia]] (600 root)
[connection] id=Familia | type=wifi | permissions=user:joao:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Familia
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=joao-H14CU01
[ipv4] method=shared
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp2s0f2  no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0f2  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ndiswrapper]
filename:       /lib/modules/4.15.0-33-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     555F759E80ADD1278ECCA2C
depends:        
retpoline:      Y
name:           ndiswrapper
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


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


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008179sv00000179sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000187sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000188sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000193sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000196sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000197sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000198sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001006sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001238sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012A8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012B8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012C8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012D8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000197Dsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001D38sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001F38sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00002199sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000219Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000219Bsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000219Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000804Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008197sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000081BFsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008317sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008318sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000E08Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000001Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000002Bsd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000003Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000818Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv00008192sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv00008193sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv00008196sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000819Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv00008202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv00008753sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00000743sd00002A6Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00000812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv000020EFsd0000148Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00003305sd00001186bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00006108sd0000168Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000807Esd000020F4bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00008200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv000086DDsd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00008812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A811sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A813sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A817sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000B812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000D822sd00007392bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008813sv00002970sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008813sv00008813sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008813sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00001611sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00001ABDsd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000207Fsd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002091sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002161sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002162sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Bsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002209sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002482sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002484sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002485sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002486sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002487sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002A09sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002B09sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00008198sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv000085B4sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00008821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A801sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A802sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A803sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A804sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A805sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A814sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A815sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A816sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A818sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A819sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A820sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000B821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00000733sd00002A6Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00001723sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00001724sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00001B7Dsd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000207Fsd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002159sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000215Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002165sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv000021FDsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002231sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002483sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002485sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002A59sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002A65sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002A66sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002A67sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000804Csd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000804Dsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00008167sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv000081C1sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00008723sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00008724sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00008739sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B001sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B725sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B726sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B727sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B728sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B729sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B730sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B731sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B732sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B733sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B734sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B735sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B736sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B737sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B738sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B740sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B741sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E089sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E08Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E090sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E091sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E09Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B814sv0000B814sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B814sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B821sv0000B821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00000808sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00001995sd000010CFbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00002950sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00002951sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00002952sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00003081sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00005467sd00002A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000831Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000840Bsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv00008746sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000874Csd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B023sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B023sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B024sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B025sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B026sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B027sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B028sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B029sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B123sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B125sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv0000B822sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B822sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00000809sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00001809sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00003040sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00003041sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00003042sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00003043sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00003044sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00003045sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00003046sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv00004134sd0000144Dbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000831Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000A416sd00001019bc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C024sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C025sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C026sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C027sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C028sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C029sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C811sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C815sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C823sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv0000C824sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000C82Bsv0000C82Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000C82Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv00000807sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv00001087sd000011ADbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv00002741sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv00002742sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv00008319sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv0000D123sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv0000D723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000D723sv*sd*bc*sc*i* ndiswrapper


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   24.571132] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ZwDeviceIoControlFile'
[   24.571145] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[   24.571150] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[   24.571155] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'EtwWriteTransfer'
[   24.571160] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'EtwSetInformation'
[   24.571164] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'EtwUnregister'
[   24.571169] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'EtwRegister'
[   24.571180] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   24.571210] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'sscanf_s'
[   24.571216] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExAllocatePoolWithQuotaTag'
[   24.571220] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PsGetVersion'
[   24.571225] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ZwQuerySystemInformation'
[   24.571230] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'__chkstk'
[   24.571234] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'strncpy_s'
[   24.571239] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'strcpy_s'
[   24.571254] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExGetFirmwareEnvironmentVariable'
[   24.571266] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'wcsstr'
[   24.571279] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ZwEnumerateKey'
[   24.571285] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'IoCsqInitialize'
[   24.571290] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'IoCsqInsertIrp'
[   24.571295] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'IoCsqRemoveNextIrp'
[   24.571310] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   24.571316] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   24.571322] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   24.571327] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   24.571333] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   24.571339] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   24.571346] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterWdiMiniportDriver'
[   24.571352] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterWdiMiniportDriver'
[   24.571357] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   24.571363] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   24.571369] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   24.571375] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   24.571392] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   24.571397] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   24.571405] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   24.571411] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   24.571416] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   24.571422] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   24.571430] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   24.571436] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   24.571446] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   24.571451] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   24.571457] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   24.571462] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   24.571468] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   24.571473] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   24.571481] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   24.571486] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   24.571492] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   24.571498] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   24.571506] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   24.571511] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   24.571517] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   24.571543] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   24.571549] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   24.571557] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   24.571569] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   24.571574] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   24.571579] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   24.571583] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   24.571586] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netrtwlane'
[   24.572369] ndiswrapper (load_wrap_driver:103): couldn't load driver netrtwlane; check system log for messages from 'loadndisdriver'


########## wireless info END ############
```


Thank you very much in advance.

---

### Post by jeremy31 on 2018-08-28
Start with ```
sudo apt purge ndiswrapper && sudo rm /etc/modprobe.d/ndiswrapper.conf
```
Reboot and provide new wireless script results

---

### Post by howefield on 2018-08-28
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by joaoricardolo on 2018-08-28
the command:
**   sudo apt purge ndiswrapper && sudo rm /etc/modprobe.d/ndiswrapper.conf**
returned:
**    rm: '/etc/modprobe.d/ndiswrapper.conf' could not be removed: nonexistent file or directory**
more uninstalled ndiswrapper, just did not remove the .conf. I do not know if that 
Below is the new wireless-info output anything.


Below is the new **wireless-info** output




```
########## wireless info START ##########


Report from: 28 Aug 2018 17:47 -03 -0300


Booted last: 28 Aug 2018 00:00 -03 -0300


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: AzureWave RTL8188EE Wireless Network Adapter [1a3b:1f38]
	Kernel modules: rtl8188ee


02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1297:2033]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 1ea7:0064  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b351 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


mac80211              778240  0
cfg80211              622592  1 mac80211
wmi                    24576  0


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0f2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.9  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::dd68:b44f:eaba:b226  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1139  bytes 836595 (836.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1008  bytes 156660 (156.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 342  bytes 30692 (30.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 342  bytes 30692 (30.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp2s0f2  no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f2
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f2


##### resolv.conf #######################


nameserver 127.0.0.53
search Home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       705     1  0 17:45 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.2/net/enp2s0f2
GENERAL.IP-IFACE:                       enp2s0f2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexão cabeada 1
GENERAL.CON-UUID:                       071dda87-922a-392a-a73a-19e8b88cb87b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.9/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        next_server = 0.0.0.0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        domain_name = Home
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       routers = 192.168.1.1
DHCP4.OPTION[11]:                       requested_wpad = 1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       requested_interface_mtu = 1
DHCP4.OPTION[16]:                       ip_address = 192.168.1.9
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_message_type = 5
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       expiry = 1535575534
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::dd68:b44f:eaba:b226/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   071dda87-922a-392a-a73a-19e8b88cb87b | Conexão cabeada 1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Familia]] (600 root)
[connection] id=Familia | type=wifi | permissions=user:joao:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Familia
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=joao-H14CU01
[ipv4] method=shared
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp2s0f2  no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0f2  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[mac80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     AFB624FD5B16A8AA59A9CF7
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   22.068449] rtlwifi: version magic '4.15.0-29-generic SMP mod_unload ' should be '4.15.0-33-generic SMP mod_unload '


########## wireless info END ############
```

---

### Post by jeremy31 on 2018-08-28
Try ```
cd rtlwifi_new
make clean
make
sudo make install
```

Reboot

---

### Post by joaoricardolo on 2018-08-28
Funcionou! Obrigado!
mas toda vez que eu reiniciar, vai funcionar agora?

---

### Post by jeremy31 on 2018-08-28
I hope it keeps working after new kernel updates.  Please remember most of ubuntuforums is english only

---

### Post by joaoricardolo on 2018-08-28
Ok, it's that I'm using Google Translate, and sometimes I fail.

---

