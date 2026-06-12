---
title: "dell inspiron 6000 wireless troubles"
date: 2016-07-19
forum: Networking &amp; Wireless
---

### Post by vbdanl-yahoo on 2016-07-19
hi.  just installed lubuntu on this old laptop.  really like this OS and all ubuntu flavors.
i have been having problems getting wireless to work on this so was hoping someone could steer me in the right direction.
i now have it hooked up to ethernet cable, but would like to cut the cord and go with the internal wireless.
this pc has a broadcom BCM4309 14e4:4324 rev 03 adapter, card, or whatever you call it.
looking at the ubuntu wiki, it shows both b43 and b43-legacy handle the 4309 model.
since i had no luck with mint 13 (probably just did something wrong), i was hoping to get some help before i messed things up this go around.
thanks so much for your help.
and btw, i do have puppy slacko 5.4 on another partition and it works fine with wireless, so i know the card/adapter works.

here is the output from the wireless-info script.
```

########## wireless info START ##########

Report from: 18 Jul 2016 23:31 CDT -0500

Booted last: 18 Jul 2016 00:00 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, video=LVDS-1:d, video=VGA-1:e, splash, video=LVDS-1:d, video=VGA-1:e, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6000 laptop [1028:0188]
    Kernel driver in use: b44

03:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1bcf:053e Sunplus Innovation Technology Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

b43                   401408  0
bcma                   49152  1 b43
mac80211              659456  1 b43
dell_laptop            24576  0
dcdbas                 16384  1 dell_laptop
cfg80211              499712  2 b43,mac80211
ssb                    57344  2 b43,b44
video                  36864  2 i915,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.240  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:30a:c0d0:f7e0:d234:b7e8:e104:30f9/64 Scope:Global
          inet6 addr: 2602:30a:c0d0:f7e0::11/128 Scope:Global
          inet6 addr: 2602:30a:c0d0:f7e0:7087:7c58:db59:6a8e/64 Scope:Global
          inet6 addr: fe80::453b:e511:ac63:bdea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:348101652 (348.1 MB)  TX bytes:512475 (512.4 KB)
          Interrupt:18 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1840     1  0 23:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX (Inspiron 6000 laptop)
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       e4ac8f92-59a9-415d-bfdc-0d1a8cfe134d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e4ac8f92-59a9-415d-bfdc-0d1a8cfe134d | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.240/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[5]:                        ip_address = 192.168.1.240
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = -21600
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.254
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = attlocal.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1468988586
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 0.0.0.0
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         2602:30a:c0d0:f7e0::11/128
IP6.ADDRESS[2]:                         2602:30a:c0d0:f7e0:7087:7c58:db59:6a8e/64
IP6.ADDRESS[3]:                         2602:30a:c0d0:f7e0:d234:b7e8:e104:30f9/64
IP6.ADDRESS[4]:                         fe80::453b:e511:ac63:bdea/64
IP6.GATEWAY:                            fe80::ea33:81ff:feb3:a4e0
IP6.ROUTE[1]:                           dst = 2602:30a:c0d0:f7e0::/64, nh = fe80::ea33:81ff:feb3:a4e0, mt = 100
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:fa:65:15:58:a9:70:6b:a6:3b:13:88:98:85:df:71:7a
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        rebind = 483840
DHCP6.OPTION[4]:                        max_life = 2592000
DHCP6.OPTION[5]:                        preferred_life = 604800
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        life_starts = 1468902187
DHCP6.OPTION[9]:                        ip6_address = 2602:30a:c0d0:f7e0::11
DHCP6.OPTION[10]:                       ip6_prefixlen = 64
DHCP6.OPTION[11]:                       renew = 302400
DHCP6.OPTION[12]:                       starts = 1468902187
DHCP6.OPTION[13]:                       iaid = 43:7b:4c:8d
DHCP6.OPTION[14]:                       dhcp6_server_id = 0:1:0:1:1c:cb:f3:8d:e8:33:81:b3:a4:e1

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

Region: America/Chicago (based on set time zone)

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

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

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

[ssb]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   19.859201] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   19.868105] b43-phy0: Found PHY: Analog 2, Type 2 (G), Revision 2
[   19.868132] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   19.868137] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[   20.255977] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   20.429690] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   20.429754] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   20.429759] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   20.429764] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   37.804226] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   40.816215] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   40.816225] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[   40.816335] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-07-19
Please do with an internet connection:
```
sudo apt-get install firmware-b43-installer
```
Reboot

---

### Post by vbdanl-yahoo on 2016-07-19
i ran the installer.  was not sure if i was supposed to unplug the ethernet or not, so left it plugged in..
```
dan@dan-Inspiron-6000:~$ sudo apt-get install firmware-b43-installer
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 30 not upgraded.
Need to get 27.2 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main i386 b43-fwcutter i386 1:019-2 [23.1 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/multiverse i386 firmware-b43-installer all 1:019-2 [4,120 B]
Fetched 27.2 kB in 0s (53.3 kB/s)            
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 146264 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a019-2_i386.deb ...
Unpacking b43-fwcutter (1:019-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-2_all.deb ...
Unpacking firmware-b43-installer (1:019-2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up b43-fwcutter (1:019-2) ...
Setting up firmware-b43-installer (1:019-2) ...
No chroot environment found. Starting normal installation
--2016-07-19 20:42:03--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119
Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip]
Saving to: ‘broadcom-wl-5.100.138.tar.bz2’

broadcom-wl-5.100.138.t 100%[=============================>]  12.89M  2.64MB/s    in 5.1s    

2016-07-19 20:42:09 (2.55 MB/s) - ‘broadcom-wl-5.100.138.tar.bz2’ saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
dan@dan-Inspiron-6000:~$ ^C
dan@dan-Inspiron-6000:~$ 

```

---

### Post by wildmanne39 on 2016-07-19
Is it now searching for networks? 
Go to network manager and see if you see any networks, make sure networking and wifi is enabled.
Thanks

---

### Post by vbdanl-yahoo on 2016-07-19
i did not see network manager under the menus of lubuntu.  i did see network connections under Preferences, and all it shows is ethernet and wired connection.
i ran the wireless script again and it looks like wifi is up and running.  the essid is mine in the output below.. should i just unplug ethernet and reboot ?
```

########## wireless info START ##########

Report from: 19 Jul 2016 20:58 CDT -0500

Booted last: 19 Jul 2016 00:00 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, video=LVDS-1:d, video=VGA-1:e, splash, video=LVDS-1:d, video=VGA-1:e, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6000 laptop [1028:0188]
    Kernel driver in use: b44

03:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1bcf:053e Sunplus Innovation Technology Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   401408  0
bcma                   49152  1 b43
dell_laptop            24576  0
mac80211              659456  1 b43
dcdbas                 16384  1 dell_laptop
cfg80211              499712  2 b43,mac80211
ssb                    57344  2 b43,b44
video                  36864  2 i915,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.240  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4f0:620f:b7c2:dc24/64 Scope:Link
          inet6 addr: 2602:30a:c0d0:f7e0::11/128 Scope:Global
          inet6 addr: 2602:30a:c0d0:f7e0:b0de:1cac:d6c3:679e/64 Scope:Global
          inet6 addr: 2602:30a:c0d0:f7e0:a697:de64:5cbb:d835/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:221357070 (221.3 MB)  TX bytes:21212 (21.2 KB)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1894     1  0 20:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX (Inspiron 6000 laptop)
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       a4718043-03df-4043-9975-53c15b660763
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a4718043-03df-4043-9975-53c15b660763 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.240/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[5]:                        ip_address = 192.168.1.240
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = -21600
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.254
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = attlocal.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1469066026
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 0.0.0.0
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         2602:30a:c0d0:f7e0::11/128
IP6.ADDRESS[2]:                         2602:30a:c0d0:f7e0:b0de:1cac:d6c3:679e/64
IP6.ADDRESS[3]:                         2602:30a:c0d0:f7e0:a697:de64:5cbb:d835/64
IP6.ADDRESS[4]:                         fe80::4f0:620f:b7c2:dc24/64
IP6.GATEWAY:                            fe80::ea33:81ff:feb3:a4e0
IP6.ROUTE[1]:                           dst = 2602:30a:c0d0:f7e0::/64, nh = fe80::ea33:81ff:feb3:a4e0, mt = 100
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:fa:65:15:58:a9:70:6b:a6:3b:13:88:98:85:df:71:7a
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        rebind = 483840
DHCP6.OPTION[4]:                        max_life = 2592000
DHCP6.OPTION[5]:                        preferred_life = 604800
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        life_starts = 1468979626
DHCP6.OPTION[9]:                        ip6_address = 2602:30a:c0d0:f7e0::11
DHCP6.OPTION[10]:                       ip6_prefixlen = 64
DHCP6.OPTION[11]:                       renew = 302400
DHCP6.OPTION[12]:                       starts = 1468979626
DHCP6.OPTION[13]:                       iaid = 43:7b:4c:8d
DHCP6.OPTION[14]:                       dhcp6_server_id = 0:1:0:1:1c:cb:f3:8d:e8:33:81:b3:a4:e1

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4309 802.11abg Wireless Network Controller (Truemobile 1450 MiniPCI)
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ATT7n9Z9G5  <MAC 'ATT7n9Z9G5' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        

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

Region: America/Chicago (based on set time zone)

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

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ATT7n9Z9G5' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"ATT7n9Z9G5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012ac7e2bd5e
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

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

[ssb]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   18.011295] Modules linked in: yenta_socket(+) pcmcia_rsrc pcmcia_core mac_hid autofs4 hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt pata_acpi psmouse fb_sys_fops ahci b44 firewire_ohci drm libahci sdhci_pci firewire_core ssb sdhci mii crc_itu_t video
[   20.390880] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   20.400067] b43-phy0: Found PHY: Analog 2, Type 2 (G), Revision 2
[   20.400095] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   20.400100] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[   38.095209] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   38.179038] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.300052] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   38.396157] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   41.816228] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   41.816238] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[   41.816342] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-07-19
Yes disable ethernet and reboot.

