---
title: "Lenovo ThinkPad P50, Ubuntu 15.10, Kernal 4.3.0: non existant wifi!"
date: 2016-02-05
forum: Networking &amp; Wireless
---

### Post by Leon_Fedden on 2016-02-05
Hi all,

I just can't get the darned wifi to work on this new laptop and its making University really difficult at the moment. Can any gurus make heads or tails of it? I would really appreciate any help offered.

Thanks for reading,

Leon

Note I tried the below and it didn't seem to work:
[http://askubuntu.com/questions/728874/intel-corporation-wireless-8260-808624f3-rev-3a](http://askubuntu.com/questions/728874/intel-corporation-wireless-8260-808624f3-rev-3a)

Dump from sticky:

```



########## wireless info START ##########


Report from: 05 Feb 2016 18:51 GMT +0000


Booted last: 05 Feb 2016 00:00 GMT +0000


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.3.0-040300-generic #201511020949 SMP Mon Nov 2 14:50:44 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-LM [8086:15b7] (rev 31)
	Subsystem: Lenovo Device [17aa:2233]
	Kernel driver in use: e1000e


04:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Device [8086:0130]


3e:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:525a] (rev 01)


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:0090 Validity Sensors, Inc. 
Bus 001 Device 002: ID 04ca:7058 Lite-On Technology Corp. 
Bus 001 Device 006: ID 8087:0a2b Intel Corp. 
Bus 001 Device 005: ID 0765:5010 X-Rite, Inc. 
Bus 001 Device 004: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


cfg80211              532480  0
compat                 16384  1 cfg80211
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.41  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fddc:6362:edd7:0:705e:2e9b:fd7:a05/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: fddc:6362:edd7:0:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3168578 (3.1 MB)  TX bytes:482805 (482.8 KB)
          Interrupt:16 Memory:c5700000-c5720000 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search Home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       746     1  0 18:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-3
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       5b37890e-ffde-4cff-9dca-8376f3662192
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5b37890e-ffde-4cff-9dca-8376f3662192 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.41/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1454784216
DHCP4.OPTION[9]:                        domain_name = Home
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.0.41
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fddc:6362:edd7:0:705e:2e9b:fd7:a05/64
IP6.ADDRESS[2]:                         fddc:6362:edd7:0:<IP6 'eth0' [IF]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'eth0' [IF]>/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fddc:6362:edd7::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fddc:6362:edd7:0:c23e:fff:fec2:dd9c
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:24:91:f7:55:a3:90:ae:86:b4:dc:46:d1:72:43:b7:40
DHCP6.OPTION[2]:                        dhcp6_name_servers = fddc:6362:edd7:0:c23e:fff:fec2:dd9c
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        dhcp6_unknown_15 = 1:20:63:30:33:65:30:66:63:32:64:64:39:63:40:73:6b:79:64:73:6c:7c:31:31:35:32:35:64:65:66:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0
DHCP6.OPTION[5]:                        dhcp6_unknown_16 = 0:0:d:e9:1:20:32:2e:38:38:2e:31:30:38:36:2e:52:7c:30:30:32:7c:53:52:31:30:32:7c:41:35:31:30:31:35:37:43:30:31:31:34:36:34:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0:0
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:c0:3e:f:c2:dd:9c


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


Region: Europe/London (based on set time zone)


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


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.3.0-040300-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150923-0-gddfdd49) using backports backports-20150923-0-g0f7130e
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     731EF46475966BA3A6FFCDB
depends:        compat
vermagic:       4.3.0-040300-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15b7 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[    9.790396] wl: disagrees about version of symbol wiphy_unregister
[    9.790397] wl: Unknown symbol wiphy_unregister (err -22)
[    9.790411] wl: disagrees about version of symbol __ieee80211_get_channel
[    9.790412] wl: Unknown symbol __ieee80211_get_channel (err -22)
[    9.790444] wl: disagrees about version of symbol wiphy_free
[    9.790445] wl: Unknown symbol wiphy_free (err -22)
[   10.031998] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   11.760455] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[   11.760459] e1000e 0000:00:1f.6 eth0: 10/100 speed: disabling TSO
[   11.760506] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   40.458057] e1000e: eth0 NIC Link is Down
[  283.416589] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[  283.416600] e1000e 0000:00:1f.6 eth0: 10/100 speed: disabling TSO


########## wireless info END ############



```

---

### Post by chili555 on 2016-02-05
Please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and show us:```
sudo modprobe iwlwifi && dmesg | grep iwl 
```

May we also see:```
modinfo iwlwifi | grep 24F3 | grep 0130 
```

---

