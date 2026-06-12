---
title: "Proxy with AD integration"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by eluzi on 2007-10-01
I'm in a network where the proxy has Active Directory integration, so the Ubuntu server i've just come up isn't capable of getting through to the internet. 

   I´ve tried setting http_proxy variable like...

```
 eluzi@server# http_proxy="http://ip: port/"  
```

  ...but it won't work... I noticed under Firefox that it actually uses a config script. So there I have "http://ip:port/something.pac". Tried this too under ubuntu, but no luck...

   After googling a while I tried:

```
 eluzi@server# http_proxy="http://login:password@ip:port/"  
```

  But no luck also...

Well, anyone got ideas on how to make it work ? Thanks in advance ! :)

---

