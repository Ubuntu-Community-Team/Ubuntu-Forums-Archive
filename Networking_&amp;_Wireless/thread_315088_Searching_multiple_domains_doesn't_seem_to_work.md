---
title: "Searching multiple domains doesn't seem to work"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by phyberoptix on 2006-12-08
Hi all, ](*,) 

I've set up my networking so that my pc is hostname.ca.companyname.com

Resolving items on my .ca.companyname.com network is ok, but I can't resolve hosts on the parent company's network companyname.com

Here's my resolv.conf file:
```
search ca.companyname.com companyname.com
nameserver 10.1.2.1
domain ca.companyname.com

```

When I attempt to ping sametime (which is really sametime.companyname.com) it fails, but if I ping sametime.companyname.com it works.

I thought by adding the search list, it would check each listed domain for a match but that doesn't appear to be working.

Am I missing something?

---

### Post by phyberoptix on 2006-12-11
Hello? anyone?

---

### Post by ericdegen on 2007-05-09
Same problem here. In fact when I edit the resolv.conf by hand or via the network gui tool, it reverts back to just my primary domain. 

Any help would be great.

---

### Post by sonic6567 on 2007-05-14
Hello,

I edited /etc/dhcp3/dhclient.conf and commented out the request for domain information.

This prevented my resolv.conf from being overwritten.

However, nslookup still is not searching the domains in the resolv.conf file.

Somebody help, please.

Thanks

---

### Post by ihpnun on 2007-11-19
I had the same problem.  Both the domain and search lines in the resolv.conf file seem to override the entire DNS search path.  Because the domain line is after the search line, only the domain is being searched.

I have edited by /etc/resolv.conf so the domain is on top:

[FONT="Courier New"]domain test.com
search test2.com test.com
nameserver 192.168.0.1[/FONT]

I can now search both test.com and test2.com domains.

---

### Post by coherence on 2008-01-10
Hi, I don't know if this still interests you but for anyone who stumbles across this discussion, try the contents of this thread: [http://www.webservertalk.com/message1119743.html]("http://www.webservertalk.com/message1119743.html")

Hope this helps.

cam

---

