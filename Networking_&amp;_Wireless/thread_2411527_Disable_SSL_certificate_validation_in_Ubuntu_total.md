---
title: "Disable SSL certificate validation in Ubuntu totally"
date: 2019-01-31
forum: Networking &amp; Wireless
---

### Post by nikhil.kadi on 2019-01-31
Hi All,

I am new to Linux and learning Linux on Ubuntu 18.0401 LTS installed on oracle virtualbox on company system. **Company has private proxy network**. So all the websites I browse on ubuntu **pass through proxy and get ssl certificate issued by the company**. 
When I browse from chrome/firefox it gives error like not a trusted source. When I go to > advance > add exception I can browse that particular website for some time and then again after some time same error (probably certificate details changes)
In browser atleast I can browse after such effort but the **Ubuntu software** does not even give such option and I am simply **not able to download any software**. Also CLI **apt-get dont work**.
Can someone tell a way to configure such a way that we **completely bypass ssl validation system wide**? something like **--disable ssl certificate validation**.. So that I am able to seamlessly connect to internet ? (of course websites blocked by proxy will still be blocked)

Thanks a ton in advance!!

NK, Linux enthusiast

**PS:** Below is the error on firefox;

**"Your connection is not secure**

**The owner of support.mozilla.org has configured their website improperly. To protect your information from being stolen, Firefox has not connected to this website."**

---

