---
title: "Intel NUC ethernet stop working"
date: 2018-09-17
forum: Networking &amp; Wireless
---

### Post by rob0214 on 2018-09-17
Hi all,

I put Ubuntu on a 7th generation Intel NUC (NUC7i7BNH).  Started with 16.04 and everything was fine until last week or so.  Then the wired ethernet stopped working (wireless is fine).

dmesg shows the following:

[    5.713374] e1000e 0000:00:1f.6: enabling device (0000 -> 0002)
[    5.713559] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    6.732187] e1000e: probe of 0000:00:1f.6 failed with error -2

After lots of Googling and troubleshooting I've tried the following:
1) upgrading to 18.04
2) disabling wake on lan
3) disabling secure boot
4) downgrading bios to version where it was working
5) using intels updated e1000 drivers

None of these are working.

Anyone else have any ideas/have run into this?  I'm at my wit's end trying to fix this.

Oh, lshw -c network:

  *-network                 
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3a:00.0
       logical name: wlp58s0
       version: 78
       serial: a0:c5:89:fc:71:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-34-generic firmware=34.0.1 ip=10.0.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:131 memory:dc200000-dc201fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Ethernet Connection (4) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       version: 21
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:dc300000-dc31ffff

---

### Post by rob0214 on 2018-09-27
Bump.  Anyone?  Tried asking on Intel support, but they were pretty useless (and directed me back here).

---

