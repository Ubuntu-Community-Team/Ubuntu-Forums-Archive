---
title: "Does not detect wireless networks"
date: 2017-07-07
forum: Networking &amp; Wireless
---

### Post by dr4gl0k on 2017-07-07
Running linux 17.04 on lenovo thinkcentre. Ethernet connects fine but the networks menu does not contain any wireless networks.
Menu reads:

Ethernet (Grey)
Auto Ethernet(Can check)
Disconnect (can check)
VPN connections > Add a vpn connection.. (grey)
Enable Networking (checked)
Connection Info
edit connections...

---

### Post by vasa1 on 2017-07-07
Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) very carefully and then please provide the output of the wireless info script. You may need to install *pastebinit* on your system first: it's a small package; you can install it with *sudo apt-get install pastebinit* or whatever other means you prefer.

---

### Post by dr4gl0k on 2017-07-08
```
########## wireless info START ##########

Report from: 08 Jul 2017 09:05 EDT -0400

Booted last: 08 Jul 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

##### kernel ############################

Linux 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
	DeviceName:  Onboard LAN
	Subsystem: Lenovo Ethernet Connection I217-LM [17aa:309b]

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0846:9053 NetGear, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 003 Device 002: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.4  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 2600:8807:a24a:bc00:8ab9:34f3:bbd5:1f8b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::d053:ce7d:c1c1:29c6  prefixlen 64  scopeid 0x20<link>
        inet6 2600:8807:a24a:bc00:a12a:62db:99d7:aad3  prefixlen 64  scopeid 0x0<global>
        inet6 2600:8807:a24a:bc00::3  prefixlen 128  scopeid 0x0<global>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 59243  bytes 83038070 (83.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 29344  bytes 2833683 (2.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7e00000-f7e20000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1120  bytes 81369 (81.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1120  bytes 81369 (81.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root       603     1  0 08:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.12-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       622578e4-f61c-42eb-a08c-780c0b6362bc
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   622578e4-f61c-42eb-a08c-780c0b6362bc | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.0.4/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             68.105.28.11
IP4.DNS[2]:                             68.105.29.11
IP4.DNS[3]:                             68.105.28.12
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1499522165
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.4
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 3600
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 68.105.28.11 68.105.29.11 68.105.28.12
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         2600:8807:a24a:bc00::3/128
IP6.ADDRESS[2]:                         2600:8807:a24a:bc00:a12a:62db:99d7:aad3/64
IP6.ADDRESS[3]:                         2600:8807:a24a:bc00:8ab9:34f3:bbd5:1f8b/64
IP6.ADDRESS[4]:                         fe80::d053:ce7d:c1c1:29c6/64
IP6.GATEWAY:                            fe80::deef:9ff:fe1e:46b
IP6.ROUTE[1]:                           dst = 2600:8807:a24a:bc00::/56, nh = fe80::deef:9ff:fe1e:46b, mt = 100
IP6.ROUTE[2]:                           dst = 2600:8807:a24a:bc00::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2001:578:3f::30
IP6.DNS[2]:                             2001:578:3f:1::30
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:c4:23:e4:9d:9a:6e:b5:22:fa:10:92:52:f0:a7:e7:e2
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:578:3f::30 2001:578:3f:1::30
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        rebind = 1350
DHCP6.OPTION[5]:                        max_life = 3600
DHCP6.OPTION[6]:                        preferred_life = 1800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1499518569
DHCP6.OPTION[10]:                       ip6_address = 2600:8807:a24a:bc00::3
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       renew = 900
DHCP6.OPTION[13]:                       starts = 1499518569
DHCP6.OPTION[14]:                       iaid = d4:43:3e:fb
DHCP6.OPTION[15]:                       dhcp6_server_id = 0:3:0:1:dc:ef:9:1e:4:6b

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

lo        no frequency information.

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############
```

---

### Post by dr4gl0k on 2017-07-08
Sorry for the delay, That's the result of the wireless info script.

---

### Post by jeremy31 on 2017-07-08
Not sure if it works with Ubuntu 17.04 but it does in Ubuntu 16.04 with these commands with working
```
sudo apt-get install build-essential git dkms
git clone https://github.com/jurobystricky/Netgear-A6210
sudo dkms add ./Netgear-A6210
sudo dkms install Netgear-A6210/2.5.0
```
Reboot

---

### Post by dr4gl0k on 2017-07-08
No, didnt do anything.

---

### Post by jeremy31 on 2017-07-08
Run the script again and post the new results using code tags

---

