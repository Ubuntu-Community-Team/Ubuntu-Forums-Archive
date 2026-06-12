---
title: "Can SSH into Linux box but can not see my network from the Linux box"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Urge on 2008-05-16
I am having a random networking issue I was hoping someone could help me with.

I can access all network related protocols on my Linux box (SSH, VNC, Samba, web server) all from inside my local network and from outside the house.  However, the Linux box can not ping or access any machine on my network.  It can access the internet and ping the router only.

The machine has 2 network cards integrated on the mobo.  I have tried both of them, I have also reinstalled the machine with those cards disabled and another NIC installed.  All configurations yielded the same results.

Any ideas?

Thanks

---

### Post by Gunman1982 on 2008-05-16
Seems to be more of an issue relating the router. Some more information would be nice. Like:
Is your linux box connected to the router via ethernet or wireless?
Are the other machines connected to the router via ethernet or wireless?
Is the router configure to allow/deny access to/from the linux box?
Do you use dhcp on the router for all other machines and the linux box?
Do you have firewalls activated on the other machines?

---

### Post by Urge on 2008-05-16
My network is made up of the Linux machine and a network storage device with a wired connection and a laptop on a wireless connection.  The laptop can connected to samba shares on the linux machine and NAS.  The router is set to assign specific IPs based on the MAC address of the NIC.  It worked fine when I was using linux on another machine.  The current box used to be my windows machine, but I decided to ditch windows completely when Hardy was released.  So this machine functioned perfectly on the network before which makes me think it is not the router.  When I try to ping my NAS or laptop from linux I use their Host name and it resolves their IP address just fine (even before I added them to the hosts file).

Running route yield these results
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.255.45.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         NO_WIRE         0.0.0.0         UG    100    0        0 eth0
```

ARP
```
Address                  HWtype  HWaddress           Flags Mask            Iface
NO_WIRE                  ether   00:18:F8:70:8A:36   C                     eth0
NAS-SERVER                       (incomplete)                              eth0
LAP-WARMER               ether   00:14:A5:86:A8:7A   C                     eth0
```

Also, firewalls on the other network devices are not a problem.

---

