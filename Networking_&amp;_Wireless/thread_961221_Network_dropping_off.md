---
title: "Network dropping off"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by wiggy85 on 2008-10-28
Hi

I have a fileserver running gutsy, which keeps losing network connection.

Approx 10 users connect to it via ssh and approx 15 connect to it via samba. But on a daily basis the server drops off and people get disconnected from it.

I've replaced the network cable and changed ports, but still it goes on.

Does anyone have any ideas what could be causing the problems?

Thanks

---

### Post by wiggy85 on 2008-10-28
I looked at my hardware and found this.

```
*-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 01
                serial: 00:01:6c:11:dc:9f
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.100.124 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=1GB/s

```

The driver is 8168B but the module says r1689, could this be a conflict?

---

### Post by Gainax on 2008-10-28
Anyone?

---

### Post by Gainax on 2008-10-28
This is getting serious now.

I can connect to the internet thorugh my router and my switch using the file server.

Just after 30 mins - an hour I'm kicked off the server when connecting via ssh/samba.

When I'm kicked off, the file server is still connected to the internet fine!

when it goes down, in /var/log/syslog I get the following:

```
Oct 28 16:28:05 bolser-server -- MARK --
```

Doesn't seem to out put anything with no explanation of what's happening.

I found []("http://ubuntuforums.org/showthread.php?t=538448")

Is it worth me doing this?

---

