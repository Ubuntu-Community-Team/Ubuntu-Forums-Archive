---
title: "Ubuntu 16 on Lenovo ThinkPad13 - wifi not working"
date: 2017-05-22
forum: Networking &amp; Wireless
---

### Post by oefa on 2017-05-22
After reading a bunch of similar posts, trying out the suggestions and failing every time to get my wifi working, it's time to start my own thread =/

I already ran the wifi script you guys cooked up for these occasions:

```
########## wireless info START ##########

Report from: 22 May 2017 21:08 CEST +0200

Booted last: 22 May 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:29:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-V [8086:15d8] (rev 21)
    Subsystem: Lenovo Ethernet Connection (4) I219-V [17aa:5063]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:1010]

04:00.0 Non-Volatile memory controller [0108]: Toshiba America Info Systems Device [1179:0115] (rev 01)

##### lsusb #############################

Bus 002 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 003: ID 1bcf:2c94 Sunplus Innovation Technology Inc. 
Bus 001 Device 006: ID 9710:7832 MosChip Semiconductor MCS7832 10/100 Mbps Ethernet adapter
Bus 001 Device 002: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f1200000-f1220000 

enx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2d75:74:2af:a84a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:803297 (803.2 KB)  TX bytes:223089 (223.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:193708 (193.7 KB)  TX bytes:193708 (193.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

enx<IF from MAC [IF2]>  no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 enx<IF from MAC [IF2]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF2]>
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 enx<IF from MAC [IF2]>

##### resolv.conf #######################

nameserver 127.0.1.1
search local

##### network managers ##################

Installed:

    NetworkManager

Running:

root       748     1  0 21:02 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx<IF from MAC [IF2]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Moschip Semiconductor
GENERAL.PRODUCT:                        USB-MAC Controller   
GENERAL.DRIVER:                         MOSCHIP usb-ethernet driver
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               MOSCHIP 7830/7832/7730 usb-NET 
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.2/1-2.2:1.0/net/enx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       557ad117-8efc-39b0-9ba5-067c2db41b0d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     10 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   557ad117-8efc-39b0-9ba5-067c2db41b0d | Wired connection 2
IP4.ADDRESS[1]:                         192.168.2.105/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
IP4.DOMAIN[1]:                          local
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.2.1
DHCP4.OPTION[5]:                        ip_address = 192.168.2.105
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.2.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 27594000
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.2.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 15768000
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = local
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1527015871
DHCP4.OPTION[22]:                       host_name = durruti
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.2.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.2.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 31536000
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::2d75:74:2af:a84a/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (4) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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

Region: Europe/Berlin (based on set time zone)

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

enp0s31f6  no frequency information.

enx<IF from MAC [IF2]>  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

enx<IF from MAC [IF2]>  Interface doesn't support scanning.

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

[    5.641234] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    5.643406] Bluetooth: hci0: Found device firmware: intel/ibt-11-16.sfi
[    7.160898] Bluetooth: hci0: Waiting for firmware download to complete
[    8.417784] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[  110.678069] MOSCHIP usb-ethernet driver 1-2.2:1.0 eth0: register 'MOSCHIP usb-ethernet driver' at usb-0000:00:14.0-2.2, MOSCHIP 7830/7832/7730 usb-NET adapter, <MAC 'enx<IF from MAC [IF2]>' [IF2]>
[  110.692809] MOSCHIP usb-ethernet driver 1-2.2:1.0 enx<IF from MAC [IF2]>: renamed from eth0
[  110.723237] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF2]>: link is not ready (repeated 2 times)
[  112.237399] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############


```

I've run ```
sudo apt-get upgrade
``` and ```
sudo apt-get update
```. No luck so far.

Thanks in advance =)

---

### Post by chili555 on 2017-05-22
Please see: [https://askubuntu.com/questions/868075/how-to-get-intel-dual-band-wireless-ac-3168-work-on-ubuntu-16-04](https://askubuntu.com/questions/868075/how-to-get-intel-dual-band-wireless-ac-3168-work-on-ubuntu-16-04)

Notice that the device id is the same 8086:24fd.

---

### Post by oefa on 2017-05-23
Works like a charm. Thanks a lot, I thought I had found each and every last thread on the subject...

If you're ever in Munich, Germany, get in touch, I owe you one ;)

---

