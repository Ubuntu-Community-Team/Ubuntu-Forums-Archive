---
title: "ethernet UNCLAIMED; wireless works fine"
date: 2017-01-27
forum: Networking &amp; Wireless
---

### Post by rgara on 2017-01-27
Hi,

I just finished a clean install (dual boot) of 16.04 on an MSI GS73VR STEALTH PRO. Everything worked fine, except that I have no wired network (wireless works fine). The network card is a Killer E2500 As far as I can tell, driver support should be part of the kernel:

[http://www.killernetworking.com/driver-downloads/knowledge-base?view=topic&id=2](http://www.killernetworking.com/driver-downloads/knowledge-base?view=topic&id=2)

The card seems to be recognized, but no driver is attached to it. Unsure how to solve ...

```
rich@rich-GS73VR-7RF:~$ lshw 

 *-pci:4
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #14
             vendor: Intel Corporation
             physical id: 1d.5
             bus info: pci@0000:00:1d.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:df400000-df4fffff
           *-network UNCLAIMED
                description: Ethernet controller
                product: Qualcomm Atheros
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:3d:00.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:df400000-df43ffff ioport:d000(size=128)
```

```
rich@rich-GS73VR-7RF:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:52753 (52.7 KB)  TX bytes:52753 (52.7 KB)

wlp62s0   Link encap:Ethernet  HWaddr 9c:b6:d0:18:1d:df  
          inet addr:10.250.250.154  Bcast:10.250.250.255  Mask:255.255.255.0
          inet6 addr: fe80::f467:71d:8a7a:c04f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22225 errors:0 dropped:1 overruns:0 frame:0
          TX packets:16910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22376486 (22.3 MB)  TX bytes:3144105 (3.1 MB)
```


```
rich@rich-GS73VR-7RF:~$ lspci -nnk | grep 0200 -A2
3d:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0b1] (rev 10)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:11ac]
3e:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
```

```
rich@rich-GS73VR-7RF:~$ modinfo alx
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
license:        GPL
description:    Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     80B89D6BA6F4A4F4A917E3C
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E0A1sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E091sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
rich@rich-GS73VR-7RF:~$ 
```

---

### Post by psm321 on 2017-01-27
```
modprobe alx
echo 1969 e0b1 | sudo tee /sys/bus/pci/drivers/alx/new_id
```
I've tested this but not used it extensively.

OR

[http://askubuntu.com/questions/670347/is-there-any-way-to-install-atheros-e2400-drivers](http://askubuntu.com/questions/670347/is-there-any-way-to-install-atheros-e2400-drivers)

(with e0b1 instead of e0a1 and a new name of course)

I haven't tested this second one myself yet, working on it at the very moment and was googling to try to figure out what to call it when I came across your post.  Out of curiosity, how did you determine that it as an E2500?

EDIT: second method tested and also works (brings up an interface at least, haven't used it yet)

---

### Post by rgara on 2017-01-27
You just erased hours of frustration! Your first suggestion worked! I can't tell you how much I appreciate your note. 

I'm dual booting - kept the original Windows OS that came with the laptop. When I boot to Win10, and go to Device manager, the card is listed as "Killer E2500"

Thanks again!

---

