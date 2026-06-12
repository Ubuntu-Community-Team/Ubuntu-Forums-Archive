---
title: "networking help please"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by cjells on 2011-03-09
Hi, I need some networking help. How do I change eth0 from dhcp to a static ip without re-instaling Ubuntu (which at this point appears easier)?
 
I have edited the /etc/network/interfaces file, where eth0 was not even listed, to add the following:
 
iface eth0 inet static
address 172.17.32.101
netmask 255.255.255.0
network 172.17.32.0
broadcast 172.17.32.255
gateway 172.17.32.1
 
so now the entire file reads:
 
#auto lo
#iface lo inet loopback
iface eth0 inet static
address 172.17.32.101
netmask 255.255.255.0
network 172.17.32.0
broadcast 172.17.32.255
gateway 172.17.32.1
 
 
Now ifconfig does not show eth0 but shows eth1, which is not in the interface file at all
 
yes, I have restarted networking , and rebooted the box. It doesnt want to take an ip.
 
 
In Windows or UNIX I would already be up and running. 
 
 
Thanks

---

### Post by GWBouge on 2011-03-09
My interfaces file only has those first two lines ... the ones you commented out.  Except don't comment those out.  Have you tried the GUI tool? System -> Preferences -> Network Connections

Or is this a server box?  Even so, you want to keep those first two lines for the loopback configuration.  Here's the full interfaces for my server VM:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.200
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 208.67.220.220 208.67.222.222
        # dns-* options are implemented by the resolvconf package, if installed
        pre-up iptables-restore < /etc/iptables.rules
        post-down iptables-save > /etc/iptables.rules

```

---

