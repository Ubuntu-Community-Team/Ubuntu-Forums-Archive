---
title: "Network issues after 16.10 update"
date: 2017-03-29
forum: Networking &amp; Wireless
---

### Post by aDAMOpl on 2017-03-29
**EDIT:** by following [this post]("http://askubuntu.com/questions/894418/internet-died-after-ubuntu-16-10-upgrade") I managed to get the network back "mostly". I am not sure if this was the kernel issue or /etc/networking/interfaces issue (or both).

But now, the networking applet does not show any connection information ("No active connectins found") and e.g. software manager says there is no internet connection but most of the stuff (browsers, Nextcloud) work fine.
I guess the network-manager settings are not right now but no idea how to fix.


Hello...

I have the same problem after update to 16.10 (from 16.04). No network.

I was messing around with Synaptic trying to replicate the steps you guys made but no luck.
Later I have manually downloaded (on my second PC) packages for kernel 4.8.0.41 and installed using gdebi but still no good.

I have checked:
**   apt-list --installed linux***
and got:[B]
linux-base
linux-firmware   
linux-headers-4.8.0-41
linux-headers-4.8.0-41-generic
linux-image-4.8.0-41-generic
linux-image-extra-4.8.0-41-generic
linux-libc-dev
linux-sound-base

[/B]I would be grateful for any advice how to proceed.

---

### Post by jeremy31 on 2017-03-29
You should be able to press Shift key at boot until the Grub menu appears, select Advanced Options, then select the 4.8.0-41 kernel to boot to

---

### Post by aDAMOpl on 2017-03-29
@jeremy31
Thank you for reply.
I was booting to 4.8.0-41 (acutally I didn't have any other kernels installed). This is "mostly" working fine now. Please see the edit to my post.

---

### Post by jeremy31 on 2017-03-29
Ok, I moved this to its own thread as the original poster had an issue caused by a incomplete kernel update.  See the wireless script link in my signature and post results

---

### Post by aDAMOpl on 2017-03-29
@jeremy31
Here are my results.

```

########## wireless info START ##########

Report from: 29 Mar 2017 23:30 CEST +0200

Booted last: 29 Mar 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

##### kernel ############################

Linux 4.8.0-41-generic #44-Ubuntu SMP Fri Mar 3 15:27:17 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC [10ec:8169]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:3f19 Creative Technology, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1e4e:0102 Cubeternet GL-UPC822 UVC WebCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c21f Logitech, Inc. F710 Wireless Gamepad [XInput Mode]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1e7d:2c2e ROCCAT 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              581632  0
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

auto enp2s7
iface enp2s7 inet dhcp

##### ifconfig ##########################

enp2s7: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.9  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::92f6:52ff:fe00:862c  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 284265  bytes 378910639 (378.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 181557  bytes 18023633 (18.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 84721  bytes 5164773 (5.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 84721  bytes 5164773 (5.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0-nic: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

virbr0    no wireless extensions.

enp2s7    no wireless extensions.

lo        no wireless extensions.

virbr0-nic  no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 enp2s7
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s7
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp2s7
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 192.168.1.254
nameserver 127.0.0.53
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1169     1  0 22:25 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         virbr0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0
GENERAL.IP-IFACE:                       virbr0
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.ADDRESS[1]:                         192.168.122.1/24
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8169 PCI Gigabit Ethernet Controller (RTL8169/8110 Family PCI Gigabit Ethernet NIC)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:02:07.0/net/enp2s7
GENERAL.IP-IFACE:                       enp2s7
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.ADDRESS[1]:                         192.168.1.9/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         fe80::92f6:52ff:fe00:862c/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         virbr0-nic
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0-nic
GENERAL.IP-IFACE:                       virbr0-nic
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
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

Region: Europe/Warsaw (based on set time zone)

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

virbr0    no frequency information.

enp2s7    no frequency information.

lo        no frequency information.

virbr0-nic  no frequency information.

##### iwlist scan #######################

virbr0    Interface doesn't support scanning.

enp2s7    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.8.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

it87

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############


```

---

### Post by jeremy31 on 2017-03-29
Can you ping the router?  I find 192.168.1.254 a strange IP for an access point, mine is 192.168.0.1 and I would have expected yours to be 192.168.1.1

---

### Post by aDAMOpl on 2017-03-29
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=0.610 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=0.553 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=0.586 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=0.577 ms

This is the correct router IP, according to the manual and I can log to control panel there.

Trivia: this is the [fancy router from Polish DSL operator Netia]("https://wiki.openwrt.org/toh/vtech/netiaspot").

---

### Post by jeremy31 on 2017-03-29
Do you have any idea why "nameserver 127.0.0.53" is in the results?

---

### Post by aDAMOpl on 2017-03-30
Nope, but as far as I can understand from [this bug]("https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1638836") discussion, it is normal.

---

### Post by tiberiup on 2017-04-11
Not sure if this will help you, but I had the same issue when upgrading from 16.04 to 16.10 and following the post you linked in the first post worked perfectly for me !

So maybe you have issues now because you messed up with the kernel / drivers

---

### Post by russkyca on 2017-04-11
If your internet connection is fixed, OP, could you post what you have in /etc/network/interfaces
and
/etc/NetworkManager

I'm just curious.   I had an issue when I upgraded from 16.04 to 16.10 and didn't have an internet connection....messed around with settings but I want to know what other users of 16.10 have in those files.

---

