---
title: "issue with wifi Ralink RT3290LE, just installed rt3290sta"
date: 2016-11-13
forum: Networking &amp; Wireless
---

### Post by js10002 on 2016-11-13
Hello,

Since few weeks, my wifi doesn't start anymore (Wifi device not ready).

I noticed my wifi driver was a rt2800, but my nw card is actually a rt3290. This configuration used to work before, but somehow it stopped working and I assumed that installing the right driver would fix things. I found this post ; [http://askubuntu.com/questions/545238/how-to-install-wifi-driver-ralink-rt3290/557427#557427](http://askubuntu.com/questions/545238/how-to-install-wifi-driver-ralink-rt3290/557427#557427) in which Jim Colaco provides a driver for the rt3290. I installed it and follow the instructions, however i did not remove the old rt2800 *before installing it *... So the whole installation of the rt3290sta went through, it showed a "FATAL" message near the end, regarding the existence of this rt2800 driver, but it didn't stop.

Then only i remove the rt2800 driver :
> sudo modprobe -rfv rt2800pci
sudo apt-get remove --purge bcmwl-kernel-source


Obvisouly I did many wrong things, the wifi configuration is now out of control and i don't know what to do. Anyone can help please ?

[COLOR=#0000cd][SIZE=3][B]Output from wireless-info : 
[/B][/SIZE][/COLOR]
```

########## wireless info START ##########


Report from: 14 Nov 2016 05:14 CET +0100


Booted last: 14 Nov 2016 00:00 CET +0100


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


MATE (from ~/.dmrc)


##### lspci #############################


01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    DeviceName: Realtek PCIe GBE Family Controller
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:1894]


02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Ada
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c0e Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              565248  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt3290sta            1155072  0
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d3e4:274:59b2:c817/64 Scope:Link
          inet6 addr: 2a01:cb04:5ab:d300:352e:c391:21b5:35c0/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:706960 (706.9 KB)  TX bytes:199384 (199.3 KB)


rename3   Link encap:Ethernet  HWaddr <MAC 'rename3' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


rename3   Ralink STA  
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       769     1  1 05:13 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.2/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       8551be98-8cd5-4e0b-8373-8a0c3b52e314
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{26}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8551be98-8cd5-4e0b-8373-8a0c3b52e314 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.17/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.17
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
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1479183202
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:42:38:32:36:36:43:5:f:41:4e:31:35:33:30:39:32:35:38:32:39:32:32:36:6:9:4c:69:76:65:62:6f:78:20:33
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         2a01:cb04:5ab:d300:352e:c391:21b5:35c0/64
IP6.ADDRESS[2]:                         fe80::d3e4:274:59b2:c817/64
IP6.GATEWAY:                            fe80::ba26:6cff:fec5:fb2
IP6.ROUTE[1]:                           dst = 2a01:cb04:5ab:d300::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::ba26:6cff:fec5:fb2
IP6.DOMAIN[1]:                          home
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::ba26:6cff:fec5:fb2
DHCP6.OPTION[3]:                        dhcp6_domain_search = home.
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_server_id = 0:1:0:1:1f:ad:96:b7:b8:26:6c:c5:f:b2
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:78:3e:f4:15:b5:22:ca:ed:6a:7:24:ba:4c:79:9b:45


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
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Livebox-4881]] (600 root)
[connection] id=Livebox-4881 | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-4881
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Livebox-0FB2]] (600 root)
[connection] id=Livebox-0FB2 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-0FB2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HUAWEI-B310-96D3]] (600 root)
[connection] id=HUAWEI-B310-96D3 | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HUAWEI-B310-96D3
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HUAWEI B310FF40]] (600 root)
[connection] id=HUAWEI B310FF40 | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HUAWEI B310FF40
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/mon-reseau]] (600 root)
[connection] id=mon-reseau | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=mon-reseau
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/yougorgeous]] (600 root)
[connection] id=yougorgeous | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=yougorgeous
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/kieboom]] (600 root)
[connection] id=kieboom | type=wifi | permissions=user:xavier:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=kieboom
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


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


eno1      no frequency information.


rename3   0 channels


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


rename3   Interface doesn't support scanning : Network is down


##### module infos ######################


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


[rt3290sta]
filename:       /lib/modules/4.4.0-47-generic/updates/dkms/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     073AC1AA84019DBCFEC8F58
depends:        
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


coretemp


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


[/etc/modprobe.d/blacklist-ralink.conf]
blacklist rt2800pci
blacklist rt2x00pci


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


[/etc/pm/power.d/disable_wol] (777 root)
(...) 


##### udev rules ########################


##### dmesg #############################


[    3.976185] rt3290sta: module license 'unspecified' taints kernel.
[    3.976768] rt3290sta: module verification failed: signature and/or required key missing - tainting kernel
[    4.249196] rt2860 0000:02:00.0 rename3: renamed from ra0
[    5.616290] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    5.704831] r8169 0000:01:00.2 eno1: link down
[    5.704898] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    7.628294] r8169 0000:01:00.2 eno1: link up
[    7.628305] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready


########## wireless info END ############

```

Thanks in advance :KS

Xavier

---

### Post by wildmanne39 on 2016-11-14
The driver is not loading because of this:
> [    3.976768] rt3290sta: module verification failed: signature and/or required key missing - tainting kernelsecure boot is not allowing it to load, if you turn secure boot off then it might load but the rt2800pci is the correct driver for your device.

Did you have issues when using that driver?

Also the one you tried to install is old I doubt it will work.

Let's try:
```
sudo rm /etc/modprobe.d/blacklist-ralink.conf
```
Then:
```
sudo modprobe -v rt2800pci
```
does the wifi work?

---

### Post by js10002 on 2016-11-14
it worked, thanks a lot !!!

i've no idea what you just did, but after exec your lines + a restart, the wifi is working again. Amazing :)

---

### Post by wildmanne39 on 2016-11-14
Glad it is working!
Enjoy!

---

