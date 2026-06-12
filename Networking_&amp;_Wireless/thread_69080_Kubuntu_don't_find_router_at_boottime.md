---
title: "Kubuntu don't find router at boottime"
date: 2005-09-25
forum: Networking &amp; Wireless
---

### Post by jafro on 2005-09-25
I installed Kubuntu 5.04 on my laptop without a glitch, but after a while I found that my wlan-card was not supported. I tried to set it up using the Control Center, but experienced an ugly hang. Now my computer won't find my network after reboot. 

I have to type 'route add default gw 10.0.0.1' to get Internet to work.

How to set things to work at boot-time?

---

### Post by mlomker on 2005-09-25
> I have to type 'route add default gw 10.0.0.1' to get Internet to work.


You'll need to look at the contents of /etc/network/interfaces.  The graphical applet probably misconfigured something in there.

---

### Post by jafro on 2005-09-25
/etc/network/interfaces
---
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 10.0.0.4
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 217.13.4.24 217.13.7.140

iface eth1 inet dhcp

auto eth0
---eof


I tried changing the line network to 10.0.0.1 but that didn't seem to change anything.

---

### Post by mlomker on 2005-09-25
```

# The primary network interface
iface eth0 inet static
        address 10.0.0.4
        netmask 255.255.255.0
        network 10.0.0.0
        **gateway 10.0.0.1**
        broadcast 10.0.0.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 217.13.4.24 217.13.7.140

```

---

### Post by jafro on 2005-09-25
Yep, that did it! Thanks :-)

---

