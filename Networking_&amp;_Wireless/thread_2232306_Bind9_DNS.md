---
title: "Bind9 DNS"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by MRHadoop on 2014-07-01
Hi 
I have configured Bind9 DNS server on internal Virtual Ubuntu 12.4 LTS machines 

I have dev.local as domain

It works only for forward resolution but reverse resolution does not work. Last week somewhere I found post which mentioned the issue in case of .local domains and I did the changes for one machine and it worked 

But now I am not able to find that link and need to make changes to other machine Please help out

Regards

---

### Post by kira_belka2 on 2014-07-01
For reverse resolution you have to use PTR record I suppose

---

### Post by MRHadoop on 2014-07-02
Hi
The PTR record is defined correctly. I can do hostname ip and it returns fqdn correctly.

Issue I see is ping with hostname and IP workds but ping with FQDN doesn't work like ping server.dev.local. doesnt resolve.

I read somewhere it was due to .local part in domain on ubuntu and there was some file in /etc which needed specific update but I have now lost that link

---