Network manager does not show in the top bar?

---

### Post by vbdanl-yahoo on 2016-07-19
i forgot to say "Thanks!!" for all your help Wild Man.  I really appreciate it.
i will search for running network manager and see what it shows..

---

### Post by vbdanl-yahoo on 2016-07-19
i don't have a top bar.  am running lubuntu 16.04 and the menu is lower left.. shows Acc, Grap, Inter, Off, S&V, System Tools, Pref, Run, and Logout
am rebooting now

---

### Post by vbdanl-yahoo on 2016-07-19
when i rebooted, it flashed something about wireless connection available in upper left corner, then it disappeared.
looking at the menus, there is a Network Settings under System tools and a Network Connections under Pref.  Neither say anything about wireless
Network connections shows Ethernet and Wired connection 1.
System tools shows Network Settings which has General, DNS, and Hosts tabs.. should i dnld some network manager app ?

---

### Post by wildmanne39 on 2016-07-19
In your menu bar if you can see your ehternet connection then network manager is already in the menu, if not then we need to find out why it is not loading.

---

### Post by wildmanne39 on 2016-07-19
Look here if the network manager applet is not in the menu bar.
[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by vbdanl-yahoo on 2016-07-19
i found a network button in lower right corner.  entered my pswd.  not sure why, but still no internet.. i rebooted.. still no internet.
i just selected my att network in lower right, and it says network connection established.. can now get on internet.
do you think i will have to select it every time i reboot ?

---

### Post by wildmanne39 on 2016-07-19
Go into edit connection then click on your network name and make sure that log on automatically is checked and that the password is saved there.
Thanks

---

### Post by vbdanl-yahoo on 2016-07-19
Looks like it is all good now.  i did a shutdown, then rebooted, and internet is working.
Thanks for all of your help !!
i do have another question.. from my research, it does not look like there is a solution..
i can open another post if you think it will help..
i am using a external monitor on this laptop, because the lcd quit working over a yr ago.
i don't find any option in grub2 that allows it to display the grub menu at boot on the external monitor.
i don't find any option in bios to do that either.
i set a couple of options so when it does boot, it will display on the external monitor without me selecting anything.
to get it to show the grub menu, i have to press Fn F8 to switch between lcd and external.
anyway, just thought i would ask.. i have seen posts with exactly the same problem, and have not seen any answers yet..
thanks again Wild Man !!

---

### Post by wildmanne39 on 2016-07-19
Your welcome! Yes please start a new with a descriptive title and use thread tools to mark this one solved.
Thanks and Enjoy!

---

