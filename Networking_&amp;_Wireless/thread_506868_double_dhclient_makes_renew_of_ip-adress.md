---
title: "double dhclient makes renew of ip-adress"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by alibobar on 2007-07-22
I've been getting this for some time now: sometimes during boot, apperantly another dhcpclient pops up .. trying to renew my ip-adress, F-ing with my network.

Here's some more info: 


```
$ ps aux |grep dhc
root      4822  0.0  0.0   1940   852 ?        Ss   12:43   0:00 /usr/sbin/dhcdbd --system
dhcp      5026  0.0  0.1   2452  1236 ?        S    12:43   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
dhcp      8274  0.0  0.0   2452   560 ?        S<s  14:42   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dreamer   8325  0.0  0.0   2884   752 pts/1    R+   14:43   0:00 grep dhc
```


it's dhclient3 that's making the trouble


It doesn't always start on boot though, like once every 5-10 boots perhaps, though I can't be sure, it just renews the ip-adress very suddenly, 2-3 hours after boot.

---

### Post by alibobar on 2007-07-23
Hmmm, today, after boot, I got this grep:

```
$ ps aux |grep dhc
root      2767  0.0  0.0   1712   480 ?        S<   08:35   0:00 /bin/sh -c dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dhcp      2768  0.0  0.1   2452  1228 ?        S<   08:35   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root      4854  0.0  0.0   1936   844 ?        Ss   08:35   0:00 /usr/sbin/dhcdbd --system
dhcp      5058  0.0  0.1   2452  1232 ?        S    08:35   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
dreamer   6541  0.0  0.0   2884   776 pts/2    S+   08:39   0:00 grep dhc
```

---

### Post by alibobar on 2007-08-08
And yet again, out of the blue (every 10th boot or something?) it happens again:

```
$ ps aux |grep dhc
root      4777  0.0  0.0   1940   832 ?        Ss   09:02   0:00 /usr/sbin/dhcdbd --system
dhcp      4981  0.0  0.1   2452  1236 ?        S    09:02   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
dhcp      8023  0.0  0.0   2456   568 ?        S<s  11:02   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dreamer   8086  0.0  0.0   2888   776 pts/2    R+   11:12   0:00 grep dhc
```


So there's no one that can help me figure out why sometimes this extra client pops up and renews my ip? It's SO anying!!

---

