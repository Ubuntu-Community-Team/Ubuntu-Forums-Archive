---
title: "How can companies sniff HTTPS through proxies ?"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by vikrant82 on 2008-07-16
Hi friends, 

I was just wondering, various ways corporate companies might sniff our HTTPS traffic. 

I am sure the ideal way is to provide us an HTTPS proxy and install the proxy certificate as trusted certicates in our browser certificate stores then they can easily and effectively do a man in the middle.

Normally they give us a HTTP proxy. Do you think they can still have another HTTPS gateway next to the HTTP proxy, (with its certificate also installed in browser certificate stores). Could they still do a MITM?

I am sure they wont't be letting us fly free by simply putting an https://

One way of testing this, could be manually SSHing into a remote machine without the proxy, Next time when I ssh again with the proxy, it should compain that the key pair has changed etc... But this could only be done at the start when ssh proxy was not there at all

Any thoughts on what tricks companies might be putting in ? Or the ways, we can identify a MITM ?

---

