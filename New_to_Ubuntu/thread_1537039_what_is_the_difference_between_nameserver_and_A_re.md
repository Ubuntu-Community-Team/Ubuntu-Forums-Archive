---
title: "what is the difference between nameserver and A record?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by 007casper on 2010-07-23
Some hosting companies dont require for you to enter nameservers.  They just give you an IP and ask you to create a new A record to map hostnames.

what is the difference between nameserver and A record?  
and what are the advantages and disadvantages?

---

### Post by Tylerjd on 2010-07-23
A nameserver is a DNS server that has a name like NS17.DOMAINCONTROL.COM and would tell where your were a website is located aka IP address ([http://en.wikipedia.org/wiki/Name_server](http://en.wikipedia.org/wiki/Name_server))

An A record is the actual record at which the translation happens:
google.com IS 74.125.67.103

---

### Post by 007casper on 2010-07-23
I read that link over at wikipedia before. 

I am just trying to figure out the difference between A record and NS record.

If I were to host friends, what is preferable to give them NS record, or A record.

I am just trying to grasp the overall picture.

you can use A record for subdomains, and to map domains etc.  

And by mapping a domain with the A record you can host mx, mysql elsewhere.  However, if you move your server to another datacenter, and if you dont own/have your own "AS" record, then you need to notify everyone to update their A record with the new IP that you get from the new datacenter. 

However, the only thing I can think of is that NS record is better, because when the IP number changes, the DNS can look for it through nameservers.  It doesnt matter if the IP changes, it will find the nameserver that points to a certain IP.  Thus, you dont need to notify anyone.

am I mistaken?

some hosting companies gives you an IP number to use as A record, and other hosting companies gives you their name servers.

how come?  

I am just trying to figure out the cons/pros and the differences between the two

---

### Post by 007casper on 2010-07-23
bump

---

### Post by 007casper on 2010-07-23
I found this online... it is exactly what Tylerjd is saying.
> The "Nameserver" record that identifies the nameserver (DNS server) that is authorative for the zone. The other is an A record, or the "Host" record that identifies the record. The NS record is based on the A record, and all DNS servers must identify themselves as authorative for a zone.

How is NS record is based on the A record.  You can have totally different A record, that has nothing to do with NS record, like when you use public DNS servers.

so A record is used when the hosting company doesnt want you to use their DNS server

???

---

