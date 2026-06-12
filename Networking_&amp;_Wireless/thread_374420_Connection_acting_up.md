---
title: "Connection acting up"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by embeemb on 2007-03-02
When I first got my ubuntu up and running last week, I could connect through a wireless and a cable connection. Now my cable connection won't work. 
System -> Administration -> Networking verifies that my eth0 connection is activated. Any ideas?

---

### Post by nyinge on 2007-03-02
What does the following show?  ```
  ifconfig eth0  
```

---

### Post by embeemb on 2007-03-02
It gave this..


> eth0      Link encap:Ethernet  HWaddr 00:16:36:5B:01:39
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7012 (6.8 KiB)  TX bytes:468 (468.0 b)

---

### Post by nyinge on 2007-03-02
What happens when you ```
  sudo dhclient eth0  
``` while the jack is plugged in?

---

### Post by embeemb on 2007-03-02
Yup it is plugged in.

And I got that
> Listening on LPF/eth0/00:16:36:5b:01:39
Sending on   LPF/eth0/00:16:36:5b:01:39
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by nyinge on 2007-03-02
hmm.. apparently no dhcp...  Are you trying to connect directly to your modem, or there's a router in between?

You said, wireless is OK.  What IP addr do you get then?  I'm thinking about manually trying to set an ip and gateway, and see if that works.  Sometimes home routers are slow in giving out dhcp.

---

### Post by embeemb on 2007-03-02
I'm connecting to a router. What are the suggested steps to work around this ickiness?

---

### Post by nyinge on 2007-03-02
I'm trying manually to set an ip addr and ping the router.  For example, if your router has an IP address of 192.168.0.1, then you'd type in
```
  ifconfig eth0 192.168.0.xx netmask 255.255.255.0 up  
```
where 2 < xx < 255, assuming the xx is an available ip on your network.  Then, I'd try to ping the router:
```
 ping 192.168.0.1 -c 5 
```

If the ping is successful, I'd try to surf around to see if that's possible.  If things go smooth, I'd try rebooting the router and test the dhcp again.

---

