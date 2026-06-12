---
title: "Slow speed ethernet I217-V"
date: 2018-12-14
forum: Networking &amp; Wireless
---

### Post by Hesediel on 2018-12-14
Hello i have this ethernet card on my Asrock H87 Fatal1ty

i have a fiber connection of 1 gigabit

so my test speed on windows gives me a 980 Mbps download speed on ubuntu this stops on 80 Mbps like if the card is limited to 100 mbps

whats the problem?
```

ale@ale-desktop:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 04)
        Subsystem: ASRock Incorporation Ethernet Connection I217-V [1849:153b]
        Kernel driver in use: e1000e
        Kernel modules: e1000e
```

```
le@ale-desktop:~$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 04
       serial: bc:5f:f4:c7:75:a6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=half firmware=0.13-4 ip=192.168.1.77 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:26 memory:f0400000-f041ffff memory:f043d000-f043dfff ioport:f080(size=32)
```


i found that this is an intel controller:

 [https://downloadcenter.intel.com/it/product/70831](https://downloadcenter.intel.com/it/product/70831)
[https://downloadcenter.intel.com/it/dow](https://downloadcenter.intel.com/it/dow) ... 2.1.tar.gz


but i dont know how to install the driver. It says to go on src folder and give the make install command but the terminal gives me:
Makefile:100: *** Compiler not found

---

### Post by chili555 on 2018-12-15
Even if you install the compiler package, build-essential, and build the later version of the driver, I don't think this is the cause of your problem. I think this is the cause:> 
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: [COLOR="#FF0000"]autonegotiation=off [/COLOR]broadcast=yes driver=e1000e driverversion=3.2.6-k [COLOR="#FF0000"]duplex=half[/COLOR] firmware=0.13-4 ip=192.168.1.77 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:26 memory:f0400000-f041ffff memory:f043d000-f043dfff ioport:f080(size=32)


Please install ethtool:```
sudo apt install ethtool
```Then run:```
sudo ethtool -s enp0s25 speed 1000 autoneg on duplex full
```Any improvement?

I'd be interested in any clues in the log:```
dmesg | grep e100
```

---

