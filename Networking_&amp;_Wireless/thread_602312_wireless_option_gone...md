---
title: "wireless option gone.."
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by terjeloe on 2007-11-04
I installed vpn connection manager(ppp genric), and now the wireless option is gone from the network setup screen.. I tried to uninstall the vpn pack again but still doesnt work.. when I click the network icon up in the right corner there's still a vpn connection option there.. When I do lspci the network device is still there..

---

### Post by terjeloe on 2007-11-04
Heres some aditional info if it helps:

```

t@ubuntu:~$ dmesg | grep pci 
[   16.698995] ACPI: bus type pci registered
[   16.752449] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.316470] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.316531] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.316725] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.316791] Allocate Port Service[0000:00:1c.1:pcie02]
[   19.220000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

```

```
t@ubuntu:~$ lspci | grep Wireless
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

and just something I tried that someone on irc told me to try:
```

t@ubuntu:~$ sudo ifup eth1
[sudo] password for t:
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```

my computer is a fujitsu siemens c1320. I the vpn option is gone now, but still doesnt work..

---

### Post by terjeloe on 2007-11-04
```
t@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by terjeloe on 2007-11-05
Anyone pleas?

---

