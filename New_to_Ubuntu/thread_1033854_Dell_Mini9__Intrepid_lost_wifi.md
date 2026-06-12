---
title: "Dell Mini9 / Intrepid: lost wifi"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by merriww on 2009-01-07
Doug -- I'm not sure if it is appropriate to jump in too, but I have the exact problem.  My Dell Mini running 8.10 has been working fine for 2 weeks.  Suddenly, both wireless and wired connectivity stopped working.  Regarding the wireless connection, when I run iwlist scan I receive:

lo Interface doesn't support scanning
eth0 Interface doesn't support scanning
pan0 Interface doesn't support scanning

Regarding the wired connection, when I connect the cable to the computer, I receive a message, connection established.  But I can't connect to the Internet.

3 other computers that use the same router work fine.

I'm considering reloading 8.10 but that seems somewhat extreme.  Any thoughts?

Wayne

---

### Post by Crafty Kisses on 2009-01-07
I'm not too sure what could have caused this, maybe a possible update you ran or something? Post the results of the following command:
```
dmesg
```
You might also want to enable the interface manually and scan and see if you get any luck, run the following:
```
sudo ifconfig eth0 up
sudo iwlist eth0 scan
```

---

### Post by merriww on 2009-01-07
Thanks for the help.  I didn't load any updates prior to this problem.  I also verified the bios had the wireless enabled.  I ran both sudo ifconfig eth0 up
sudo iwlist eth0 scan commands.  And received the following:

eth0 Interface doesn't support scanning.

When I run dmesg, the only line that mentions eth0, states r8169: eth0 link down. If you would like the entire output from this command, then I will have to use a memory stick and copy and paste bewteen computers.  Let me know.

Many thanks,

---

### Post by Crafty Kisses on 2009-01-07
Yeah that would be great, if you could also give me the results of these commands:
```
lshw -C network
```
Then here is the last one I want:
```
sudo iwlist eth1 auth
```
Yeah I read that you tried to manually enable the interface, but I wanted to see if you get any different results. :)

---

### Post by merriww on 2009-01-07
Here you go:

wayne@wayne-laptop:~$ sudo iwlist eth0 scan
eth0      Interface doesn't support scanning.

wayne@wayne-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:c9:66:e6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:c0:1b:8c:3e:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

wayne@wayne-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:c9:66:e6
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:c0:1b:8c:3e:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


wayne@wayne-laptop:~$ sudo iwlist eth1 auth
eth1      no authentication information.

wayne@wayne-laptop:~$

---

