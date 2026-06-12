---
title: "DNS questions"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Jjjakal on 2009-03-30
I had an extra, unused desktop sitting around so I decided to try some experimenting with servers.  I got Ubuntu Server and a LAMP stack installed on the system, and now I've got questions about how to get further.  Now I'm left with a few questions about DNS servers and how to use them, and I was hoping someone could help get me started. 
1) Is getting a domain name as simple as finding an unused domain and using it when setting up the DNS?

2) What do websites like No-ip.com do to help?

3) Are there any legal measures required in creating a DNS server?  (Registering the domain, meeting standards, etc.)

Sorry for being entirely clueless, but everyone has to start somewhere, and I figure right in the middle is a great place.

---

### Post by spiderbatdad on 2009-03-30
I think this will help: [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by metallicamaster3 on 2009-03-30
If you want a private DNS, it's pretty simple. 

sudo apt-get install bind9

That will install the software needed to run your own servers. Internally, there's no legal measures you need to read up on whatsoever.

Services like no-ip.com and dyndns.com allow you to run an external DNS using their freely available subdomains; and can update your IP every 5 minutes or so incase your ISP-assigned IP is not static.

Read up here: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Questions? Shoot me a PM

---

### Post by alphacrucis2 on 2009-03-30
> **Jjjakal said:**
> I had an extra, unused desktop sitting around so I decided to try some experimenting with servers.  I got Ubuntu Server and a LAMP stack installed on the system, and now I've got questions about how to get further.  Now I'm left with a few questions about DNS servers and how to use them, and I was hoping someone could help get me started. 
1) Is getting a domain name as simple as finding an unused domain and using it when setting up the DNS?

2) What do websites like No-ip.com do to help?

3) Are there any legal measures required in creating a DNS server?  (Registering the domain, meeting standards, etc.)

Sorry for being entirely clueless, but everyone has to start somewhere, and I figure right in the middle is a great place.

You can install bind and configure it any way you like, you can even pretend it is a root server. It will however have no effect whatsoever on the public DNS for anyone except the machines you configure to use your private DNS server. You could even set up a rival DNS system on the public internet but you might have a hard time to convince anyone to take any notice and use it. I would advise not attempting what this guy did though:

[AlterNIC]("http://en.wikipedia.org/wiki/AlterNIC")

---

