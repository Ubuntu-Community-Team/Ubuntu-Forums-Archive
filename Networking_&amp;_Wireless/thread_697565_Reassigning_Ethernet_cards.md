---
title: "Reassigning Ethernet cards"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by wo_shi_big_stomach on 2008-02-15
Greetings. I am fortunate to have a server with seven (count 'em!) Ethernet cards, and I'm trying 7.10 server on it.

Ubuntu reassigned interface numbers (eth0, eth1, ...) to something different than what I had previously with CentOS. For various reasons it's important that I keep the previous numbering scheme. 

Is it possible to statically bind interfaces to interface numbers in Ubuntu, and if so, how?

many thanks

/wsbs

---

### Post by lloyd_b on 2008-02-15
> **wo_shi_big_stomach said:**
> Greetings. I am fortunate to have a server with seven (count 'em!) Ethernet cards, and I'm trying 7.10 server on it.

Ubuntu reassigned interface numbers (eth0, eth1, ...) to something different than what I had previously with CentOS. For various reasons it's important that I keep the previous numbering scheme. 

Is it possible to statically bind interfaces to interface numbers in Ubuntu, and if so, how?

many thanks

/wsbs

Take a look at the file "/etc/iftab".  This file creates a binding between the MAC address of a network device and the interface number.  

Lloyd B.

---

### Post by The Cog on 2008-02-15
There is no /etc/ifab on my system. But there _is_ this file:
/etc/udev/rules.d/70-persistent-net.rules
and it contains this:```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x165d (tg3)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:11:43:51:b5:e8", NAME="eth0"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0e:35:d3:65:a8", NAME="eth1"

```
After my faulty motherboard was replaced, my ethernet port became eth2, and I had to edit this file to make it eth0 again, so I know this is the right place.

---

### Post by wo_shi_big_stomach on 2008-03-26
Thanks. On Ubuntu 7.10, I too had to edit /etc/udev/rules.d/70-persistent-net.rules to get the interfaces reassigned. 

There were a few more steps than that, actually -- mainly figuring out which NIC was where. In my case it went like this:

1. Run 'ifconfig -a' and copy down all MAC addresses.

2. In my case, I have a Tyan mobo with three interfaces and four Intel gig NICs. I used the Ethernet OUI page to figure out which is which:

[http://standards.ieee.org/regauth/oui/index.shtml](http://standards.ieee.org/regauth/oui/index.shtml)

3. I ran 'lspci' to figure out which PCI slots had gig cards:

# lspci | grep -i intel
01:01.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
02:02.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
02:03.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
03:04.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)

4. Using the PCI assignments, I looked through dmesg to relate MAC addresses to PCI slots. For example:

# dmesg | grep 01:01.0

[  105.588139] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 29 (level, low) -> IRQ 29
[  105.867063] e1000: 0000:01:01.0: e1000_probe: (PCI:66MHz:32-bit) 00:0e:0c:cf:f4:29

5. I edited  /etc/udev/rules.d/70-persistent-net.rules so that the right MAC addresses had the right ethX  assignments.

6. I edited /etc/network/interfaces  so the (newly correct) ethN assignments had the right IP parameters.

7. reboot

8. voila

Thanks again for telling me where to look!

/wsbs

---

