---
title: "How to create an eth0:1 virtual interface with netplan and DHCP? (Ubuntu 18)"
date: 2018-10-31
forum: Networking &amp; Wireless
---

### Post by entilza2 on 2018-10-31
Hi everyone,

I am migrating an Ubuntu 14 server to 18 server. I am creating a fresh 18 install and setting up all tools/app afresh.

The 14 server (and 18 server) needs a virtual interface and has the following set up:
eth0 (the native interface - IP details set via DHCP)
eth0:1 (a virtual interface with the same MAC as eth0 - static IP and details set by the sysadmin)

I cannot fathom how to achieve this using netplan and my attempts have often left me with no network (including eth0) on reboot, leading to unrecoverable instances (I'm using AWS = no console).

I'd be looking for something like the following (warning, this does not work - netplan ignores the eth0:1 section, but at least the network comes up in a workable state for eth0, unlike most of my attempts):
```

network:
    version: 2
    ethernets:
        eth0:
            dhcp4: true
            match:
                macaddress: <eth0 mac here>
            set-name: eth0


        eth0:1:
            dhcp4: false
            addresses: [172.31.3.80/16]
            gateway4: 172.31.0.1

```


I found this bug report suggesting netplan cannot support virtual interfaces (eth0:1):
[https://bugs.launchpad.net/ubuntu/+source/nplan/+bug/1743200](https://bugs.launchpad.net/ubuntu/+source/nplan/+bug/1743200)

My question is: if this cannot be done through netplan, how do I create (and keep between reboots) eth0:1 in Ubuntu 18, or is there an alternative to using eth0:1?

Both interfaces are on the same subnet, by the way.

Thanks!
Ent.

---

### Post by entilza2 on 2018-11-02
I could not find how to add a virtual interface with netplan and DHCP in play. What little info I can find suggests netplan does not support this.

I ended up "fixing" the problem by following the advice at the end of this thread: [https://askubuntu.com/questions/990825/virtual-interface-in-netplan](https://askubuntu.com/questions/990825/virtual-interface-in-netplan)

The solution is to roll back to using ifupdown instead of netplan. This solution doesn't really answer the question, but it gets me back on track after days of no progress.

---

