---
title: "No Wi-Fi adapter Found(rtl8811au)"
date: 2017-10-25
forum: Networking &amp; Wireless
---

### Post by dannal on 2017-10-25
Hi there,
I am freshman of Ubuntu. I am using a USB wireless adapter and it works in windows 10 but can not make it to work in Ubuntu. I have tried to install drivers for it following post instruction in this forum, and still can not make it work.

The following is the wireless info script([http://paste.ubuntu.com/25820399/](http://paste.ubuntu.com/25820399/)) and looking for help.

Thanks!


```
########## wireless info START ##########

Report from: 25 Oct 2017 19:50 CDT -0500

Booted last: 25 Oct 2017 00:00 CDT -0500

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-16-generic #19-Ubuntu SMP Wed Oct 11 18:35:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 06)
    Subsystem: Lenovo 82579LM Gigabit Network Connection (Lewisville) [17aa:1027]
    Kernel driver in use: e1000e

09:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
    Subsystem: Lenovo 82574L Gigabit Network Connection [17aa:1027]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 004: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wmi_bmof               16384  0
mxm_wmi                16384  1 nouveau
wmi                    24576  3 wmi_bmof,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.1.76/24 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 86332sec preferred_lft 86332sec
    inet6 2602:30a:2c79:44c0:b406:a7df:a8d4:4090/64 scope global temporary dynamic 
       valid_lft 604735sec preferred_lft 85739sec
    inet6 2602:30a:2c79:44c0:9667:bdd3:31d3:77a2/64 scope global mngtmpaddr noprefixroute dynamic 
       valid_lft 2591935sec preferred_lft 604735sec
    inet6 fe80::7c05:9ab:f5fc:7fec/64 scope link 
       valid_lft forever preferred_lft forever
3: enp9s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp9s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

eno1      no wireless extensions.

enp9s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.254 dev eno1 proto static metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.76 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       919     1  0 19:49 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection (Lewisville)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
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
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       53d04518-c0c3-3ec4-b361-92c9a53c0bbb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   53d04518-c0c3-3ec4-b361-92c9a53c0bbb | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.76/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.254
DHCP4.OPTION[11]:                       expiry = 1509065390
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.76
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = attlocal.net
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         2602:30a:2c79:44c0:b406:a7df:a8d4:4090/64
IP6.ADDRESS[2]:                         2602:30a:2c79:44c0:9667:bdd3:31d3:77a2/64
IP6.ADDRESS[3]:                         fe80::7c05:9ab:f5fc:7fec/64
IP6.GATEWAY:                            fe80::e222:3ff:fe52:d3c1
IP6.ROUTE[1]:                           dst = 2602:30a:2c79:44c0::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2602:30a:2c79:44c0::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2602:30a:2c79:44c0::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:e0:22:3:52:d3:c1
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:7f:5:c8:a1:12:78:b1:16:2e:bd:52:a6:36:d2:c9:8c

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82574L Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               2.1-0
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:09:00.0/net/enp9s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

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

[device]
wifi.scan-rand-mac-address=no
[device]
wifi.scan-rand-mac-address=0

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

eno1      no frequency information.

enp9s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

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
blacklist rtl8812au
blacklist rtl8812au

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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    6.052039] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[    6.271212] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready (repeated 2 times)
[    9.761974] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    9.762012] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

########## wireless info END ############
```

---

### Post by dannal on 2017-10-27
still waiting for help!!

Thanks in advance!

Weiyan

---

### Post by chili555 on 2017-10-27
Please try:

```
sudo apt install rtl8812au-dkms
```

And then reboot.

---

### Post by dannal on 2017-10-29
Hi chili555,
Thank you very much for your reply.
I tried the code, but still not working~

here is the code:
> 
weiyan@Weiyan-ThinkStation-D30 ~
$ sudo apt install rtl8812au-dkms
[sudo] password for weiyan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu7).
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

---

### Post by chili555 on 2017-10-30
Let's try a different approach.

```
sudo apt purge rtl8812au-dkms
sudo apt install git
git clone https://github.com/gnab/rtl8812au.git
sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2


```Reboot and tell us if the wireless is working.

---

### Post by dannal on 2017-10-30
still can not find Wifi adapter!


```
weiyan@Weiyan-ThinkStation-D30 ~
$ sudo apt purge rtl8812au-dkms
[sudo] password for weiyan: 
Sorry, try again.
[sudo] password for weiyan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  rtl8812au-dkms*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
After this operation, 8905 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 146250 files and directories currently installed.)
Removing rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu7) ...

-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.8.12175.20140902+dfsg
Kernel:  4.13.0-16-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.3.8.12175.20140902+dfsg
completely from the DKMS tree.
------------------------------
Done.

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo apt install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version (1:2.14.1-1ubuntu4).
The following package was automatically installed and is no longer required:
  dkms
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

weiyan@Weiyan-ThinkStation-D30 ~
$ git clone https://github.com/gnab/rtl8812au.git
Cloning into 'rtl8812au'...
remote: Counting objects: 607, done.
remote: Total 607 (delta 0), reused 0 (delta 0), pack-reused 607
Receiving objects: 100% (607/607), 1.67 MiB | 2.38 MiB/s, done.
Resolving deltas: 100% (250/250), done.

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo dkms add -m rtl8812au -v 4.2.2

Creating symlink /var/lib/dkms/rtl8812au/4.2.2/source ->
                 /usr/src/rtl8812au-4.2.2

DKMS: add completed.

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo dkms build -m rtl8812au -v 4.2.2

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' all KVER=4.13.0-16-generic................
cleaning build area...

DKMS: build completed.

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo dkms install -m rtl8812au -v 4.2.2

8812au:
Running module version sanity check.
Error! Module version v4.2.2_7502.20130517 for 8812au.ko
is not newer than what is already found in kernel 4.13.0-16-generic (v4.3.8_12175.20140902).
You may override by specifying --force.

depmod...

DKMS: install completed.

weiyan@Weiyan-ThinkStation-D30 ~
$ 
```

---

### Post by chili555 on 2017-10-31
> Error! Module version v4.2.2_7502.20130517 for 8812au.ko
is not newer than what is already found in kernel 4.13.0-16-generic (v4.3.8_12175.20140902).
You may override by specifying --force.
I suggest that you do just that:```
sudo dkms install --force -m rtl8812au -v 4.2.2
```Reboot.

---

### Post by dannal on 2017-10-31
still no.....

```
weiyan@Weiyan-ThinkStation-D30 ~
$ sudo dkms install --force -m rtl8812au -v 4.2.2
[sudo] password for weiyan: 
Module rtl8812au/4.2.2 already installed on kernel 4.13.0-16-generic/x86_64
```

---

### Post by praseodym on 2017-10-31
Lets see
```

sudo modprobe -v 8812au
dmesg | grep 8812
modinfo 8812au
```

---

### Post by dannal on 2017-11-01
Not working.

here is the codes:

weiyan@Weiyan-ThinkStation-D30 ~
```
$ sudo modprobe -v 8812au
[sudo] password for weiyan: 
insmod /lib/modules/4.13.0-16-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko 

weiyan@Weiyan-ThinkStation-D30 ~
$ dmesg | grep 8812
[   83.086075] RTL871X: rtl8812au v4.3.8_12175.20140902
[   83.086104] usbcore: registered new interface driver rtl8812au

weiyan@Weiyan-ThinkStation-D30 ~
$ modinfo 8812au
filename:       /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     497B724524736A2C9A9E6C5
alias:          usb:v056Ep4007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0242d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0953d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0820d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p025Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9097d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
name:           8812au
vermagic:       4.13.0-16-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_nhm_en:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
```

---

### Post by chili555 on 2017-11-01
> $ modinfo 8812au
filename:       /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902I thought that you purged version 4.3.8_xx:> Removing rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu7) ...

