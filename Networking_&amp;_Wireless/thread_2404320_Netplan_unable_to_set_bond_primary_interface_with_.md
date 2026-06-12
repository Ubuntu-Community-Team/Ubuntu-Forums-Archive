---
title: "Netplan unable to set bond primary interface with netlinks match."
date: 2018-10-22
forum: Networking &amp; Wireless
---

### Post by sysadm-k on 2018-10-22
I have a netplan setup with 4 interfaces bonded together, using "netlinks: match: name: 'eno*'" syntax.  This is because this config is used across 8 machines of slightly different types, and if I use the regex I can have the files be the same except for the single "address" line.

But, an error is reported if one of the interfaces is specified as a primary:  Error in network definition //etc/netplay/50-local.yaml line 17 column 25: bond0: interface eno1np0 is not defined.

The configuration in 50-local.yaml is:

    network:
      version: 2
      ethernets:
        netlinks:
          match:
            name: "eno*"
      bonds:
        bond0:
          interfaces:
            - netlinks
          parameters:
            mode: active-backup
            mii-monitor-interval: 101
            primary: eno1nop
        [...]

If I comment out the "primary" line, it works fine *EXCEPT* that I have no influence over which interface is the primary.

If I change it to list the individual interfaces, it also works, but means I have to maintain it differently for each system.  That config looks like:

[...]
ethernets:
eno1np0:
dhcp4: false
eno3:
dhcp4: false
eno2np1:
dhcp4: false
eno4:
dhcp4: false
bonds:
bond0:
interfaces:
- eno1np0
- eno3
- eno2np1
- eno4
parameters:
mode: active-backup
mii-monitor-interval: 101
primary: eno1np0
[...]

That works fine.

---

