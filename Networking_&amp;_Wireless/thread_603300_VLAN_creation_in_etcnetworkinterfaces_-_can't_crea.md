---
title: "VLAN creation in /etc/network/interfaces - can't create more than one"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by michael_bne on 2007-11-05
Hi,

I'm trying to configure Xubuntu 7.10 as a VLAN router, connecting two different VLANS. Both VLANS connect via the same physical interface, which uses version 7.6.9 of the e1000 driver.

Everything works fine when I create the VLAN interfaces manually using vconfig.

When I specify a configuration in /etc/network/interfaces, such as:

auto vlan10
iface vlan10 inet dhcp
    vlan-raw-device eth0

auto vlan20
iface vlan20 inet manual
    vlan-raw-device eth0

The interface that appears first in the file is created correctly, and subsequent interfaces are assigned seemingly random names - "inv" followed by a four digit number. The number changes between boots. It doesn't matter which VLAN naming syntax I use - they all behave the same way.

If experimented with the order or VLANS in the configuration file. Whichever definition appears first is configured correctly - regardless of what it is.

I've tried defining lots of VLANS - all but the first one defined in the config file are assigned random names - inv2048, inv5776 etc.

In /proc/net/vlan, all of the "file" names appear correctly for the individual VLANs, but the config file and the contents of the interface-specific file list the random names, for example The file named "vlan30" starts off "inv5507  VID: 30"

Please help! Thanks.

---

