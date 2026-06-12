---
title: "Unable to access website behind VPN from the Internet"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by dodul on 2013-10-26
Hi,

I have one server with public IP address. That server is connected with another server with private IP via openVPN. The public server has IP 200.x.x.x on eth0 interface and 10.8.0.1 on tap0 interface. The private server has IP 10.8.0.2 on tap0 which is connected with the tap0 interface (10.8.0.1) of the public server through VPN. A webserver with IP 192.156.102.12 is connected with the eth0 interface of the private server. 

Server 1(Public)..........................................Server 2(Private).................................................Server 3(Web server)
eth0 200.x.x.x|tap0 10.8.0.1 <------VPN----->tap0 10.8.0.2 | eth0 192.168.102.2 <-------------->eth0 192.168.102.12

I can ping and browse server 3 webpages from server 1.  Now I am trying to access server 3  through web browser from the Internet. To do that I added a port forward to server 1 which forwards 2511 port to port 80 of server 3. However, when request 200.x.x.x:2511 from browser, I see request timed out. From packet tracing i found the request can reach server 2 and no response after that. 


Below is my firewall and routing configaration

Server 1
------------------
IP forward:
```
13   DNAT       tcp  --  0.0.0.0/0            200.x.x.x        tcp dpt:2511 to:192.168.102.12:80
```

Route Table
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.102.0   10.8.0.2        255.255.255.0   UG    0      0        0 tap0

```


Server 2
-------------------
Route table

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.8.0.0        linux.local     255.255.255.0   UG    0      0        0 tap0
10.8.0.0        *               255.255.255.0   U     0      0        0 tap0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.102.0   *               255.255.255.0   U     0      0        0 eth0

```


Not sure what im doing wrong. Please help me..... 

Thanks in advanced

BR//Kamrul

---

### Post by dodul on 2013-10-27
No reply so far...

Can anyone help me ? If my issue is not clear enough please let me know .. ill explain again

---

