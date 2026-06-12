---
title: "WIFI Not Working ! Ubuntu Jammy jellyfish 22.04"
date: 2023-04-07
forum: Networking &amp; Wireless
---

### Post by jiyuu31 on 2023-04-07
Hi, I tried the already solved postings of WIFI related problem but still have not been able to solve mine. Pls help. I'll be posting some info of my device and codes I tried. 
```
########## wireless info START ##########

Report from: 08 Apr 2023 01:44 AWST +0800

Booted last: 08 Apr 2023 00:00 AWST +0800

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy

##### kernel ############################

Linux 5.19.0-38-generic #39~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Mar 17 21:16:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

pcilib: Error reading /sys/bus/pci/devices/0000:00:08.3/label: Operation not permitted

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b852]
    Subsystem: Lenovo Device [17aa:4853]

03:00.0 SD Host controller [0805]: O2 Micro, Inc. SD/MMC Card Reader Controller [1217:8621] (rev 01)

##### lsusb #############################

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 04f2:b78d Chicony Electronics Co., Ltd Integrated Camera
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 2717:ff80 Xiaomi Inc. Mi/Redmi series (RNDIS)
Bus 003 Device 002: ID 1ea7:0064 SHARKOON Technologies GmbH 2.4GHz Wireless rechargeable vertical mouse [More&Better]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0bda:4853 Realtek Semiconductor Corp. Bluetooth Radio
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

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

wmi_bmof               16384  0
ideapad_laptop         36864  0
sparse_keymap          16384  1 ideapad_laptop
platform_profile       16384  1 ideapad_laptop
wmi                    32768  2 wmi_bmof,ideapad_laptop
video                  65536  1 ideapad_laptop

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enx<IF from MAC [IF1]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enx<IF from MAC [IF1]>' [IF1]> brd <MAC address>
    inet 192.168.112.205/24 brd 192.168.112.255 scope global dynamic noprefixroute enx<IF from MAC [IF1]>
       valid_lft 3392sec preferred_lft 3392sec
    inet6 fe80::c01f:b4b:f095:fdb3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enx<IF from MAC [IF1]>  no wireless extensions.

##### route #############################

default via 192.168.112.141 dev enx<IF from MAC [IF1]> proto dhcp metric 100 
169.254.0.0/16 dev enx<IF from MAC [IF1]> scope link metric 1000 
192.168.112.0/24 dev enx<IF from MAC [IF1]> proto kernel scope link src 192.168.112.205 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search .

##### network managers ##################

Installed:

    NetworkManager

Running:

root         656       1  0 01:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Xiaomi Inc.
GENERAL.PRODUCT:                        Mi/Redmi series (RNDIS)
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 5.19.0-38-generic
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:08.1/0000:04:00.4/usb3/3-2/3-2:1.0/net/enx<IF from MAC [IF1]>
GENERAL.PATH:                           pci-0000:04:00.4-usb-0:2:1.0
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b3b554f6-7856-3938-8947-f34a4394d3fe
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.112.205/24
IP4.GATEWAY:                            192.168.112.141
IP4.ROUTE[1]:                           dst = 192.168.112.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 0.0.0.0/0, nh = 192.168.112.141, mt = 100
IP4.DNS[1]:                             192.168.112.141
DHCP4.OPTION[1]:                        broadcast_address = 192.168.112.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 3599
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.112.141
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.112.141
DHCP4.OPTION[5]:                        expiry = 1680892835
DHCP4.OPTION[6]:                        host_name = van
DHCP4.OPTION[7]:                        ip_address = 192.168.112.205
DHCP4.OPTION[8]:                        next_server = 192.168.112.141
DHCP4.OPTION[9]:                        requested_broadcast_address = 1
DHCP4.OPTION[10]:                       requested_domain_name = 1
DHCP4.OPTION[11]:                       requested_domain_name_servers = 1
DHCP4.OPTION[12]:                       requested_domain_search = 1
DHCP4.OPTION[13]:                       requested_host_name = 1
DHCP4.OPTION[14]:                       requested_interface_mtu = 1
DHCP4.OPTION[15]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[16]:                       requested_nis_domain = 1
DHCP4.OPTION[17]:                       requested_nis_servers = 1
DHCP4.OPTION[18]:                       requested_ntp_servers = 1
DHCP4.OPTION[19]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[20]:                       requested_root_path = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       requested_static_routes = 1
DHCP4.OPTION[23]:                       requested_subnet_mask = 1
DHCP4.OPTION[24]:                       requested_time_offset = 1
DHCP4.OPTION[25]:                       requested_wpad = 1
DHCP4.OPTION[26]:                       routers = 192.168.112.141
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::c01f:b4b:f095:fdb3/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b3b554f6-7856-3938-8947-f34a4394d3fe | Wired connection 1

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com./

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

enx<IF from MAC [IF1]>  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enx<IF from MAC [IF1]>  Interface doesn't support scanning.

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

[    3.772760] [drm] Loading DMUB firmware via PSP: version=0x06000800
[    3.794633] [drm] Found VCN firmware Version ENC: 1.21 DEC: 2 VEP: 0 Revision: 10
[  102.120543] rndis_host 3-2:1.0 enx<IF from MAC [IF1]>: renamed from usb0

########## wireless info END ############
```

