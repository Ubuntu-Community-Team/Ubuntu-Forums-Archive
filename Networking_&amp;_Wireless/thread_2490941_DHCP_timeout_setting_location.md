---
title: "DHCP timeout setting location"
date: 2023-09-21
forum: Networking &amp; Wireless
---

### Post by julian-g71 on 2023-09-21
Hi - I'm hoping someone can help me with something I thought would be very simple. I have an Ubuntu server running 22.04 LTS that uses systemd-networkd for its network configuration. My netplan file is:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    all:
      match:
        name: enp*
      dhcp4: true
      dhcp-identifier: mac
      optional: true
```

Is there a setting somewhere so that the server will wait indefinitely for a DHCP offer? It seems to timeout after about 5mins / 300secs.

I can see this on the console when it finally gives up:

```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
no search or nameservers found in /run/net-.conf /run/net-*.conf /run/net6-*.conf
```

I've had a look in the dhclient.conf file and edited the systemd-networkd-wait-online.service but still the same result.

Any help would be really appreciated.

---

### Post by TheFu on 2023-09-21
```
name: enp*
```

Is that valid?  I've never seen pattern matching in a netplan file.  Would be helpful if it works.  Perhaps is it new and older netplan versions didn't support it?

I specifically set the "ethernets" , no wild card.  And when I need an "interfaces", I use the specific internfaces from those listed under ethernets.
```
  ethernets:
     ens3:
```

Could be a bug, so that's the first thing I'd try.
[https://netplan.readthedocs.io/en/latest/netplan-yaml/](https://netplan.readthedocs.io/en/latest/netplan-yaml/) does show an example with a match similar to yours.  Have you checked that the ethernet device name matches the pattern?  **ip a** would show that.  On some of my systems, the ethernet devices begin with ens, not enp.

---

