---
title: "No eth0 after fresh install"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by jeeper08jk on 2016-08-11
Hello, 

Just installed the Ubuntu Xenial, I am unable to bring up my wired internet connection.

Ifconfig returns the loopback and virbr0

LSPCI shows ny Broadcom NetXtreme BCM5721 Gigbit Ethernet PCI Express Rev11 as available

In interfaces i have

auto eth0
 iface eth0 inet static
    address 10.0.0.1
    gateway 10.0.0.254
    netmask 255.255.0.0
    network 10.0.0.0
    broadcast 10.0.0.255


ifconfig eth0  up returns an "error while getting interface flags: No such device.

---

### Post by howefield on 2016-08-11
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by jeeper08jk on 2016-08-11
Appears eth0 is no longer a naming convention ("WHY!"), Doing ip a showed me it was named as enp6s0 for whatever bizarre-o reason.

 Changing my interface config to match that brought the connection up on a reboot. MArking as resolved.

---

### Post by howefield on 2016-08-11
> **jeeper08jk said:**
> Appears eth0 is no longer a naming convention ("WHY!") ....

[Predictable Network Interface Names]("https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/")

---

### Post by QIII on 2016-08-11
New for systemd, these are called Predictable Network Interface Names.  Not "predictable" as in you knowing beforehand what will be assigned, but predictable in that the name is permanently assigned to a particular interface by MAC.

Two NIC cards?  It used to be if you swapped their PCI-e slots, you reversed eth0 and eth1 with unpredictable results depending on how the bios reported them to the OS.

This way there is no renumeration, names are consistent across reboots, you can add or remove hardware, etc.

---

### Post by jeeper08jk on 2016-08-11
(Unforeseen) predictable names! now that I know about it it makes a lot of sense. Thanks for the info, +1

---

