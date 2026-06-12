---
title: "Bond or Bridge or something else"
date: 2016-06-09
forum: Networking &amp; Wireless
---

### Post by Andrew_Hobson on 2016-06-09
Hello,

I searched on the web and didn't find a solution to my specific need. So I am asking for advice on this forum !

I have 2 seperated networks.

Network A with an ADSL router and access to Internet used for teachers
Network B with a Cable router and access to Internet used for students

Now I have a Ubuntu machine hosting a webserver. I would like this webserver to be accessible to both networks A & B.

So I installed two network cards in the Ubuntu machine and connected each one on a Network. eth0 on network A and eth1 on network B.

What must I do to configure this Ububtu machine so that the webserver can be accessed indiferently from both networks.

Must I Bond the interfaces? Must I Bridge the interfaces? Must I use another solution?

Can someone give me some advice on how to make this work?

Thank you.

Andrew

---

### Post by SeijiSensei on 2016-06-09
You shouldn't need to do anything special.  Perhaps it's a DNS issue?  Can you see the server if you use an IP address instead of a domain name in the browser, e.g, [http://10.10.10.10/?](http://10.10.10.10/?)  Can you ping the server from both networks?

You probably don't want to specify a default gateway in the server's routing table if the two networks cannot see each other.  Let's see the results of the command "route -n" on the server inside [noparse]```

```[/noparse] tags.

---

### Post by Andrew_Hobson on 2016-06-10
Here is the result from route -n

```

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         10.192.120.1    0.0.0.0         UG    0      0        0 eth0
10.192.120.0    0.0.0.0         255.255.254.0   U     1      0        0 eth0
193.134.217.128 0.0.0.0         255.255.255.224 U     1      0        0 eth1

```

---

### Post by SeijiSensei on 2016-06-10
OK.  As I asked, can you ping the server from both networks?  I assume the machines on the eth0 side have addresses in 10.192.120.0/23, and the ones on the eth1 side have addresses in 192.134.217.128/27.

---

### Post by Andrew_Hobson on 2016-06-13
Hello,
Yes, I am able to ping successfully the server from both networks. eth0 has IP 10.192.120.12 and eth1 has IP 193.134.217.134.
And yes you assume correctly about the address range of both networks.

---

### Post by SeijiSensei on 2016-06-13
Good.  

Now make sure Apache is running correctly on the server by opening a browser on that machine and navigating to [http://localhost/](http://localhost/).  You should see the "Apache2 Ubuntu Default Page."  If not, the problem has to do with Apache.  If it works via localhost, use a browser on each network and open [http://ip.addr.on.net1/](http://ip.addr.on.net1/) or [http://ip.addr.on.net2/](http://ip.addr.on.net2/). You should see the same result.  If not, what do you see in /var/log/apache2/access.log and /var/log/apache2/error.log?

If you want to access the server with a domain name rather than an IP address, you'd need to have separate local DNS servers supporting the two networks so that the A record for "www.example.com" points to the appropriate IP address on each network.  You could use "hosts" files on the various client machines, but that would be a pain in the neck to administer.

---

### Post by Andrew_Hobson on 2016-06-14
Hello,

Everything is OK direct from the server. I can access my webserver with: [http://localhost](http://localhost) or [http://10.192.120.12](http://10.192.120.12) or [http://193.134.217.134](http://193.134.217.134). It works.

But this doesn't work from one network to the other. That's why I wanted to do a bridge or bond or something else. Because before I replaced the machine with a Linux machine, with Windows or MacOS this feature worked perfectly. By having two network cards in a same machine it gave me access to this server from both networks. What must I do to have the same functionality from Lunix?

---

### Post by SeijiSensei on 2016-06-14
You do have access to the server from both networks already, just with different IP addresses.  Do you mean you want to use just one of the machines IP addresses on both networks?  That's certainly possible, but it's not clear how to do this safely.

I assumed from your original posting that you wanted to keep the teacher and student networks isolated from each other.  I certainly think that's a smart idea from a security point of view.  You could let the teachers see the student network but not vice versa with some appropriate iptables rules.  

The reason things aren't working the way they did with Windows is because Ubuntu ships with tighter security.  Look at the file /etc/sysctl.conf.  You'll see this directive:
```

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

```
If you remove the hash mark from the second line and reboot, then traffic will flow from each network to the other.  Then you can publish just one of the IP addresses for the server but have it be reachable from both networks.

Personally I wouldn't want to let the students see the teachers' network.  So you could add some iptables rules like this (assuming 10.192.120.0/23 is the teachers' network):
```

/sbin/iptables -A FORWARD -s 10.192.12.0/23 -d 192.134.217.128/27 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.134.217.128/27 -d 10.192.12.0/23 -j REJECT

```
That permits traffic from the teachers' network to the students' network but not the other way around. You'll need to publish the address on the students' side because both groups can access that IP.

Add these rules to the file /etc/rc.local just above the "exit 0" line so they will be run every time the machine boots up.

---

### Post by Andrew_Hobson on 2016-06-16
I'm sorry but it doesn't work for me. This is weird...

I even tried to uncomment the line:
net.ipv4.ip_forward=1

And rebooted the server.
But I cannot access the server from one network to another... I am stuck !

Can it be a something to do with the gateway?

---

### Post by SeijiSensei on 2016-06-16
If you're trying to access network B from network A, you may need to add a static route to network A's router.  Have it use the server as the gateway to the 192.134 network.  In Linux you'd use a command like
```
ip route add 192.134.217.128/27 via 10.192.20.12
```
You'll need to use the router's own configuration methods to add an equivalent route.

What is probably happening is that requests from the 10.192 network for 192.134 get sent out to the Internet and not permitted back in on the students' side.  With the static route added, the router will know to send the traffic to your server and not out to the Internet.

I'm also having trouble understanding the network architecture.  The 192.134.217.128/27 address space is a public network, apparently in France.  The teachers are on a private address space 10.192.20.x.  Is the ADSL router that serves those addresses itself on a separate connection?  Why not send all the 10.x traffic through the Linux box and out to the Internet via the public connection?  Personally, I'd put the students on a private network as well and have only the Linux box connected to the public Internet.  Having the students on publicly-accessible IP addresses seems like a pretty massive security hole to me.

---

### Post by Andrew_Hobson on 2016-06-28
Hello SeijiSensei,

I wanted to take the time to say thank-you for your help.
I need to make my network more coherent and secure. I will have to work on it. I'll keep you updated if you want to !
I'll probably need some advice again.
Thanks for all. Andrew

---

