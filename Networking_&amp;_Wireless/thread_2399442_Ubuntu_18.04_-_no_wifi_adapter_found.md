---
title: "Ubuntu 18.04 - no wifi adapter found"
date: 2018-08-25
forum: Networking &amp; Wireless
---

### Post by harryhorus on 2018-08-25
Hi, i have just installed Ubuntu but it is not finding the wifi adapter, i have turned off secure boot in the bios which was recommended in another thread but it is still not working, the laptop is a HP 15bs506na, thanks

this is the wireless-info text:
```
########## wireless info START ##########

Report from: 25 Aug 2018 13:46 BST +0100

Booted last: 25 Aug 2018 00:00 BST +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:832c]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05c8:0233 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
wmi_bmof               16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    24576  2 wmi_bmof,hp_wmi

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
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.1.74/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 85624sec preferred_lft 85624sec
    inet6 fe80::381e:baac:afae:4bf/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.254 dev eno1 proto dhcp metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.74 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       584     1  0 13:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       ba1db20e-62b1-3fb1-aa2d-1dc28ad0f238
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.74/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.254, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        domain_name = home
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        host_name = HP-Laptop
DHCP4.OPTION[6]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        expiry = 1535290397
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.254
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.254
DHCP4.OPTION[16]:                       ip_address = 192.168.1.74
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       dhcp_message_type = 5
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       network_number = 192.168.1.0
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::381e:baac:afae:4bf/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ba1db20e-62b1-3fb1-aa2d-1dc28ad0f238 | Wired connection 1

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

Region: Europe/London (based on set time zone)

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

lo        no frequency information.

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/ideapad-laptop.conf]
blacklist ideapad-laptop

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

[   17.820386] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   17.820391] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   17.897186] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   17.897194] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   33.795217] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   33.867463] r8169 0000:03:00.0 eno1: link down
[   33.867860] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  608.723690] r8169 0000:03:00.0 eno1: link up
[  608.723727] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

########## wireless info END ############
```

@arpi732- i tried but it said "unable to locate package bcmwl-kernel-source"

---

### Post by arpi732 on 2018-08-25
try this 

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

and reboot

---

### Post by jeremy31 on 2018-08-25
See the wireless script link in my signature and post results

---

### Post by harryhorus on 2018-08-25
hi, i tried typing that in but got this message [COLOR=#000000]"unable to locate package bcmwl-kernel-source"[/COLOR]

---

### Post by jeremy31 on 2018-08-25
See [https://ubuntuforums.org/showthread.php?t=2395655&p=13781215#post13781215](https://ubuntuforums.org/showthread.php?t=2395655&p=13781215#post13781215)

---

### Post by harryhorus on 2018-08-25
do i type each of those lines individually and press enter or type all of them and press enter, sorry for my lack of understanding, i have never used linux before.

---

### Post by jeremy31 on 2018-08-25
Just one line at a time

---

### Post by harryhorus on 2018-08-25
typed in the first line and got this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package dkms
E: Package 'build-essential' has no installation candidate

Never mind got past that by using- sudo apt-get update.

Typed in the rest of the code and the wifi is now working, thank you for the help.

---

