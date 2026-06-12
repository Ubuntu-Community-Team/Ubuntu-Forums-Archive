---
title: "Ipv6 DNS address leaking"
date: 2019-04-03
forum: Networking &amp; Wireless
---

### Post by mlempenau on 2019-04-03
I am using Ubuntu 18.04 with all the updates.  I am also using a VPN that supports Ipv6.  After setting up my VPN some time ago I kept getting stuff from Thailand where I live.  I finally found doileak.com.  When I run the doileak.com test I had several issues I corrected, but one I have not been able to correct.  
**IPv6 Request Source:**

                      Your  IPv6 request and IPv4 request are coming from different  sources.2403:6200:8851:d7f9:7806:8845:5358:a895 Jasmine International  Tower (), Thailand (AS)

                              Your IPv6 request seem not  to go through the same route as your IPv4. If you are using a proxy or  VPN, make sure it supports IPv6 or you are easily identified.
                    
Doing a lookup query I get:
mlempenau@mlempenau18:~$ nslookup [www.google.com]("http://www.google.com")
Server:        127.0.0.53
Address:    127.0.0.53#53

Non-authoritative answer:
Name:    [www.google.com]("http://www.google.com")
Address: 172.217.11.36
Name:    [www.google.com]("http://www.google.com")
Address: 2607:f8b0:4006:815::2004

This tells me I have Ipv6 and for that matter Ipv4 correctly set up (I think!) so people think I'm in the US.  Yet when I run doileak.com it gets something different.  I'm not sure what to do next to determine where my leak is.  Any help would be appreciated.

One more observation.  I use Windows 10 from time to time.  I set windows up with the VPN and changed all the DNS settings.  It works just fine and without the above problem.

---

