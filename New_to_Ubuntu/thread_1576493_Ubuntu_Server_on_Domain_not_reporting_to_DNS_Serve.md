---
title: "Ubuntu Server on Domain not reporting to DNS Server"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Jloser on 2010-09-17
I just introduced our first Ubuntu server to our domain.  Not 100% sure how everything works, but the new ubuntu server isn't reporting it's static IP address to our DNS servers, so I cannot access it by hostname.  Is there a simple fix to allow this to happen?

---

### Post by SlugSlug on 2010-09-17
a simple fix would be to manually add it to the records

---

### Post by Jloser on 2010-09-17
Agreed, that would be simple, but I meant a way to have the new server communicate directly with the DNS server so that next time if it is dynamic we know how to resolve it.

---

### Post by JKyleOKC on 2010-09-17
> **Jloser said:**
> Agreed, that would be simple, but I meant a way to have the new server communicate directly with the DNS server so that next time if it is dynamic we know how to resolve it.If your DNS server allows other systems to register themselves with it, then anyone (such as a spam robot) could do so. This is a serious security issue; such possibilities have happened in the past, leading to the class of vulnerabilities known as "DNS poisoning" that result in malware sites being able to masquerade as your own site names.

Commercial services that do permit servers hosted at dynamic addresses exist, but they depend on having a "heartbeat" program at the dynamic address periodically reporting its address to the DNS server. This adds overhead, both at the client server and the DNS server, and increases the network traffic. If it's an enterprise server you're dealing with, it should have a static address and the DNS zone files should be manually updated to include it.

---

### Post by Jloser on 2010-09-17
So there is no way to authorize an Ubuntu server onto a Windows domain?

---

### Post by Grenage on 2010-09-17
You can log onto a desktop with NT network credentials, and that would likely sort the DNS.  I've net done it on a server, but the theory is the same.

All our servers have static IPs.

---

