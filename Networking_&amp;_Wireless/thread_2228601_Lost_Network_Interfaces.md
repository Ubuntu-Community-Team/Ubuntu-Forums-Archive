---
title: "Lost Network Interfaces"
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by Soon_Yew on 2014-06-08
Hi all, any help is appreciated. 

I am running Ubuntu Server 12.04 with Virtualbox installed. It also contains an onboard ethernet (eth0) and a quad port Intel ethernet card (eth1-4). Couple of weeks ago for reasons unknown I lost eth2. But today while clearing up the cabling behind the server and upon reboot I lost all of eth1 to 4. It was working fine just before I shut the server down. I rebooted the system, edited /etc/udev/rules.d/70-persistent-net.rules but I am lost as to why the network card just went blank on me. Below are some of my outputs.

Many thanks in advance.

nano /etc/network/interfaces
```
# The loopback network interfaceauto lo
iface lo inet loopback


# The primary network interface


auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet static
address 0.0.0.0


auto eth2
iface eth2 inet static
address 0.0.0.0


auto eth3
iface eth3 inet static
address 0.0.0.0


auto eth4
iface eth4 inet dhcp
```


ifconfig -a | grep eth
```
eth0      Link encap:Ethernet  HWaddr e4:11:5b:13:85:55



 lshw -C network
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:d8000000-d80fffff memory:d8400000-d8403fff memory:d8600000-d867ffff memory:d8404000-d8423fff memory:d8424000-d8443fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:d8100000-d81fffff memory:d8444000-d8447fff memory:d8448000-d8467fff memory:d8468000-d8487fff
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.2
       bus info: pci@0000:02:00.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:d8200000-d82fffff memory:d8488000-d848bfff memory:d848c000-d84abfff memory:d84ac000-d84cbfff
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.3
       bus info: pci@0000:02:00.3
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:d8300000-d83fffff memory:d84cc000-d84cffff memory:d84d0000-d84effff memory:d84f0000-d850ffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: e4:11:5b:13:85:55
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=5723-v3.35 ip=192.168.2.110 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:fe9f0000-fe9fffff
```


nano /etc/udev/rules.d/70-persistent-net.rules
```
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:06.0/0000:03:00.0 (tg3)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e4:11:5b:13:85:55", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.2 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a0:36:9f:00:65:ca", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.3 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a0:36:9f:00:65:cb", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.1 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a0:36:9f:00:65:c9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a0:36:9f:00:65:c8", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```


I also tried following the instructions on this tread but after reboot it remains the same

[HTML]http://ubuntuforums.org/showthread.php?t=2166562[/HTML]

---

### Post by TheFu on 2014-06-09
Dead hardware?
Try the card in a different system to determine if it is the card, the slot, or something else TBD.

---

### Post by Soon_Yew on 2014-06-09
> **TheFu said:**
> Dead hardware?
Try the card in a different system to determine if it is the card, the slot, or something else TBD.


Any headers that it is pointing you to a dead hardware? Reason being I do not have a spare system lying around to test it. So before I disassemble the system ( the card is located in a quite hard to reach region of the system) to test the card. I can however try to install another OS on another HDD to see if it works but on the same system.

Many thanks.

---

### Post by TheFu on 2014-06-10
Often, HW doesn't die all at once. It has 1 small failure then more and finally dies.
Heck - booting off any other Distro's liveCD should provide this.  Intel PRO/1000 cards are very well supported.

BTW, I've never seen people enter the "address 0.0.0.0" in their config files. Why do that? Please teach.

---

### Post by Soon_Yew on 2014-06-10
> **TheFu said:**
> Often, HW doesn't die all at once. It has 1 small failure then more and finally dies.
Heck - booting off any other Distro's liveCD should provide this.  Intel PRO/1000 cards are very well supported.

BTW, I've never seen people enter the "address 0.0.0.0" in their config files. Why do that? Please teach.


Tested it earlier trying to reinstall Ubuntu Server on a spare HDD using the Intel card. No issues. The installer detected and downloaded files during the installation process. BUT... when the system has been installed I was back to square one with the exact same issue of "unclaimed" network card. Kind of lost since a new install is giving me the same problem. Wondering if it could be because of a recent update which is causing the problem....


Regarding your question as to why I used "address 0.0.0.0" is because I am using those interfaces to virtualise pfsense and I did not want the base OS to be using them or have visibility of those interfaces. From my limited understanding this turns the port to just "listening" and allows me to specify virtualbox/pfsense to manage the incoming traffic and not the base OS.

---

