---
title: "No wifi adaptor found Ubuntu 18.04"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by mrboler on 2018-06-20
Hi guys, I was using Ubuntu 18.04 on my laptop without problem but now I  have to move desktop for a project. I have a problem. (No wifi and  bluetooth adaptor found) I read too many thread on internet to solving  the problem but all of them didn't work :(

I will give you some information code and hardware.

I am using Win10 and Ubuntu in same P.C. Secure boot is disabled. Anything for bios ?


Also I tried and more more way to fix it :(
like,

```

sudo apt remove bcmwl-kernel-source && sudo apt install git dkms
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6sudo apt install --reinstall bcmwl-kernel-source


```


_**sudo lshw -short   **_output:


```
 
H/W path       Device       Class          Description
======================================================
                            system         CASPER NIRVANA (CASPER H110M4-C43)
/0                          bus            CASPER NIRVANA DESKTOP
/0/0                        memory         64KiB BIOS
/0/3c                       memory         16GiB System Memory
/0/3c/0                     memory         8GiB DIMM DDR4 Synchronous Unbuffered
/0/3c/1                     memory         8GiB DIMM DDR4 Synchronous Unbuffered
/0/41                       memory         256KiB L1 cache
/0/42                       memory         1MiB L2 cache
/0/43                       memory         6MiB L3 cache
/0/44                       processor      Intel(R) Core(TM) i5-7500 CPU @ 3.40G
/0/100                      bridge         Intel Corporation
/0/100/1                    bridge         Skylake PCIe Controller (x16)
/0/100/1/0                  display        GP107 [GeForce GTX 1050 Ti]
/0/100/1/0.1                multimedia     NVIDIA Corporation
/0/100/8                    generic        Skylake Gaussian Mixture Model
/0/100/14                   bus            Sunrise Point-H USB 3.0 xHCI Controll
/0/100/14/0    usb1         bus            xHCI Host Controller
/0/100/14/0/1               input          HP USB 1000dpi Laser Mouse
/0/100/14/0/2               input          Wired Keyboard 600
/0/100/14/0/6               communication  SAMSUNG_Android
/0/100/14/1    usb2         bus            xHCI Host Controller
/0/100/14.2                 generic        Sunrise Point-H Thermal subsystem
/0/100/16                   communication  Sunrise Point-H CSME HECI #1
/0/100/17                   storage        Sunrise Point-H SATA controller [AHCI
/0/100/1c                   bridge         Sunrise Point-H PCI Express Root Port
/0/100/1c/0    enp2s0       network        RTL8111/8168/8411 PCI Express Gigabit
/0/100/1c.6                 bridge         Sunrise Point-H PCI Express Root Port
/0/100/1c.6/0               network        RT5390 Wireless 802.11n 1T/1R PCIe
/0/100/1c.7                 bridge         Sunrise Point-H PCI Express Root Port
/0/100/1c.7/0               bridge         IT8893E PCIe to PCI Bridge
/0/100/1f                   bridge         Sunrise Point-H LPC Controller
/0/100/1f.2                 memory         Memory controller
/0/100/1f.3                 multimedia     Sunrise Point-H HD Audio
/0/100/1f.4                 bus            Sunrise Point-H SMBus
/0/1           scsi0        storage        
/0/1/0.0.0     /dev/sda     disk           1TB WDC WD10EZEX-75W
/0/1/0.0.0/1   /dev/sda1    volume         127MiB reserved partition
/0/1/0.0.0/2   /dev/sda2    volume         931GiB Windows NTFS volume
/0/2           scsi1        storage        
/0/2/0.0.0     /dev/cdrom   disk           DVDRAM GH24NSD1
/0/3           scsi2        storage        
/0/3/0.0.0     /dev/sdb     disk           128GB SAMSUNG MZNLF128
/0/3/0.0.0/1   /dev/sdb1    volume         99MiB Windows FAT volume
/0/3/0.0.0/2   /dev/sdb2    volume         15MiB reserved partition
/0/3/0.0.0/3   /dev/sdb3    volume         79GiB Windows NTFS volume
/0/3/0.0.0/4   /dev/sdb4    volume         899MiB Windows NTFS volume
/0/3/0.0.0/5   /dev/sdb5    volume         39GiB EXT4 volume
/1                          power          To Be Filled By O.E.M.
/2             pan1         network        Ethernet interface
/3             enp0s20f0u6  network        Ethernet interface

```

_**Edited:**_

```


########## wireless info START ##########

Report from: 20 Jun 2018 11:34 +03 +0300

Booted last: 20 Jun 2018 00:00 +03 +0300

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Elitegroup Computer Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1019:9c55]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Kernel modules: rt2800pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 003: ID 045e:0751 Microsoft Corp. 
Bus 001 Device 002: ID 03f0:1198 Hewlett-Packard HID-compliant mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              778240  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              622592  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau

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
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: enp0s20f0u6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s20f0u6' [IF2]> brd <MAC address>
    inet 192.168.42.13/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s20f0u6
       valid_lft 2810sec preferred_lft 2810sec
    inet6 fe80::246:57ac:3c82:cd55/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp0s20f0u6  no wireless extensions.

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.42.129 dev enp0s20f0u6 proto dhcp metric 100 
169.254.0.0/16 dev enp0s20f0u6 scope link metric 1000 
192.168.42.0/24 dev enp0s20f0u6 proto kernel scope link src 192.168.42.13 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       731     1  0 11:21 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20f0u6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20f0u6' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/net/enp0s20f0u6
GENERAL.IP-IFACE:                       enp0s20f0u6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       be406f05-445e-363d-8e87-cae183828776
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.13/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.13
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1529486498
DHCP4.OPTION[20]:                       host_name = Ubuntu-Desktop
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::246:57ac:3c82:cd55/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   be406f05-445e-363d-8e87-cae183828776 | Wired connection 1

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

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

Region: Europe/Istanbul (based on set time zone)

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

enp0s20f0u6  no frequency information.

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp0s20f0u6  Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.15.0-23-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9B5C2765C235C863C24FDE0
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.15.0-23-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2AF67DBF566ACB443136786
depends:        rt2x00mmio,rt2x00lib,rt2800lib
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2800lib]
filename:       /lib/modules/4.15.0-23-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     E3426613D56538B49359106
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00pci]
filename:       /lib/modules/4.15.0-23-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EF62F1ED5B94FD33F012351
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00mmio]
filename:       /lib/modules/4.15.0-23-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DE3F68ABAA885403D3E251A
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00lib]
filename:       /lib/modules/4.15.0-23-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     61C3C15FFF5FD57ADC4DEB0
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-23-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-23-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

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

[    3.612545] rndis_host 1-6:1.0 enp0s20f0u6: renamed from usb0
[    4.165792] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u6: link is not ready
[    4.168030] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    4.214557] r8169 0000:02:00.0 enp2s0: link down
[    4.214617] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready

########## wireless info END ############



```

---

### Post by mrboler on 2018-06-21
up

---

### Post by jeremy31 on 2018-06-21
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo apt-get purge bcmwl-kernel-source
sudo dkms remove rtlwifi-new/0.6 --all
sudo dkms uninstall rtlwifi-new/0.6
sudo rm -r /usr/src/rtlwifi-new-0.6
```
Reboot

---

### Post by mrboler on 2018-06-21
sudo dkms remove rtlwifi-new/0.6 --all :

```

Error! There are no instances of module: rtlwifi-new
0.6 located in the DKMS tree.

```


sudo dkms uninstall rtlwifi-new/0.6 :

```
Error! There are no instances of module: rtlwifi-new
located in the DKMS tree.

```



sudo rm -r /usr/src/rtlwifi-new-0.6  :

```

rm: cannot remove '/usr/src/rtlwifi-new-0.6': No such file or directory

```

These codes give me outputs ;(

---

### Post by monkeybrain20122 on 2018-06-21
Sounds like [this thread]("https://ubuntuforums.org/showthread.php?t=2387505") and [this one]("https://ubuntuforums.org/showthread.php?t=2386964") .

Long story short, kernels 4.15.x have problems with some wifi cards.  So if that is your problem upgrading kernel might help.
grab kernel 4.16 [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16.17/"), Assuming you are on 64 bit OS, download 4 debs for amd64 (headers all, headers generic, image generic and modules generic) , put them all in one folder, say call it ker, then

```
cd ker
sudo dpkg -i *.deb
```

Reboot.

---

### Post by mrboler on 2018-06-21
> **monkeybrain20122 said:**
> Sounds like [this thread]("https://ubuntuforums.org/showthread.php?t=2387505") and [this one]("https://ubuntuforums.org/showthread.php?t=2386964") .

Long story short, kernels 4.15.x have problems with some wifi cards.  So if that is your problem upgrading kernel might help.
grab kernel 4.16 [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16.17/"), Assuming you are on 64 bit OS, download 4 debs for amd64 (headers all, headers generic, image generic and modules generic) , put them all in one folder, say call it ker, then

```
cd ker
sudo dpkg -i *.deb
```

Reboot.

*Thanks for helping*, I tried these threads. Also tried your way,

Build for amd64 succeeded :

[ linux-headers-4.16.17-041617_4.16.17-041617.201806201630_all.deb]("http://linux-headers-4.16.17-041617_4.16.17-041617.201806201630_all.deb")
[ linux-headers-4.16.17-041617-generic_4.16.17-041617.201806201630_amd64.deb]("http://linux-headers-4.16.17-041617-generic_4.16.17-041617.201806201630_amd64.deb")
[ linux-image-unsigned-4.16.17-041617-generic_4.16.17-041617.201806201630_amd64.deb]("http://linux-image-unsigned-4.16.17-041617-generic_4.16.17-041617.201806201630_amd64.deb")
[ linux-modules-4.16.17-041617-generic_4.16.17-041617.201806201630_amd64.deb]("http://linux-modules-4.16.17-041617-generic_4.16.17-041617.201806201630_amd64.deb")

After reboot, no wifi :(

Edited: I change OS to Ubuntu 16.04 and I tried these advises but I have same problem.

---

### Post by praseodym on 2018-06-22
I don't know if this still works with newer kernels
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/34/30/3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3 
wget media.cdn.ubuntu-de.org/forum/attachments/08/18/3473742-RT2860STA.dat.tar.gz
sudo mkdir -p /etc/Wireless/RT2860STA
sudo tar xvf 3473742-RT2860STA.dat.tar.gz -C /etc/Wireless/RT2860STA 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf
```
Reboot. If its not working, revert it
```

sudo dkms remove -m Ralink_5390sta -v 2.5.0.3 --all
sudo rm -r /var/lib/dkms/Ralink_5390sta/2.5.0.3 
sudo rm /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -v rt2800pci
```

---

### Post by rasaborio on 2018-06-22
It also sounds like the issue I had with [my laptop]("https://ubuntuforums.org/showthread.php?t=2394691"), I think the same: it's the kernel package, would you try to start your ubuntu OS with another kernel version??? it worked for me...

---

### Post by jeremy31 on 2018-06-22
> **rasaborio said:**
> It also sounds like the issue I had with [my laptop]("https://ubuntuforums.org/showthread.php?t=2394691"), I think the same: it's the kernel package, would you try to start your ubuntu OS with another kernel version??? it worked for me...

That would be unlikely unless the code for a Ralink wifi device has the same issue as the Broadcom Proprietary driver does.  I am using a USB wifi device that needs source code from github and I have no issue with the 4.15.0-24 kernel

---

### Post by rasaborio on 2018-06-22
> **jeremy31 said:**
> That would be unlikely unless the code for a Ralink wifi device has the same issue as the Broadcom Proprietary driver does.  I am using a USB wifi device that needs source code from github and I have no issue with the 4.15.0-24 kernel

I know they are different wifi devices, they are even different ubuntu versions, just suggested it could be the kernel because the error it showed to me was pretty similar, especially about not been able to create wireless connections, sometimes a single solution could help a lot of people...

---

### Post by jeremy31 on 2018-06-22
> **rasaborio said:**
> I know they are different wifi devices, they are even different ubuntu versions, just suggested it could be the kernel because the error it showed to me was pretty similar, especially about not been able to create wireless connections, sometimes a single solution could help a lot of people...

I have yet to see an error posted by mrboler that would suggest the issue is similar to yours.  mrboler is still using the 4.15.0-23 kernel from the wifi script results and the driver is part of the kernel
The perplexing thing is that is says, Kernel modules: rt2800pci rather than Kernel Driver in use rt2800pci

---

### Post by mrboler on 2018-06-23
I needed Ubuntu for the project I developed at work, first I installed ubuntu on my own computer and brought the project to the end point. After a week I have to make a presentation for the project, but the system has to be working on the company network. I met this problem on the business computer.


Tomorrow, Sunday, I will go all day to deal with this problem. I will try your last advices. I hope I can reach the solution... If I can not solve the problem, I might need someone to help me connect to my computer and help out.

Have a good night.

---

### Post by mrboler on 2018-06-24
Hi guys,

> **praseodym said:**
> I don't know if this still works with newer kernels
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/34/30/3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3 
wget media.cdn.ubuntu-de.org/forum/attachments/08/18/3473742-RT2860STA.dat.tar.gz
sudo mkdir -p /etc/Wireless/RT2860STA
sudo tar xvf 3473742-RT2860STA.dat.tar.gz -C /etc/Wireless/RT2860STA 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf
```
Reboot. If its not working, revert it
```

sudo dkms remove -m Ralink_5390sta -v 2.5.0.3 --all
sudo rm -r /var/lib/dkms/Ralink_5390sta/2.5.0.3 
sudo rm /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -v rt2800pci
```




 ***sudo dkms build -m Ralink_5390sta -v 2.5.0.3 : ***Output:

```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -C src/ all.........(bad exit status: 2)
**ERROR** (dkms apport): binary package for Ralink_5390sta: 2.5.0.3 not found
**Error**! Bad return status for module build on kernel: 4.16.17-041617-generic (x86_64)
Consult /var/lib/dkms/Ralink_5390sta/2.5.0.3/build/make.log for more information.

```

I tried also,
[https://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](https://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

still no wifi adaptor found...

---

### Post by jeremy31 on 2018-06-24
What happens when you ```
sudo modprobe -v rt2800pci
```
Also post results for ```
dmesg | tail -15
```

---

### Post by mrboler on 2018-06-24
> **jeremy31 said:**
> What happens when you ```
sudo modprobe -v rt2800pci
```
Also post results for ```
dmesg | tail -15
```

sudo modprobe -v rt2800pci
+
dmesg | tail -15

```

**mrboler@PC-Ubuntu:**~$ *sudo modprobe -v rt2800pci*
[sudo] password for mrboler: 

**mrboler@PC-Ubuntu:**~$* dmesg | tail -15*
[  461.358069] raid6: sse2x2   gen() 16801 MB/s
[  461.406068] raid6: sse2x2   xor() 11318 MB/s
[  461.454069] raid6: sse2x4   gen() 19467 MB/s
[  461.502070] raid6: sse2x4   xor() 11849 MB/s
[  461.550071] raid6: avx2x1   gen() 26679 MB/s
[  461.598071] raid6: avx2x1   xor() 18559 MB/s
[  461.646070] raid6: avx2x2   gen() 33509 MB/s
[  461.694075] raid6: avx2x2   xor() 20554 MB/s
[  461.742038] raid6: avx2x4   gen() 37396 MB/s
[  461.790076] raid6: avx2x4   xor() 21859 MB/s
[  461.790077] raid6: using algorithm avx2x4 gen() 37396 MB/s
[  461.790077] raid6: .... xor() 21859 MB/s, rmw enabled
[  461.790078] raid6: using avx2x2 recovery algorithm
[  461.791020] xor: automatically using best checksumming function   avx       
[  461.804515] Btrfs loaded, crc32c=crc32c-intel

```


Also
```
wget media.cdn.ubuntu-de.org/forum/attachments/08/18/3473742-RT2860STA.dat.tar.gz
sudo mkdir -p /etc/Wireless/RT2860STA
sudo tar xvf 3473742-RT2860STA.dat.tar.gz -C /etc/Wireless/RT2860STA 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo service network-manager stop

sudo modprobe -rfv rt2800pci
```

-->  ```
modprobe: FATAL: Module rt5390sta not found in directory /lib/modules/4.15.0-23-generic
```

---

### Post by jeremy31 on 2018-06-24
Anything for ```
dmesg | grep rt2
```

---

### Post by mrboler on 2018-06-24
Hi,
Thank you but nothing happened.

---

### Post by praseodym on 2018-06-24
Please check
```

dpkg -l linux-* | grep ii
```

---

### Post by mrboler on 2018-06-24
I reinstalled Ubuntu 18.04 again. I only do update-upgrade and update to kernel 4.16.17. I'll never try another internet solution :). I am waiting for your advices. 

So when I tried again with a clean OS.


**dmesg | tail -15 :**
```

[    4.409617] audit: type=1400 audit(1529872585.847:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4486/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=628 comm="apparmor_parser"
[    4.411110] audit: type=1400 audit(1529872585.847:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=634 comm="apparmor_parser"
[    4.411458] audit: type=1400 audit(1529872585.847:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=635 comm="apparmor_parser"
[    4.411460] audit: type=1400 audit(1529872585.847:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc//sanitized_helper" pid=635 comm="apparmor_parser"
[    4.412277] audit: type=1400 audit(1529872585.851:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=627 comm="apparmor_parser"
[    4.805773] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u4: link is not ready
[    4.808131] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    4.882157] r8169 0000:02:00.0 enp2s0: link down
[    4.882237] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    5.438392] nouveau 0000:01:00.0: gr: intr 00000040
[    6.366887] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    6.366961] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    6.367010] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    9.581612] rfkill: input handler disabled
[   11.195441] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
```

**dmesg | grep rt2 :**
```

[    4.198031] rt2800pci 0000:03:00.0: enabling device (0000 -> 0002)
[    4.198177] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[    4.203553] ieee80211 phy0: rt2800_init_eeprom: Error - Invalid RF chipset 0x5314 detected
[    4.203566] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device

```

[B]dpkg -l linux-* | grep ii :
[/B]```

ii  linux-base                                  4.5ubuntu1                  all          Linux image base package
ii  linux-firmware                              1.173.1                     all          Firmware for Linux kernel drivers
ii  linux-generic                               4.15.0.23.25                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-20                     4.15.0-20.21                all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-20-generic             4.15.0-20.21                amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-23                     4.15.0-23.25                all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-23-generic             4.15.0-23.25                amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.16.17-041617                4.16.17-041617.201806201630 all          Header files related to Linux kernel version 4.16.17
ii  linux-headers-4.16.17-041617-generic        4.16.17-041617.201806201630 amd64        Linux kernel headers for version 4.16.17 on 64 bit x86 SMP
ii  linux-headers-generic                       4.15.0.23.25                amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-20-generic               4.15.0-20.21                amd64        Signed kernel image generic
ii  linux-image-4.15.0-23-generic               4.15.0-23.25                amd64        Signed kernel image generic
ii  linux-image-generic                         4.15.0.23.25                amd64        Generic Linux kernel image
ii  linux-image-unsigned-4.16.17-041617-generic 4.16.17-041617.201806201630 amd64        Linux kernel image for version 4.16.17 on 64 bit x86 SMP
ii  linux-modules-4.15.0-20-generic             4.15.0-20.21                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-23-generic             4.15.0-23.25                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.16.17-041617-generic        4.16.17-041617.201806201630 amd64        Linux kernel extra modules for version 4.16.17 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-20-generic       4.15.0-20.21                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-23-generic       4.15.0-23.25                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic                        4.15.0.23.25                amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5        all          base package for ALSA and OSS sound systems
```

Also [B]Wifi-Script :

[http://paste.ubuntu.com/p/DBrCjqzC3K/](http://paste.ubuntu.com/p/DBrCjqzC3K/)
[/B]

---

### Post by jeremy31 on 2018-06-24
I am not sure what that invalid RF chipset error is about, you should file a bug report @ bugs.launchpad.com/ubuntu against package linux and at the kernel.org bug system

---

### Post by mrboler on 2018-06-25
I don't know how can I sen a bug file. Also When do I get a solution ? I think this is a more than a week. I must be harry,

- Alternative solution, a usb wifi adapter, which one of models are good for ubuntu ? with using the desktop.

- I can send  a request for a new(old) laptop form IT. without using the desktop.

---

### Post by jeremy31 on 2018-06-25
Use a TP-Link WN722N 150 mbps version 1, supported by the Linux kernel for some time.

The only way to fix the internal device is by filing bugs reports as I am not that familiar with the source code for Ralink wireless devices

---