---

### Post by jiyuu31 on 2023-04-07
```
van@van:~$ lspci -vvnn | grep Network
pcilib: Error reading /sys/bus/pci/devices/0000:00:08.3/label: Operation not permitted
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b852]
van@van:~$ lspci -vvnn | grep Network
pcilib: Error reading /sys/bus/pci/devices/0000:00:08.3/label: Operation not permitted
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b852]
```

---

### Post by jiyuu31 on 2023-04-07
```
van@van:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14b5 (rev 02)
    Subsystem: Lenovo Device 3813
    Flags: fast devsel

00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 14b6
    Subsystem: Lenovo Device 3811
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Capabilities: <access denied>

00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14b7 (rev 02)
    Flags: fast devsel, IOMMU group 0

00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14b7 (rev 02)
    Flags: fast devsel, IOMMU group 1

00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14ba (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 33, IOMMU group 2
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: c0700000-c07fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14ba (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 34, IOMMU group 3
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff [size=4K]
    Memory behind bridge: c0600000-c06fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14ba (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 35, IOMMU group 4
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: c0500000-c05fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14b7 (rev 02)
    Flags: fast devsel, IOMMU group 5

00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14b9 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 36, IOMMU group 6
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff [size=4K]
    Memory behind bridge: c0100000-c04fffff [size=4M]
    Prefetchable memory behind bridge: 0000007ce0000000-0000007cf01fffff [size=258M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:08.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14b9 (prog-if 00 [Normal decode])
pcilib: Error reading /sys/bus/pci/devices/0000:00:08.3/label: Operation not permitted
    Flags: bus master, fast devsel, latency 0, IRQ 37, IOMMU group 7
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: c0000000-c00fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 71)
    Subsystem: Lenovo FCH SMBus Controller
    Flags: 66MHz, medium devsel, IOMMU group 8
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
    Subsystem: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0, IOMMU group 8

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1724
    Flags: fast devsel, IOMMU group 9

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1725
    Flags: fast devsel, IOMMU group 9

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1726
    Flags: fast devsel, IOMMU group 9

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1727
    Flags: fast devsel, IOMMU group 9

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1728
    Flags: fast devsel, IOMMU group 9

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1729
    Flags: fast devsel, IOMMU group 9

00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 172a
    Flags: fast devsel, IOMMU group 9

00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 172b
    Flags: fast devsel, IOMMU group 9

01:00.0 Non-Volatile memory controller: Micron Technology Inc Device 5413 (rev 03) (prog-if 02 [NVM Express])
    Subsystem: Micron Technology Inc Device 1100
    Flags: bus master, fast devsel, latency 0, IRQ 66, NUMA node 0, IOMMU group 10
    Memory at c0700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: nvme
    Kernel modules: nvme

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b852
    Subsystem: Lenovo Device 4853
    Flags: fast devsel, IRQ 255, IOMMU group 11
    I/O ports at 2000 [disabled] [size=256]
    Memory at c0600000 (64-bit, non-prefetchable) [disabled] [size=1M]
    Capabilities: <access denied>

03:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01) (prog-if 01)
    DeviceName: Realtek
    Subsystem: O2 Micro, Inc. SD/MMC Card Reader Controller
    Flags: bus master, fast devsel, latency 0, IRQ 69, IOMMU group 12
    Memory at c0501000 (32-bit, non-prefetchable) [size=4K]
    Memory at c0500000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 1506 (rev c2) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 380e
    Flags: bus master, fast devsel, latency 0, IRQ 48, IOMMU group 13
    Memory at 7ce0000000 (64-bit, prefetchable) [size=256M]
    Memory at 7cf0000000 (64-bit, prefetchable) [size=2M]
    I/O ports at 1000 [size=256]
    Memory at c0400000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

04:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1640
    Subsystem: Lenovo Device 3812
    Flags: bus master, fast devsel, latency 0, IRQ 89, IOMMU group 14
    Memory at c04c8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

04:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] VanGogh PSP/CCP
    Subsystem: Lenovo VanGogh PSP/CCP
    Flags: bus master, fast devsel, latency 0, IRQ 24, IOMMU group 15
    Memory at c0300000 (32-bit, non-prefetchable) [size=1M]
    Memory at c04cc000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ccp
    Kernel modules: ccp

04:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 1503 (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 3809
    Flags: bus master, fast devsel, latency 0, IRQ 39, IOMMU group 16
    Memory at c0100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

04:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 1504 (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 380a
    Flags: bus master, fast devsel, latency 0, IRQ 48, IOMMU group 17
    Memory at c0200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

04:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 6f)
    Subsystem: Lenovo Raven/Raven2/FireFlight/Renoir Audio Processor
    Flags: bus master, fast devsel, latency 0, IRQ 88, IOMMU group 18
    Memory at c0480000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: snd_pci_acp6x
    Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x, snd_acp_pci, snd_pci_ps, snd_sof_amd_renoir

04:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
    Subsystem: Lenovo Family 17h (Models 10h-1fh) HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 90, IOMMU group 19
    Memory at c04c0000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

05:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 1505 (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 380b
    Flags: bus master, fast devsel, latency 0, IRQ 57, IOMMU group 20
    Memory at c0000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
```

