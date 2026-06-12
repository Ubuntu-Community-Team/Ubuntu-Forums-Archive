---
title: "unable to connect to web server from external IP"
date: 2023-02-23
forum: Networking &amp; Wireless
---

### Post by JimLS on 2023-02-23
Apache2 works from local addresses but not from external.  I don't find any restrictions in the config file (mostly or all defaults).  Verified packets are getting to PC with

sudo tcpdump -i eno1 port 80

but the apache2 log only shows local addresses.  I don't see the address with I tried to access it from that was external in the apache2 logs but did see them in the tcpdump.

---

### Post by The Cog on 2023-02-24
I have a feeling that Apache only listens on the loopback address unless you configure a different listening address (0.0.0.0 or :: means all local addresses). These will list all the listening addresses so you can see what's currently happening:
```
sudo ss -lntp
sudo netstat -lntp
```

---

### Post by JimLS on 2023-02-24
Thanks!  I am not sure how to interpret the results...
For the pc that only responds to local machines (Ubuntu 18.04) I get(just posting port 80 lines):
```
LISTEN   0         128                       *:80                      *:*        users:(("apache2",pid=6542,fd=4),("apache2",pid=6461,fd=4),("apache2",pid=6449,fd=4),("apache2",pid=6176,fd=4),("apache2",pid=5534,fd=4),("apache2",pid=3835,fd=4),("apache2",pid=2539,fd=4),("apache2",pid=1435,fd=4),("apache2",pid=915,fd=4),("apache2",pid=702,fd=4),("apache2",pid=419,fd=4))

```
and (I noticed that I don't have a tcp response for port 80 and I don't use tcp6 on my network)
```
tcp6       0      0 :::80                   :::*                    LISTEN      419/apache2

```
For a PC that works (Ubuntu 14.04) I get:
```
LISTEN     0      128                      :::80                      :::*                                   users:(("apache2",2838,4),("apache2",2837,4),("apache2",2836,4),("apache2",2835,                             4),("apache2",2834,4),("apache2",2828,4))

```
and
```
tcp6       0      0 :::80                   :::*                    LISTEN      2828/apache2
```

---

### Post by TheFu on 2023-02-24
Firewall?
WAN Router port forwarding?

---

### Post by JimLS on 2023-02-24
Router is pfsense with openvpn client so not a simple port forwarding situation.  vpn packets arrive with ip of vpn tunnel.  Just default firewall settings on the PCs - no restrictive firewall rules were added.  Not at the machine currently but could check details later.  Several other PCs can be accessed from external ip (via VPN), this one doesn't.

---

