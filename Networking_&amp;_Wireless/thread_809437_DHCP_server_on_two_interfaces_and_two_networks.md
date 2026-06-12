---
title: "DHCP server on two interfaces and two networks"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by mmerlone on 2008-05-27
Hello,

I have a server with two network cards:

```
root@marte:/etc/dhcp3# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.202
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        dns-nameservers 127.0.0.1

auto eth1
iface eth1 inet static
        address 10.0.0.3
        netmask 255.0.0.0
        network 10.0.0.0
        broadcast 10.255.255.255
        gateway 10.0.0.1
        dns-nameservers 10.0.0.2
root@marte:/etc/dhcp3#
```

Both logical networks are at the same ethernet segment, i.e. same fisical network.

I want to configure a dhcp server in such a way that known clients get an 192.168.0.0/24 address via eth0 and unknown clients get 10.0.0.0/8 address via eth1. I have tried this straight on dhcpd.conf:

```
subnet 192.168.0.0 netmask 255.255.255.0 {
ignore unknown-clients;
host mic-052{
hardware ethernet 00:1e:c9:1b:xx:xx;
fixed-address 192.168.0.52;
}
... etc
}

subnet 10.0.0.0 netmask 255.255.255.0 {
... etc
}
```

It did not work, gave me the error:

```
May 27 13:01:06 marte dhcpd: DHCPREQUEST for 192.168.0.52 (192.168.0.202) from 00:1e:c9:1b:xx:xx via eth1: wrong network.
```

Is it doable? Can anybody help me?

Best regards,

---

### Post by SpaceTeddy on 2008-05-28
you cannot have two network card on the same (physcial) subnet and have a dhcp server running on both network cards. That leads to conflicts, since both dhcp-server processes will pick up the DHCPREQUEST from the client and will BOTH issue a DHCPLEASE to it. This will lead to a race condition which will - most likely - result in you not being able to use the network at all.
I've just seen the "ignore unknown clients" - i've neber read anything like this before, nor do i understand what exactly that should do. What is an "unknown" client to a dhcp-server ?

Instead of doing it this way, i would suggest you do special configurations based on the MAC's of the devices. This is not really a better security (since a MAC address can be spoofed) but it would probably be able to do what you want to do. 

So, what you want to do is configure only one dhcp range for the clients that you don't know, and special cases for the ones you do know. a sample would look like this:

```

host mic-052{
hardware ethernet 00:1e:c9:1b:xx:xx;
fixed-address 192.168.0.52;
}

subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.5 10.0.0.100;
... etc
}

```

but then, i have no tried this setup myself (if i want to seperate clients i either use firewalls or segmented networks)

hope it helps :)

---

### Post by mmerlone on 2008-05-29
> **SpaceTeddy said:**
> (...) That leads to conflicts, since both dhcp-server processes will pick up the DHCPREQUEST from the client and will BOTH issue a DHCPLEASE to it.

No. It is only one DHCP server process. It will serve two distinct logical networks, both on the same physical network. But only one server process. It will DHCPLEASE on 192.x.x.x if a known client or 10.x.x.x for unknown clients.

It seems I got it working by enclosing the subnet statements by the shared-network statement:

```

shared-network foo{

    subnet 10.0.0.0 netmask 255.255.255.0 {
        pool{
            range 10.0.0.4 10.0.0.254;
            allow unknown-clients;
        }
    }

    subnet 192.168.0.0 netmask 255.255.255.0 {
        pool{
            range 192.168.0.51 192.168.0.190;
            deny unknown-clients;
            host mic-xxx{ hardware ethernet 00:1d:60:c9:xx:xx; }
        }
    }
}

```


> **SpaceTeddy said:**
> I've just seen the "ignore unknown clients" - i've neber read anything like this before, nor do i understand what exactly that should do. What is an "unknown" client to a dhcp-server ?

Is a client that does not match any host entry (like mic-xxx above).

> **SpaceTeddy said:**
> Instead of doing it this way, i would suggest you do special configurations based on the MAC's of the devices.

That's what the 'host' is for.


> **SpaceTeddy said:**
> So, what you want to do is configure only one dhcp range for the clients that you don't know, and special cases for the ones you do know. a sample would look like this:

```

host mic-052{
hardware ethernet 00:1e:c9:1b:xx:xx;
fixed-address 192.168.0.52;
}

subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.5 10.0.0.100;
... etc
}

```

but then, i have no tried this setup myself (if i want to seperate clients i either use firewalls or segmented networks)

Looks almost the same I did, except that you must have the host entry inside a subnet declaration. The shared-network  did the trick.

And, for the sake of internet records, it must be said that this is not secure in any way. As Teddy said, mac addresses are spoofable, and one can configure ip address by hand.

Thanks a lot for your time. :)

---

### Post by Iowan on 2008-05-29
I was trying to set up a DHCP server today, and did notice something in **/etc/dhcp3/dhcp.conf** about class-based addressing.  One challenge would be in defining the class, another would seem to be piping the results down the proper interface.  IIRC, the DHCP server could do all assigning via one card.

---

