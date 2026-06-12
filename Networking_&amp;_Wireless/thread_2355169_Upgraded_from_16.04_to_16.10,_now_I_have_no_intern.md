---
title: "Upgraded from 16.04 to 16.10, now I have no internet"
date: 2017-03-09
forum: Networking &amp; Wireless
---

### Post by jlee87 on 2017-03-09
Like the title says, I upgraded now my internet doesn't work it is a wired connection when I pull up my network setting it says wired followed by not moderated. 
When I ran lshw -c network I get 

```
*-network DISABLED
   description: Ethernet interface
   product: Ethernet Connection (2) I219-V
   vendor: Intel Corporation
   physical id: 1f.6
   bus info: pci@0000:00:1f.6
   logical name: enp0s31f6
   version: 31
   serial: 70:8b:cd:58:02:2a
   capacity: 1Gbit/s
   width: 32 bits
   clock: 33MHz
   capabilities: pm msi bus_master cap_list ethernet physical tp 10t 10bt-f d 100bt 100bt-fd 1000t-fd autonegotiation
   configuration: autonegotiaotion=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.7-4 latency=0 link=no multicast=yes port=twisted pair 
   resources: irq:131 memory:df20000-df21ffff
  
```

---

### Post by bkline on 2017-03-10
Same thing happened to me. I was forced to upgrade from the LTS 16.04 when the Python paramiko package started spamming my cron job messages with "future" warnings, and I wasn't able to upgrade paramiko without upgrading Ubuntu. I'm a little surprised that I'm not seeing more discussion of the problem on the forums, but maybe it's limited to wired connections, and the numbers of users who aren't using wireless connections is dwindling rapidly.

Anyway, I solved the problem by editing /etc/network/interfaces as root, adding

auto eth0
iface eth0 inet dhcp

and rebooting. Same problem hit two different boxes after the 16.04 -> 16.10 upgrade. Same solution worked for both. As I say, I haven't yet come across the explanation for why the upgrade killed the ethernet connection. Would be delighted if anyone who knows could shed some light on the problem.

Hope this helps.

---

