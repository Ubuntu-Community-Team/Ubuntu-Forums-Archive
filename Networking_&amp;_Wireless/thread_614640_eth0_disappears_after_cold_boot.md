---
title: "eth0 disappears after cold boot"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by gutsy_user on 2007-11-16
Hi all,

I am experiencing a problem that drives me desperate: After installing Ubuntu Gutsy on my desktop computer a weird problem with networking occured:

- After a cold start, eth0 is not present

- When I then restart the system (logout -> restart), eth0 shows up and everything works fine. However, the next day when I turn on the computer again, eth0 has disappeared again.

This is very annoying and I haven't been able to resolve the problem so far. I've run dmesg, lsmod and lshw when eth0 was present and when it had disappeared, and it seems that the tg3 module isn't loaded when eth0 is not there. Also, dmesg reports a a disabled memory window but I have no idea what that means.

Any help is greatly appreciated

Pascal


##### dmesg :
##        after cold start, eth0 not_working:

PCI: Bridge: 0000:00:1c.2
   IO window: disabled.
   MEM window: disabled.

NET: Registered protocol family 17

##        dmesg : after restart, eth0 working:

PCI: Bridge: 0000:00:1c.2
   IO window: disabled.
   MEM window: f0200000-f02fffff

 tg3.c:v3.77 (May 31, 2007)
 ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 18 (level, low) -> IRQ 18
 PCI: Setting latency timer of device 0000:07:00.0 to 64
 eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:30:05:97:58:90
 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
 eth0: dma_rwctrl[76180000] dma_mask[64-bit]

 tg3: eth0: Link is up at 100 Mbps, full duplex.
 tg3: eth0: Flow control is on for TX and on for RX.
 Linux agpgart interface v0.102 (c) Dave Jones
 NET: Registered protocol family 17

 NET: Registered protocol family 10
 lo: Disabled Privacy Extensions
 eth0: no IPv6 routers present

##### lsmod : 
##        after cold start, eth0 not_working:

af_packet              24840  0

#           lsmod : after restart, eth0 working:

af_packet              24840  2

ipv6                  273892  10

tg3                   110980  0

##### lshw: 
##        after restart, eth0 working (this section is missing when eth0 is not there)

           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 01
                serial: 00:30:05:97:58:90
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5751-v3.29a ip=129.132.143.65 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

---