-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.8.12175.20140902+dfsg
Kernel:  4.13.0-16-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.In fact, the version we thought you removed doesn't cover your exact device, as you can see:> 0bda:a811 Realtek Semiconductor Corp. The driver version I suggested, 4.2.2, *does* cover it.```
chili@T440p:~$ modinfo 8812au
filename:       /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko
version:        v[COLOR="#FF0000"]4.2.2_7502.20130517[/COLOR]
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     E96B8D9016B150E0F37C9AE
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]A811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0953d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v056Ep4007d*dc*dsc*dp*ic*isc*ip*in*
<snip>
```

Let's dig a bit deeper:```
sudo dkms status
sudo updatedb
locate 8812au.ko
```

---

### Post by dannal on 2017-11-02
Thanks CHili555!

here is the code:
```
weiyan@Weiyan-ThinkStation-D30 ~
$ sudo dkms status
[sudo] password for weiyan: 
bbswitch, 0.8, 4.13.0-16-generic, x86_64: installed
nvidia-384, 384.90, 4.13.0-16-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-16-generic, x86_64: installed (WARNING! Diff between built and installed module!)
rtl8812au, 4.3.14, 4.13.0-16-generic, x86_64: built

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo updatedb

weiyan@Weiyan-ThinkStation-D30 ~
$ locate 8812au.ko
/lib/modules/4.13.0-16-generic/kernel/drivers/net/wireless/rtl8812au.ko
/lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko
/var/lib/dkms/rtl8812au/4.2.2/4.13.0-16-generic/x86_64/module/8812au.ko
/var/lib/dkms/rtl8812au/4.3.14/4.13.0-16-generic/x86_64/module/rtl8812au.ko
```

---

### Post by chili555 on 2017-11-02
Please confirm that rtl8812au is NOT loaded:```
lsmod | grep 8812
```If it is, unload it:```
sudo modprobe -r rtl8812au
```Now load the module that we hope and assume will work:```
sudo insmod  /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko 
```Any improvement? If so, we'll make it permanent.

---

### Post by dannal on 2017-11-02
Hi Chili555,

seems some problems with the code:

```
weiyan@Weiyan-ThinkStation-D30 ~
$ lsmod | grep 8812

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo modprobe -r rtl8812au

