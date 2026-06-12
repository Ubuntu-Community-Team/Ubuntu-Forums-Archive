---
title: "Ethernet problem"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by sammy888 on 2008-10-30
Hi!

I have Ubuntu 8.10 and I have one little problem with the my internet card. With every reboot, card gets a new "name". At first is's name is eth0 then eth1, etc. It's really annoying. Any idea what could be wrong?:confused:

P.S.
I had the same problem in Ubuntu 8.04.1.

---

### Post by cariboo on 2008-10-30
Could you paste the output of:

```
sudo lshw -C network
```

You will have to do this in a terminal. let us see the results in your next post.

Jim

---

### Post by sammy888 on 2008-10-30
[I]sammy@sammy-linux:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:8e:d2:ff:69:c9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/I]

---

### Post by sammy888 on 2008-10-31
This is copied from /etc/udev/rules.d/70-persistent-net.rules. I hope it helps, for solving the problem.:?

[I]
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:3e:a2:dd", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:53:fd:cf", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:0b:99:43", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:43:37:f8", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:c2:ef:74", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"[/I]


----

P.S. Sorry for duble-post.

---

