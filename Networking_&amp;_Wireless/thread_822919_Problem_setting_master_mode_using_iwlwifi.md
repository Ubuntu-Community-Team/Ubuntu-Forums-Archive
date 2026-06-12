---
title: "Problem setting master mode using iwlwifi"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by brozarg on 2008-06-08
Hi, I have a dell inspiron 1525 notebook and I'm using Ubuntu Hardy 8.04 (x64 edition). I'm trying to set master mode in my wireless card (to turn it into an access point), it's an intel 3945abg (the chipset is ipw3945). According to this article ( [https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode) ) this can be achieved using iwlwifi drivers. I think ubuntu hardy has already this driver (iwlwifi). "sudo lshw -C network" prints:

```
  
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4d:f0:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.0.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:ad:e6:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

But if I try to enable master mode it gives me an error:

```

$ sudo iwconfig eth1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

```

Any ideas?

thx

---

### Post by chili555 on 2008-06-08
The link refers to **ipw3945** and not iwl3945, which you have:> driver=iwl3945Some of the older kernels which may be on your machine, use ipw3945. Please check:```
cat  /boot/grub/menu.lst
```See if an older kernel exists on your machine. Here is a snipped copy of mine:> title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

---snip---

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

---snip---

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

---snip---So, if I wanted to use ipw3945, I could interrupt the boot process at the GRUB countdown with Esc and select, for example, the 2.6.20-x kernel by pressing Enter. If you do not have an older, pre-2.6.24-x kernel, you could certainly install one in Synaptic.

POSTSCRIPT: Sounds good, doesn't it? It's just that it doesn't work.

---

### Post by brozarg on 2008-06-08
> **chili555 said:**
> The link refers to **ipw3945** and not iwl3945...

ipw3945 stands for the name of the driver or the chipset?
Link says:

> 
For ipw2100/ipw2200, unfortunately there is no way to use them as AP, but this can be done for ipw3945 and ipw4965, maybe ipw2915 too, which are pretty good cards anyway, using fully open-source iwlwifi drivers...


I think ipw3945 there refers to the name of the chipset. It says that master mode can be turn on using "iwlwifi" drivers, and iwlwifi drivers for the intel 3945 are "iwl3945", the one i'm currently using.

Anyway, I tried using kernel 2.6.22-14-generic. The driver now shows "ipw3945" but it also fails when setting master mode. Results:

```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4d:f0:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.0.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:ad:e6:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated

```

and...

```

$ sudo iwconfig eth1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

```

---

### Post by brozarg on 2008-06-08
The driver ipw3945 doesn't support master mode.

[http://ipw3945.sourceforge.net/README.ipw3945](http://ipw3945.sourceforge.net/README.ipw3945)

> 
5.3.4. iwconfig mode

See iwconfig man page for general description.  

Current modes supported: Ad-Hoc and Managed (Auto)
Current modes enabled but untested: Monitor
Current modes unsupported: Master, Repeater, Secondary.


---

### Post by brozarg on 2008-06-09
Ok, I'm starting to think that ubuntu help is wrong ([https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)), that iwlwifi drivers for intel 3945 actually doesn't support master mode. Hopefully in the future they will...

Any other help will be greatly appreciated. Thanks!

---

