---
title: "Compaq Presario V2000 No Wifi"
date: 2016-07-29
forum: Networking &amp; Wireless
---

### Post by emilianomans on 2016-07-29
Hi, don't know where to post this (and my English isn't so good, sorry). 
I just install the 16.04 in this old computer, a Compaq Presario V2000, and doesn't recognize the wifi. I have run the wireless scrip from @kc1di

```

########## wireless info START ##########

Report from: 29 Jul 2016 02:44 ART -0300

Booted last: 29 Jul 2016 00:00 ART -0300

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [103c:3091]
    Kernel driver in use: 8139too

05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1356]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 17ef:6019 Lenovo 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6152192  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              499712  1 wl
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp5s0    Link encap:Ethernet  HWaddr <MAC 'enp5s0' [IF1]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c902:b621:e807:4583/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:532026 (532.0 KB)  TX bytes:121798 (121.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp5s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp5s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp5s0

##### resolv.conf #######################

nameserver 127.0.1.1
search cpe.telecentro.net.ar

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1854     1  0 02:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp5s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:05:00.0/net/enp5s0
GENERAL.IP-IFACE:                       enp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexión cableada 1
GENERAL.CON-UUID:                       a59da3f1-dce4-45ac-be45-3a79b0c103d8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a59da3f1-dce4-45ac-be45-3a79b0c103d8 | Conexión cableada 1
IP4.ADDRESS[1]:                         192.168.0.6/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             181.47.248.145
IP4.DNS[2]:                             200.115.192.28
IP4.DNS[3]:                             200.115.192.89
IP4.DOMAIN[1]:                          cpe.telecentro.net.ar
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 181.47.248.145 200.115.192.28 200.115.192.89
DHCP4.OPTION[5]:                        ip_address = 192.168.0.6
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = cpe.telecentro.net.ar
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1469774448
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::c902:b621:e807:4583/64
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

[[/etc/NetworkManager/system-connections/Conexión inalámbrica 1]] (600 root)
[connection] id=Conexión inalámbrica 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Telecentro-c7e0
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

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

enp5s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp5s0    Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-31-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/sl-modem.conf]
install slamr /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slamr; test -e /dev/slamr0 && (chmod 660 /dev/slamr0 && chgrp dialout /dev/slamr0) || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)
remove slamr /sbin/modprobe --remove --ignore-remove slamr; test -e /dev/slamr0 && /bin/rm -f /dev/slamr0 2>/dev/null
install slusb /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slusb; test -e /dev/slusb0 && (chmod 660 /dev/slusb0 && chgrp dialout /dev/slusb0) || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)
remove slusb /sbin/modprobe --remove --ignore-remove slusb; test -e /dev/slusb0 && /bin/rm -f /dev/slusb0 2>/dev/null

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   23.866825] wl driver 6.30.223.248 (r487574) failed with code 21
[   23.868007]  [<e9b5da43>] wl_free_if.isra.15+0x23/0xa0 [wl]
[   23.868007]  [<e9b5e2a2>] wl_free+0x52/0x240 [wl]
[   23.868007]  [<e9b5e7e0>] wl_pci_probe+0x350/0x6d0 [wl]
[   23.868007]  [<e8cec06d>] wl_module_init+0x6d/0x1000 [wl]
[   44.721977] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready
[   44.725962] 8139too 0000:05:00.0 enp5s0: link down
[   44.735355] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready
[  529.852866] 8139too 0000:05:00.0 enp5s0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  529.853183] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready

########## wireless info END ############


```

Thanks for advance.

---

### Post by praseodym on 2016-07-29
Please run:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

