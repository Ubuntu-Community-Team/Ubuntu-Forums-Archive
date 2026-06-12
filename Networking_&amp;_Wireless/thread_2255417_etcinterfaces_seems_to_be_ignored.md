---
title: "/etc/interfaces seems to be ignored"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by greg66 on 2014-12-04
My ethernet card does not get configured at boot time (or at resume time); "ifconfig" only shows lo but "ifconfig -a" shows lo and eth3.
Running "/etc/init.d/networking start" does't do anything...

My /etc/interfaces is like this:

auto lo
iface lo inet loopback
iface eth3 inet static
        address 192.168.0.30
        netmask 255.255.255.0
        gateway 192.168.0.1


dns-nameservers 127.0.0.1

Network manager is not installed.

What should I do to avoid configuring manually each time?

TIA

greg

---

### Post by tgalati4 on 2014-12-04
Yes, /etc/network/interfaces is ignored.

Try changing /etc/NetworkManager/NetworkManager.conf to managed=true.

Welcome to the forums.

---

### Post by steeldriver on 2014-12-05
@tgalati4 the OP said they do not have network-manager installed

To bring up an interface at boot time via the /etc/init.d/networking service (ifupdown), you need to add the auto keyword

```

**auto eth3**
iface eth3 inet static
        address 192.168.0.30
        netmask 255.255.255.0
        gateway 192.168.0.1

```

As well, you probably also want something different from your localhost address in the dns-nameservers field - it should be your actual upstream DNS server (which may be the same as your gateway address, if your LAN router provides a name service, or a public server such as google or opendns) even if your system uses dnsmasq under the hood giving anapparent DNS server address of 127.0.0.1

```

dns-nameservers 8.8.8.8 8.8.4.4

```

---

### Post by chili555 on 2014-12-05
My colleague steeldriver is quite correct. I might just supplement his very good explanation to add that, with /etc/network/interfaces correctly populated, the preferred way to get the system to read and use the changes is:```
sudo ifdown eth3 && sudo ifup -v eth3
```The '-v' for verbose will produce some output allowing you to see if an error or warning is issued.

---

### Post by greg66 on 2014-12-06
> **chili555 said:**
> My colleague steeldriver is quite correct. I might just supplement his very good explanation to add that, with /etc/network/interfaces correctly populated, the preferred way to get the system to read and use the changes is:```
sudo ifdown eth3 && sudo ifup -v eth3
```The '-v' for verbose will produce some output allowing you to see if an error or warning is issued.
"auto" did the trick, thanks a lot!

---

