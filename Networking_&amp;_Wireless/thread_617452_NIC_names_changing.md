---
title: "NIC names changing"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by secureboot on 2007-11-19
Everything below is running gutsy.

I've had trouble recently with my nics being renamed across reboots.

On my dell poweredge 6850 server, my nic was installed at eth1.  When I rebooted some time later, it became eth2.

VMs have been even worse - when I restart VMs, they often increment - so eth0 becomes eth1 on next reboot, then eth2, and is now eth3.

What could be causing this, and is there any way to stop it? 

I've observed the same behavior on other machines as well... but usually only one increment (installed eth0 becomes eth1)

---

### Post by noob12 on 2007-11-19
In each of the hosts/virtual hosts where the interface numbers are changing you need to check the file [B]/etc/udev/rules.d/70-persistent-net.rules[/code] and make sure the rules are referring to attributes that are actually persistent for your devices and assign the name that you want.

The specifics are going to vary on a case-by-case basis.

First make sure the physical host OS is doing stable name assignments and using the names you want, then move to  the VMs.

---

### Post by secureboot on 2007-11-20
This seems to solve my problem - I knew something like this had to exist, I just didn't know where.

Thanks - I can simply assign the right mac address to the right interface name, and I'm good to go.

---