### Post by Hadaka on 2014-06-10
Hi, take a read of this thread,,,see if it will help.
[http://ubuntuforums.org/showthread.php?t=2222374](http://ubuntuforums.org/showthread.php?t=2222374)

---

### Post by TheFu on 2014-06-10
I don't use those address lines on my hostOS for my pfsense VM.

---

### Post by Soon_Yew on 2014-06-15
anyone can help? The network card works perfectly fine in 14.04 new install on the existing setup (installing on a separate HDD)

---

### Post by varunendra on 2014-06-15
Please try -
```
sudo modprobe -v igb
```
Does it return any errors? If yes please post them back. If not, do the ports work?

If the command load the module 'igb' without errors, but the ports still don't work, please post the output of -
```
sudo lshw -numeric -C network
```

---

### Post by Soon_Yew on 2014-06-16
I made a huge mistake over the weekend while trying to solve this problem... i accidentally upgraded to Utopic Unicorn (development branch) #-o

I am going to put this on hold and just try to reinstall the system to 14.04. 

As for the comments

modprobe -v igb
Returned nothing

lshw -numeric -C network
```
lshw -numeric -C network  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0000000-c00fffff memory:c0400000-c0403fff memory:c0600                                                                                                                     000-c067ffff memory:c0404000-c0423fff memory:c0424000-c0443fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0100000-c01fffff memory:c0444000-c0447fff memory:c0448                                                                                                                     000-c0467fff memory:c0468000-c0487fff
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0.2
       bus info: pci@0000:02:00.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0200000-c02fffff memory:c0488000-c048bfff memory:c048c                                                                                                                     000-c04abfff memory:c04ac000-c04cbfff
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0.3
       bus info: pci@0000:02:00.3
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0300000-c03fffff memory:c04cc000-c04cffff memory:c04d0                                                                                                                     000-c04effff memory:c04f0000-c050ffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe [14E4:165B]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: e4:11:5b:13:85:55
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical                                                                                                                      tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=                                                                                                                     3.128 duplex=full firmware=5723-v3.35 ip=192.168.2.110 latency=0 link=yes multic                                                                                                                     ast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:fe9f0000-fe9fffff



```

As mentioned the card is there and port works as it is fully functional to download file while installing new systems and in 14.04 desktop version. Moreover the system is detecting the card.

---

### Post by varunendra on 2014-06-17
> **Soon_Yew said:**
> modprobe -v igb
Returned nothing

Next time, try -
```
sudo modprobe -rv igb
sudo modprobe -v igb
```
..and post back whatever you see on the terminal, along with the outputs of -
```
sudo lshw -numeric -C network
lsmod
```
Run the "lshw..." command _AFTER_ running the 'modprobe' commands suggested above.

---

### Post by Soon_Yew on 2014-06-18
I ran the commands per your instructions in sequence. I would ignore the leaking memory part though... as mentioned i messed up when trying to move from 12.04 to 14.04. It was never there before. 

```
sudo modprobe -rv igbno talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
rmmod igb
rmmod dca

```

```
 sudo modprobe -v igb
insmod /lib/modules/3.8.0-41-generic/kernel/drivers/dca/dca.ko
insmod /lib/modules/3.8.0-41-generic/kernel/drivers/net/igb/igb.ko

```

```
lshw -numeric -C network
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0000000-c00fffff memory:c0400000-c0403fff memory:c0600                                                                                                                     000-c067ffff memory:c0404000-c0423fff memory:c0424000-c0443fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0100000-c01fffff memory:c0444000-c0447fff memory:c0448                                                                                                                     000-c0467fff memory:c0468000-c0487fff
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0.2
       bus info: pci@0000:02:00.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0200000-c02fffff memory:c0488000-c048bfff memory:c048c                                                                                                                     000-c04abfff memory:c04ac000-c04cbfff
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection [8086:1521]
       vendor: Intel Corporation [8086]
       physical id: 0.3
       bus info: pci@0000:02:00.3
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0300000-c03fffff memory:c04cc000-c04cffff memory:c04d0                                                                                                                     000-c04effff memory:c04f0000-c050ffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe [14E4:165B]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: e4:11:5b:13:85:55
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical                                                                                                                      tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=                                                                                                                     3.128 duplex=full firmware=5723-v3.35 ip=192.168.2.110 latency=0 link=yes multic                                                                                                                     ast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:fe9f0000-fe9fffff



```

```
lsmod
Module                  Size  Used by
igb                   179577  0
dca                    15232  1 igb
pci_stub               12622  1
vboxpci                23236  0
vboxnetadp             25670  0
vboxnetflt             27612  0
vboxdrv               339324  4 vboxnetadp,vboxnetflt,vboxpci
xt_hl                  12521  6
ip6t_rt                12558  3
nf_conntrack_ipv6      18387  8
nf_defrag_ipv6         17492  1 nf_conntrack_ipv6
ipt_REJECT             12576  1
xt_comment             12504  2
xt_LOG                 17504  9
xt_multiport           12597  2
xt_limit               12711  12
xt_tcpudp              12603  28
xt_addrtype            12713  4
nf_conntrack_ipv4      14538  8
kvm_amd                60277  0
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_conntrack           12760  16
ip6table_filter        12815  1
kvm                   452238  1 kvm_amd
ip6_tables             27502  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0
nf_nat                 26216  1 nf_nat_ftp
zfs                  1151914  0
nf_conntrack_ftp       13464  1 nf_nat_ftp
nf_conntrack           84199  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
zcommon                47225  1 zfs
iptable_filter         12810  1
znvpair                88641  2 zfs,zcommon
zavl                   15010  1 zfs
zunicode              331225  1 zfs
ip_tables              27473  1 iptable_filter
x_tables               29938  14 ip6table_filter,xt_hl,xt_comment,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,xt_multiport,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype
spl                   172744  5 zfs,zavl,zunicode,zcommon,znvpair
zlib_deflate           27139  1 spl
joydev                 17613  0
microcode              23075  0
amd64_edac_mod         24557  0
k10temp                13173  0
edac_core              62754  2 amd64_edac_mod
edac_mce_amd           23343  1 amd64_edac_mod
sp5100_tco             13870  0
i2c_piix4              13459  0
lp                     17799  0
parport                46562  1 lp
radeon                966875  1
ttm                    88279  1 radeon
drm_kms_helper         49597  1 radeon
drm                   287796  3 ttm,drm_kms_helper,radeon
i2c_algo_bit           13564  1 radeon
shpchp                 37201  0
mac_hid                13253  0
hid_generic            12540  0
usbhid                 47346  0
hid                   105826  2 hid_generic,usbhid
tg3                   166030  0
ptp                    18668  1 tg3
pps_core               14109  1 ptp
ahci                   25879  4
libahci                31636  1 ahci



```

---

### Post by varunendra on 2014-06-19
Please post back the outputs of -
```
modinfo igb
modprobe -c | grep 8086.*1521
```

---

### Post by Soon_Yew on 2014-06-22
> **varunendra said:**
> Please post back the outputs of -
```
modinfo igb
modprobe -c | grep 8086.*1521
```

```
modinfo igb
filename:       /lib/modules/3.8.0-41-generic/kernel/drivers/net/igb/igb.ko
version:        5.1.2
license:        GPL
description:    Intel(R) Gigabit Ethernet Network Driver
author:         Intel Corporation, <e1000-devel@lists.sourceforge.net>
srcversion:     E7A5DDD65A476D0F4BE0882
alias:          pci:v00008086d000010D6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A7sv*sd*bc*sc*i*
alias:          pci:v00008086d000010E8sv*sd*bc*sc*i*
alias:          pci:v00008086d00001526sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E7sv*sd*bc*sc*i*
alias:          pci:v00008086d000010E6sv*sd*bc*sc*i*
alias:          pci:v00008086d00001518sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C9sv*sd*bc*sc*i*
alias:          pci:v00008086d00000440sv*sd*bc*sc*i*
alias:          pci:v00008086d0000043Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000043Asv*sd*bc*sc*i*
alias:          pci:v00008086d00000438sv*sd*bc*sc*i*
alias:          pci:v00008086d00001516sv*sd*bc*sc*i*
alias:          pci:v00008086d00001511sv*sd*bc*sc*i*
alias:          pci:v00008086d00001510sv*sd*bc*sc*i*
alias:          pci:v00008086d00001527sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Esv*sd*bc*sc*i*
alias:          pci:v00008086d00001524sv*sd*bc*sc*i*
alias:          pci:v00008086d00001523sv*sd*bc*sc*i*
alias:          pci:v00008086d00001522sv*sd*bc*sc*i*
alias:          pci:v00008086d00001521sv*sd*bc*sc*i*
alias:          pci:v00008086d00001539sv*sd*bc*sc*i*
alias:          pci:v00008086d0000157Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000157Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00001538sv*sd*bc*sc*i*
alias:          pci:v00008086d00001537sv*sd*bc*sc*i*
alias:          pci:v00008086d00001536sv*sd*bc*sc*i*
alias:          pci:v00008086d00001533sv*sd*bc*sc*i*
alias:          pci:v00008086d00001F45sv*sd*bc*sc*i*
alias:          pci:v00008086d00001F41sv*sd*bc*sc*i*
alias:          pci:v00008086d00001F40sv*sd*bc*sc*i*
depends:        dca
vermagic:       3.8.0-41-generic SMP mod_unload modversions
parm:           InterruptThrottleRate:Maximum interrupts per second, per vector, (max 100000), default 3=adaptive (array of int)
parm:           IntMode:Change Interrupt Mode (0=Legacy, 1=MSI, 2=MSI-X), default 2 (array of int)
parm:           Node:set the starting node to allocate memory on, default -1 (array of int)
parm:           LLIPort:Low Latency Interrupt TCP Port (0-65535), default 0=off (array of int)
parm:           LLIPush:Low Latency Interrupt on TCP Push flag (0,1), default 0=off (array of int)
parm:           LLISize:Low Latency Interrupt on Packet Size (0-1500), default 0=off (array of int)
parm:           RSS:Number of Receive-Side Scaling Descriptor Queues (0-8), default 1, 0=number of cpus (array of int)
parm:           VMDQ:Number of Virtual Machine Device Queues: 0-1 = disable, 2-8 enable, default 0 (array of int)
parm:           max_vfs:Number of Virtual Functions: 0 = disable, 1-7 enable, default 0 (array of int)
parm:           MDD:Malicious Driver Detection (0/1), default 1 = enabled. Only available when max_vfs is greater than 0 (array of int)
parm:           QueuePairs:Enable Tx/Rx queue pairs for interrupt handling (0,1), default 1=on (array of int)
parm:           EEE:Enable/disable on parts that support the feature (array of int)
parm:           DMAC:Disable or set latency for DMA Coalescing ((0=off, 1000-10000(msec), 250, 500 (usec)) (array of int)
parm:           LRO:Large Receive Offload (0,1), default 0=off (array of int)
parm:           debug:Debug level (0=none, ..., 16=all) (int)



```

```
 modprobe -c | grep 8086.*1521
alias pci:v00008086d00001521sv*sd*bc*sc*i* igb
```

Sorry for the slow replies and many thanks! :)

