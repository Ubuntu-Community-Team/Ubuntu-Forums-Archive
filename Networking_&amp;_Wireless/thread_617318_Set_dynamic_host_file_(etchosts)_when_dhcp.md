---
title: "Set dynamic host file (/etc/hosts) when dhcp"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by manosx on 2007-11-19
Hello,
I want to set host names to my computers in order to mount nfs partitions without typing the ip address every time. The implementation will be either in fstab or a script.

The thing is that I am getting dhcp. The configuration is like this:
HOST 1: sonic
br0 - eth0 and eth1 (bridged network br0, bridging eth0 and eth1)
        getting dhcp
HOST 2:lapton
eth0 - getting dhcp
       - connected with interface eth1 of sonic
So, I dynamical get addresses for br0 and eth0.
In /etc/dhcp3/dhclient.conf I tried:
 ```
 part of /etc/dhcp3/dhclient.conf
[CODE]
#send host-name "<hostname>";
send host-name "sonic";

```
[/CODE]
I also tried not to request a host name from dhcp:
 ```
 part of /etc/dhcp3/dhclient.conf
[CODE]
#send host-name "<hostname>";
send host-name "sonic";

...
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers,
        netbios-name-servers, netbios-scope; # I removed host-name

```
[/CODE]

I don't know what to set to /etc/hosts

thank you

---

### Post by manosx on 2007-11-19
I finally did a workaround.. So, for people that are interested or want to do the same thing..
I created an alias for br0 and configured an internal ip:
```

root@sonic:/home/manos# ifconfig br0:0 192.168.0.1 up

```
Did the same in my laptop:
```

root@lapton:/home/manos# ifconfig eth0:0 192.168.0.2 up

```

Inserted the hosts to the /etc/hosts :
```

root@sonic:/# cat /etc/hosts | grep lapton
192.168.0.2     lapton

```
Did the same for the other host  (192.168.0.1 sonic)
Set the allowed hosts in /etc/exports :
```

root@sonic:/# cat /etc/exports |grep lapton
/media/sdb1/ lapton(rw,async,all_squash)

```

---

