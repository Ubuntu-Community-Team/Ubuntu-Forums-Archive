---
title: "Hard and soft blocked WIFI on HP Compaq nx6310 xUbuntu 16.02"
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by Davor_Hranjec on 2016-06-24
Hi everyone!

So i am having xUbuntu 16.02 on HP Compaq nx6310 and nothing from this closed thread [http://ubuntuforums.org/showthread.php?t=2237576](http://ubuntuforums.org/showthread.php?t=2237576) didn't worked for me - because of some reason - after all when I type [COLOR=#000000][FONT=Ubuntu Mono]rfkill list all[/FONT][/COLOR]
 it only says this:

0: hp-gps: GPS
	Soft blocked: yes
	Hard blocked: yes

and  button (of course) doesn't do anything when I press it - and it worked before.

Please help me turn on my WIFI, because otherwise I can't do my job :( Thank you in advance!
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Davor_Hranjec on 2016-06-27
So i run the script for 5th post on this page [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)

and i got this - can somebody help me pls?

```
[COLOR=#000000]########## wireless info START ##########[/COLOR]
Report from: 27 Jun 2016 10:40 CEST +0200

Booted last: 27 Jun 2016 00:00 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Hewlett-Packard Company BCM4401-B0 100Base-TX [103c:30aa]
	Kernel driver in use: b44

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: hp-gps: GPS
	Soft blocked: yes
	Hard blocked: yes

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
ssb                    57344  1 b44
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e90c:661c:795a:4e3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2180622 (2.1 MB)  TX bytes:297087 (297.0 KB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       635     1  0 10:33 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/ssb0:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       3072f093-209a-4833-95c9-001a3e15cea4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3072f093-209a-4833-95c9-001a3e15cea4 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.19/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             83.139.104.2
IP4.DNS[2]:                             83.139.105.2
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 83.139.104.2 83.139.105.2
DHCP4.OPTION[5]:                        ip_address = 192.168.0.19
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1467621249
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 604800
IP6.ADDRESS[1]:                         fe80::e90c:661c:795a:4e3c/64
IP6.GATEWAY:                            

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

Region: Europe/Zagreb (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ssb]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

##### module parameters #################

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

[/etc/modprobe.d/hp.conf]
options hp_wmi wireless=1

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/sl-modem.conf]
install slamr /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slamr; test -e /dev/slamr0 && (chmod 660 /dev/slamr0 && chgrp dialout /dev/slamr0) || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)
remove slamr /sbin/modprobe --remove --ignore-remove slamr; test -e /dev/slamr0 && /bin/rm -f /dev/slamr0 2>/dev/null
install slusb /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slusb; test -e /dev/slusb0 && (chmod 660 /dev/slusb0 && chgrp dialout /dev/slusb0) || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)
remove slusb /sbin/modprobe --remove --ignore-remove slusb; test -e /dev/slusb0 && /bin/rm -f /dev/slusb0 2>/dev/null

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   30.786081] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   33.816228] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   33.816237] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[   33.816397] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 [COLOR=#000000]########## wireless info END ############[/COLOR]
```

---

### Post by jeremy31 on 2016-06-27
Is wifi enabled in BIOS as there is no sign of a wireless device in the script results

---

### Post by Davor_Hranjec on 2016-06-27
Hi jeremy31,

here are the all modifiable screens in my BIOS except password and boot stuff:

[http://i.share.pho.to/94ee1444_l.jpeg](http://i.share.pho.to/94ee1444_l.jpeg)

[http://i.share.pho.to/6bec64ad_l.jpeg](http://i.share.pho.to/6bec64ad_l.jpeg)

[http://i.share.pho.to/94ee1444_l.jpeg](http://i.share.pho.to/94ee1444_l.jpeg)

and also the hardware proof that there is wifi inside, but even on click, light doesn't want to turn on :confused:

[http://i.share.pho.to/f1a305fd_l.jpeg](http://i.share.pho.to/f1a305fd_l.jpeg)

---

### Post by X-RED_Tech on 2016-06-27
Disconnected -> Remove and re-seat the WiFi card.
Busted (more likely) -> Replace it.

---

