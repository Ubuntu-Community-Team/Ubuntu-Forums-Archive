---
title: "NAT forwarding Problems"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by justinwol on 2013-09-17
I am setting up a linux gateway on a prototype small business network. It is a  prototype because the goal is to learn through the process of setting  it up.

I've been unable to successfully forward traffic to any  computer within my LAN. The LAN has internet access and the firewall is  functional, and after testing the firewall, I have cleared the iptables in my  troubleshooting the NAT forwarding. I have been using a webserver to test the forwarding and am trying to forward web traffic (80) to the  server, but have not been able to do so successfully.

This is a common thing to do and I have found a tonne of information on how to do this, but, after a couple weeks off and on, I have not been able to figure why I've had no success. Many solutions I've tried have seemed to fix other peoples problems, but have not helped me.

Here is some of the relevant info of the Gateway:

Firewall iptables:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

NAT iptables
```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       tcp  --  anywhere             anywhere             tcp dpt:http to:10.0.0.4

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere 
```

ipv4 in [I]/etc/sysctl.conf:
[/I]```
net.ipv4.ip_forward = 1
```

Routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         216-197-185-1.m 0.0.0.0         UG    100    0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1
216.197.185.0   *               255.255.255.0   U     0      0        0 eth0
```

Here is the network details:
Network 10.0.0.0/24
GATEWAY 10.0.0.1
- NAT/firewall (iptables) and DCHP
- This machine is running ubuntu server 12.04 LTS.
- Internet facing NIC is eth0 xxx.xxx.xxx.xxx dynamic IP from ISP
- Internal network facing NIC is eth1 10.0.0.1

WEBSERVER 10.0.0.4
- Apache http server
- ubuntu desktop 12.04 LTS
- Is accesible on LAN
- Prior to building my own gateway  I was using a Linksys E3200 and forwarding the traffic to the server  just fine.

The DHCP server and ip forwarding work fine, the LAN  has internet access. NAT forwarding has had me stumped for a couple  weeks. It is time for some direct help.

What am I missing in order to forward traffic to a specific IP behind the NAT?

Thank you.

---

### Post by ashish_belwase on 2013-09-17
If your want to redirect port 80 to another computer then use the following iptables script : 
iptables -t nat -A PREROUTING -p tcp --dport 80 -d $old_ip -j DNAT --to $new_ip

iptables -t nat -A POSTROUTING -p tcp --sport 80 -d $new_ip -j SNAT --to $old_ip

---

### Post by justinwol on 2013-09-17
Thanks for the help, but still unable to access server outside of LAN. Here is my NAT table now.

```
Chain PREROUTING (policy ACCEPT 60 packets, 5095 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            10.0.0.1             tcp dpt:80 to:10.0.0.4

Chain INPUT (policy ACCEPT 46 packets, 4251 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 63 packets, 4642 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1 packets, 84 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 SNAT       tcp  --  *      *       0.0.0.0/0            10.0.0.4             tcp spt:80 to:10.0.0.1
   82  5807 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0 
```

---

### Post by justinwol on 2013-09-18
Well I tried a different script, but still no connection. In other words I still cannot establish a connection to the webserver with a browser an browse the website. This time, port 80 is opened ([www.grc.com]("http://www.grc.com")) as it was not listed open before and there appears to be some traffic flow.

```
Chain PREROUTING (policy ACCEPT 1 packets, 236 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    1    44 DNAT       tcp  --  eth0   *       0.0.0.0/0            216.197.185.210      tcp dpt:80 to:10.0.0.4:80

Chain INPUT (policy ACCEPT 1 packets, 236 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  919 69032 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0
```

---

### Post by justinwol on 2013-09-18
Checking the apache access log it does not appear that web traffic is reaching the apache server. I'm very confused at to what is happening and can't seem to make any progress.

---

### Post by Doug S on 2013-09-18
My suggestions are: Take out the second rule given by ash; Add interface specifications to your iptables rules; Check that your ISP does not block port 80 access.
Starting from nothing (empty IPtables):```
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j DNAT --to 10.0.0.4:80
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 216.197.185.XXX
```This is just a starting point, correct? You should do a great deal more in your iptables rule set (just my opinion).

---

### Post by justinwol on 2013-09-18
My ISP does not block port 80. I have been hosting and web developing for years. As I said in the first post, I have been using a Linksys E3200 router and forwarding web traffic to my apache server for a long time. I have taken on learning to build my own gateway using a linux server as a prototype for a more flexible and powerful network in the future.

As you said, this is just the start of the iptables rule set. I have emptied them for the sake of troubleshooting.

I suspect I am missing something beyond the iptables, because it seems straightfoward to me, but it does not work. The apache access log registers no hits from beyond the LAN and no connection when I browse to the site.

As per Doug's suggestion, my iptables sit this way, but still no traffic to the apache server:
```
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 to:10.0.0.4:80

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 SNAT       all  --  *      eth0    0.0.0.0/0            0.0.0.0/0            to:216.197.185.210
 3213  233K MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0
```

---

### Post by Doug S on 2013-09-18
delete your masquerade line. The two lines I gave were to be added to an empty table and my SNAT line replaces your masquerade line.
Please post both the nat tables and the normal tables next time. Do and post from:```
sudo iptables -t nat -v -x -n -L
sudo iptables -v -x -n -L
```

---

### Post by justinwol on 2013-09-18
Thank you for helping me Doug. I've deleted the MASQUERADE rule. Still no connection to the webserver.
Checked port 80 again, just because it's always good to check if "its plugged in". Used [www.whatsmyip.org/port-scanner/](www.whatsmyip.org/port-scanner/) port scanner this time, says port 80 is open.

NAT:
```
Chain PREROUTING (policy ACCEPT 91 packets, 6395 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 to:10.0.0.4:80

Chain INPUT (policy ACCEPT 42 packets, 3173 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 249 packets, 18329 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 2 packets, 120 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     296    21431 SNAT       all  --  *      eth0    0.0.0.0/0            0.0.0.0/0            to:216.197.185.210
```

Filters:
```
Chain INPUT (policy ACCEPT 603 packets, 138158 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 38721 packets, 18179106 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 507 packets, 49046 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

---

### Post by Doug S on 2013-09-18
If I go to that ip address I get a web page. "Farm App"
To try to narrow things down, it might be time to look at the packet level with either tpcdump or wireshark.

---

### Post by justinwol on 2013-09-19
Thank you Doug. I have been operating entirely within my LAN and had not realized that the NAT was actually operating as it should. I did not realize the site was accesible outside the LAN. It is only accessible within the LAN via local IP. I use DynDNS with ddclient and the domain name does not work to access the site, but from within my LAN only. This a very helpful discovery as I can move beyond the iptables, as they are functioning properly and I can manipulate them as I need to.

I am also working on a DNS server and so I will call this problem solved as it was specific to the NAT.

---

