---
title: "Toshiba Portege R500 - Wifi not working"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by erictlee on 2007-10-04
**This issue has now been resolved - thank you all!**

Any ideas on what I need to do?  Thanks very much.

---

### Post by Lambert on 2007-10-04
> **erictlee said:**
> Any ideas on what I need to do?  Thanks very much.

You will get help but more detail is needed. You can also search wiki.ubuntu.com and type wifidocs in the search box.

Post anything and everything you've checked or done and what it is you see? I don't use kubuntu but believe it's kwifi that manage's wireles.. Do you see the wireless device when you open up that program?

What's your experience with the command line / linux?

Open up a terminal window (konsole I believe) and type in this command.

```

sudo lshw -C network

```

Post the output from that here.

---

### Post by erictlee on 2007-10-07
Here's the output of that command - does this help?

Thanks.

 *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 00
       serial: 00:15:b7:99:37:ef
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.7 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ff9e0000-ff9fffff ioport:bfe0-bfff irq:21
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:ff8fe000-ff8fffff irq:11

---

### Post by erictlee on 2007-10-07
ericlee@ericlee-laptop:~$ sudo pccardctl ident
Socket 0:
  no product info available

---

### Post by erictlee on 2007-10-07
Intel 4965AGN - details here:

[http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm](http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm)

---

### Post by Lambert on 2007-10-07
See this tutorial.

[http://ubuntuforums.org/showthread.php?t=493095&highlight=4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=4965)

---

### Post by erictlee on 2007-10-07
The problem was solved by installed Gutsy - Ubuntu 7.10.

---

