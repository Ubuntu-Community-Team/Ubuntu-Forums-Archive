---
title: "ISP's DNS sucks; what DNS cache / proxy to set up?"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by MikeBenza on 2007-08-03
My ISP's DNS just plain sucks.  Here is a sample from a windows machine:

```
C:\>nslookup en.wikipedia.org
Server:  ns.direcpc.com
Address:  66.82.4.8

DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
*** Request to ns.direcpc.com timed-out

C:\>nslookup en.wikipedia.org 4.2.2.2
Server:  vnsc-bak.sys.gtei.net
Address:  4.2.2.2

Non-authoritative answer:
Name:    en.wikipedia.org
Address:  66.230.200.100


C:\>nslookup en.wikipedia.org
Server:  ns.direcpc.com
Address:  66.82.4.8

Non-authoritative answer:
Name:    en.wikipedia.org
Address:  66.230.200.100


C:\>nslookup en.wikipedia.org
*** Default servers are not available
Server:  UnKnown
Address:  127.0.0.1

*** UnKnown can't find en.wikipedia.org: No response from server

C:\>nslookup en.wikipedia.org
*** Default servers are not available
Server:  UnKnown
Address:  127.0.0.1

*** UnKnown can't find en.wikipedia.org: No response from server
```

So I changed my DNS 4.2.2.2 and 4.2.2.3:

```
C:\>nslookup en.wikipedia.org
Server:  vnsc-bak.sys.gtei.net
Address:  4.2.2.2

Non-authoritative answer:
Name:    en.wikipedia.org
Address:  66.230.200.100

```

Changing ISPs is not an option.

I'm running an Ubuntu file server, which I'd like to set up for DNS for my network.  Am I looking for a dns cache or a dns proxy?  What's the difference?  Do you have any suggestions?  I can set up the machine as a gateway, too, but I'd prefer to do that only if needed.

- Mike Benza

---

### Post by stalker145 on 2007-08-03
I had problems with my ISP's DNS being slow and unreliable as well. I got a free account with [OpenDNS]("http://www.opendns.com/"), pointed all of my computers at their DNS servers, and haven't had a problem since.

Just a thought.

---

### Post by attadaved on 2008-04-17
Check out [http://www.dnsenquiry.com/](http://www.dnsenquiry.com/) A great dnsstuff.com replacement.

---

