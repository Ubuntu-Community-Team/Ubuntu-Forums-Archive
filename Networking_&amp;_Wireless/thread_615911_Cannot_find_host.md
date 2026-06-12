---
title: "Cannot find host"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by mercedcollege on 2007-11-17


I am working with a Sun spar 6.06 LTS cluster. the nodes have all  static  ip address and they are all talking within the network. I have ssh client install on all the nodes. I use Putty to ssh in to them But the Nodes aren't talking to the outside world. (yahoo.com etc) 

I have all my configurations set up 

/etc/network/interfaces
/etc/network/resolv.config

I cant Ping the hostname but I can ping the host IP Adrees

(ex) Ping: [www.yahoo.com](www.yahoo.com) host not found

What can be the problem

---

### Post by Brautigam on 2007-11-17
have you checked your network status yet?

---

### Post by mercedcollege on 2007-11-17
these nodes dont have GUI Interface 

Ifconfig says there all talking

I cant use apt-get install because I cant talk to the sever

---

### Post by mercedcollege on 2007-11-17
I will post all of the configurations I have on Monday

It's possible a DNS error

---

### Post by netreg on 2007-11-17
have you checked your dns entries?

---

### Post by mercedcollege on 2007-11-19
The configurations are 

/etc/network/interfaces

Address 10.64.5.2
netmask 255.255.248.0
gateway 10.64.0.1
network 10.64.0.0
broadcast 10.64.7.255
 
/etc/resolv.config

nameserver 10.64.0.6

I try nslookup host and it connection timed out 

some nodes don't have the dns entries  but they work.

The big picture: I want to install basic-essentials and perl (perl is one the cd). To run a MIS clustering program. (CDS Cluster) I only have one node install basic-essentials and perl I have 18 nodes to go and this talking awhile to install these two problem that are requirld by the cluster program 

Any help would be nice :(

---

### Post by mercedcollege on 2007-11-19
The configurations are 

/etc/network/interfaces

Address 10.64.5.2
netmask 255.255.248.0
gateway 10.64.0.1
network 10.64.0.0
broadcast 10.64.7.255
 
/etc/resolv.config

nameserver 10.64.0.6

I try nslookup host and it connection timed out 

some nodes don't have the dns entries  but they work.

The big picture: I want to install basic-essentials and perl (perl is one the cd). To run a MIS clustering program. (CDS Cluster) I only have one node install basic-essentials and perl I have 18 nodes to go and this talking awhile to install these two problem that are requirld by the cluster program 

Any help would be nice :)

---

### Post by mellowd on 2007-11-19
What happens if you do this:

```
traceroute yahoo.com
```

How far does it get?

---

### Post by mercedcollege on 2007-11-19
I hadn't try that yet 

On wedneday I will try that

---

### Post by mercedcollege on 2007-11-21
that command isn't vailld

---

### Post by mellowd on 2007-11-22
What does it say? traceroute is a standard terminal command

---

### Post by jetsam on 2007-11-22
I was surprised by this recently, but traceroute isn't in the default install.  I recently had to apt-get it onto a few machines.  

Can you ping the nameserver?
```
ping 10.64.0.6
```

Dig might shed some light:
```
dig www.yahoo.com
```

also:
```
dig 208.67.222.222 www.yahoo.com
```

The second dig tries a DNS lookup using an openDNS server.  If it works you could put 
```
nameserver 208.67.222.222
``` at the top of your resolv.conf file, then try to apt-get the packages.  That's a hack, though, and you'd want to take it out afterwards and troubleshoot your DNS.

---

### Post by mellowd on 2007-11-22
Not by default on the desktop? I'm suprised. I reccomend installing. It's a valuble network troubleshooting tool

---

### Post by mercedcollege on 2007-11-26
> **jetsam said:**
> I was surprised by this recently, but traceroute isn't in the default install.  I recently had to apt-get it onto a few machines.  

Can you ping the nameserver?
```
ping 10.64.0.6
```

Dig might shed some light:
```
dig www.yahoo.com
```

also:
```
dig 208.67.222.222 www.yahoo.com
```

The second dig tries a DNS lookup using an openDNS server.  If it works you could put 
```
nameserver 208.67.222.222
``` at the top of your resolv.conf file, then try to apt-get the packages.  That's a hack, though, and you'd want to take it out afterwards and troubleshoot your DNS.
 
yes i can ping dns

dig say 
global options printcmd
connection time out

and for the open dns server i got nothing

---

### Post by jetsam on 2007-11-26
...bumping this because it's beyond me.:confused:

mercedcollege, you might be best off consulting the networking folks at your school.

It seems an interesting project; I wish I could help more.  If I had to guess, I'd say that a firewall was blocking the dns, but I'd also guess that the firewall isn't on the cluster, so you'll have to bring in the IT staff at some point...

---

### Post by mercedcollege on 2007-11-27
Thank you for all of your help

---

### Post by mellowd on 2007-11-28
Have you tried installing and running a traceroute yet?

---