---

### Post by coffeecat on 2023-04-07
@jiyuu31, I've added BBCode code tags to your various terminal and script outputs. See how that restores the columnar formatting which was lost when you posted them as plain text. Without code tags, terminal output, etc, is near-unreadable. There is a link in my sig for the use of code tags if you need it.

---

### Post by jiyuu31 on 2023-04-07
> **coffeecat said:**
> @jiyuu31, I've added BBCode code tags to your various terminal and script outputs. See how that restores the columnar formatting which was lost when you posted them as plain text. Without code tags, terminal output, etc, is near-unreadable. There is a link in my sig for the use of code tags if you need it.

my bad. Thanks for the fix.

---

### Post by jiyuu31 on 2023-04-07
okay I got it now, This link helped me and got the instructions

---

### Post by chili555 on 2023-04-07
> Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b852]
    Subsystem: Lenovo Device [17aa:4853]The method to install the wireless driver is outlined here: [https://askubuntu.com/questions/1412219/how-to-solve-no-wi-fi-adapter-found-error-with-realtek-rtl8852be-wifi-6-802-11/1412264#1412264](https://askubuntu.com/questions/1412219/how-to-solve-no-wi-fi-adapter-found-error-with-realtek-rtl8852be-wifi-6-802-11/1412264#1412264)

---

