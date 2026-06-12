---
title: "Network card gone missing?"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by Mithrilhall on 2008-01-07
I just installed Xubuntu 7.10.

I have two network cards installed and both worked when booting off of the live cd. Once I installed the OS I only see 1 network card now (eth0). If I put the Live CD back in and boot off of it, both network cards show and are working again.

If I do a ```
sudo ifconfig eth1
``` I get this back:
```

eth1: error fetching interface information: Device not found

```

But if I open /etc/udev/rules.d/70-persistent-net.rules I see there should be two network cards (eth0 and eth1).

P.S.

Neither network card is wireless. This is a desktop computer.

---

### Post by Mithrilhall on 2008-01-07
Output of a lspci.

```

root@MS:/# lspci | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
03:00.0 Ethernet controller: ADMtek NC100 Everywhere Fast Ethernet 10/100 (rev 11)
root@MS:/#

```

---

