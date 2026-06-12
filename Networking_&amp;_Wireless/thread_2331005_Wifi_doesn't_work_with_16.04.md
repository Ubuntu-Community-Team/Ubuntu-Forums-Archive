---
title: "Wifi doesn't work with 16.04"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by mitroffsky on 2016-07-17
Hi guys,

I've got a nasty issue with my Ubuntu. Two days ago (I was still using Ubuntu 15.10), I found that my Wifi was not working (having the icon there, but cannot connect). Since then I've tried so many things, none of which worked out fine. Today I installed the new 16.04 Ubuntu and still the same issue. Can you help me? Thanks!

---

### Post by jeremy31 on 2016-07-17
Please see the wireless script link in my signature and post your results

---

### Post by mitroffsky on 2016-07-19
Hi,

This is the info:

```


########## wireless info START ##########


Report from: 19 Jul 2016 21:13 EEST +0300


Booted last: 19 Jul 2016 00:00 EEST +0300


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e071]
	Kernel modules: bcma, wl


0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Sony Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [104d:90b8]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:5729 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
7: nfc0: NFC
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


cfg80211              565248  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp14s0   Link encap:Ethernet  HWaddr <MAC 'enp14s0' [IF1]>  
          inet addr:130.204.13.158  Bcast:130.204.31.255  Mask:255.255.224.0
          inet6 addr: fe80::847a:89bc:1ab5:f979/64 Scope:Link
          inet6 addr: 2a00:4802:3a0::2fc5/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:563705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:704442201 (704.4 MB)  TX bytes:33195067 (33.1 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp14s0   no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         130.204.0.1     0.0.0.0         UG    100    0        0 enp14s0
130.204.0.0     0.0.0.0         255.255.224.0   U     100    0        0 enp14s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp14s0
213.240.237.69  130.204.0.1     255.255.255.255 UGH   100    0        0 enp14s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       678     1  0 Jul17 ?        00:00:06 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp14s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp14s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:0e:00.0/net/enp14s0
GENERAL.IP-IFACE:                       enp14s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       91dc1952-5c9b-4d94-89fa-1013b32ee8c1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   91dc1952-5c9b-4d94-89fa-1013b32ee8c1 | Wired connection 1
IP4.ADDRESS[1]:                         130.204.13.158/19
IP4.GATEWAY:                            130.204.0.1
IP4.ROUTE[1]:                           dst = 213.240.237.69/32, nh = 130.204.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             217.9.239.90
IP4.DNS[2]:                             217.9.239.94
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 213.240.237.69
DHCP4.OPTION[10]:                       expiry = 1468960713
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 8966
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 130.204.13.158
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 130.204.0.1
DHCP4.OPTION[19]:                       broadcast_address = 130.204.31.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       wpad = docsis
DHCP4.OPTION[23]:                       domain_name_servers = 217.9.239.90 217.9.239.94
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.224.0
DHCP4.OPTION[26]:                       network_number = 130.204.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 213.240.237.69
IP6.ADDRESS[1]:                         2a00:4802:3a0::2fc5/128
IP6.ADDRESS[2]:                         fe80::847a:89bc:1ab5:f979/64
IP6.GATEWAY:                            fe80::26e9:b3ff:fe1b:72d9


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


Region: Europe/Sofia (based on set time zone)


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


enp14s0   no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp14s0   Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS


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


[12212.587582] r8169 0000:0e:00.0 enp14s0: link down
[12217.947456] r8169 0000:0e:00.0 enp14s0: link up
[12223.550435] IPv6: ADDRCONF(NETDEV_UP): enp14s0: link is not ready
[12223.
596557] r8169 0000:0e:00.0 enp14s0: link down (repeated 2 times)
[12223.596790] IPv6: ADDRCONF(NETDEV_UP): enp14s0: link is not ready
[12226.823798] r8169 0000:0e:00.0 enp14s0: link up
[12226.823822] IPv6: ADDRCONF(NETDEV_CHANGE): enp14s0: link becomes ready
[14617.517476] r8169 0000:0e:00.0 enp14s0: link down (repeated 2 times)
[14806.627186] IPv6: ADDRCONF(NETDEV_UP): enp14s0: link is not ready
[14806.682678] r8169 0000:0e:00.0 enp14s0: link down
[14806.683112] IPv6: ADDRCONF(NETDEV_UP): enp14s0: link is not ready
[15473.251308] r8169 0000:0e:00.0 enp14s0: link up
[15473.251334] IPv6: ADDRCONF(NETDEV_CHANGE): enp14s0: link becomes ready


########## wireless info END ############
```

---

### Post by jeremy31 on 2016-07-20
See if disabling secure boot in BIOS helps

---

### Post by mitroffsky on 2016-07-20
This didn't work, but something else did: I clicked on restore default settings of security boot in Bios and now wifi is back in the game:0 Thanks for the help!

---

