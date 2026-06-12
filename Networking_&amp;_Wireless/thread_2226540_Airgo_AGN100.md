---
title: "Airgo AGN100"
date: 2014-05-27
forum: Networking &amp; Wireless
---

### Post by Garrett_Ratsoy_ on 2014-05-27
Brand new to lubuntu, I'm used to Ubuntu doing all the driver work and such for me. 

I have literally no idea how to get my wifi working, AT ALL.

It does seem like the device is recognized and there is a drivers, here's some info

PCI (sysfs)  
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AGN100 802.11 a/b/g True MIMO Wireless Card [17CB:1]
       vendor: Airgo Networks, Inc. [17CB]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=24
       resources: memory:ff9e0000-ff9fffff memory:ff900000-ff97ffff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039]
       vendor: Intel Corporation [8086]
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:a1:3f:56
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.133 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:ff9df000-ff9dffff ioport:d400(size=64)
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty
3.13.0-24-generic
02:00.0 Ethernet controller [0200]: Airgo Networks, Inc. AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 03)
        Subsystem: Linksys WMP54GX v1 802.11g Wireless-G PCI Adapter with SRX [1737:0045]
02:01.0 Serial controller [0700]: Lava Computer mfg Inc Lava Dual Serial [1407:0100]
--
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 81)
        Subsystem: Intel Corporation Device [8086:3008]
        Kernel driver in use: e100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    0.121412] NET: Registered protocol family 16
[    0.213545] NET: Registered protocol family 2
[    0.214323] NET: Registered protocol family 1
[    0.215195] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.739981] NET: Registered protocol family 10
[    1.740461] NET: Registered protocol family 17
[    8.560282] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.333105] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.544211] intel_rng: Firmware space is locked read-only. If you can't or
[   10.544211] intel_rng: don't want to disable this in firmware setup, and if
[   12.542940] NET: Registered protocol family 31
[   17.373163] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.377036] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  682.006862] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  702.004274] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
garage@Garage-Desktop:~$ 
garage@Garage-Desktop:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
garage@Garage-Desktop:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
garage@Garage-Desktop:~$ sudo lshw -C network -numeric ; lsb_release -rcd ; uname -r ; lspci -nnk | grep -iA2 net ; lsusb ; rfkill list all ; dmesg | egrep 'error|irmware|NET|wlan'
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AGN100 802.11 a/b/g True MIMO Wireless Card [17CB:1]
       vendor: Airgo Networks, Inc. [17CB]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=24
       resources: memory:ff9e0000-ff9fffff memory:ff900000-ff97ffff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039]
       vendor: Intel Corporation [8086]
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:a1:3f:56
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.133 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:ff9df000-ff9dffff ioport:d400(size=64)
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty
3.13.0-24-generic
02:00.0 Ethernet controller [0200]: Airgo Networks, Inc. AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 03)
        Subsystem: Linksys WMP54GX v1 802.11g Wireless-G PCI Adapter with SRX [1737:0045]
02:01.0 Serial controller [0700]: Lava Computer mfg Inc Lava Dual Serial [1407:0100]
--
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 81)
        Subsystem: Intel Corporation Device [8086:3008]
        Kernel driver in use: e100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    0.121412] NET: Registered protocol family 16
[    0.213545] NET: Registered protocol family 2
[    0.214323] NET: Registered protocol family 1
[    0.215195] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.739981] NET: Registered protocol family 10
[    1.740461] NET: Registered protocol family 17
[    8.560282] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.333105] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.544211] intel_rng: Firmware space is locked read-only. If you can't or
[   10.544211] intel_rng: don't want to disable this in firmware setup, and if
[   12.542940] NET: Registered protocol family 31
[   17.373163] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.377036] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  682.006862] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  702.004274] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


Linksys WMP54GX v1 802.11g Wireless-G PCI Adapter with SRX is the wireless card in the machine, so it seems the OS is seeing the hardware, and I don't see any errors so I assume it does have the firmware, But I CANNOT seem to get any kind of wifi to work. 
It also doesnt help that there doesnt seem to be any way of knowing if the damn card is actually working or no, normally one would scan the area for a network but with lubuntu asfar as I can tell I have to input all the network info manually click save and just assume it'll work.... Well it doesn't.


Soo, to do a little more troubleshooting it appears that rather than broadcom this device is using Airgo Networks true MIMO wireless. Interesting, haven't heard of that one before, maybe it is actually a broadcom, most Cisco products are.
I did find one thread in regards to this card, however it is from 2007 :(

I am running a much more modern router but it is runing with G compabatibility mode on and uses WPA2 encryption (which this card supports)


What do I do?

---

### Post by Garrett_Ratsoy_ on 2014-05-28
Okay, so I made some progress, however, it's a bit like one step forward two steps back.


I downloaded the driver package from some site online for the WMP54GX, using the Netani.inf file included in the driver package I was able to use ndiskwrapper to make a driver for the card.

At this point, I'm sure the device is now working, I can use "iwlist scan" and can see wifi networks around me. Alright so that issue is resolved.


I still cant make any connections, first I got all invovled in wpa_supplicant which turned into a giant mess.... Lots of conflicting information online. That lead to nothing.
So I switched to something easy, I pulled the security off my router and tried:

sudo iwconfig wlan0 essid (my network)

     After I hit this I get no message, a new line appears and then I type in:

dhclient wlan0

Then the cursor goes away, my directory information goes away and I can't execute anymore commands, the terminal essentially becomes useless, no wireless connection gets made and nothing happens.
So I have the card and drivers up but cant get any kind of connection.

Where do I go now? Any information I could post to help people help me? Thanks!

---

