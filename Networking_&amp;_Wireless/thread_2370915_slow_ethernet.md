---
title: "slow ethernet"
date: 2017-09-08
forum: Networking &amp; Wireless
---

### Post by p33r on 2017-09-08
Hi
im only getting 30mbit off 100mbit,
internet runs fine in windows 10 and getting 100 there, but thats another computer..
any ideas?

---

### Post by BenginM on 2017-09-09
Hiya, how is the condition of the cable? have you tried with another cable ..! 

which ubuntu version , and in a terminal please run the followin' and paste the result under a CODE tag as follow without the PHP code :
[PHP]
```

$ sudo lshw -C network 

```
[/PHP]

---

### Post by p33r on 2017-09-09
another cable doesnt work... not using second network card either.
i have
xubuntu v 17.04

```

 *-network                 
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 20
       serial: 00:15:f2:cd:3a:2c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:dddfc000-dddfffff ioport:d800(size=256) memory:dddc0000-ddddffff
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 14
       bus info: pci@0000:01:14.0
       logical name: enp1s20
       version: 14
       serial: 00:15:f2:cd:37:0c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full ip=192.168.1.47 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:21 memory:ddcfc000-ddcfffff ioport:c800(size=256) memory:ddcc0000-ddcdffff

```

---

### Post by praseodym on 2017-09-09
There is a network-manager bug in 17.04. Please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service

```

---

### Post by p33r on 2017-09-10
after code it runs up to 100mbit as nothing!,
thank u for the help! :D

---

