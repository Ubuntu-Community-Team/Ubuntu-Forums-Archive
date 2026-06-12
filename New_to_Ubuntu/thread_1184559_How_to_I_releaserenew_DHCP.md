---
title: "How to I release/renew DHCP?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by kendoori on 2009-06-11
Long time windows guy, can't seem to figure out how to release and renew my IP while attached to my home private network. I had temporarily given myself a static, and have now shifted back my connection on Auto eth0 to automatic, but it still has the static in there in the "connection information" applet.

I tried: 

```

user@ubuntu:~$ sudo ifdown eth0
ifdown: interface eth0 not configured


``` 

ifconfig shows

```

eth0      Link encap:Ethernet  HWaddr 00:16:d3:c4:b6:c1  
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fec4:b6c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26600397 (26.6 MB)  TX bytes:5049546 (5.0 MB)
          Memory:fe000000-fe020000 


```

---

### Post by whoop on 2009-06-11
There might be an cleaner/better way but shouldn't
```

sudo /etc/init.d/networking restart

```
do the trick?

---

### Post by Cheesemill on 2009-06-11
```
sudo dhclient
```

Cheesemill

---

### Post by kendoori on 2009-06-11
Thanks 2nd option worked, the first, didn't.

```

sudo dhclient

```

---

### Post by kevdog on 2009-06-11
See the link about manually connecting via the command line in my signature for some tips and tricks

---

### Post by Saghaulor on 2009-06-11
First, you can read up on dhclient with
```
man dhclient
```

But to answer your question, to release an ip address
```
sudo dhclient -r
```

To establish a new ip address
```
sudo dhclient
```

---