---

### Post by varunendra on 2014-06-23
Interesting! The system has the driver and knows which device(s) it is for, still not loading it when the device is detected!

I am a bit lost now but lets try a few things. First, move (backup) your current 70-persistent-net.rules file -
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules 70-persistent-net.rules.bak
```
..and reboot. Then check if the new file was auto-generated and whether it contains the ethernet entries -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

If this doesn't solve the issue, try rebuilding the module dependency tree and update initramfs -
```
sudo depmod -a
sudo update-initramfs -u
```
Reboot again and see if it helped. If not, I may be out of ideas here.

---

### Post by Soon_Yew on 2014-06-25
> **varunendra said:**
> Interesting! The system has the driver and knows which device(s) it is for, still not loading it when the device is detected!

I am a bit lost now but lets try a few things. First, move (backup) your current 70-persistent-net.rules file -
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules 70-persistent-net.rules.bak
```
..and reboot. Then check if the new file was auto-generated and whether it contains the ethernet entries -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

If this doesn't solve the issue, try rebuilding the module dependency tree and update initramfs -
```
sudo depmod -a
sudo update-initramfs -u
```
Reboot again and see if it helped. If not, I may be out of ideas here.


Haha that doesnt sound good! Anyways

```
cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x14e4:0x165b (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e4:11:5b:13:85:55", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"



```

