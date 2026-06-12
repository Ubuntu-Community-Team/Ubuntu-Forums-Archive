---
title: "WiFi not working"
date: 2018-08-07
forum: Networking &amp; Wireless
---

### Post by ravensm on 2018-08-07
Ubuntu GamePack 16.04
New linux user and just installed linux
my ethernet works but not my wifi
i under stand that there is alot of wifi cards with no linux drivers. with that said my two cards are usb netgear a6200 and d-link dwa-171
the dwa 171 usb  sort of works, i can see all the networks in my area, but it wont connect. password goes in.....and the connection process just times out

the a6200 wont show up at all

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 15
       serial: b0:6e:bf:2d:b6:a3
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.0.32 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:19 ioport:d000(size=256) memory:f7104000-f7104fff memory:f7100000-f7103fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:13
       logical name: wlxa0ab1b34332e
       serial: a0:ab:1b:34:33:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au multicast=yes wireless=unassociated

```

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0846:9050 NetGear, Inc. A6200 802.11a/b/g/n/ac Wireless Adapter [Broadcom BCM43526]
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 2001:3314 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

any help would be greatly appreciated

---

### Post by jeremy31 on 2018-08-07
For the netgear adapter try
```
sudo apt install git dkms build-essential
git clone https://github.com/jurobystricky/Netgear-A6210
sudo dkms add ./Netgear-A6210
sudo dkms install netgear-a6210/2.5.0
```
Reboot, if you still have issues see the wireless script link in my signature and post results

---

### Post by ravensm on 2018-08-07
> raven@raven-machine:/$ sudo dkms install netgear-a6210/2.5.0

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=4.15.0-30-generic......(bad exit status: 2)
ERROR (dkms apport): binary package for netgear-a6210: 2.5.0 not found
Error! Bad return status for module build on kernel: 4.15.0-30-generic (x86_64)
Consult /var/lib/dkms/netgear-a6210/2.5.0/build/make.log for more information.



looks like thats fora different kernel

what should i do?

---

### Post by jeremy31 on 2018-08-07
See the wireless script link in my signature and post results as we might be able to fix the other wifi

---

### Post by ravensm on 2018-08-07
[http://paste.ubuntu.com/p/K2s7rT7tPk/](http://paste.ubuntu.com/p/K2s7rT7tPk/)

hows this?

---

### Post by jeremy31 on 2018-08-07
Try ```
echo "options rtl8812au rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8812au.conf
```
Then reboot and see what happens with wifi power management disabled

---

### Post by ravensm on 2018-08-07
[http://paste.ubuntu.com/p/wrmn3xbs3B/](http://paste.ubuntu.com/p/wrmn3xbs3B/)

no luck. i cant see any networks but i 'can' attempt to connect to a hidden network. it still times out though, trys to connect and then cancles

---

### Post by jeremy31 on 2018-08-07
You might have to be close to the wifi router with the Dlink wifi dongle.  I would suggest a TP Link WN722N 150 mbps version 1 as it has an external antenna and is supported by a kernel module

---

### Post by ravensm on 2018-08-07
its right beside me, right now im using a 6 ft either net cord. im thinking of getting a 100 ft cord. 22 dollars on amazon.ca

i tried looking around for that wifi usb card. anything on amazon doesnt say whether it is v 1 or up to v3. how do i tell so i dont buy the wrong one?

---

### Post by jeremy31 on 2018-08-07
I guess you could get an Edimax EW7833UAC as I am using one with source code I got from github.  I can detect my neighbors wifi at about 400 meters

I think there is source code on github for the V2 and possibly V3 versions of the WN722N but I don't remember the USB ID's that they use

---

### Post by ravensm on 2018-08-07
[https://www.amazon.ca/TP-Link-TL-WN722N-Wireless-Adapter-Detachable/dp/B002SZEOLG](https://www.amazon.ca/TP-Link-TL-WN722N-Wireless-Adapter-Detachable/dp/B002SZEOLG)

i think this should work

someone on amazon mentioned that it works with raspberry pi 2 and 3

---

### Post by ravensm on 2018-08-07
[https://www.amazon.ca/Edimax-EW-7833UAC-Dual-Band-Adapter-Supports/dp/B01G51FBF6/ref=sr_1_1?ie=UTF8&qid=1533682592&sr=8-1&keywords=edimax+ew-7833uac&dpID=41JaFeQ7l7L&preST=_SY300_QL70_&dpSrc=srch](https://www.amazon.ca/Edimax-EW-7833UAC-Dual-Band-Adapter-Supports/dp/B01G51FBF6/ref=sr_1_1?ie=UTF8&qid=1533682592&sr=8-1&keywords=edimax+ew-7833uac&dpID=41JaFeQ7l7L&preST=_SY300_QL70_&dpSrc=srch)

this one states its compatible with linux systems

[https://www.amazon.ca/TP-Link-TL-WN722N-Wireless-Adapter-Detachable/dp/B002SZEOLG](https://www.amazon.ca/TP-Link-TL-WN722N-Wireless-Adapter-Detachable/dp/B002SZEOLG)
this one has a person stating it works with raspbery bi 2 and 3. so thats promissing to

---

