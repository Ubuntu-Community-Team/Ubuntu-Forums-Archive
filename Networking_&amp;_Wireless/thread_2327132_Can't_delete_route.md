---
title: "Can't delete route"
date: 2016-06-08
forum: Networking &amp; Wireless
---

### Post by bizhat on 2016-06-08
Here is my routing table

```

root@hon-pc-01:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.8.1     0.0.0.0         UG    100    0        0 enp0s29f7u3
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlxe8de270b3955
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s29f7u3
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlxe8de270b3955
192.168.8.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s29f7u3
root@hon-pc-01:~# 

```

I am trying to delete first route as i need all traffic go through iface wlxe8de270b3955.

When i run route del, i get following error

```

root@hon-pc-01:~# route del 0.0.0.0 192.168.8.1 netmask 0.0.0.0
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
root@hon-pc-01:~# 

```

Anyone know what i am doing wrong, why can't i delete the first route ?

---

### Post by Fire_Chief on 2016-06-08
You need to edit the NIC configuration setting for the enp0s29f7u3 interface to remove the default gateway/default route setting. If you are using DHCP on both interfaces, then you should configure the enp0s interface with a static IP and leave the default gateway empty.

---

### Post by bizhat on 2016-06-08
Thanks, got it working with


```

sudo route del default gw 192.168.8.1 dev enp0s29f7u3

```

Is there anyway i can delete this entry by default ? I did edited "Wired connection 2" and set only connect to resources in this network check box selected. It worked properly on connect/disconnect. But when i reboot PC, a new connection "Wired connection 3" auto created. This network interface is USB device. Anyway i can remove this device default gateway on boot itself ?  I can add the above command in "Startup Applications", any better way ?

---

