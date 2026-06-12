---
title: "Feisty Desktop network interface stops responding"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by baruthegreat on 2007-11-29
I've been having problems with the network interface on a box running Feisty Desktop Edition. The network interface stops responding at what seems to be random lengths of time, from 5 to 30 minutes. When the interface stops responding, System Monitor shows data being received, but no data is sent. Sometimes the box can be made to respond again by pinging another computer, sometimes that doesn't work. It always works after bringing the interface down and back up using ifconfig. dmesg showed an error

```
eth0: no IPV6 routers present
```

Disabling IPV6 eliminated that error, but the problem still remains.

I found what seems to be a somewhat similar problem here:
[http://ubuntuforums.org/showthread.php?t=186430]("http://ubuntuforums.org/showthread.php?t=186430")

but lsmod doesn't show that I have the tulip module running, so that doesn't seem applicable. netstat shows only hpiod, mysqld, sshd, cupsd, and python as the active listening processes.

lshw shows the network hardware as

```
$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 01
       serial: 00:07:e9:6c:4c:c0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=134.173.38.196 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:ff8ff000-ff8fffff ioport:bc00-bc3f irq:19

```

If any more information would help, I can get it for you. Any help would be greatly appreciated.

edit: Just had it stop responding and bringing it down using ifconfig and back up again didn't work. '$ /etc/init.d/networking restart' did, however.

---

