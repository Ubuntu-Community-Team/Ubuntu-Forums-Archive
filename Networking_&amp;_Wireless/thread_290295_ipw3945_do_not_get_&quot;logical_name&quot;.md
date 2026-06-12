---
title: "ipw3945 do not get &quot;logical name&quot;"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by deadland on 2006-11-01
Hi there,

I do have the following device:

```
sudo lshw -class network 
Password:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:d8000000-d8000fff irq:169

```

As you can see this device doesn't get a logical name, like my usual network device:

```
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:87:a2:86
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.6.1 duplex=full firmware=N/A ip=192.168.178.23 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:da000000-da003fff ioport:4000-40ff irq:58

```

How I can fix that problem?

Thanks for any help.

My System:
Benq Joybook R55.G21
T2400@1,83GHz
2.6.17-10-generic #2 SMP
Edgy Eft

---

### Post by sonny on 2006-11-03
I have the same problem, the only solution that came to me is to recompile the kernel, I haven't do it because I haven't got the time, once I do it i'll post you my results.

---

### Post by sonny on 2006-11-04
> **deadland said:**
> Hi there,

I do have the following device:

```
sudo lshw -class network 
Password:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:d8000000-d8000fff irq:169

```As you can see this device doesn't get a logical name, like my usual network device:

```
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:87:a2:86
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.6.1 duplex=full firmware=N/A ip=192.168.178.23 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:da000000-da003fff ioport:4000-40ff irq:58

```How I can fix that problem?

Thanks for any help.

My System:
Benq Joybook R55.G21
T2400@1,83GHz
2.6.17-10-generic #2 SMP
Edgy Eft

Ok.. this is how I manage to get my ipw3945 wireless card working:
first make sure you have the following: /sbin/ipw3945d-2.6.17-10-generic binary, if you don't try installing the restricted modules of the kernel, by doing: 
```
sudo apt-get install linux-restricted-modules-2.6.17-10-generic
```after that you need to include the modules into the kernel, open a terminal and type:
```
sudo depmod -ae
sudo modprobe ipw3945
dmesg
ps -C ipw3945d-2.6.17-10-generic
```
Let me know if this work for you.

---

### Post by deadland on 2006-11-07
Hi thanks for this information, I don't recieved a notification, so I don't knew that you responsed. I will try it at home this afternoon.

Thanks for your advice

---

### Post by deadland on 2006-11-08
Well sonny that helped alot. Thanks for your help.

---

