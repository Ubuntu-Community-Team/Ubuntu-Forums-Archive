---
title: "Persistent Static Routes with Netplan"
date: 2017-11-29
forum: Networking &amp; Wireless
---

### Post by mjjazz on 2017-11-29
I am trying to create a 2-NIC server with Ubuntu Server 17.10, but with the move to Netplan (default to networkd as renderer), deprecation of ifupdown, and the disappearance of rc.local, I have no idea where to put the necessary static routes such that they are loaded at boot.

I tried to add the routes to the Netplan config like the example at the bottom of the man page, but I received the error of "unknown key routes" when trying to generate.  Where in 17.10 can I execute an "ip route add" command at boot after the network is up, or is there another way to add some static routes?

TIA!

---

### Post by powersj on 2017-11-29
Would you be willing to share your netplan configuration that failed? Given that is the default going forward it would be nice to make sure it is documented how to properly use it or fix it if it is not working :)

I assume you are using syntax similar to:
```

  routes:
   - to: 192.168.1.1/0
     via: 10.0.0.1

```

---

### Post by mjjazz on 2017-11-29
Per the man page the routes key is at the same level as the ethernets, wifis, etc. keys.  This produces the error.  Below is configuration for my second NIC.  The first NIC does not have any routes key in it, but names a gateway for the that NIC.

```

[FONT=courier new]# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens192:
#      set-name: Hostnet
      wakeonlan: true
      dhcp4: no
      addresses: [10.11.0.9/24]
      gateway4: 10.11.0.6
      nameservers:
        search: [halff.ad, dal.halff.ad, ext.halff.ad, halff.com]
        addresses: [10.11.0.206,10.12.8.206,10.1.9.201]
  routes:
   - to: 0.0.0.0/0
     via: 10.11.0.6
   - to: 10.11.11.0/24
     via: 10.11.9.254
   - to: 10.6.0.0/23
     via: 10.11.9.254[/FONT]

```

What is the correct way to use the routes key if it is implemented and working?

---

### Post by powersj on 2017-11-29
> **mjjazz said:**
> What is the correct way to use the routes key if it is implemented and working?

Looks like the man page and docs need to be updated, as it appears the routes key needs to be under a device, like so:

```

network:
    version: 2
    renderer: networkd
    ethernets:
        eth0:
            dhcp4: yes
            routes:
                - to: 192.168.2.1/24
                  via: 192.168.1.1/24

```

Putting it as a top level gave me:
Error in network definition //etc/netplan/test.yaml line 1 column 4: unknown key routes

and putting it under ethernets:
Error in network definition //etc/netplan/test.yaml line 7 column 12: expected mapping

Edit:
There already is a bugs for this, first the doc bug: [https://bugs.launchpad.net/netplan/+bug/1726695](https://bugs.launchpad.net/netplan/+bug/1726695)
and then whether or not global routes should be supported: [URL="https://bugs.launchpad.net/netplan/+bug/1720418"]https://bugs.launchpad.net/netplan/+bug/1720418

[/URL]

---

### Post by mjjazz on 2017-12-07
Thanks for the troubleshooting help.  Yes, currently the routes must be listed under the device heading.

In addition to the routes being interface specific, the routes that are specified must have a gateway that is reachable to the network(s) on that specific interface.  This could mean that you will need to list routes under each and every device to build your full table.

---

