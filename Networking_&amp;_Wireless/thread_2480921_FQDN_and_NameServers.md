---
title: "FQDN and NameServers"
date: 2022-11-14
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2022-11-14
Folks,

Recently I have been experimenting with DNS settings.   I have three FQDNs with uk2.net

I think therefore uk2.net is my authorative Name Server

I understand A names point to an IP address, I understand cnames are aliases that point to an A name.

What is confusing me is I am given a choice of adding name servers.  By default it shows three Name Servers, dns1.uk2.net then dns2 then dns3 etc

I am guessing as uk2.net is my authorative NS then using their Name Servers would be logical, maybe I am wrong.  Appreciate an alternative useful in case uk2.net fails but would there be any reason to have something other than uk2.net?

Geoff

---

### Post by TheFu on 2022-11-14
A domain name is something bought from a registrar.  It is about 20 records that usually get modified once every 1, 5, 10 yrs.  A 3x5 card could easily hold the data.  Part of the data points at a primary (authoritative) and a secondary DNS server.  

The DNS for the domain doesn't need to be from the same company. It can  (and I'd argue SHOULD!) be at a different company.  If you have a solid internet connection, you can even host your own DNS, but there are risks in doing that, since nefarious people like to take over DNS records.  Around 20 yrs ago, my public DNS was hacked because I was a few months behind on patching.  It didn't need to be public. I messed up.  

Then there's the servers that sit at specific IP addresses that are available for web, mail, gopher, SOAP, APIs, and other network needs.  There are multiple types of DNS records - find a table with all of them. There aren't many. Some record types have become multi-purposed like the TXT record is used for DMARC and SPF stuff.  These servers can be in someone else's data center or at your home or on shared systems spread all around the world. It is up to you.

So, there are 3 different things for the internet to work.  All three can be bundled or all three can be separate.  I keep them separate as a way to prevent 1 company from having too much power over the public internet needs.  It also means that I need an understanding of each portion so the connections from A --> B --> C happen.
[https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) explains all this, hopefully, a little clearer.

BTW, the NS entries need to be specific IP addresses where you've entered the CNAM/A/MX/TXT/SOA records. Be certain to bump the ID for each record a little higher, so the changes are replicated out.  Also, may want to start with a TTL of 10 minutes and slowly up that time to 1 week as you are positive that all the records are correct.  The downside is that to make any changes, you'll need to change the DNS TTL  back down and wait upto that former TTL before making nearly seamless DNS record changes.  DNS services often charge by the number of queries, so a longer TTL should reduce the number of queries as local DNS caching saves the answers for that TTL value (or until a reboot).  Of course, if this is a corporate thing, just pay the DNS the $20-$40/yr they want and be done with it.  

For my personal domains, I want to stay under the free plan query limits, so even the $20/yr (that was the price last time I looked) isn't necessary.

---

### Post by Geoff_Lane on 2022-11-15
Thank you, a very in depth reply.  Link is useful too.

For my own use I have a private domain merely for friends and relatives so not available for public use.  Two others are experimental with cloud services, just a learning curve really.

Seems my TTL maximum is 86400 (one day).  Can have less but not more.

Strangely I have noticed, if I have any aliases in my /etc/hosts file the alias cannot begin with a number, (maybe it thinks it is an IP address) it can have a subsequent number though.  p62 is ok but 62p doesn't seem to work.

Geoff

---

### Post by TheFu on 2022-11-15
[https://www.ietf.org/rfc/rfc1035.txt](https://www.ietf.org/rfc/rfc1035.txt) spells out the requirements for names.
```
2.3.1. Preferred name syntax
...
The labels must follow the rules for ARPANET host names.  They must
start with a letter, end with a letter or digit, and have as interior
characters only letters, digits, and hyphen.  There are also some
restrictions on the length.  Labels must be 63 characters or less.
```

Both the rules for DNS and for hostnames must be met. There are specific rules for different types of services, which must also be met.
[https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)
 2.1  Host Names and Numbers
 .... says they changed it to allow beginning with a number and, optionally, to increase the length of a hostname to 255 characters.  63 characters is mandatory. 255 characters is a "SHOULD" requirement.
The parsing systems (programs/OS) have to recognize an IP address as an IP address anywhere a FQDN could be used.

You've probably read these sections already.  RFCs tend to be no-nonsense, clear, requirements.

Any domain name that can be reached by the internet without a VPN, isn't private.  People scan every IP, every 5 minutes looking for new servers.  If you use any TLS certificates, those names are also discovered, since they are public too, just like DNS domain name registrar names.  Even if you capture requests that don't correctly specify the host and redirect it somewhere else, chances are that your ISP or one of the browsers or browser addons will leak the name of your webserver.  I remember when google was new and didn't honor my robots.txt, then specifically indexed parts of my "private" website that was never intended for anyone except family. Beware. If you don't actually make it impossible to access by outsiders, then it will be found, indexed, and searched.

---

### Post by Geoff_Lane on 2023-01-03
I do wonder on occasions how it all works.  Flashes across the world in the blink of an eye.

We've come a long way since dot dot, dash dash.

Geoff

---

