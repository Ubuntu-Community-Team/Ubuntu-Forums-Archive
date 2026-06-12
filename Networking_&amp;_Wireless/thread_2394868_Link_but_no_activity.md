---
title: "Link but no activity"
date: 2018-06-22
forum: Networking &amp; Wireless
---

### Post by rmcgowen on 2018-06-22
Ubuntu 16.04.4 LTS
w/ 4.4.0-130-generic kernel

I have tried install the realtek r8168 driver but to no avail. I currently have a USB adapter plugged in so I can SSH into the machine.

This is what "lsmod | grep r8" gives me:
```
r8152                  49152  0
mii                    16384  2 r8152,usbnet
```

I only have link light and no activity. Only loopback in the interfaces when running "ifconfig". Unless I of course have my USB eth dongle in

This is also what "sudo lshw -short" gives me with my USB dongle plugged in, its the only detected network device....:
```
H/W path             Device           Class          Description================================================================
                                      system         Default string (Default string)
/0                                    bus            Default string
/0/0                                  memory         64KiB BIOS
/0/30                                 memory         4GiB System Memory
/0/30/0                               memory         DIMM [empty]
/0/30/1                               memory         4GiB SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/30/2                               memory         DIMM [empty]
/0/30/3                               memory         DIMM [empty]
/0/36                                 memory         112KiB L1 cache
/0/37                                 memory         2MiB L2 cache
/0/38                                 processor      Intel(R) Celeron(R) CPU N3350 @ 1.10GHz
/0/100                                bridge         Intel Corporation
/0/100/2                              display        Intel Corporation
/0/100/f                              communication  Intel Corporation
/0/100/12                             storage        Intel Corporation
/0/100/13                             bridge         Intel Corporation
/0/100/13/0                           display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13/0.1                         multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1                           bridge         Intel Corporation
/0/100/13.1/0                         bridge         Pericom Semiconductor
/0/100/13.1/0/1                       bridge         Pericom Semiconductor
/0/100/13.1/0/1/0                     display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/1/0.1                   multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/2                       bridge         Pericom Semiconductor
/0/100/13.1/0/2/0                     display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/2/0.1                   multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/3                       bridge         Pericom Semiconductor
/0/100/13.1/0/3/0                     display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/3/0.1                   multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/4                       bridge         Pericom Semiconductor
/0/100/13.1/0/4/0                     display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/4/0.1                   multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/5                       bridge         Pericom Semiconductor
/0/100/13.1/0/5/0                     display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.1/0/5/0.1                   multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.2                           bridge         Intel Corporation
/0/100/13.2/0                         display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.2/0.1                       multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.3                           bridge         Intel Corporation
/0/100/13.3/0                         display        Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/13.3/0.1                       multimedia     Advanced Micro Devices, Inc. [AMD/ATI]
/0/100/15                             bus            Intel Corporation
/0/100/15/0          usb2             bus            xHCI Host Controller
/0/100/15/0/2        scsi0            storage        ADATA USB Flash Drive
/0/100/15/0/2/0.0.0  /dev/sdb         volume         14GiB Windows FAT volume
/0/100/15/1          usb1             bus            xHCI Host Controller
/0/100/15/1/1                         generic        USB 10/100/1000 LAN
/0/100/15/1/2                         input          USB Keyboard
/0/100/15/1/4                         generic        USB 10/100/1000 LAN
/0/100/1a                             bus            Intel Corporation
/0/100/1f                             bridge         Intel Corporation
/0/100/1f.1                           bus            Broxton SMBus Controller
/0/1                 scsi1            storage
/0/1/0.0.0           /dev/sda         disk           64GB FORESEE 64GB SSD
/0/1/0.0.0/1                          volume         511MiB Windows FAT volume
/0/1/0.0.0/2         /dev/sda2        volume         51GiB EXT4 volume
/0/1/0.0.0/3         /dev/sda3        volume         4015MiB Linux swap volume
/1                   enx00e04c60050b  network        Ethernet interface
```

---

### Post by praseodym on 2018-06-22
Please run the wireless script from the sticky thread and show the outputs here

---

### Post by rmcgowen on 2018-06-22
[https://paste.ubuntu.com/p/msThMJhXP7/]("https://paste.ubuntu.com/p/76ChhwyFXc/")

```
[COLOR=#000000]########## wireless info START ##########[/COLOR]
Report from: 25 Jun 2018 16:45 CST +0800

Booted last: 25 Jun 2018 00:00 CST +0800

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.4 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-130-generic #156-Ubuntu SMP Thu Jun 14 08:53:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, amdgpu.vm_fragment_size=9, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

##### lsusb #############################

Bus 002 Device 002: ID 125f:dc1a A-DATA Technology Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 002: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:10.33.1.20  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::8b7c:1080:1d5f:9795/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1387533 (1.3 MB)  TX bytes:67472 (67.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:6554 (6.5 KB)  TX bytes:6554 (6.5 KB)

##### iwconfig ##########################

enx<IF from MAC [IF1]>  no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.1.1        0.0.0.0         UG    100    0        0 enx<IF from MAC [IF1]>
10.0.0.0        0.0.0.0         255.0.0.0       U     100    0        0 enx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF1]>

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       811     1  0 16:41 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        USB 10/100/1000 LAN
GENERAL.DRIVER:                         r8152
GENERAL.DRIVER-VERSION:                 v1.08.3
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/usb1/1-1/1-1:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       75a5170a-18db-4b4f-b8eb-59a1c803b549
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   75a5170a-18db-4b4f-b8eb-59a1c803b549 | Ethernet connection 1
IP4.ADDRESS[1]:                         10.33.1.20/8
IP4.GATEWAY:                            10.1.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.4.4
IP4.DNS[2]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 10.5.1.1
DHCP4.OPTION[10]:                       expiry = 1529916740
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.33.1.20
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 10.1.1.1
DHCP4.OPTION[19]:                       broadcast_address = 10.255.255.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 8.8.4.4 8.8.8.8
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.0.0.0
DHCP4.OPTION[25]:                       network_number = 10.0.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 10.5.1.1
IP6.ADDRESS[1]:                         fe80::8b7c:1080:1d5f:9795/64
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

##### Netplan config ####################

##### iw reg get ########################

Region: Asia/Chongqing (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enx<IF from MAC [IF1]>  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enx<IF from MAC [IF1]>  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

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
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-radeon.conf]
blacklist radeon

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

[   24.730416] r8152 1-1:1.0 eth0: v1.08.3
[   28.323943] r8152 1-1:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[   28.366249] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF1]>: link is not ready (repeated 2 times)
[   49.443230] r8152 1-1:1.0 enx<IF from MAC [IF1]>: carrier on
[   49.443272] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF1]>: link becomes ready

########## wireless info END ############
```

---

### Post by praseodym on 2018-06-23
First uninstall ndiswrapper

```
sudo apt-get remove --purge ndiswrapper* ndisgtk
```
Reboot

---

### Post by rmcgowen on 2018-06-25
Done. 

Still no connection.

---

### Post by chili555 on 2018-06-25
Please show the result of the terminal commands:```
ping -c3 10.1.1.1
ping -c3 8.8.8.8

```

---

