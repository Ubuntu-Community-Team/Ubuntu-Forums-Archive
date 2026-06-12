---
title: "another broadcom victim crying for help."
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by grandpasguitars on 2008-09-29
i have been trying to figure this out for a few days now, i have read into a lot of options, i feel like i understand them for the most part, but i must be doing something wrong. although i did have it working for a little while.
a little info..

```
lspci

05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```
 
```
 sudo lshw -C network

*-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:51:18:93
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:4c:47:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lsmod

b43                   144420  0

```

```
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1a:92:4c:47:6b
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
but
```
sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
```

i had it up and connected last night using b43-fwcutter 11 and version 4.150.10.5 of Broadcom's proprietary driver. but i power on today, and nothing, just like it was before.

i have tried ndiswrapper, and got no results, i must be able to use b43, it has already worked for me, i don't know why it doesn't now.

my dmesg..

```
dmesg

[ 6687.558015] b43-phy0 ERROR: YOUR FIRMWARE IS TOO NEW. Please downgrade your firmware.
[ 6687.558032] b43-phy0 ERROR: Use this firmware tarball: http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
[ 6687.558041] b43-phy0 ERROR: Use this b43-fwcutter tarball: http://bu3sch.de/b43/fwcutter/b43-fwcutter-009.tar.bz2
[ 6687.558050] b43-phy0 ERROR: Read, understand and _do_ what this message says, please.
[ 6701.610836] input: b43-phy0 as /devices/virtual/input/input1020
[ 6701.626327] evdev: no more free evdev devices
[ 6701.626345] input: failed to attach handler evdev to device input1020, error: -23
[ 6701.723224] b43-phy0 ERROR: Microcode not responding
[ 6701.723241] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
```

filling up my console input0-input1020

i have tried installing the firmware from broadcom-wl-4.80 like it tells me, to no avail. i got it working using 4.150, so i see no reason to downgrade.. 

if i remember correctly, while it was working my dmesg was still full of errors.

---

### Post by Ayuthia on 2008-09-29
> **grandpasguitars said:**
> i have been trying to figure this out for a few days now, i have read into a lot of options, i feel like i understand them for the most part, but i must be doing something wrong. although i did have it working for a little while.
a little info..

```
lspci

05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```
 
```
 sudo lshw -C network

*-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:51:18:93
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:4c:47:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lsmod

b43                   144420  0

```

```
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1a:92:4c:47:6b
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
but
```
sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
```

i had it up and connected last night using b43-fwcutter 11 and version 4.150.10.5 of Broadcom's proprietary driver. but i power on today, and nothing, just like it was before.

i have tried ndiswrapper, and got no results, i must be able to use b43, it has already worked for me, i don't know why it doesn't now.

my dmesg..

```
dmesg

[ 6687.558015] b43-phy0 ERROR: YOUR FIRMWARE IS TOO NEW. Please downgrade your firmware.
[ 6687.558032] b43-phy0 ERROR: Use this firmware tarball: http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
[ 6687.558041] b43-phy0 ERROR: Use this b43-fwcutter tarball: http://bu3sch.de/b43/fwcutter/b43-fwcutter-009.tar.bz2
[ 6687.558050] b43-phy0 ERROR: Read, understand and _do_ what this message says, please.
[ 6701.610836] input: b43-phy0 as /devices/virtual/input/input1020
[ 6701.626327] evdev: no more free evdev devices
[ 6701.626345] input: failed to attach handler evdev to device input1020, error: -23
[ 6701.723224] b43-phy0 ERROR: Microcode not responding
[ 6701.723241] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
```

filling up my console input0-input1020

i have tried installing the firmware from broadcom-wl-4.80 like it tells me, to no avail. i got it working using 4.150, so i see no reason to downgrade.. 

if i remember correctly, while it was working my dmesg was still full of errors.

As the message says, you will need to downgrade.  The newer firmware works for kernels 2.6.25 and higher.  From all the installs that I have done with this chipset, the newer firmware does not work.

You might just want to move the /lib/firmware/b43 folder over to your home directory (so that you don't lose the files) and run b43-fwcutter with the older firmware.

---

