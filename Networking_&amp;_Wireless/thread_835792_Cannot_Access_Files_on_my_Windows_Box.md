---
title: "Cannot Access Files on my Windows Box"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by punjabdasher on 2008-06-20
I just received my new laptop today, and I installed Ubuntu on it. I haven't had any problems with the installation, but I have run into one hitch. When I try to access my network files that I am sharing off my Windows PC, it does not want to show me my PC on my MSHOME network. Any help would be appreciated, I need to migrate about 20 gigs of data, and I'm not looking forward to burning all that onto DVD's. :( 
Thanks again for your help!

---

### Post by superprash2003 on 2008-06-20
go to places->Computer and type smb://x.x.x.x where x.x.x.x is the ip of the windows machine

---

### Post by punjabdasher on 2008-06-20
> **superprash2003 said:**
> go to places->Computer and type smb://x.x.x.x where x.x.x.x is the ip of the windows machine
Unfortunately it doesn't work, says there is no such file or directory. The machine does respond to ping though.

---

### Post by cariboo on 2008-06-21
Are the ip addresses on both computers in the same net block eg:

```
ubuntu  192.169.0.1
windows 192.169.0.2
```


Jim

---

