---
title: "Intel PRO/Wireless 3945ABG not detected"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by Nikusan on 2007-06-02
Hi all,

I've got intel pro wireless as the title suggests. The Restricted Driver Manager has installed drivers for it, but it does not show up as an interface in the network applet.

Here's the output of lspci:
```

dan@starbuck:~$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Help? :(

---

### Post by chili555 on 2007-06-02
What does:```
sudo cat /var/log/messages | grep -i Kill
```tell us?

---

### Post by harty83 on 2007-06-02
Make sure the module is loaded.

```
lsmod | grep 'ipw3945'
```

If not then load it
```
sudo modprobe ipw3945
```

---

### Post by zachflanders on 2007-06-03
I am having the same problem. 

when i run: 

sudo lshw -C network 

it returns:

*-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d6000000-d6000fff irq:17
 *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:af:71:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.67.231 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d8000000-d8000fff ioport:4000-403f irq:21


There are a few threads out there on this, but I haven't been able to get anything to work yet.  Any suggestions?

---

