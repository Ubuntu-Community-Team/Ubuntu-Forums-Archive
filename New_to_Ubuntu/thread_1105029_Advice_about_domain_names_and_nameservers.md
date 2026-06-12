---
title: "Advice about domain names and nameservers"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-03-24
I would like some advice concerning domain names and nameservers.  I finally registered domain name with GoDaddy. This is just one that I made u* (sorry, the key for the letter between  o and q does not work now, along with a few other keys, dont know why.  Anyway, I had an account at DynDNS where I got free nameservers, but that was before I got the domain, so my hostname uses THEIR domain, with my name that I always *lanned to use as a domain, at the beginning as a sub-domain, so it is something like this-  FabWebs.homelinux.com.  I would like it to just be FabWebs.com. I  had chosen DynDNS, because my router lists that service, on a dro* down list with two other services (TZO,org, and disabled. But DynDNS charges to give nameservers to my own domain, so I guess my question is-  Is there a free nameserver service (I have dynamic i* and need it to be static( that will let me use my own domain name without charging, and the second question is, how do I let my router or server know  how to use this info, as it only shows for TZO and DynDNS  I guess what I SHOULD have done was instead of buying the domain for GoDaddy, should have registered my domain with DynDNS, then they would serve it for free. oh well :)

---

### Post by paultag on 2009-03-24
if all you want it one-way, you can either set up a subdomain on GoDaddy to forward, or mask the page. The second is to point your whole domain to the dynamic domain.

But then you can't really use hoasting.

Cheers,
Tag

---

### Post by Lakeside5 on 2009-03-24
Well after my nice long rambling...I remembered that GoDaddy gives free nameservers as a service for the domain name I bought there. I guess what I should have asked was, where does that info go- the name of their nameservers, like ns51.domaincontrol.com. I cannot enter it into my router, like I could for the DynDNS info on nameservers.

---

### Post by paultag on 2009-03-24
I can only assume you are again, talking about a dynamic DNS service.

GoDaddy assumes that you will have the server hosted, on a staticly IP'd box. In the real world, DNS servers take hours to update. The reason is it needs to propegate across the chan of DNS servers that we call 'teh interwebz'. Dynamic DNS services work in a different manner, allowing the client to update their IP by way of Client, Script, or yes, even a friendly chunk of code in the router. Not all DNS servers work this way.

You can assign your GoDaddy Domain to forward to your dynamic Domain, if this is in fact what you want to do.

I am still unsure of what the query is.

---

### Post by Lakeside5 on 2009-03-24
I am  trying my hand at webhosting, so I installed Hardy Heron Server on here. I do not have a static ip from my ISP, so I was looking for free nameservers. DynDNS is good because my router even has a drop down box where I can chose it as a service for dns (on the DNS page).  The problem is, if I then want to use my OWN domain name that I just payed to register at GoDaddy, instead of a DynDNS domain, they will charge for that,if they even allow that. GoDaddy has nameservers for my domain, BUT I am unsure of where to enter that info (name of their nameservers) in my router or whatever.  Maybe I don't understand this whole webserving stuff, but I thought you get a domain, get dns sservice for it, configure the router to work with dns, etc.

---

### Post by paultag on 2009-03-24
I don't think you fully understand how this works.

Perhaps work a bit on learning and understanding how this works, read a bit more about DNS servers.

---

