---
title: "DNS server"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by aircon on 2010-02-14
Hi All,
 
Now i want to setup new DNS server for our netwrok. 
 
I m using Ubuntu server 9.10. 
 
Our company don't have a webserver, DNS server and mail server. 
 
We give this service for outsourcing.
 
I want to setup DNS server with our company domain name.
 
example abc.com
 
In my new DNS server if i setup example 10.0.0.1 abc.com it can be conflict with our outsourcing company DNS?
 
If can be conflict how can i setup for our Own DNS server for our network.
 
Now we must setup DNS server.
 
If you don't mind can someone can advise for this issue.
 
Thanks & Regards
 
aircon

---

### Post by localhost8080 on 2010-02-14
i dont think you should try to set up a dns server unless you understand what a dns server is and why they are used. oyu should also understand IP and learn what an A record is.

---

### Post by uncannybuzzard on 2010-02-14
> **localhost8080 said:**
> i dont think you should try to set up a dns server unless you understand what a dns server is and why they are used. oyu should also understand IP and learn what an A record is.

seriously, a DNS server can be a whole world of hurt. they're incredibly picky about syntax.
if you're outsourcing everything already, why would you need this even? also, in my opinion freebsd is the platform for a DNS server. in all honesty, i would never run ubuntu on a server. either debian if you must have linux, or if possible freebsd.

---

### Post by madverb on 2010-02-14
Ubuntu is fine to run as a server.
I would recommend aircon not to bother with anything like this until they understand it. Getting an inexperienced person to setup a production DNS server for a company isn't a good idea.

---