weiyan@Weiyan-ThinkStation-D30 ~
$ sudo insmod  /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko
insmod: ERROR: could not insert module /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko: Unknown symbol in module

weiyan@Weiyan-ThinkStation-D30 ~
$  sudo insmod  /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko
insmod: ERROR: could not insert module /lib/modules/4.13.0-16-generic/updates/dkms/8812au.ko: Unknown symbol in module

weiyan@Weiyan-ThinkStation-D30 ~
$  sudo insmod /lib/modules/4.13.0.16-generic/updates/dkms/8812au.ko
insmod: ERROR: could not load module /lib/modules/4.13.0.16-generic/updates/dkms/8812au.ko: No such file or directory
```

---

### Post by dannal on 2017-11-07
still waiting for help~~

Thanks!

---

### Post by praseodym on 2017-11-07
Please check
```

dmesg | grep 88
```

---

### Post by dannal on 2017-11-07
> **praseodym said:**
> Please check
```

dmesg | grep 88
```

Hi Praseodym,

Here is the code:
```

$ dmesg | grep 88
[    0.000000] e820: last_pfn = 0x880000 max_arch_pfn = 0x400000000
[    0.000000] RAMDISK: [mem 0x3112b000-0x3488cfff]
[    0.000000]   Normal zone: 122880 pages used for memmap
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.046128] Mount-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.046228] Mountpoint-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.200683] futex hash table entries: 8192 (order: 7, 524288 bytes)
[    0.315710] pci 0000:00:05.0: [8086:0e28] type 00 class 0x088000
[    0.315818] pci 0000:00:05.2: [8086:0e2a] type 00 class 0x088000
[    0.316882] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.317880] pci 0000:00:1f.2: reg 0x14: [io  0x9080-0x9083]
[    0.317887] pci 0000:00:1f.2: reg 0x18: [io  0x9070-0x9077]
[    0.328817] pci 0000:05:00.1: [10de:0e0b] type 00 class 0x040300
[    0.328828] pci 0000:05:00.1: reg 0x10: [mem 0xdf080000-0xdf083fff]
[    0.364588] pci_bus 0000:1f: root bus resource [bus 1f]
[    0.364594] pci 0000:1f:08.0: [8086:0e80] type 00 class 0x088000
[    0.364635] pci 0000:1f:09.0: [8086:0e90] type 00 class 0x088000
[    0.364674] pci 0000:1f:0a.0: [8086:0ec0] type 00 class 0x088000
[    0.364708] pci 0000:1f:0a.1: [8086:0ec1] type 00 class 0x088000
[    0.364743] pci 0000:1f:0a.2: [8086:0ec2] type 00 class 0x088000
[    0.364784] pci 0000:1f:0a.3: [8086:0ec3] type 00 class 0x088000
[    0.364819] pci 0000:1f:0b.0: [8086:0e1e] type 00 class 0x088000
[    0.364850] pci 0000:1f:0b.3: [8086:0e1f] type 00 class 0x088000
[    0.364882] pci 0000:1f:0c.0: [8086:0ee0] type 00 class 0x088000
[    0.364912] pci 0000:1f:0c.1: [8086:0ee2] type 00 class 0x088000
[    0.364943] pci 0000:1f:0c.2: [8086:0ee4] type 00 class 0x088000
[    0.364975] pci 0000:1f:0c.3: [8086:0ee6] type 00 class 0x088000
[    0.365007] pci 0000:1f:0c.4: [8086:0ee8] type 00 class 0x088000
[    0.365040] pci 0000:1f:0d.0: [8086:0ee1] type 00 class 0x088000
[    0.365072] pci 0000:1f:0d.1: [8086:0ee3] type 00 class 0x088000
[    0.365103] pci 0000:1f:0d.2: [8086:0ee5] type 00 class 0x088000
[    0.365134] pci 0000:1f:0d.3: [8086:0ee7] type 00 class 0x088000
[    0.365165] pci 0000:1f:0d.4: [8086:0ee9] type 00 class 0x088000
[    0.365197] pci 0000:1f:0e.0: [8086:0ea0] type 00 class 0x088000
[    0.365271] pci 0000:1f:0f.0: [8086:0ea8] type 00 class 0x088000
[    0.365321] pci 0000:1f:0f.1: [8086:0e71] type 00 class 0x088000
[    0.365366] pci 0000:1f:0f.2: [8086:0eaa] type 00 class 0x088000
[    0.365414] pci 0000:1f:0f.3: [8086:0eab] type 00 class 0x088000
[    0.365459] pci 0000:1f:0f.4: [8086:0eac] type 00 class 0x088000
[    0.365503] pci 0000:1f:0f.5: [8086:0ead] type 00 class 0x088000
[    0.365548] pci 0000:1f:10.0: [8086:0eb0] type 00 class 0x088000
[    0.365591] pci 0000:1f:10.1: [8086:0eb1] type 00 class 0x088000
[    0.365641] pci 0000:1f:10.2: [8086:0eb2] type 00 class 0x088000
[    0.365686] pci 0000:1f:10.3: [8086:0eb3] type 00 class 0x088000
[    0.365732] pci 0000:1f:10.4: [8086:0eb4] type 00 class 0x088000
[    0.365776] pci 0000:1f:10.5: [8086:0eb5] type 00 class 0x088000
[    0.365820] pci 0000:1f:10.6: [8086:0eb6] type 00 class 0x088000
[    0.365864] pci 0000:1f:10.7: [8086:0eb7] type 00 class 0x088000
[    0.365906] pci 0000:1f:13.0: [8086:0e1d] type 00 class 0x088000
[    0.365976] pci 0000:1f:13.4: [8086:0e81] type 00 class 0x088000
[    0.366045] pci 0000:1f:16.0: [8086:0ec8] type 00 class 0x088000
[    0.366077] pci 0000:1f:16.1: [8086:0ec9] type 00 class 0x088000
[    0.366108] pci 0000:1f:16.2: [8086:0eca] type 00 class 0x088000
[    0.366686] pci 0000:20:05.0: [8086:0e28] type 00 class 0x088000
[    0.366789] pci 0000:20:05.2: [8086:0e2a] type 00 class 0x088000
[    0.366888] pci 0000:20:05.4: [8086:0e2c] type 00 class 0x080020
[    0.367168] pci 0000:3f:08.0: [8086:0e80] type 00 class 0x088000
[    0.367216] pci 0000:3f:09.0: [8086:0e90] type 00 class 0x088000
[    0.367262] pci 0000:3f:0a.0: [8086:0ec0] type 00 class 0x088000
[    0.367305] pci 0000:3f:0a.1: [8086:0ec1] type 00 class 0x088000
[    0.367350] pci 0000:3f:0a.2: [8086:0ec2] type 00 class 0x088000
[    0.367390] pci 0000:3f:0a.3: [8086:0ec3] type 00 class 0x088000
[    0.367431] pci 0000:3f:0b.0: [8086:0e1e] type 00 class 0x088000
[    0.367471] pci 0000:3f:0b.3: [8086:0e1f] type 00 class 0x088000
[    0.367511] pci 0000:3f:0c.0: [8086:0ee0] type 00 class 0x088000
[    0.367550] pci 0000:3f:0c.1: [8086:0ee2] type 00 class 0x088000
[    0.367589] pci 0000:3f:0c.2: [8086:0ee4] type 00 class 0x088000
[    0.367627] pci 0000:3f:0c.3: [8086:0ee6] type 00 class 0x088000
[    0.367669] pci 0000:3f:0c.4: [8086:0ee8] type 00 class 0x088000
[    0.367709] pci 0000:3f:0d.0: [8086:0ee1] type 00 class 0x088000
[    0.367747] pci 0000:3f:0d.1: [8086:0ee3] type 00 class 0x088000
[    0.367787] pci 0000:3f:0d.2: [8086:0ee5] type 00 class 0x088000
[    0.367826] pci 0000:3f:0d.3: [8086:0ee7] type 00 class 0x088000
[    0.367865] pci 0000:3f:0d.4: [8086:0ee9] type 00 class 0x088000
[    0.367904] pci 0000:3f:0e.0: [8086:0ea0] type 00 class 0x088000
[    0.368004] pci 0000:3f:0f.0: [8086:0ea8] type 00 class 0x088000
[    0.368061] pci 0000:3f:0f.1: [8086:0e71] type 00 class 0x088000
[    0.368118] pci 0000:3f:0f.2: [8086:0eaa] type 00 class 0x088000
[    0.368175] pci 0000:3f:0f.3: [8086:0eab] type 00 class 0x088000
[    0.368231] pci 0000:3f:0f.4: [8086:0eac] type 00 class 0x088000
[    0.368288] pci 0000:3f:0f.5: [8086:0ead] type 00 class 0x088000
[    0.368348] pci 0000:3f:10.0: [8086:0eb0] type 00 class 0x088000
[    0.368403] pci 0000:3f:10.1: [8086:0eb1] type 00 class 0x088000
[    0.368459] pci 0000:3f:10.2: [8086:0eb2] type 00 class 0x088000
[    0.368514] pci 0000:3f:10.3: [8086:0eb3] type 00 class 0x088000
[    0.368569] pci 0000:3f:10.4: [8086:0eb4] type 00 class 0x088000
[    0.368630] pci 0000:3f:10.5: [8086:0eb5] type 00 class 0x088000
[    0.368691] pci 0000:3f:10.6: [8086:0eb6] type 00 class 0x088000
[    0.368748] pci 0000:3f:10.7: [8086:0eb7] type 00 class 0x088000
[    0.368804] pci 0000:3f:13.0: [8086:0e1d] type 00 class 0x088000
[    0.368844] pci 0000:3f:13.1: [8086:0e34] type 00 class 0x110100
[    0.368891] pci 0000:3f:13.4: [8086:0e81] type 00 class 0x088000
[    0.368976] pci 0000:3f:16.0: [8086:0ec8] type 00 class 0x088000
[    0.369014] pci 0000:3f:16.1: [8086:0ec9] type 00 class 0x088000
[    0.369054] pci 0000:3f:16.2: [8086:0eca] type 00 class 0x088000
[    0.388080] system 00:01: [io  0x0a00-0x0a3f] has been reserved
[    0.388082] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.388237] pnp 00:02: [dma 0 disabled]
[    0.388268] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.388357] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.388429] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.388431] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.388460] pnp 00:05: Plug and Play ACPI device, IDs PNP0c31 (active)
[    0.388602] system 00:06: [io  0x0400-0x0453] has been reserved
[    0.388603] system 00:06: [io  0x0458-0x047f] has been reserved
[    0.388604] system 00:06: [io  0x1180-0x119f] has been reserved
[    0.388605] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.388607] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.388608] system 00:06: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.388609] system 00:06: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.388610] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.388612] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.388675] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.388677] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.388786] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.388983] pnp: PnP ACPI: found 9 devices
[    0.396172] UDP hash table entries: 16384 (order: 7, 524288 bytes)
[    0.396264] UDP-Lite hash table entries: 16384 (order: 7, 524288 bytes)
[    1.231088] libphy: Fixed MDIO Bus: probed
[    2.488977] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    2.588892] scsi host3: isci
[    2.588978] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    2.861088] e1000e 0000:09:00.0 eth1: (PCI Express:2.5GT/s:Width x1) fc:4d:d4:3e:32:ed
[    4.508882] ata9.00: configured for UDMA/100
[    5.108865] sd 2:0:1:0: [sdb] Attached SCSI disk
[    5.541036] Adding 2097148k swap on /swapfile.  Priority:-1 extents:6 across:2260988k SSFS
[    5.943883] EDAC sbridge: Seeking for: PCI ID 8086:0ea8
[  154.674500] 8812au: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[  154.674525] 8812au: Unknown symbol cfg80211_scan_done (err 0)
[  154.674540] 8812au: Unknown symbol cfg80211_remain_on_channel_expired (err 0)
[  154.674551] 8812au: Unknown symbol cfg80211_new_sta (err 0)
[  154.674558] 8812au: Unknown symbol cfg80211_disconnected (err 0)
[  154.674576] 8812au: Unknown symbol wiphy_new_nm (err 0)
[  154.674584] 8812au: Unknown symbol cfg80211_ready_on_channel (err 0)
[  154.674594] 8812au: Unknown symbol wiphy_register (err 0)
[  154.674602] 8812au: Unknown symbol __cfg80211_alloc_reply_skb (err 0)
[  154.674609] 8812au: Unknown symbol __cfg80211_alloc_event_skb (err 0)
[  154.674615] 8812au: Unknown symbol cfg80211_put_bss (err 0)
[  154.674621] 8812au: Unknown symbol cfg80211_roamed (err 0)
[  154.674631] 8812au: Unknown symbol __cfg80211_send_event_skb (err 0)
[  154.674637] 8812au: Unknown symbol cfg80211_ibss_joined (err 0)
[  154.674648] 8812au: Unknown symbol cfg80211_michael_mic_failure (err 0)
[  154.674654] 8812au: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  154.674664] 8812au: Unknown symbol ieee80211_get_channel (err 0)
[  154.674670] 8812au: Unknown symbol cfg80211_del_sta_sinfo (err 0)
[  154.674678] 8812au: Unknown symbol wiphy_unregister (err 0)
[  154.674688] 8812au: Unknown symbol cfg80211_get_bss (err 0)
[  154.674696] 8812au: Unknown symbol cfg80211_vendor_cmd_reply (err 0)
[  154.674707] 8812au: Unknown symbol cfg80211_mgmt_tx_status (err 0)
[  154.674722] 8812au: Unknown symbol cfg80211_rx_mgmt (err 0)
[  154.674738] 8812au: Unknown symbol ieee80211_frequency_to_channel (err 0)
[  154.674745] 8812au: Unknown symbol cfg80211_connect_done (err 0)
[  154.674750] 8812au: Unknown symbol cfg80211_unlink_bss (err 0)
[  154.674756] 8812au: Unknown symbol wiphy_free (err 0)
[  213.603815] 8812au: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[  213.603868] 8812au: Unknown symbol cfg80211_scan_done (err 0)
[  213.603903] 8812au: Unknown symbol cfg80211_remain_on_channel_expired (err 0)
[  213.603931] 8812au: Unknown symbol cfg80211_new_sta (err 0)
[  213.603950] 8812au: Unknown symbol cfg80211_disconnected (err 0)
[  213.603985] 8812au: Unknown symbol wiphy_new_nm (err 0)
[  213.604005] 8812au: Unknown symbol cfg80211_ready_on_channel (err 0)
[  213.604031] 8812au: Unknown symbol wiphy_register (err 0)
[  213.604053] 8812au: Unknown symbol __cfg80211_alloc_reply_skb (err 0)
[  213.604070] 8812au: Unknown symbol __cfg80211_alloc_event_skb (err 0)
[  213.604088] 8812au: Unknown symbol cfg80211_put_bss (err 0)
[  213.604103] 8812au: Unknown symbol cfg80211_roamed (err 0)
[  213.604127] 8812au: Unknown symbol __cfg80211_send_event_skb (err 0)
[  213.604143] 8812au: Unknown symbol cfg80211_ibss_joined (err 0)
[  213.604171] 8812au: Unknown symbol cfg80211_michael_mic_failure (err 0)
[  213.604187] 8812au: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  213.604210] 8812au: Unknown symbol ieee80211_get_channel (err 0)
[  213.604225] 8812au: Unknown symbol cfg80211_del_sta_sinfo (err 0)
[  213.604246] 8812au: Unknown symbol wiphy_unregister (err 0)
[  213.604272] 8812au: Unknown symbol cfg80211_get_bss (err 0)
[  213.604292] 8812au: Unknown symbol cfg80211_vendor_cmd_reply (err 0)
[  213.604319] 8812au: Unknown symbol cfg80211_mgmt_tx_status (err 0)
[  213.604356] 8812au: Unknown symbol cfg80211_rx_mgmt (err 0)
[  213.604395] 8812au: Unknown symbol ieee80211_frequency_to_channel (err 0)
[  213.604415] 8812au: Unknown symbol cfg80211_connect_done (err 0)
[  213.604429] 8812au: Unknown symbol cfg80211_unlink_bss (err 0)
[  213.604446] 8812au: Unknown symbol wiphy_free (err 0)
[  252.720712] 8812au: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[  252.720737] 8812au: Unknown symbol cfg80211_scan_done (err 0)
[  252.720753] 8812au: Unknown symbol cfg80211_remain_on_channel_expired (err 0)
[  252.720764] 8812au: Unknown symbol cfg80211_new_sta (err 0)
[  252.720771] 8812au: Unknown symbol cfg80211_disconnected (err 0)
[  252.720788] 8812au: Unknown symbol wiphy_new_nm (err 0)
[  252.720796] 8812au: Unknown symbol cfg80211_ready_on_channel (err 0)
[  252.720806] 8812au: Unknown symbol wiphy_register (err 0)
[  252.720814] 8812au: Unknown symbol __cfg80211_alloc_reply_skb (err 0)
[  252.720821] 8812au: Unknown symbol __cfg80211_alloc_event_skb (err 0)
[  252.720828] 8812au: Unknown symbol cfg80211_put_bss (err 0)
[  252.720833] 8812au: Unknown symbol cfg80211_roamed (err 0)
[  252.720843] 8812au: Unknown symbol __cfg80211_send_event_skb (err 0)
[  252.720849] 8812au: Unknown symbol cfg80211_ibss_joined (err 0)
[  252.720861] 8812au: Unknown symbol cfg80211_michael_mic_failure (err 0)
[  252.720867] 8812au: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  252.720877] 8812au: Unknown symbol ieee80211_get_channel (err 0)
[  252.720882] 8812au: Unknown symbol cfg80211_del_sta_sinfo (err 0)
[  252.720890] 8812au: Unknown symbol wiphy_unregister (err 0)
[  252.720901] 8812au: Unknown symbol cfg80211_get_bss (err 0)
[  252.720909] 8812au: Unknown symbol cfg80211_vendor_cmd_reply (err 0)
[  252.720920] 8812au: Unknown symbol cfg80211_mgmt_tx_status (err 0)
[  252.720935] 8812au: Unknown symbol cfg80211_rx_mgmt (err 0)
[  252.720950] 8812au: Unknown symbol ieee80211_frequency_to_channel (err 0)
[  252.720958] 8812au: Unknown symbol cfg80211_connect_done (err 0)
[  252.720963] 8812au: Unknown symbol cfg80211_unlink_bss (err 0)
[  252.720969] 8812au: Unknown symbol wiphy_free (err 0)
[  791.217234] 8812au: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[  791.217271] 8812au: Unknown symbol cfg80211_scan_done (err 0)
[  791.217292] 8812au: Unknown symbol cfg80211_remain_on_channel_expired (err 0)
[  791.217309] 8812au: Unknown symbol cfg80211_new_sta (err 0)
[  791.217319] 8812au: Unknown symbol cfg80211_disconnected (err 0)
[  791.217342] 8812au: Unknown symbol wiphy_new_nm (err 0)
[  791.217354] 8812au: Unknown symbol cfg80211_ready_on_channel (err 0)
[  791.217368] 8812au: Unknown symbol wiphy_register (err 0)
[  791.217381] 8812au: Unknown symbol __cfg80211_alloc_reply_skb (err 0)
[  791.217391] 8812au: Unknown symbol __cfg80211_alloc_event_skb (err 0)
[  791.217402] 8812au: Unknown symbol cfg80211_put_bss (err 0)
[  791.217411] 8812au: Unknown symbol cfg80211_roamed (err 0)
[  791.217425] 8812au: Unknown symbol __cfg80211_send_event_skb (err 0)
[  791.217434] 8812au: Unknown symbol cfg80211_ibss_joined (err 0)
[  791.217452] 8812au: Unknown symbol cfg80211_michael_mic_failure (err 0)
[  791.217461] 8812au: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  791.217475] 8812au: Unknown symbol ieee80211_get_channel (err 0)
[  791.217484] 8812au: Unknown symbol cfg80211_del_sta_sinfo (err 0)
[  791.217496] 8812au: Unknown symbol wiphy_unregister (err 0)
[  791.217511] 8812au: Unknown symbol cfg80211_get_bss (err 0)
[  791.217524] 8812au: Unknown symbol cfg80211_vendor_cmd_reply (err 0)
[  791.217539] 8812au: Unknown symbol cfg80211_mgmt_tx_status (err 0)
[  791.217561] 8812au: Unknown symbol cfg80211_rx_mgmt (err 0)
[  791.217584] 8812au: Unknown symbol ieee80211_frequency_to_channel (err 0)
[  791.217595] 8812au: Unknown symbol cfg80211_connect_done (err 0)
[  791.217604] 8812au: Unknown symbol cfg80211_unlink_bss (err 0)
[  791.217613] 8812au: Unknown symbol wiphy_free (err 0)
[  952.793302] 8812au: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[  952.793357] 8812au: Unknown symbol cfg80211_scan_done (err 0)
[  952.793392] 8812au: Unknown symbol cfg80211_remain_on_channel_expired (err 0)
[  952.793419] 8812au: Unknown symbol cfg80211_new_sta (err 0)
[  952.793438] 8812au: Unknown symbol cfg80211_disconnected (err 0)
[  952.793474] 8812au: Unknown symbol wiphy_new_nm (err 0)
[  952.793495] 8812au: Unknown symbol cfg80211_ready_on_channel (err 0)
[  952.793520] 8812au: Unknown symbol wiphy_register (err 0)
[  952.793540] 8812au: Unknown symbol __cfg80211_alloc_reply_skb (err 0)
[  952.793556] 8812au: Unknown symbol __cfg80211_alloc_event_skb (err 0)
[  952.793575] 8812au: Unknown symbol cfg80211_put_bss (err 0)
[  952.793591] 8812au: Unknown symbol cfg80211_roamed (err 0)
[  952.793615] 8812au: Unknown symbol __cfg80211_send_event_skb (err 0)
[  952.793631] 8812au: Unknown symbol cfg80211_ibss_joined (err 0)
[  952.793660] 8812au: Unknown symbol cfg80211_michael_mic_failure (err 0)
[  952.793677] 8812au: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  952.793700] 8812au: Unknown symbol ieee80211_get_channel (err 0)
[  952.793715] 8812au: Unknown symbol cfg80211_del_sta_sinfo (err 0)
[  952.793737] 8812au: Unknown symbol wiphy_unregister (err 0)
[  952.793762] 8812au: Unknown symbol cfg80211_get_bss (err 0)
[  952.793783] 8812au: Unknown symbol cfg80211_vendor_cmd_reply (err 0)
[  952.793810] 8812au: Unknown symbol cfg80211_mgmt_tx_status (err 0)
[  952.793846] 8812au: Unknown symbol cfg80211_rx_mgmt (err 0)
[  952.793884] 8812au: Unknown symbol ieee80211_frequency_to_channel (err 0)
[  952.793904] 8812au: Unknown symbol cfg80211_connect_done (err 0)
[  952.793919] 8812au: Unknown symbol cfg80211_unlink_bss (err 0)
[  952.793935] 8812au: Unknown symbol wiphy_free (err 0)
[182562.558850] rfkill: input handler enabled
[182563.882302] IRQ 23: no longer affine to CPU18
[182563.883328] smpboot: CPU 18 is now offline
[182563.947188] smpboot: CPU 22 is now offline
[182564.248988] intel_rapl: Found RAPL domain package
[182564.303288]  cache: parent cpu18 should not be sleeping
[182575.788078] e1000e: enp9s0 NIC Link is Down

```

---

### Post by dannal on 2017-11-13
@[B]praseodym and @chili555
Any new ideas?

Thank you very much guys!!

Weiyan[/B]

---

### Post by praseodym on 2017-11-14
Where did you get the driver from?

---

### Post by dannal on 2017-11-14
I bought form Amazon
Here is the link:

[https://www.amazon.com/gp/product/B074WNFBPQ/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B074WNFBPQ/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1)

---

### Post by jeremy31 on 2017-11-14
I would reinstall Ubuntu and then follow instructions on [https://ubuntuforums.org/showthread.php?t=2375603&p=13705226#post13705226](https://ubuntuforums.org/showthread.php?t=2375603&p=13705226#post13705226)

---

### Post by dannal on 2017-11-15
After i re-installed the system and followed this code and it finally worked!

Thanks all your guys help!!!!

---

### Post by dannal on 2017-11-15
Thanks jeremy31. After reinstall Ubuntu and finally made it work.

---

