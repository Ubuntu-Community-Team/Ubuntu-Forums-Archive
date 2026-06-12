---
title: "Interface number changes"
date: 2005-09-11
forum: Networking &amp; Wireless
---

### Post by mlomker on 2005-09-11
I have wired and wireless interfaces on my laptop, eth0 and eth1.  The problem is that the number keeps switching back and forth depending upon which interface is connected...and that's making configuring everything complicated!

Is the eth0 or eth1 assignment based upon which card comes up first or is there a configuration file where I can nail down what MAC address is which port?  I've never seen this particular problem before, so I'm not sure why it is happening...

---

### Post by mlomker on 2005-09-11
It turns out that you cannot control what eth# gets assigned and that it can vary depending upon what kernel you load.  You can, however, make sure that correct TCP/IP settings get applied when switching kernels by using a script that comes with the ifupdown package (installed by default).

Snippet from /etc/network/interfaces:

```

mapping eth0 eth1
        script /usr/share/doc/ifupdown/examples/get-mac-address.sh
        map 00:12:F0:CC:5D:06 wireless
        map 00:03:0D:33:CC:F0 wired

# The primary network interface
iface wired inet dhcp
        up ifmetric wireless 1
iface wireless inet dhcp
        up ifmetric wireless 1

```

---

### Post by mlomker on 2005-09-11
I finally found it.  You can rename your interfaces to anything that you want by editing /etc/iftab.

---