### Post by dr4gl0k on 2017-07-08
```

########## wireless info START ##########

Report from: 08 Jul 2017 12:23 EDT -0400

Booted last: 08 Jul 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

##### kernel ############################

Linux 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
	DeviceName:  Onboard LAN
	Subsystem: Lenovo Ethernet Connection I217-LM [17aa:309b]

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0846:9053 NetGear, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 003 Device 002: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.4  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 2600:8807:a24a:bc00:8836:f31c:a157:22d5  prefixlen 64  scopeid 0x0<global>
        inet6 2600:8807:a24a:bc00:8ab9:34f3:bbd5:1f8b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::d053:ce7d:c1c1:29c6  prefixlen 64  scopeid 0x20<link>
        inet6 2600:8807:a24a:bc00::3  prefixlen 128  scopeid 0x0<global>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 7037100  bytes 10402722018 (10.4 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1497304  bytes 125886392 (125.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7e00000-f7e20000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 35176  bytes 2145370 (2.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 35176  bytes 2145370 (2.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root       554     1  0 09:50 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.12-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       622578e4-f61c-42eb-a08c-780c0b6362bc
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   622578e4-f61c-42eb-a08c-780c0b6362bc | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.0.4/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             68.105.28.11
IP4.DNS[2]:                             68.105.29.11
IP4.DNS[3]:                             68.105.28.12
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1499533607
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.4
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 3600
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 68.105.28.11 68.105.29.11 68.105.28.12
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         2600:8807:a24a:bc00::3/128
IP6.ADDRESS[2]:                         2600:8807:a24a:bc00:8836:f31c:a157:22d5/64
IP6.ADDRESS[3]:                         2600:8807:a24a:bc00:8ab9:34f3:bbd5:1f8b/64
IP6.ADDRESS[4]:                         fe80::d053:ce7d:c1c1:29c6/64
IP6.GATEWAY:                            fe80::deef:9ff:fe1e:46b
IP6.ROUTE[1]:                           dst = 2600:8807:a24a:bc00::/56, nh = fe80::deef:9ff:fe1e:46b, mt = 100
IP6.ROUTE[2]:                           dst = 2600:8807:a24a:bc00::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2001:578:3f::30
IP6.DNS[2]:                             2001:578:3f:1::30
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:c4:23:e4:9d:9a:6e:b5:22:fa:10:92:52:f0:a7:e7:e2
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:578:3f::30 2001:578:3f:1::30
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        rebind = 1350
DHCP6.OPTION[5]:                        max_life = 3600
DHCP6.OPTION[6]:                        preferred_life = 1800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1499530270
DHCP6.OPTION[10]:                       ip6_address = 2600:8807:a24a:bc00::3
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       renew = 900
DHCP6.OPTION[13]:                       starts = 1499530270
DHCP6.OPTION[14]:                       iaid = d4:43:3e:fb
DHCP6.OPTION[15]:                       dhcp6_server_id = 0:3:0:1:dc:ef:9:1e:4:6b

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

lo        no frequency information.

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############

```

---

### Post by jeremy31 on 2017-07-08
Try
```
cd Netgear-A6210
make 
sudo make install
```

Post any errors, if no errors reboot

---

### Post by dr4gl0k on 2017-07-08
```

otis@otis-ThinkCentre-M93z:~$ cd Netgear-A6210
bash: cd: Netgear-A6210: No such file or directory
otis@otis-ThinkCentre-M93z:~$ make 
make: *** No targets specified and no makefile found.  Stop.
otis@otis-ThinkCentre-M93z:~$ sudo make install
[sudo] password for otis: 
make: *** No rule to make target 'install'.  Stop.
otis@otis-ThinkCentre-M93z:~$ 


```

---

### Post by jeremy31 on 2017-07-08
```
git clone https://github.com/jurobystricky/Netgear-A6210
cd Netgear-A6210
make
sudo make install
```
Reboot

---

### Post by dr4gl0k on 2017-07-09
Hello? That's the result of the script...

---

### Post by dr4gl0k on 2017-07-09
Ok now it says "device not managed" under the "wifi networks" tab

---

### Post by praseodym on 2017-07-09
Now run

```
sudo touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
```
Reboot

