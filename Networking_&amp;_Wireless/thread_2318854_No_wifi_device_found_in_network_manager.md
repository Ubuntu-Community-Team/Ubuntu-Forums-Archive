---
title: "No wifi device found in network manager"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by bluepicaso2 on 2016-03-30
So bought this new laptop Lenovo Ideapad 300 i5 (6th gen)
and installed 14.04, but most of the stuff did not work. So updated to 15.10 from update manager.
Everything seems to work except the wifi, there is no "enable wireless" section in network manager.
I can only use 3G usb device, it connects automatically.
I want wifi to work. Below is output of wifi script(suggested in sticky)
```


########## wireless info START ##########

Report from: 30 Mar 2016 09:36 IST +0530

Booted last: 30 Mar 2016 00:00 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lenovo Device [17aa:4035]

03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330] [1002:6660] (rev ff)

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e360 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 5986:0671 Acer, Inc 
Bus 001 Device 006: ID 05c6:6001 Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              548864  1 wl
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16605410 (16.6 MB)  TX bytes:3116343 (3.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       616     1  0 09:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm, Incorporated
GENERAL.PRODUCT:                        Qualcomm mobile device
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'eth1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/eth1
GENERAL.IP-IFACE:                       eth1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       20409b38-3c66-4d47-a5f3-f1d28a105434
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   20409b38-3c66-4d47-a5f3-f1d28a105434 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.100/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        fqdn_hostname = harpreet-ideapad
DHCP4.OPTION[6]:                        ip_address = 192.168.1.100
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        fqdn_fqdn = harpreet-ideapad
DHCP4.OPTION[9]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[10]:                       fqdn_server_update = true
DHCP4.OPTION[11]:                       fqdn_encoded = false
DHCP4.OPTION[12]:                       fqdn_rcode1 = 255
DHCP4.OPTION[13]:                       fqdn_rcode2 = 255
DHCP4.OPTION[14]:                       requested_time_offset = 1
DHCP4.OPTION[15]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[16]:                       dhcp_rebinding_time = 63000
DHCP4.OPTION[17]:                       requested_interface_mtu = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       dhcp_message_type = 5
DHCP4.OPTION[20]:                       requested_broadcast_address = 1
DHCP4.OPTION[21]:                       routers = 192.168.1.1
DHCP4.OPTION[22]:                       dhcp_renewal_time = 36000
DHCP4.OPTION[23]:                       requested_domain_name = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       expiry = 1459382034
DHCP4.OPTION[26]:                       requested_wpad = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       fqdn_no_client_update = true
DHCP4.OPTION[29]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[30]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[31]:                       network_number = 192.168.1.0
DHCP4.OPTION[32]:                       requested_domain_search = 1
DHCP4.OPTION[33]:                       next_server = 192.168.1.1
DHCP4.OPTION[34]:                       requested_ntp_servers = 1
DHCP4.OPTION[35]:                       dhcp_lease_time = 72000
DHCP4.OPTION[36]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::<IP6 'eth1' [IF]>/64
IP6.GATEWAY:                            fe80::fedd:55ff:fe08:12a0
IP6.ROUTE[1]:                           dst = fe80::fedd:55ff:fe08:12a0/128, nh = ::, mt = 100
IP6.DNS[1]:                             fd00::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd00::1 fd00::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:fc:dd:55:8:12:a0
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_status_code = success
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:67:3c:17:b8:4:fe:48:39:ef:c5:22:e1:bc:de:e8:a1

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
WimaxEnabled=true

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

eth0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rndis_host)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[   12.101574] Bluetooth: hci0: QCA: patch rome 0x300 build 0x3e8, firmware rome 0x300 build 0x111
[   17.739335] rndis_host 1-2:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-2, RNDIS device, <MAC 'eth1' [IF]>
[   27.890102] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.603727] r8169 0000:01:00.0 eth0: link down
[   28.603764] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.605999] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready

########## wireless info END ############



```

Please help me thank you

---

### Post by wildmanne39 on 2016-03-30
Hello, first remove the wl driver it is the wrong one.
```
sudo apt-get purge bcmwl-kernel-source
```
Then go to this link and follow the directions in the answer posted there.
[http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation](http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation)
Thanks

---

### Post by bluepicaso2 on 2016-03-30
> **Wild Man said:**
> Hello, first remove the wl driver it is the wrong one.
```
sudo apt-get purge bcmwl-kernel-source
```
Then go to this link and follow the directions in the answer posted there.
[http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation](http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation)
Thanks

Ok, Hope that works out.

---

### Post by jeremy31 on 2016-03-30
See if this fixes it
[http://askubuntu.com/a/708103/300665](http://askubuntu.com/a/708103/300665)

---

### Post by bluepicaso2 on 2016-03-30
> **jeremy31 said:**
> See if this fixes it
[http://askubuntu.com/a/708103/300665](http://askubuntu.com/a/708103/300665)

Yep, both reply offered same link. working on it.

---

### Post by bluepicaso2 on 2016-03-30
in the link you suggested
there is a command
```

git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
```
BUT after doing git there is nothing like
```

ath10k-firmware/QCA9377

```
Check screenshot
[ATTACH=CONFIG]268069[/ATTACH]

---

### Post by bluepicaso2 on 2016-03-30
Thank you both of you.
This "Thank you" is from wifi connection.

---

