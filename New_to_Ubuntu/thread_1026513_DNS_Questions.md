---
title: "DNS Questions"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by OneMixDJ on 2008-12-31
Greetings from a certified newbie...:)

I've been working on my Ubuntu server for DNS that I'm setting up for my internal "domains" and I have a few questions.

1. Is having my own ".com" domain a requirement?

My Ubuntu server has a dual NIC for internal and DMZ networks.
I only want my DNS server to resolve two internal domains and let the DNS servers from my ISP handle all the external stuff (.com, .net, etc...).


Basically, my internal domain suffixes would be:

.homenet - for my internal network (172.26.75.0/24)
.dmz - for my internal dmz (192.168.26.0/24)


2. In /etc/bind/named.conf.local, am I only limited to one zone or can I set up a zone for each internal domain? Since they are both to be independent from each other, would both zone types be set to "master"?

3. Since these domains are internal only, do I still need to configure the DNS servers from my ISP as the forwarders since they are only for my internal networks?

Sorry for all the questions all at once, but I'm trying to get this right. :)

Thanks in advance!

---

### Post by OneMixDJ on 2008-12-31
*bump*

---

### Post by OneMixDJ on 2009-01-01
Is there anyone who knows the answers to my questions above? 
Thanks!

---

### Post by DGortze380 on 2009-01-01
You may have better luck in the Networking forum: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Don't know much about DNS, but one basic question I can answer... Yes, you can use a local DNS for internal domains and forward the local to your ISP's DNS if the address is not resolved at in the Local DNS.

---

### Post by OneMixDJ on 2009-01-01
Thanks DGortze380, I'll try there...   :)

---