From here: [https://forum.ubuntuusers.de/topic/wlan-treiber-installation-avm-fritz-wlan-usb-a/](https://forum.ubuntuusers.de/topic/wlan-treiber-installation-avm-fritz-wlan-usb-a/)

Edit: Rebooting is stupid, see below!

---

### Post by praseodym on 2017-07-09
If it works it may need to be repeated on every boot. Then modify this file:
```

gksudo gedit /etc/rc.local
```

Add these lines before "exit 0"

```
sleep 5
touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
systemctl restart network-manager
```
Save, close and reboot

---

### Post by dr4gl0k on 2017-07-09
No file is coming up... also it still says "device not managed"

---

### Post by dr4gl0k on 2017-07-09
the document is blank i think...

---

### Post by praseodym on 2017-07-09
Ok, so it shall look like this in the end

```
sleep 5
touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
systemctl restart network-manager

exit 0
```

---

### Post by dr4gl0k on 2017-07-09
** (gedit:2969): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

---

### Post by praseodym on 2017-07-09
Doesn't matter what the terminal shows here. Please add this line at the top of the file (open it again) with blank line before "sleep 5":

```
#!/bin/sh -e
```

---

### Post by dr4gl0k on 2017-07-09
still "device not managed"

---

### Post by BenginM on 2017-07-09
Salutations!

Do you have  "secure boot" enabled or disabled in the UEFI BIOS!

---

### Post by dr4gl0k on 2017-07-09
nope

---

### Post by dr4gl0k on 2017-07-09
disabled

---

### Post by BenginM on 2017-07-09
> **dr4gl0k said:**
> disabled

[SIZE=3][FONT=arial narrow] OK, did you follow**ed jeremy31's instractions in post #11 ! did the "sudo make install" succeed ? if so please run: lsmod and paste the output .**[/FONT][/SIZE]

---

### Post by dr4gl0k on 2017-07-09
```

Module                  Size  Used by
mt7662u_sta          1032192  0
cfg80211              602112  1 mt7662u_sta
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   593920  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_hda_codec_hdmi     49152  1
input_leds             16384  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_seq_midi           16384  0
snd_hda_intel          36864  4
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_rawmidi            32768  1 snd_seq_midi
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
lpc_ich                24576  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
shpchp                 36864  0
mei_me                 40960  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
mei                   102400  1 mei_me
snd                    77824  19 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
acpi_als               16384  0
mac_hid                16384  0
kfifo_buf              16384  1 acpi_als
industrialio           69632  2 acpi_als,kfifo_buf
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   114688  2 hid_generic,usbhid
i915                 1449984  97
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
e1000e                249856  0
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  1
libahci                32768  1 ahci
drm                   352256  5 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
wmi                    16384  0
fjes                   73728  0
video                  40960  1 i915

```

---

### Post by dr4gl0k on 2017-07-09
```

Module                  Size  Used by
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm                   593920  0
snd_hda_intel          36864  4
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
input_leds             16384  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    77824  19 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
lpc_ich                24576  0
shpchp                 36864  0
mei_me                 40960  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
industrialio           69632  2 acpi_als,kfifo_buf
mac_hid                16384  0
mt7662u_sta          1032192  0
cfg80211              602112  1 mt7662u_sta
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   114688  2 hid_generic,usbhid
i915                 1449984  92
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
ahci                   36864  1
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
libahci                32768  1 ahci
e1000e                249856  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  5 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
wmi                    16384  0
fjes                   73728  0
video                  40960  1 i915

```

---

### Post by BenginM on 2017-07-09
That shows that the kernel driver is loaded , 
Module                 
mt7662u_sta

now you might need to restart network manger, run:

sudo service network-manager restart

if the device still not shown up in network manger then run:
sudo modprobe -r mt7662u_sta
sudo modprobe mt7662u_sta 

you might need to restart network-manger again!

---

### Post by dr4gl0k on 2017-07-09
it now says "disconnected" instead.

---

### Post by dr4gl0k on 2017-07-09
working now Thanks everyone!!!

---

### Post by BenginM on 2017-07-09
> **dr4gl0k said:**
> it now says "disconnected" instead.

while the adapter dongle plugged in , i suggest you do a quick reboot .. hopefully!

---

### Post by BenginM on 2017-07-09
> **dr4gl0k said:**
> working now Thanks everyone!!!

Great! if you plan on upgrading the kernel in the future , #See "DKMS install" in:
[https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210)

---

### Post by dr4gl0k on 2017-07-10
Wait... It stopped working upon reboot

---

### Post by jeremy31 on 2017-07-10
Post results for ```
uname -a
```

---

### Post by BenginM on 2017-07-10
You might need to add the kernel driver Module
mt7662u_sta , to
/etc/modules

---

### Post by dr4gl0k on 2017-07-10
```

Linux otis-ThinkCentre-M93z 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```

---

### Post by dr4gl0k on 2017-07-10
otis@otis-ThinkCentre-M93z:~$  /etc/modules 
bash: /etc/modules: Permission denied

---

### Post by jeremy31 on 2017-07-10
A new kernel, try
```
sudo dkms add ./Netgear-A6210
sudo dkms install Netgear-A6210/2.5.0
```
Reboot

---

### Post by dr4gl0k on 2017-07-10
device not managed again

---

### Post by jeremy31 on 2017-07-10
Run the script again and post new results ```
./wireless-info
```

---

### Post by dr4gl0k on 2017-07-11
```

########## wireless info START ##########

Report from: 11 Jul 2017 07:57 EDT -0400

Booted last: 11 Jul 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

##### kernel ############################

Linux 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
	DeviceName:  Onboard LAN
	Subsystem: Lenovo Ethernet Connection I217-LM [17aa:309b]

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0846:9053 NetGear, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 003 Device 003: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 003 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

cfg80211              602112  1 mt7662u_sta
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.4  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 2600:8807:a24a:bc00:8ab9:34f3:bbd5:1f8b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::d053:ce7d:c1c1:29c6  prefixlen 64  scopeid 0x20<link>
        inet6 2600:8807:a24a:bc00:180e:20b1:8ad:8dba  prefixlen 64  scopeid 0x0<global>
        inet6 2600:8807:a24a:bc00::3  prefixlen 128  scopeid 0x0<global>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 125071  bytes 11960945 (11.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2944  bytes 368704 (368.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7e00000-f7e20000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 342  bytes 25182 (25.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 342  bytes 25182 (25.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlan0     Ralink STA  
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root       811     1  0 Jul10 ?        00:00:09 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.12-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       622578e4-f61c-42eb-a08c-780c0b6362bc
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   622578e4-f61c-42eb-a08c-780c0b6362bc | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.0.4/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             68.105.28.11
IP4.DNS[2]:                             68.105.29.11
IP4.DNS[3]:                             68.105.28.12
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1499776910
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.4
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 3600
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 68.105.28.11 68.105.29.11 68.105.28.12
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         2600:8807:a24a:bc00::3/128
IP6.ADDRESS[2]:                         2600:8807:a24a:bc00:180e:20b1:8ad:8dba/64
IP6.ADDRESS[3]:                         2600:8807:a24a:bc00:8ab9:34f3:bbd5:1f8b/64
IP6.ADDRESS[4]:                         fe80::d053:ce7d:c1c1:29c6/64
IP6.GATEWAY:                            fe80::deef:9ff:fe1e:46b
IP6.ROUTE[1]:                           dst = 2600:8807:a24a:bc00::/56, nh = fe80::deef:9ff:fe1e:46b, mt = 100
IP6.ROUTE[2]:                           dst = 2600:8807:a24a:bc00::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2001:578:3f::30
IP6.DNS[2]:                             2001:578:3f:1::30
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:c4:23:e4:9d:9a:6e:b5:22:fa:10:92:52:f0:a7:e7:e2
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:578:3f::30 2001:578:3f:1::30
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        rebind = 1350
DHCP6.OPTION[5]:                        max_life = 3600
DHCP6.OPTION[6]:                        preferred_life = 1800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1499773365
DHCP6.OPTION[10]:                       ip6_address = 2600:8807:a24a:bc00::3
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       renew = 900
DHCP6.OPTION[13]:                       starts = 1499773365
DHCP6.OPTION[14]:                       iaid = d4:43:3e:fb
DHCP6.OPTION[15]:                       dhcp6_server_id = 0:3:0:1:dc:ef:9:1e:4:6b

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         NETGEAR
GENERAL.PRODUCT:                        A6210
GENERAL.DRIVER:                         RALINK WLAN
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/2
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/1E046F 1]] (600 root)
[connection] id=1E046F 1 | type=wifi | permissions=user:otis:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=1E046F
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sweetie 4]] (600 root)
[connection] id=sweetie 4 | type=wifi | permissions=user:otis:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=sweetie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sweetie 1]] (600 root)
[connection] id=sweetie 1 | type=wifi | permissions=user:otis:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=sweetie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/1E046F]] (600 root)
[connection] id=1E046F | type=wifi | permissions=user:otis:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=1E046F
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sweetie 2]] (600 root)
[connection] id=sweetie 2 | type=wifi | permissions=user:otis:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=sweetie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sweetie 3]] (600 root)
[connection] id=sweetie 3 | type=wifi | permissions=user:otis:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=sweetie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sweetie]] (600 root)
[connection] id=sweetie | type=wifi | permissions=user:otis:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=sweetie
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

lo        no frequency information.

wlan0     0 channels

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.10.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

sleep 5
touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
systemctl restart network-manager

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    2.855677] rtusb init rt2870 --->
[    2.856872] ==>rlt_wlan_chip_onoff(): OnOff:1, Reset= 1, pAd->WlanFunCtrl:0x0, Reg-WlanFunCtrl=0x20a

########## wireless info END ############

```

---

### Post by BenginM on 2017-07-13
[FONT=courier new]I suppose you need to reload the module manually after a reboot for now with..

$ sudo modprobe mt7662u_sta

In order to make the driver load on startup add 
mt7662u_sta

into /etc/modules

with your favorite text editor , for example:

sudo gedit /etc/modules[/FONT]

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

mt7662u_sta


```

[FONT=courier new]save the file and exit.

you might only need to restart Network manager with $ sudo service network-manager restart .. when network manager fails to detect the dongle after unpluggin'/re-plugging.[/FONT]

---

