---
title: "Static IPAC has no Internet connectivity"
date: 2016-11-16
forum: Networking &amp; Wireless
---

### Post by super_awesome on 2016-11-16
So I've been casually using ubuntu server for a few years and I've never had a problem that I couldn't Google through. Enter ubuntu 14.04.5 LTS. I originally tried to install 16.04 LTS but I couldn't get that to work on my old system. That's another story. 

Anyway, I finished installing 14.04.5 and everything is working fine. The network connection is fine, it works great on dhcp. Now, when I set it statically as I've been doing for years, all I can see is the local network. Can't ping hosts or IP addresses outside of my network. Obviously it's not a DNS issue then if I can't ping IP addresses outside the local network. 

My configuration file looks like this:

auto eth0 inet static
address 10.10.10.3
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255
gateway 10.10.10.1

I didn't worry about dns servers as of yet because that's obviously not the problem. But I have zero connection outside of my gateway. What's the deal?

---

### Post by chili555 on 2016-11-16
> I didn't worry about dns servers as of yet because that's obviously not the problem.I must respectfully disagree; I think that is *_exactly_* the problem. I suggest that you amend your /etc/network/interfaces file to:```
auto lo
iface lo inet loopback

auto eth0 inet static
address 10.10.10.3
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 10.10.10.1 8.8.8.8

```Restart the interface:```
sudo ifdown eth0 && sudo ifup -v eth0
```And test:```
ping -c3 www.ubuntu.com
```

---

