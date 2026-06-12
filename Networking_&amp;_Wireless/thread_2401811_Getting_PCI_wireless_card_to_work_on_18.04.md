---
title: "Getting PCI wireless card to work on 18.04"
date: 2018-09-22
forum: Networking &amp; Wireless
---

### Post by Haven_McClure on 2018-09-22
I have a Broadcom PCI wireless card that I have to struggle to get to work with every fresh install of Ubuntu. 

For various reasons, I switched from Ubuntu Studio 16.04 to Kubuntu 18.04. The system only sees the wired ethernet connection, but none of the networks near me show, nor can I find the networks when I enter their name.  

Here is the info I get about my connection.
```

########## wireless info START ##########

Report from: 22 Sep 2018 20:44 CDT -0500

Booted last: 22 Sep 2018 00:00 CDT -0500

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Plasma

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:380b]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0621]
    Kernel modules: wl

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 002 Device 004: ID 5986:055e Acer, Inc 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 1852:7022 GYROCOM C&C Co., LTD 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              622592  0
ideapad_laptop         32768  0
sparse_keymap          16384  1 ideapad_laptop
mxm_wmi                16384  1 nouveau
video                  45056  3 nouveau,i915,ideapad_laptop
wmi                    24576  3 mxm_wmi,nouveau,ideapad_laptop

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
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
    inet 192.168.1.62/24 brd 192.168.1.255 scope global dynamic noprefixroute enp1s0
       valid_lft 85281sec preferred_lft 85281sec
    inet6 fe80::5f0b:9f47:42b6:e457/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

##### route #############################

default via 192.168.1.1 dev enp1s0 proto dhcp metric 100 
169.254.0.0/16 dev enp1s0 scope link metric 1000 
192.168.1.0/24 dev enp1s0 proto kernel scope link src 192.168.1.62 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       672     1  0 20:26 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
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
GENERAL.CON-UUID:                       f4e8dbab-43ff-32ba-a3db-f48eefa4284f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.62/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        expiry = 1537752368
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       requested_wpad = 1
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       ip_address = 192.168.1.62
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::5f0b:9f47:42b6:e457/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f4e8dbab-43ff-32ba-a3db-f48eefa4284f | Wired connection 1

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
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-34-generic SMP mod_unload 
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

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[    9.193157] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    9.193160] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   10.251350] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   10.297947] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   10.298063] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   13.300374] r8169 0000:01:00.0 enp1s0: link up
[   13.300384] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready

########## wireless info END ############

```

I've spent hours checking various sources to work through this conundrum such as 

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)  (the Broadcom sticky) 
[https://askubuntu.com/questions/1052403/how-can-i-fix-broadcom-driver-wifi-with-4-15-0-xx-kernel-on-ubuntu-16-04](https://askubuntu.com/questions/1052403/how-can-i-fix-broadcom-driver-wifi-with-4-15-0-xx-kernel-on-ubuntu-16-04)
[https://ubuntuforums.org/showthread.php?t=2397377&highlight=Broadcom+4365](https://ubuntuforums.org/showthread.php?t=2397377&highlight=Broadcom+4365)
[https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-install](https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-install)

I haven't gotten any solutions from these links. Also, I haven't seen yeet any information regarding work with these cards in 18.04. 

Any insight people have on this would be deeply appreciated.

---

### Post by chili555 on 2018-09-24
What is the exact response to the terminal command:```
sudo modprobe wl
```If it turns out to be:> modprobe: ERROR: could not insert 'wl': Required key not availableThen check here: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

Disable secure boot and your wireless should be working.

---

### Post by Haven_McClure on 2018-09-27
I had that precise error you reported so I followed your link, followed the directions for disabling secure boot, and Boom! Success.  One of the easiest fixes ever.

Thanks so much for your help!

---

### Post by chili555 on 2018-09-27
Glad it's working! Have fun.

---

