---
title: "dhcp6 static lease problem - only works when manual dhclient -6"
date: 2020-08-09
forum: Networking &amp; Wireless
---

### Post by jsbiff on 2020-08-09
Hi,

   I have a router running OpenWRT, and a desktop running Ubuntu 20.04. I have setup networking on the Ubuntu desktop using netplan, to create a bridge connection, br0. Below is my netplan conf file:

network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eno1:
      dhcp4: no
      dhcp6: no
  bridges:
    br0:
      dhcp4: yes
      dhcp6: yes
      interfaces:
        - eno1

As for the OpenWRT router, I think I have the static lease for the IPv6 address setup correctly, because it works if I manually run dhclient (it's a suffix-based static lease - the network prefix is dynamic and occasionally changes, but I wanted the suffix ::3 for my desktop):

dhclient -6 br0

After I run that as root, then br0 gets the static IPv6 address.

Any thoughts how I get this to work automatically on boot up?

---

### Post by jsbiff on 2020-08-12
I should add, in OpenWRT, I setup a static lease for both IPv4 and IPv6 - the IPv4 static lease works automatically on bootup, but for some reason, as I said previously, I have to manually run dhclient to get the IPv6 lease.

---

