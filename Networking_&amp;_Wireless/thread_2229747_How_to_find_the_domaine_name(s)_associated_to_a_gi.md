---
title: "How to find the domaine name(s) associated to a given IP?"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by Mariane on 2014-06-15
Hi, 

To find the IP of a domain name, an easy way is to ping: 
```

ping ubuntuforums.org

```
and then "control C" to stop. The IP 91.189.94.12 appears between brackets. 

But how to do the reverse? What command could I type, using 91.189.94.12, which would tell me "ubuntuforums.org"?

---

### Post by Morbius1 on 2014-06-15
```
whois 91.189.94.12
```
Will give you more information than you'd ever need.
```
host 91.189.94.12
```
Will give you the url but not the one you are expecting because 91.189.94.12 doesn't resolve to ubuntu.org. It resolves to [www.canonical.com]("http://www.canonical.com").

The easiest way is to put the ip address in your internet browser.

---

