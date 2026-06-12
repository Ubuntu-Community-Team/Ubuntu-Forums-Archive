---
title: "Ubuntu doesn't detect my wireless card"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-11
Ubuntu 9.10 doesn't detect my wireless card. It used to work splendidly in 9.04. I have the HP Compaq 6720s laptop. Any ideas?

---

### Post by northern lights on 2009-12-11
Can you please post the outputs of```
sudo lshw -C network
```and```
iwconfig
```

Thanks.

---

### Post by rkakkar on 2009-12-11
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:29:9d:c0:88
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-2 ip=172.22.36.26 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:e4600000-e461ffff memory:e4620000-e4620fff ioport:4020(size=32)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:e4000000-e4003fff

```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by northern lights on 2009-12-11
Aight.

Your system recognizes the card and it's driver is assigned.Weird enough it's missing a logical name. Are you sure you haven't just manually disabled it? (Check the network-manager icon in the gnome panel)

If it is not disabled, please post the output of```
sudo pccardctl ident
```



P.S. this is your wireless device:>   *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:e4000000-e4003fffand here it should appear as *wlan0*:> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by rkakkar on 2009-12-11
oh cool!

nah i haven't touched it ... usually in 9.04, ubuntu assigns "auto etho0" and auto wireless (something) by default ... however here it configured the "auto etho0" profile automatically, but no profiles are configured under the wireless section.

if i could get the MAC address of my wireless card somehow .. i think i could create a wifi profile..

btw the command you gave posted nothing as the output.

---

### Post by fooman on 2009-12-11
if you are not already hooked up....plug in the ethernet connection,  open a terminal and run this:

```
 sudo apt-get --reinstall install bcmwl-kernel-source                      
```not sure,  but you may have to reboot afterwards.

see if that helps.

---

### Post by rkakkar on 2009-12-11
is there any way i can get the MAC address of my wireless card?

---

### Post by fooman on 2009-12-11
sure,  in a terminal:

```
ifconfig
```

then look for the "HWaddr" of the wlan card.

---

### Post by rkakkar on 2009-12-12
> **fooman said:**
> if you are not already hooked up....plug in the ethernet connection,  open a terminal and run this:

```
 sudo apt-get --reinstall install bcmwl-kernel-source                      
```not sure,  but you may have to reboot afterwards.

see if that helps.

this worked!! thanks!

---

### Post by rkakkar on 2009-12-12
> **fooman said:**
> if you are not already hooked up....plug in the ethernet connection,  open a terminal and run this:

```
 sudo apt-get --reinstall install bcmwl-kernel-source                      
```not sure,  but you may have to reboot afterwards.

see if that helps.

this worked!! thanks!

---

### Post by humanracer on 2013-02-23
> **fooman said:**
> if you are not already hooked up....plug in the ethernet connection,  open a terminal and run this:

```
 sudo apt-get --reinstall install bcmwl-kernel-source                      
```not sure,  but you may have to reboot afterwards.

see if that helps.

I had a similar issue (no wireless on Compaq mini 110c ). this worked!!! thanks

---

### Post by matt_symes on 2013-02-23
Old thread. Closed

---