```
depmod -a
update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.8.0-41-generic



```

Unfortunately it doesnt work :(

```
lshw -C network  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0000000-c00fffff memory:c0400000-c0403fff memory:c0600000-c067ffff memory:c0404000-c0423fff memory:c0424000-c0443fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0100000-c01fffff memory:c0444000-c0447fff memory:c0448000-c0467fff memory:c0468000-c0487fff
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.2
       bus info: pci@0000:02:00.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0200000-c02fffff memory:c0488000-c048bfff memory:c048c000-c04abfff memory:c04ac000-c04cbfff
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: I350 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.3
       bus info: pci@0000:02:00.3
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:c0300000-c03fffff memory:c04cc000-c04cffff memory:c04d0000-c04effff memory:c04f0000-c050ffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: e4:11:5b:13:85:55
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=5723-v3.35 ip=192.168.2.110 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:fe9f0000-fe9fffff



```

I think I will go ahead and try a reinstall of the system this weekend. I tried last weekend using a separate HDD installing 14.04 Server 64 bit and it detected the Network card and downloaded using it. Only problem was the naming of the cards were off. Will try installing using 12.04.4 this weekend instead.

Many thanks for your help! :)

---

### Post by varunendra on 2014-06-26
How about reinstalling just the kernel? The driver is part of it and creation/updation of initramfs and other driver related settings is part of kernel installation. Generation of the udev rules file indicates that udev package itself is functional, and the detection of the card in 'lshw' indicates the PCI slot (and its driver) is also functional. All this points to some craziness in the kernel or the driver.

So I think it may be worth a shot -
```
sudo apt-get clean
sudo apt-get install --reinstall linux-image-$(uname -r)
```
..followed by a reboot.

---

