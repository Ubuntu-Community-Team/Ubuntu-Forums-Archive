---
title: "Problem with ssh: Unable to conect to server"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by bte_rajan on 2014-04-21
I am Unable to conect to cluster server

when I ssh to the server. It is showing following error

ssh: connect to host server.IP.goes.here port 22: No route to host

I am new in ubuntu, using Ubuntu 12.04 

please help

Thanks

---

### Post by TheFu on 2014-04-21
Check your routing. That is the issue.

---

### Post by Lars Noodén on 2014-04-21
Or you may be trying the wrong address.  Can you even [ping](http://manpages.ubuntu.com/manpages/trusty/en/man8/ping.8.html) the server?

```

ping *server.IP.goes.here*

```

---

### Post by bte_rajan on 2014-04-21
Here is the outcome of ping

ping server.IP.goes.here
PING server.IP.goes.here (my.IP.goes.here) 56(84) bytes of data.
From my.IP.goes.here icmp_seq=1 Destination Host Unreachable
From my.IP.goes.here icmp_seq=2 Destination Host Unreachable
-
-
-



please let me know, how can I Check my routing ?
[I]
Thanks[/I]

---

### Post by The Cog on 2014-04-21
Start with the command
```
route -n
```
which displays your routing table. I would hope to see a default route (to 0.0.0.0).

If there are no routes at all, try
```
ipconfig
```
to show the state of your network interfaces.

---

### Post by bte_rajan on 2014-04-21
Here is the output of route -n


Kernel IP routing table
Destination         Gateway           Genmask           Flags    Metric Ref    Use Iface
0.0.0.0               10.154.1.1          0.0.0.0             UG         0      0        0 eth0
10.154.0.0           0.0.0.0              255.255.0.0      U            1      0        0 eth0
169.254.0.0         0.0.0.0               255.255.0.0     U          1000   0        0 eth0

---

### Post by bte_rajan on 2014-04-21
a

---

### Post by The Cog on 2014-04-21
Routing table looks good. You have a default gateway on your network.
Let's see how far the pings get. Try this command, which gives the IP address of each hop along the way until it reaches the target (or reaches a network break and stops getting replies).
You may want to disguise some of the IP addresses if you want to keep them secret. What we are really looking for is whether you are getting out of the local area and into the public internet or not.
```
tracepath -n server.IP.goes.here
```

---

### Post by Danger_Monkey on 2014-04-21
If you want to start at the beginning, you can make sure you can ping your default gateway.  This will ensure that your NIC is, indeed working.

```

ping 10.154.1.1

```

After than, make sure you can ping machines out on hte internet by IP address:

```

ping 4.2.2.2

```

Tehn, check to make sure your DNS is working:

```

ping ubuntu.com

```

if anything fails, you will know where the problem lies.

-DM

---

### Post by TheFu on 2014-04-21
Well put DM - [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has a longer explanation, bu the same idea.

---

### Post by bte_rajan on 2014-04-22
Here is the outcome of 
tracepath -n server.IP.goes.here 1:  my.ip.goes.here                                            0.129ms pmtu 1500
 1:  my.ip.goes.here                                         2999.250ms !H
     Resume: pmtu 1500

---

### Post by bte_rajan on 2014-04-22
I am able to ping to all... that is default gateway, machines out on hte internet by IP address and DNS

---

### Post by TheFu on 2014-04-22
Perhaps I'm out of the loop, but I've NEVER heard of tracepath before. What's wrong with dig, traceroute and ping? Please educate me.

---

### Post by bte_rajan on 2014-04-24
I am Unable to connect to cluster server, when I ssh to the server. It is showing following error

ssh: connect to host server.IP.goes.here port 22: No route to host

I am new in ubuntu, using Ubuntu 12.04 

please help

Thanks

---

