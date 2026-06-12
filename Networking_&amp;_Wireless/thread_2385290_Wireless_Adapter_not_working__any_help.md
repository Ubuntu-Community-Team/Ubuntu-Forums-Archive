---
title: "Wireless Adapter not working  any help?"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by zekahs12 on 2018-02-18
```
########## wireless info START ##########

Report from: 18 Feb 2018 16:55 CST -0600

Booted last: 18 Feb 2018 00:00 CST -0600

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-32-generic #35-Ubuntu SMP Thu Jan 25 09:13:46 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Limited NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Dell NetLink BCM57780 Gigabit Ethernet PCIe [1028:0400]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

ndiswrapper           282624  0
dell_wmi               16384  0
dell_smbios            16384  1 dell_wmi
sparse_keymap          16384  1 dell_wmi
wmi_bmof               16384  0
video                  40960  2 dell_wmi,i915
wmi                    24576  2 dell_wmi,wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
    inet 192.168.1.91/24 brd 192.168.1.255 scope global dynamic enp1s0
       valid_lft 258661sec preferred_lft 258661sec
    inet6 fe80::b2ad:6b59:8d63:2337/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp1s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.1 dev enp1s0 proto static metric 100 
192.168.1.0/24 dev enp1s0 proto kernel scope link src 192.168.1.91 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       449     1  0 15:25 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        NetLink BCM57780 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       090b411a-09e8-3dde-9a42-bec66ab97b16
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   090b411a-09e8-3dde-9a42-bec66ab97b16 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.91/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1519253179
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.91
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 259200
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::b2ad:6b59:8d63:2337/64
IP6.GATEWAY:                            fe80::6caf:2fff:fe99:24ae
IP6.ROUTE[1]:                           dst = 2600:6c44:800:1d18::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = fe80::6caf:2fff:fe99:24ae/128, nh = ::, mt = 100
IP6.DNS[1]:                             2607:f428:ffff:ffff::1
IP6.DNS[2]:                             2607:f428:ffff:ffff::2

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

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

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

enp1s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp1s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ndiswrapper]
filename:       /lib/modules/4.13.0-32-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     CC9F8E33CF3A11EB1B122E4
depends:        
name:           ndiswrapper
vermagic:       4.13.0-32-generic SMP mod_unload 
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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   58.914347]  ? win2lin_IoInvalidDeviceRequest_2+0x20/0x20 [ndiswrapper]
[   58.914356]  lin2win2+0xd/0x20 [ndiswrapper]
[   58.914367]  ? KeReleaseSpinLock+0x4f/0x70 [ndiswrapper]
[   58.914382]  IofCallDriver+0x6b/0xc0 [ndiswrapper]
[   58.914393]  win2lin_IofCallDriver_2+0x18/0x20 [ndiswrapper]
[   58.914404]  ? ExAllocatePoolWithTag+0x37/0x50 [ndiswrapper] (repeated 3 times)
[   58.914436]  ? NdisAllocateMemoryWithTag+0x16/0x30 [ndiswrapper]
[   58.914448]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper] (repeated 2 times)
[   58.914473]  ? win2lin_KeReleaseSpinLock_2+0x18/0x20 [ndiswrapper]
[   58.914483]  ? lin2win6+0x22/0x28 [ndiswrapper]
[   58.914495]  ? mp_init+0x7a/0x250 [ndiswrapper]
[   58.914507]  ? NdisDispatchPnp+0xd9/0xc00 [ndiswrapper]
[   58.914520]  ? IoAllocateIrp+0x48/0x70 [ndiswrapper]
[   58.914531]  ? IoInitializeIrp+0x1e/0x50 [ndiswrapper]
[   58.914541]  ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper] (repeated 2 times)
[   58.914560]  ? win2lin_NdisDispatchDeviceControl_2+0x20/0x20 [ndiswrapper]
[   58.914569]  ? lin2win2+0xd/0x20 [ndiswrapper]
[   58.914582]  ? IofCallDriver+0x6b/0xc0 [ndiswrapper]
[   58.914593]  ? IoSendIrpTopDev+0xd6/0x130 [ndiswrapper]
[   58.914604]  ? wrap_pnp_start_device+0x1fe/0x2e0 [ndiswrapper]
[   58.914615]  ? wrap_pnp_start_usb_device+0xcc/0x100 [ndiswrapper]
[   58.914645]  ? loader_init+0xba/0x140 [ndiswrapper]
[   58.914653]  ? wrapper_init+0xa1/0x1000 [ndiswrapper]
[   58.914735] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   58.914737] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   58.914740] ndiswrapper (mp_halt:254): device ffff8af23405f8c0 is not initialized - not halting
[   58.914740] ndiswrapper: device eth%d removed
[   58.914837] ndiswrapper: probe of 1-8:1.0 failed with error -22
[   85.783263] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready (repeated 2 times)
[   86.813050] tg3 0000:01:00.0 enp1s0: Link is down
[   88.861070] tg3 0000:01:00.0 enp1s0: Link is up at 1000 Mbps, full duplex
[   88.861072] tg3 0000:01:00.0 enp1s0: Flow control is on for TX and on for RX
[   88.861093] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[ 3606.149872] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[ 3606.448678] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 3606.449269] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 3606.449271] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 3606.449274] ndiswrapper (mp_halt:254): device ffff8af21484a8c0 is not initialized - not halting
[ 3606.449275] ndiswrapper: device eth%d removed
[ 3606.449352] ndiswrapper: probe of 1-8:1.0 failed with error -22

########## wireless info END ############
```

---

### Post by wildmanne39 on 2018-02-18
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2018-02-19
```
[   58.914735] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   58.914737] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   58.914740] ndiswrapper (mp_halt:254): device ffff8af23405f8c0 is not initialized - not halting
[   58.914740] ndiswrapper: device eth%d removed
[   58.914837] ndiswrapper: probe of 1-8:1.0 failed with error -22
[   85.783263] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready (repeated 2 times)
[   86.813050] tg3 0000:01:00.0 enp1s0: Link is down
[   88.861070] tg3 0000:01:00.0 enp1s0: Link is up at 1000 Mbps, full duplex
[   88.861072] tg3 0000:01:00.0 enp1s0: Flow control is on for TX and on for RX
[   88.861093] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[ 3606.149872] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[ 3606.448678] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 3606.449269] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 3606.449271] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 3606.449274] ndiswrapper (mp_halt:254): device ffff8af21484a8c0 is not initialized - not halting
[ 3606.449275] ndiswrapper: device eth%d removed
[ 3606.449352] ndiswrapper: probe of 1-8:1.0 failed with error -22
```That's what we driver dawgs call a train wreck. The longer version is that the ndiswrapper package, your kernel version, in your case, 4.13.0-xx and the Windows .inf and .sys files you installed don't work and play well together; in fact, they don't work at all.

Now it is a bit tempting to ask where you got the Windows .inf and .sys files and point out that the must be XP files; not 7 or 8 or 10 and ask you to try again. It is tempting to ask you to try installing Ubuntu 16.04 with an earlier kernel and the associated component parts and try again. It is tempting to try to recompile ndiswrapper from source code and try again but I already know that each and every step will probably fail. I haven't seen ndiswrapper work correctly on any Ubuntu version that it not end-of-life and therefore still getting crucial security updates, for a couple of years. It is dead and gone.

I suggest that you search this forum for recommendations about working by default USB wireless devices and get one.

---

### Post by zekahs12 on 2018-02-19
thank you for your advise and input im still trying to get it to work its been days no results

---

