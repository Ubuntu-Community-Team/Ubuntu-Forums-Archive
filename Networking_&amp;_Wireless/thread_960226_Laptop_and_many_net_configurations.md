---
title: "Laptop and many net configurations"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by risolner on 2008-10-27
Hello all,

I would like some input on the best way to configure a laptop
with multiple network configurations (see below) in ubuntu 8.04
with Gnome. Using the usual tools that come out of the box,
I have experienced difficulties, like for instance avahi
getting in the way, or NetworkManager not doing what I expected.
And of course it would be nice for each location to have
different printing queues defined (and maybe shares as well).

What I am doing right now is to disable avahi and NetworkManager,
and for each configuration, I have a set of files (/etc/hosts,
/etc/resolv.conf, /etc/network/interfaces) which replace
the ones in place with a script (for instance,
"interfaces.office-eth-static"
replacing the current active "interfaces"). Of course the script
will also start and stop daemons when needed (dhcp client for
instance).

I think there should be a better way of handling this!

Here are the configurations I use most often:

location: office
  - wired ethernet:
    + static address in, say, somedomain.com, with appropriate DNS server
    + dhcp
  - wireless:
    + dhcp and open (no key)
    + dhcp and WPA2 enterprise

location: home
  - wired ethernet:
    + static address in a private subnet like 192.168.1.0, with DNS server
      and special /etc/hosts file
  - wireless:
    + static address and WEP
    + dhcp and WPA

location: on-the-road
  - wireless:
    + dhcp and open (no key)

Thanks for your advices!

---

