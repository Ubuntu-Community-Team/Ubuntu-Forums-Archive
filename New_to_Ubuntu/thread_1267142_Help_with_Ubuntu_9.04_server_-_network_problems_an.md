---
title: "Help with Ubuntu 9.04 server - network problems and Iptables config"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by camargo70 on 2009-09-15
Hi,

Few days ago, i configured a new ubuntu 9.04 server into a compaq proliant, but after upgrade packets updates, after restart the machine the network don't start with the system.

and another problem is the iptables config, i apply somes rules, but the restart machines the rules dissapear.

Thanks

---

### Post by cariboo on 2009-09-15
Could you provide use with a bit more information. Did you install a desktop? what is the make model of your network device? Could you paste the output of:

```
sudo lshw -C network
```

in your next post, this command will tell us if your device is detected and the proper driver loaded.

How are you setting your iptables rules?

---

### Post by camargo70 on 2009-09-15
> **cariboo907 said:**
> Could you provide use with a bit more information. Did you install a desktop? what is the make model of your network device? Could you paste the output of:

```
sudo lshw -C network
```in your next post, this command will tell us if your device is detected and the proper driver loaded.

How are you setting your iptables rules?

Hi, the result:

 *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:0b:cd:4f:ad:6c
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10                                                                              bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=                                                                              3.94 duplex=half firmware=5702-v2.24a latency=64 link=yes mingnt=64 module=tg3 m                                                                              ulticast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:05:01.0
       logical name: eth1
       version: 08
       serial: 00:d0:b7:3f:5e:ee
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-f                                                                              d 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion                                                                              =3.5.23-k6-NAPI duplex=full firmware=N/A ip=127.0.0.1 latency=64 link=yes max                                                                              latency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


the ubuntu is a server edition

---

