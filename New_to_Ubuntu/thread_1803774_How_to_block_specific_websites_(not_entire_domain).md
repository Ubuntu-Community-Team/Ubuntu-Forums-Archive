---
title: "How to block specific websites? (not entire domain)"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by jayi on 2011-07-13
Hi, I am trying to figure out a way to block very specific websites. I know about Firefox addon's like Leechblock and I know a little bit about how to redirect to localhost with /etc/hosts, but from what I can tell... these tools only block entire domains.

How would I go about doing something like this:

Block web addresses:
[www.example.com]("http://www.example.com") (only the homepage)
example.com (only the homepage)
[www.example.com/news/*]("http://www.example.com/news/*") (the * is a wildcard)
example.com/news/*
[www.example.com/shopping/hello.html]("http://www.example.com/shopping/hello.html")

Not blocked web addresses (assuming it does not match the blocked web address list):
[www.example.com/shopping/*]("http://www.example.com/shopping/*")
example.com/shopping/*

So there are are specific parts within a domain that I am trying to block, but not the entire website. Is there some tool or method to do this kind of blocking in ubuntu? It's just for personal use to help me focus when I work.

---

### Post by mikejonesey on 2011-07-13
easyest way i'd guess would be to change your isp dns to one like [http://www.opendns.com/](http://www.opendns.com/) who allow you to block pages, sites... also open dns is supposed to speed up web browsing at the same time with faster dns resolution...

---

### Post by jayi on 2011-07-13
> **mikejonesey said:**
> easyest way i'd guess would be to change your isp dns to one like [http://www.opendns.com/](http://www.opendns.com/) who allow you to block pages, sites... also open dns is supposed to speed up web browsing at the same time with faster dns resolution...

Thanks for that link, it looks like an interesting service that I will look into, but I see it also has some limitations for free users.

If possible, I wanted to use something that wasn't proprietary even if it is more work.

---

### Post by mikejonesey on 2011-07-14
diy: the long road would be to setup a dns server (bind) with custom rules, setup all machines on netowrk to use the one pc with bind as the dns server, the pc with bind would then have to have it's name resolution order set /etc/nsswitch.conf...

diy alternative; using a proxy server to connect to the net (all pcs on network are blocked from internet par one, which all use as a proxy), on this proxy server you can then set rules... eg if you use squid as the proxy server, you can also install webmin to configure this and set rules to block... or you can use squid guard

other solutions: include "time lock" software that block software / websites...

all would take some time and never be as reliable or fast as a reliable dns with a few rules...

---

