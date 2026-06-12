---
title: "Realtek Ethernet not connecting properly on 15.04"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by Bowei_Zhao on 2015-09-03
Just installed a fresh 15.04 on my desktop. 

I have a Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller but nothing is allowing it to connect.

Drivers are R8169 from Realtek

I have included the info-txt below. I have already tried modifying resolv.conf with Google's DNS's and adding eth0 and dhcp to network interfaces. None of it really working. 

```


########## wireless info START ##########

Report from: 03 Sep 2015 20:15 EDT -0400

Booted last: 03 Sep 2015 20:08 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:32 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 262a:10ac  
Bus 006 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05c6:676a Qualcomm, Inc. 
Bus 001 Device 004: ID 1532:011a Razer USA, Ltd 
Bus 001 Device 003: ID 046d:c249 Logitech, Inc. 
Bus 001 Device 002: ID 2109:3431  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              540672  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:235 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56209 (56.2 KB)  TX bytes:1113 (1.1 KB)

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.193  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6780894 (6.7 MB)  TX bytes:611748 (611.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

usb0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    1024   0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     0      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       622     1  0 20:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         OnePlus
GENERAL.PRODUCT:                        A0001
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'usb0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/usb1/1-1/1-1.4/1-1.4:1.0/net/usb0
GENERAL.IP-IFACE:                       usb0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       c4cc10f0-479c-43f0-8031-4976bb6775fa
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c4cc10f0-479c-43f0-8031-4976bb6775fa | Wired connection 2
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.42.193/24, gw = 192.168.42.129
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.193
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1441329228
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = bowei-Linuxbook
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'usb0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         39 (Device disconnected by user or client)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4e98bf4c-d851-4595-abdd-565ffd663c3a | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on

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

Sorry, try again.

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

eth0      no frequency information.

usb0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:BF:A7:5C:65:57:07:FD:5A:4B:C3:A9:A6:CB:49:E0:1A:16:E1:F5
sig_hashalgo:   sha512
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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############




```

below are additionals
```


**bowei@bowei-Linuxbook:~$ cat /etc/network/interfaces**
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**bowei@bowei-Linuxbook:~$ cat /etc/resolv.conf**
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


```

If anyone can help I would appreciate it.

I am currently using my tethered phone to access the net through Wifi.

Thanks.

---

### Post by Bowei_Zhao on 2015-09-03
SOLVED

My drivers r8169 were the issue.

I installed Synaptic Package Manager

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install synaptic

```

and then reloaded/updated it.

Search 'Realtek' and get and install r8168-dkms

then 

```

sudo gedit  /etc/modprobe.d/blacklist.conf
```
to open up the blacklist file and add the line

blacklist r8169 to it

then sudo reboot and it should work.

---

