---
title: "Unclaimed Wireless 7265"
date: 2018-05-01
forum: Networking &amp; Wireless
---

### Post by rm2889 on 2018-05-01
I recently installed updated kernel headers   

sudo apt-get install linux-headers-$(uname -r)

  sudo apt autoremove

  
Upon restarting, I've lost my wifi and sound input and ouput. It seems to be driver issue, since when I run:  

sudo lshw -class network

         
                                       I recently installed updated kernel headers 
  sudo apt-get install linux-headers-$(uname -r)
  sudo apt autoremove
  Upon restarting, I've lost my wifi and sound input and ouput. It seems to be driver issue, since when I run:  sudo lshw -class network
  ```
Output:
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (3) I218-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 03
       serial: 20:47:47:c5:93:90
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.2-3 ip=200.200.200.142 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:46 memory:f7200000-f721ffff memory:f7243000-f7243fff ioport:f080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7000000-f7001fff
```


I copied over the wifi driver from intel's website ([https://www.intel.co.za/content/www/za/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.co.za/content/www/za/en/support/articles/000005511/network-and-i-o/wireless-networking.html)) over to my firmware folder, but not sure what to do after that.

---

### Post by jeremy31 on 2018-05-02
Post results for ```
dpkg -l | grep linux-image
```

---

### Post by rm2889 on 2018-05-03
```
rc  linux-image-4.10.0-28-generic               4.10.0-28.32~16.04.2                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-38-generic               4.10.0-38.42~16.04.1                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-40-generic               4.10.0-40.44~16.04.1                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-42-generic               4.10.0-42.46~16.04.1                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-26-generic               4.13.0-26.29~16.04.2                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-32-generic               4.13.0-32.35~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-36-generic               4.13.0-36.40~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-37-generic               4.13.0-37.42~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-38-generic               4.13.0-38.43~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-39-generic               4.13.0-39.44~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-28-generic         4.10.0-28.32~16.04.2                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-38-generic         4.10.0-38.42~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-40-generic         4.10.0-40.44~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-42-generic         4.10.0-42.46~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-26-generic         4.13.0-26.29~16.04.2                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-32-generic         4.13.0-32.35~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-36-generic         4.13.0-36.40~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-37-generic         4.13.0-37.42~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-38-generic         4.13.0-38.43~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-39-generic         4.13.0-39.44~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
```

---

### Post by jeremy31 on 2018-05-03
See the wireless script link in my signature and post results

---

### Post by rm2889 on 2018-05-03
```
########## wireless info START ##########

Report from: 04 May 2018 08:39 IST +0530

Booted last: 04 May 2018 00:00 IST +0530

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.4 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.13.0-39-generic #44~16.04.1-Ubuntu SMP Thu Apr 5 16:43:10 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

lspci: Unable to load libkmod resources: error -12

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-LM [8086:15a2] (rev 03)
	DeviceName:  Onboard LAN
	Subsystem: Dell Ethernet Connection (3) I218-LM [1028:062e]

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5410]

##### lsusb #############################

Bus 001 Device 004: ID 0c45:6709 Microdia 
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 002: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wmi                    24576  0

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:200.200.200.142  Bcast:200.200.200.255  Mask:255.255.255.0
          inet6 addr: fe80::7818:98a7:230a:14f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3143 errors:0 dropped:48 overruns:0 frame:0
          TX packets:2438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2407248 (2.4 MB)  TX bytes:267000 (267.0 KB)
          Interrupt:20 Memory:f7200000-f7220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35862 (35.8 KB)  TX bytes:35862 (35.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         200.200.200.100 0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
200.200.200.0   0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       747     1  0 08:37 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (3) I218-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-3
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       414659b7-3c03-3a8c-9235-f565c23af0be
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{11}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   414659b7-3c03-3a8c-9235-f565c23af0be | Wired connection 1
IP4.ADDRESS[1]:                         200.200.200.142/24
IP4.GATEWAY:                            200.200.200.100
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP6.ADDRESS[1]:                         fe80::7818:98a7:230a:14f3/64
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

[[/etc/NetworkManager/system-connections/acc]] (600 root)
[connection] id=acc | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=acc
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AD]] (600 root)
[connection] id=AD | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AD
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEARRR]] (600 root)
[connection] id=NETGEARR | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEARR
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/tuam]] (600 root)
[connection] id=tuam | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=tuam
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/XT]] (600 root)
[connection] id=XT | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=XT
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone]] (600 root)
[connection] id=iPhone | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iPhone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/li]] (600 root)
[connection] id=li | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=li
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Shark Virus]] (600 root)
[connection] id=Shark Virus | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Shark Virus
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/M2]] (600 root)
[connection] id=M2 | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=M2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Bri]] (600 root)
[connection] id=Bri | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Bri
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR92]] (600 root)
[connection] id=NETGEAR92 | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR92
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TKG]] (600 root)
[connection] id=TKG | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TKG
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_w3]] (600 root)
[connection] id=_w3 | type=wifi | permissions=user:rm:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=_w3
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    1.273322] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) <MAC 'eno1' [IF1]>
[    1.273324] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.273353] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    1.273939] e1000e 0000:00:19.0 eno1: renamed from eth0
[    3.082156] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[    8.924566] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[    8.924595] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

########## wireless info END ############
```

---

