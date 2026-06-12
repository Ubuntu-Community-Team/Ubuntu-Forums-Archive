---
title: "Wifi not working - 16.04 LTS - Broadcom BCM43142"
date: 2016-09-23
forum: Networking &amp; Wireless
---

### Post by sunil.patidar on 2016-09-23
I have installed ubuntu 16.04 LTS and after installing it my wifi is not working. Before ubuntu installation it was working all fine.
I am using Sony VAIO SVF152A29W laptop.

I am new to ubuntu, so i dont have any idea how to resolve this problem.

Here is the output of the Wireless Info Script.

```
########## wireless info START ##########

Report from: 23 Sep 2016 11:07 IST +0530

Booted last: 23 Sep 2016 00:00 IST +0530

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e071]
    Kernel modules: bcma, wl

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: nfc0: NFC
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              565248  0
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp14s0   Link encap:Ethernet  HWaddr <MAC 'enp14s0' [IF1]>  
          inet addr:192.168.0.68  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7908:c9f5:6702:a01e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22639 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39054153 (39.0 MB)  TX bytes:2268482 (2.2 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp14s0   no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp14s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp14s0
192.168.0.0     0.0.0.0         255.255.0.0     U     100    0        0 enp14s0

##### resolv.conf #######################

nameserver 127.0.1.1
search pathindia.local

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2425     1  0 10:30 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp14s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp14s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:0e:00.0/net/enp14s0
GENERAL.IP-IFACE:                       enp14s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       df94c8a6-6a18-4ff8-bff9-1c93da803df5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   df94c8a6-6a18-4ff8-bff9-1c93da803df5 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.68/16
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.2
IP4.DNS[2]:                             8.8.8.8
IP4.DOMAIN[1]:                          pathindia.local
IP4.WINS[1]:                            192.168.0.2
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.0.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.0.2 8.8.8.8
DHCP4.OPTION[5]:                        ip_address = 192.168.0.68
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.2
DHCP4.OPTION[8]:                        netbios_name_servers = 192.168.0.2
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.255.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 9450
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.0.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 5400
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = pathindia.local
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1474619544
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 0.0.0.0
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 10800
IP6.ADDRESS[1]:                         fe80::7908:c9f5:6702:a01e/64
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

Region: Asia/Kolkata (based on set time zone)

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

lo        no frequency information.

enp14s0   no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp14s0   Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
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

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   26.153494] IPv6: ADDRCONF(NETDEV_UP): enp14s0: link is not ready
[   26.292530] r8169 0000:0e:00.0 enp14s0: link down (repeated 2 times)
[   26.292601] IPv6: ADDRCONF(NETDEV_UP): enp14s0: link is not ready
[   28.532974] r8169 0000:0e:00.0 enp14s0: link up
[   28.532984] IPv6: ADDRCONF(NETDEV_CHANGE): enp14s0: link becomes ready
[   76.995097] r8169 0000:0e:00.0 enp14s0: link down
[   87.729938] r8169 0000:0e:00.0 enp14s0: link up
[  277.905611] r8169 0000:0e:00.0 enp14s0: link down
[  287.192749] r8169 0000:0e:00.0 enp14s0: link up
[  287.473752] r8169 0000:0e:00.0 enp14s0: link down
[  293.657802] r8169 0000:0e:00.0 enp14s0: link up
[  297.608054] r8169 0000:0e:00.0 enp14s0: link down
[  317.067390] r8169 0000:0e:00.0 enp14s0: link up
[ 1613.645958] r8169 0000:0e:00.0 enp14s0: link down
[ 1645.133694] r8169 0000:0e:00.0 enp14s0: link up
[ 1645.372693] r8169 0000:0e:00.0 enp14s0: link down
[ 1655.172780] r8169 0000:0e:00.0 enp14s0: link up
[ 1658.380433] r8169 0000:0e:00.0 enp14s0: link down
[ 1913.504466] r8169 0000:0e:00.0 enp14s0: link up

########## wireless info END ############
```

---

### Post by howefield on 2016-09-23
Welcome to the forums, thread moved to the "*Networking & Wireless*" forum where you are more likely to get help.

---

