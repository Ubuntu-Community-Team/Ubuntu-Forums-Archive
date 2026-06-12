---
title: "Domain to home server?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by sheldonnbbaker on 2009-10-10
Hey everyone,

Forgive me for asking a question that has probably been asked many times - I haven't been able to find a straight answer.

So I've finally got a new ISP that doesn't block incoming connections to my home network, and I have a domain name (purchased at netfirms.ca). I would like to forward all subdomains, mail, etc. to my home server (I have set up an address at dyndns.org).

For mail I set MX records, but how do I send all requests to example.com and all subdomains (sub1.example.com or (somerandomsubdomain.example.com) to my server?

I tried using A records but they only accept IPs - not name-based URLs.

Thanks for your help :)__

---

### Post by SkyNet2029 on 2009-10-10
the 'name' portion of a host always translates into a corresponding IP address. that is what the DynDNS service is for. Domain Name Resolution. You will need to point the A record at the DynDNS address.
If you do a whois on the DynDNS name portion, it should give you the registrar listing, along with the proper IP to use for A record transfers

---

### Post by uncannybuzzard on 2009-10-10
> **SkyNet2029 said:**
> the 'name' portion of a host always translates into a corresponding IP address. that is what the DynDNS service is for. Domain Name Resolution. You will need to point the A record at the DynDNS address.
If you do a whois on the DynDNS name portion, it should give you the registrar listing, along with the proper IP to use for A record transfers

what? i'm not familiar with dyndns and their setup may be atypical but it breaks down like this:
A records are subdomains more or less. 'www' would be an A record, so you can point [www.domain.tld](www.domain.tld) at one server, and domain.tld at another. what you're referring to is known as a 'star record', which is just another A record, but instead of say 'www' you'd use an asterisk. it forwards all non-matching requests to an ip address. so, you could have the A record for www pointed at server 1, * pointed at server 2, and domain.tld pointed at server 3 (this is typically defined as a blank A record). so *.domain.tld would match server 2, which is what i think you are looking for? sorry if this is rambling.

---

### Post by sandyd on 2009-10-10
set a CNAME record pointing at your dyndns.org account.

for the wildcard subdomains, do "*.example.com"

it should work.
or at least it works on servers running BIND.

---

