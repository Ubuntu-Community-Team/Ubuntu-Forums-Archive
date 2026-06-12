---
title: "Java popup using squid3 and qlproxy"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by John_Haswell on 2014-09-17
Hi,  

When we try to use a site which uses Java we get a popup asking for authentication using basic method. 

I have tried adding the below into the squid.conf file but it is still doing it. Can anyone help please?  
acl Java browser Java/1.4 Java/1.5 Java/1.6 java/1.7 
http_access allow localnet Java

---

