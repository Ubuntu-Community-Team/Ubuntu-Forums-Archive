---
title: "rtl8822bu Driver Issues"
date: 2018-04-06
forum: Networking &amp; Wireless
---

### Post by chapterjason on 2018-04-06
Hey I got some issues with my driver the last days. My computer doesn't recognize the Wireless stick anymore.

I had the following driver: rtl8822bu
But it seems that its not the newest?

[PHP]

########## wireless info START ##########

Report from: 06 Apr 2018 19:34 CEST +0200

Booted last: 06 Apr 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Budgie Desktop

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 04d9:fa50 Holtek Semiconductor, Inc. 
Bus 002 Device 004: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:0a4d Logitech, Inc. G430 Surround Sound Gaming Headset
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              614400  0

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

br-6834ac2e6947: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.18.0.1  netmask 255.255.0.0  broadcast 172.18.255.255
        ether <MAC address>  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

docker0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        inet6 fe80::42:56ff:feac:9851  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 208  bytes 30935 (30.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.10  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4294:70a0:5408:9360  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 116265  bytes 122083668 (122.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 19669  bytes 2305735 (2.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2323  bytes 161349 (161.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2323  bytes 161349 (161.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

veth9da45a1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::8407:f9ff:fee5:554  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 310  bytes 46764 (46.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

docker0   no wireless extensions.

veth9da45a1  no wireless extensions.

enp3s0    no wireless extensions.

br-6834ac2e6947  no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br-6834ac2e6947
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-6834ac2e6947
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.0.53

search localdomain

##### network managers ##################

Installed:

    NetworkManager

Running:

root       567     1  0 19:12 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         br-6834ac2e6947
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/br-6834ac2e6947
GENERAL.IP-IFACE:                       br-6834ac2e6947
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     br-6834ac2e6947
GENERAL.CON-UUID:                       6ca19761-8a4c-485a-b3fe-173738564030
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6ca19761-8a4c-485a-b3fe-173738564030 | br-6834ac2e6947
IP4.ADDRESS[1]:                         172.18.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            --

GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       a1d27f3a-6e9c-41ae-a3f9-14b46d9241e5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a1d27f3a-6e9c-41ae-a3f9-14b46d9241e5 | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            --
IP6.ADDRESS[1]:                         fe80::42:56ff:feac:9851/64
IP6.GATEWAY:                            --

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard (one of many))
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       dac8cf9b-8667-4c51-b53f-d2bef0a011a9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dac8cf9b-8667-4c51-b53f-d2bef0a011a9 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.10/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1523640016
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.10
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = localdomain
DHCP4.OPTION[19]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 604800
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::4294:70a0:5408:9360/64
IP6.GATEWAY:                            --
IP6.DNS[1]:                             fe80::1

GENERAL.DEVICE:                         veth9da45a1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         veth
GENERAL.DRIVER-VERSION:                 1.0
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/veth9da45a1
GENERAL.IP-IFACE:                       veth9da45a1
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     10000 Mb/s
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
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

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WG-ALU-REC-SCH-2]] (600 root)
[connection] id=WG-ALU-REC-SCH-2 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WG-ALU-REC-SCH-2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/o2-WLAN82]] (600 root)
[connection] id=o2-WLAN82 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=o2-WLAN82
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WG-ALU-REC-SCH]] (600 root)
[connection] id=WG-ALU-REC-SCH | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WG-ALU-REC-SCH
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

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

docker0   no frequency information.

veth9da45a1  no frequency information.

enp3s0    no frequency information.

br-6834ac2e6947  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

docker0   Interface doesn't support scanning.

veth9da45a1  Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

br-6834ac2e6947  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-38-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
blacklist rtl8192cu
blacklist rtl8xxxu
blacklist xpad
blacklist rtl8xxxu

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false

[/etc/modprobe.d/blacklist-native-rtl-wlan-drivers.conf]
blacklist rtl8192c_common
blacklist rtlwifi
blacklist rtl8192cu
blacklist rtl8xxxu

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

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.984773] eth0: renamed from veth4ef40a3

########## wireless info END ############

[/PHP]

---

### Post by chili555 on 2018-04-06
How did you install rtl8822bu? Did you compile it; make, sudo make install, etc.? Or dkms? Or...what?

---

### Post by chapterjason on 2018-04-06
I used this Fork [https://github.com/FomalhautWeisszwerg](https://github.com/FomalhautWeisszwerg)
And I just done [PHP]make[/PHP] and [PHP]make install[/PHP]
I also installed all the build dependencies, literally I just followed the readme.

---

### Post by chili555 on 2018-04-06
Are you aware that after a kernel update, usually offered by Update Manager, you must recompile?

```
cd rtl8822bu
make clean
make
sudo make install
sudo modprobe 8822bu
```

---

### Post by praseodym on 2018-04-06
[https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836](https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836)

Don't know which one is better/newer?!

---

### Post by chapterjason on 2018-04-06
> **chili555 said:**
> Are you aware that after a kernel update, usually offered by Update Manager, you must recompile?

```
cd rtl8822bu
make clean
make
sudo make install
sudo modprobe 8822bu
```

Yeah it make sense and I already tried. But I doesn't knew about "make clean".

It's working now, thank you, I'll remember this next time!

---

### Post by chili555 on 2018-04-06
Glad it's working! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by jeremy31 on 2018-04-06
If you want to automate the build for kernel updates
```
sudo apt-get install dkms
cd rtl8822bu
make clean
gedit dkms.conf
```
Enter the following into the text editor
```
PACKAGE_NAME=8822bu
PACKAGE_VERSION=1.1

DEST_MODULE_LOCATION=/kernel/drivers/net/wireless
BUILT_MODULE_NAME=8822bu

MAKE="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
AUTOINSTALL="yes"
```

Save and exit gedit, then
```
cd ~
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```

The next kernel update should be installed with the driver compiled at the same time

---

### Post by chapterjason on 2018-04-07
> **jeremy31 said:**
> If you want to automate the build for kernel updates
```
sudo apt-get install dkms
cd rtl8822bu
make clean
gedit dkms.conf
```
Enter the following into the text editor
```
PACKAGE_NAME=8822bu
PACKAGE_VERSION=1.1

DEST_MODULE_LOCATION=/kernel/drivers/net/wireless
BUILT_MODULE_NAME=8822bu

MAKE="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
AUTOINSTALL="yes"
```

Save and exit gedit, then
```
cd ~
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```

The next kernel update should be installed with the driver compiled at the same time

Awesome, I'll try. Thank you for this incredible support! :D

---

### Post by jglen4902 on 2018-06-01
> **jeremy31 said:**
> If you want to automate the build for kernel updates
```
sudo apt-get install dkms
cd rtl8822bu
make clean
gedit dkms.conf
```
Enter the following into the text editor
```
PACKAGE_NAME=8822bu
PACKAGE_VERSION=1.1

DEST_MODULE_LOCATION=/kernel/drivers/net/wireless
BUILT_MODULE_NAME=8822bu

MAKE="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
AUTOINSTALL="yes"
```

Save and exit gedit, then
```
cd ~
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```

The next kernel update should be installed with the driver compiled at the same time
Again, thank you.  Good info and I have this in a text file (that gets backed up) for after I upgrade to Bionic.

---

