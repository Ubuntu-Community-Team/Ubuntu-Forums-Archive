---
title: "Ubuntu 14.04 and Realtek Ethernet"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by thehappiestturtle on 2015-12-01
Hello

I have a server running Ubuntu 14.04. We use it as an FTP server and it is critical to our operation. When we first set it up, we had trouble with the built in Ethernet adapter but this somehow self resolved. Well we just moved it from one location to another and the problem has resurfaced. I am using a Gigabyte GA-990FXA-UD3 motherboard, which uses realtek ethernet. When I plug the ethernet cable in I have internet for exactly 10 seconds before it disconnects.  If I click on the networking Icon and then click on Ethernet1, it works again for exactly 10 seconds.  I have repeated this multiple times.  Always after 10 pings the connection fails.  

I have been browsing online and cannot seem to find an answer.  This seems to be an issue directly related to Realtek and 14.04. Can anyone provide some insight? 

Thank you,

---

### Post by Bucky Ball on 2015-12-01
Can you run:

```
sudo lshw -C network
```

... and post the output here, please. This will give some basic info about your connection(s). If you are so inclined, run the wirelessinfo script in my signature. That will give a whole lot more detail. Please use code tags when posting output. See the last link in my signature. Thanks.

---

### Post by thehappiestturtle on 2015-12-01
Thank you, I am at home now but plan to return to the server at around 5am CST tomorrow. I will post the info requested then. 

Thank you,

---

### Post by thehappiestturtle on 2015-12-01
Here is the output 

**Sudo lshw -C network**

```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: fc:aa:14:90:64:48
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.040.00-NAPI duplex=full ip=192.168.2.240 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:73 ioport:b000(size=256) memory:fe600000-fe600fff memory:d0000000-d0003fff
global@GB-UBNT-SERVER:~$ 


```

---

### Post by Bucky Ball on 2015-12-01
Perhaps now the wirelessinfo script output and see what we see and if someone gives a yelp. Link in my signature. ;)

---

