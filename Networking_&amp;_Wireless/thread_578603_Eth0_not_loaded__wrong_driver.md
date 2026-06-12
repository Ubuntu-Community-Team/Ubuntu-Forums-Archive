---
title: "Eth0 not loaded : wrong driver"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by littlebigman on 2007-10-17
Hello

I'm new to Ubuntu/Debian, so don't know where to look to solve this one.

Here's what I did:
1. Installed Ubuntu Server 7.04 on a newer AMD-based PC with an embedded Ethernet port on the motherboard
2. Moved the hard-disk on an older AMD-based PC with a PCI network card
3. When I boot up, Ubuntu fails loading the right driver, so I have no network.

Here's some error messages I wrote down (failed loading a USB key too):

dmesg
```

8139cp : This is not an 8139C+ compatible chip. Try 8139too instead
8139too : 8139too Fast Ethernet 0.9.28
eth0 : RealTek RTL8139 at someaddress IRQ9
eth0 : Identified 8139 chip type 'RTL-8139A'

```

ifup eth0
```

eth0 : Error while getting interface flags : No such device
There is already a PID file /var/run/dhclient.eth0.pid
SIOCSIFADDR : No such device

```

Deleting /var/run/dhclient.eth0.pid and /var/run/dhclient.pid and rerunning dhclient makes no difference, nor rebooting.

Do I need to recompile the kernel myself? Can I just enable the right driver?

Thanks for any tip

---

### Post by littlebigman on 2007-10-17
FWIW, I get the same error when removing the RealTek card and using an old DLink DE-530+ : It's listed in dmesg and lspci, but no IP configuration is assigned by DHCP.

Seems like a known issue:

[http://www.nabble.com/Networking-problem-in-Ubuntu-Feisty-p13094081.html](http://www.nabble.com/Networking-problem-in-Ubuntu-Feisty-p13094081.html)

---

### Post by littlebigman on 2007-10-17
If someone else has the same issue, here's what happened: Ubuntu saved the NIC's MAC address in /etc/iftab, which kept the DHCP client from using the new card. What a pain.

Edit, reboot (/etc/init.d/networking restart didn't help), and voilà.

More information at [http://stateless.geek.nz/2007/02/01/ubuntu-and-vmware-losing-your-ethernet-device-when-migrating/](http://stateless.geek.nz/2007/02/01/ubuntu-and-vmware-losing-your-ethernet-device-when-migrating/)

---

