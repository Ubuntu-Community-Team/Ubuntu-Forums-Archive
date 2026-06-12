---
title: "Setting up NIC failover?"
date: 2019-05-23
forum: Networking &amp; Wireless
---

### Post by ogeron on 2019-05-23
Trying to make a 2 nic server use route via one network card and then fail over to the other if the first goes down and vice versa. Read so many man pages last few days, seen lots of similar unanswered questions.  Primary resource: [http://manpages.ubuntu.com/manpages/cosmic/man5/netplan.5.html](http://manpages.ubuntu.com/manpages/cosmic/man5/netplan.5.html)

Static IP on each NIC, each NIC goes to a different firewall/ISP.  ACL's on the routers set up and they fail over fine between each other.  This routing exists solely to handle if a nic/switch fails in between.
Gateway removed to allow route table to have only weighted routes, otherwise you wind up with 4 default routes, 2 weighted 0, 1 1 and 1 2.

Tried source routing, bonds and weighted routes.  Can't get the switching to work.  

Routing-policy block WAG.  

Netplan applies with or without that block, no change.  Can ping and access each separate network and all hosts on them.  Traffic only routes out primary gateway.

Any pointers?

KISS yaml

```

network:
    ethernets:
        ens192:
            dhcp4: no
            dhcp6: no
#            addresses: []
            addresses: [192.168.0.108/24]
#            gateway4: 192.168.0.1
            nameservers:
                addresses: [192.168.0.1,8.8.8.8]
            routing-policy:
                - to: 192.168.0.1
                  priority: 1
            routes:
                - to: 0.0.0.0/0
                  via: 192.168.0.1
                  metric: 1
                  scope: link
                  on-link: true
#                - to: 0.0.0.0/0
#                  via: 192.168.1.1
#                  metric: 2
##                  scope: link
#                  on-link: true
        ens256:
            dhcp4: no
            dhcp6: no
#            addresses: []
            addresses: [192.168.1.108/24]
#            gateway4: 192.168.1.1
            nameservers:
                addresses: [192.168.1.1,8.8.8.8]
            routing-policy:
                - to: 192.168.1.1
                  priority: 2
            routes:
#               - to: 0.0.0.0/0
#                  via: 192.168.0.1
#                  metric: 1
#                  on-link: true
                - to: 0.0.0.0/0
                  via: 192.168.1.1
                  metric: 2
                  scope: link
                  on-link: true
    version: 2
    renderer: networkd



```

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    1      0        0 ens192
default         _gateway        0.0.0.0         UG    2      0        0 ens256
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ens192
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ens256

---

