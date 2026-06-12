---
title: "One day networking stopped fetching dns from the router"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by cmatte on 2008-08-19
Hi,
today, suddenly, Ubuntu does not load dns addresses from my router,
and I don't get internet if I don't add them manually.
I've a static IP configuration,
but DNS were always been taken from my router.
I post some files...
/etc/dhcp3/dhclient.conf(without many commented lines):
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#
[...]
send host-name "<hostname>";
[...]
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
[...]
timeout 30;
[...]

```
/etc/resolv.conf NOW is empty (except commented lines) if I don't add dns manually. Before it normally contained the nameserver(s) taken from my router.
/etc/network/ineterfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
	address 127.0.0.1
	netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.100
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

```
As you see, my network is 192.168.1.x, router is .1, my pc is .100.
If I manually set 192.168.1.1 as DNS from NetworkManager gui, I get internet connectivity.
I also tried adding a ```
prepend domain-name-servers 192.168.1.1,208.67.222.222,208.67.220.220;
``` line into dhclient.conf, but it's not loaded anyway(resolv.con doesn't contain the nameserver(s)...

Any idea? What happened?What could I do?

---

### Post by ModelM on 2008-08-19
Maybe dhclient is broken but if it's broken I'd expect it to do nothing. Are you saying that if you manually add your DNS addresses to /etc/resolv.conf, then connect to the network, something erases the contents of this file?

---

### Post by cmatte on 2008-08-19
Network cable is always connected so I can't do nothing but change its settings.
Anyway,
I meant that if I add dns from the NetworkManager gui, by left-click on it-manual config-Unlock button-DNS-Add, I get internet connection.
And yes,
the resolv.conf is overwritten with the dns I've just added in the gui.

The fact is dns were previously written there automatically. I mean, they were somehow loaded from my home router, where I've set them manually (don't like the ones from my isp, I'm using opendns)...and this behaviour is exactly what I want, because the router can eventually use the other dns given by my isp.

---

### Post by cmatte on 2008-08-20
I found what could be causing troubles: it's my Windows Mobile device!
It didn't cause any trouble before, but I've recently done a hard-reset and now it seems not only to be recognized as a network card, but also to mess up completely the ubuntu networking system: after having connected my device dns are erased from resolv.conf even if I had set them manually.
Also, if I try to disconnect it, I don't get any connectivity if I don't re-add dns manually from the gui (or writing them in resolv.conf).

Is there any suggestion to avoid all this?
A network restart isn't even enough to make networking work again:(

---

### Post by ModelM on 2008-08-20
You might try editing your /etc/resolv.conf to your liking, then making it read-only for everyone. That should prevent it from being modified.

It's not an elegant solution, but it should achieve your desired results.

---

### Post by Malfredious on 2008-08-20
What does ifconfig show?  After an update today all I've gotten is lo interface, my eth0 has disappeared.

---

### Post by cmatte on 2008-08-20
Mmh not bad ModelM, could be a cool idea :popcorn:

In the meanwhile, I managed to disable my phone network card from its settings (I only connect it to recharge its battery!), so I shouldn't experience strange problems anymore...but if it happens I will try to denied the resolv.conf writing...here we say "extreme bads, extreme remedies :lolflag:"

Malfredious,
I get my eth0 correctly in ifconfig...try restarting your networking (/etc/init.d/networking restart) or open another thread, doesn't seem on topic!

---

