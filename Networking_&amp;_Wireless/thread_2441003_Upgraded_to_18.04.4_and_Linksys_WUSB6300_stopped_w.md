---
title: "Upgraded to 18.04.4 and Linksys WUSB6300 stopped working"
date: 2020-04-17
forum: Networking &amp; Wireless
---

### Post by rpessoa on 2020-04-17
Hello,

I was using Ubuntu 18.04.3 and no problem with my Linksys WUSB6300 usb wifi.
 
However, after I upgraded my system, my wifi is gone. I tried to install different drivers I found in github but no luck. So I hope someone here can help me.

My system is updated.

All the infos I got from the script here:

```
########## wireless info START ##########

Report from: 17 Apr 2020 13:08 EDT -0400

Booted last: 17 Apr 2020 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.3.0-46-generic #38~18.04.1-Ubuntu SMP Tue Mar 31 04:17:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

sed: can't read /home/user/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Ethernet Connection (2) I219-V [1462:7968]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 001 Device 004: ID 1038:1260 SteelSeries ApS 
Bus 001 Device 003: ID 13b1:003f Linksys WUSB6300 802.11a/b/g/n/ac Wireless Adapter [Realtek RTL8812AU]
Bus 001 Device 002: ID 1b1c:0c03 Corsair 
Bus 001 Device 006: ID 046d:c332 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

mxm_wmi                16384  0
cfg80211              704512  0
wmi                    32768  1 mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.0.119/24 brd 192.168.0.255 scope global dynamic noprefixroute enp0s31f6
       valid_lft 38418sec preferred_lft 38418sec
    inet6 fe80::ec39:cef1:ef63:d9a1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp0s31f6 proto dhcp metric 100 
169.254.0.0/16 dev enp0s31f6 scope link metric 1000 
192.168.0.0/24 dev enp0s31f6 proto kernel scope link src 192.168.0.119 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search test.example.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       962     1  0 11:47 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       80372d4f-5237-36d1-8b9f-258cf0343c47
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.119/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             24.200.243.189
IP4.DNS[3]:                             24.200.210.241
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.0.1 24.200.243.189 24.200.210.241
DHCP4.OPTION[5]:                        ip_address = 192.168.0.119
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.0.1
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1587181753
DHCP4.OPTION[20]:                       host_name = linux
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       interface_mtu = 1500
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 43200
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::ec39:cef1:ef63:d9a1/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::5ef4:abff:feac:2e6a
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_domain_search = test.example.com.
DHCP6.OPTION[3]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        dhcp6_server_id = 0:1:0:1:5e:a:3f:ca:5c:f4:ab:ac:2e:6a
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:56:37:f0:ab:2e:89:9e:5b:77:d2:6f:a5:94:bd:d9:39
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   80372d4f-5237-36d1-8b9f-258cf0343c47 | Wired connection 1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Ipanema]] (600 root)
[connection] id=Ipanema | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Ipanema
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

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

enp0s31f6  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/5.3.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8F07355AEBF42CFCE5139A3
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.3.0-46-generic SMP mod_unload 
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

[   61.426200] e1000e: enp0s31f6 NIC Link is Down
[   66.345151] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   66.345236] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready

########## wireless info END ############


```

Thanks! :)

---

### Post by rpessoa on 2020-04-18
Solved by following the steps here:

[https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)

:)

---

### Post by stafio on 2020-05-05
Hi,

Had you tried installing this package? [https://packages.ubuntu.com/search?keywords=rtl8812au-dkms&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=rtl8812au-dkms&searchon=names&suite=bionic&section=all)

I'm on Ubuntu 20.04 and am looking to get a USB wireless adapter. Finding information on which ones work without too much manual configuration isn't all that easy. I'm looking at the Linksys WUSB6300 because it apparently uses the [Realtek RTL8812AU chipset]("https://wiki.gentoo.org/wiki/AC1200_Wireless_Adapters") and it seems like [installing rtl8812au-dkms should work for this adapter as well]("https://ubuntuforums.org/showthread.php?t=2402629&p=13832528#post13832528"), but I'd like to know for sure before I spend money on it.

---

### Post by jeremy31 on 2020-05-05
> **stafio said:**
> Hi,

Had you tried installing this package? [https://packages.ubuntu.com/search?keywords=rtl8812au-dkms&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=rtl8812au-dkms&searchon=names&suite=bionic&section=all)

I'm on Ubuntu 20.04 and am looking to get a USB wireless adapter. Finding information on which ones work without too much manual configuration isn't all that easy. I'm looking at the Linksys WUSB6300 because it apparently uses the [Realtek RTL8812AU chipset]("https://wiki.gentoo.org/wiki/AC1200_Wireless_Adapters") and it seems like [installing rtl8812au-dkms should work for this adapter as well]("https://ubuntuforums.org/showthread.php?t=2402629&p=13832528#post13832528"), but I'd like to know for sure before I spend money on it.

The Ubuntu package rtl8812au-dkms has had a broken dkms.conf since Ubuntu 16.04

---

### Post by stafio on 2020-05-05
> **jeremy31 said:**
> The Ubuntu package rtl8812au-dkms has had a broken dkms.conf since Ubuntu 16.04

Alright, that's good to know. Do you have any recommendation on a wireless USB adapter that will work 'out of the box' or with one package install?

---

### Post by jeremy31 on 2020-05-05
The [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au) works with over 70 different devices as it covers RTL8812AU, RTL8814AU, and RTL8821AU chipsets
The TP Link TL WN721N should work out of the box as long as they haven't switched chipsets like they did for the TL WN722N

---

### Post by stafio on 2020-05-11
Thanks for providing that info. Not to hijack this thread any further, I've made a post about what I went with [over here]("https://ubuntuforums.org/showthread.php?t=2443132&p=13956286").

---

