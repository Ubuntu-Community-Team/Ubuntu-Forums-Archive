---
title: "ssh to server internet problems"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Jusdogmatik on 2009-05-21
I've been connecting to a server my Brother and I have set up (which is running Ubuntu 9.04 Server edition), through ssh and my own computer and while I am not having any problems connecting to it I am not able to connect to the Internet through the server. What I mean is that while I am connected to it when I try to install something with the sudo apt-get install command it will load everything up going through all the list and set it up for installation but when It actually tries to download the files It won't connect. When I try to access a web site through w3m it, again won't connect. 

I'm not entirely sure whats going on here. Our server is set up through the same network as all of out other computers in the house and none of them are having any problems connecting. Is it just the limitations of ssh? I highly doubt that but I really can't figure out anything else.

---

### Post by asmoore82 on 2009-05-21
Just a wild guess -
If it's to be "server" you guys may have given it a static IP address;
When you go this route you have to also manually give it a Default Gateway and DNS nameserver.

---

### Post by Jusdogmatik on 2009-05-21
Well we have never had a problem getting online in the past. When we first set it up I checked my email on it a few times and used Google to help me out on installing a few things on it.

---

### Post by alphacrucis2 on 2009-05-21
> **Jusdogmatik said:**
> Well we have never had a problem getting online in the past. When we first set it up I checked my email on it a few times and used Google to help me out on installing a few things on it.

What do you get in response to this command on the server:


```
route
```

---

### Post by Jusdogmatik on 2009-05-21
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by alphacrucis2 on 2009-05-22
> **Jusdogmatik said:**
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0


OK. You want to check dns is working next. What do you get from:

```
dig www.google.com
```

---

### Post by Jusdogmatik on 2009-05-22
; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached

---

### Post by alphacrucis2 on 2009-05-22
> **Jusdogmatik said:**
> ; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached

Maybe you can't even get to the default gateway. Try:

```
ping -c 5 192.168.1.1
```

Also

```
ifconfig
```

---

### Post by Jusdogmatik on 2009-05-22
Well for ping I got

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.110 icmp_seq=1 Destination Host Unreachable
From 192.168.1.110 icmp_seq=2 Destination Host Unreachable
From 192.168.1.110 icmp_seq=3 Destination Host Unreachable
From 192.168.1.110 icmp_seq=4 Destination Host Unreachable
From 192.168.1.110 icmp_seq=5 Destination Host Unreachable

I think I am going to worry about this in the morning. I had a long day at work and I am about to fall out. Thanks for all your help man.

---

### Post by alphacrucis2 on 2009-05-22
> **Jusdogmatik said:**
> Well for ping I got

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.110 icmp_seq=1 Destination Host Unreachable
From 192.168.1.110 icmp_seq=2 Destination Host Unreachable
From 192.168.1.110 icmp_seq=3 Destination Host Unreachable
From 192.168.1.110 icmp_seq=4 Destination Host Unreachable
From 192.168.1.110 icmp_seq=5 Destination Host Unreachable

I think I am going to worry about this in the morning. I had a long day at work and I am about to fall out. Thanks for all your help man.

Hmmm. Looks like you may have a subnet mask problem. You may have missed it but try this command I mentioned above

```
ifconfig 
```

You need to verify that the subnet mask is correct.

---

### Post by anewguy on 2009-05-22
Follow asmoore82's advice:  you probably do have a static ip on your server, and as such you need to specify the default gateway and dns.  The samba.conf file contains this, and there are tutorials on the net for setting these up.

I ran an Ubuntu server for a while, wireless, and I had to specify a static ip address and in turn the default gateway and dns.

Dave :)

---

### Post by alphacrucis2 on 2009-05-22
> **anewguy said:**
> Follow asmoore82's advice:  you probably do have a static ip on your server, and as such you need to specify the default gateway and dns.  The samba.conf file contains this, and there are tutorials on the net for setting these up.

I ran an Ubuntu server for a while, wireless, and I had to specify a static ip address and in turn the default gateway and dns.

Dave :)

He has set a default gateway as shown by the output of the route command. The main problem initially is that the machine is unable to actually talk to the default gateway.

---

### Post by asmoore82 on 2009-05-22
> **alphacrucis2 said:**
> Hmmm. Looks like you may have a subnet mask problem. You may have missed it but try this command I mentioned above

```
ifconfig 
```

You need to verify that the subnet mask is correct.

[SIZE="3"]**+1**[/SIZE] for `ifconfig` and maybe add
```
cat /etc/resolv.conf
```

---

