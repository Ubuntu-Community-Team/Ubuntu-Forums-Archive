---
title: "How do you set a domain name?"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by Bagboy23 on 2008-11-30
Hi, I'm trying to setup a domain name (oracle.com) on my PC. The computer name is "oracle" which I am assuming is the hostname also?

So my overall hosts file looks like this:

127.0.0.1   oracle localhost.localdomain localhost

This doesn't seem to work for some reason. Can someone help?

Thank you.

---

### Post by cmnorton on 2008-11-30
127.0.0.1    my-server.my-domain localhost.localdomain localhost

Please note that in Windows, our domain is really known as my-domain.local. I don't know why it was set up this way, but I only list my-domain as the domain name.

Is this for samba, because you have to set it up there as well (/etc/samba/smb.conf).

---

### Post by Bagboy23 on 2008-12-01
> **cmnorton said:**
> 127.0.0.1    my-server.my-domain localhost.localdomain localhost

Please note that in Windows, our domain is really known as my-domain.local. I don't know why it was set up this way, but I only list my-domain as the domain name.

Is this for samba, because you have to set it up there as well (/etc/samba/smb.conf).

So would that be:

127.0.0.1
127.0.0.1 oracle.localdomain localhost

---

### Post by superprash2003 on 2008-12-01
where do you want to access this domain name from?? from your own pc?? from your LAN pcs or from the internet?

---

### Post by Bagboy23 on 2008-12-01
> **superprash2003 said:**
> where do you want to access this domain name from?? from your own pc?? from your LAN pcs or from the internet?

I'm trying to access from my own PC and LAN. Any suggestions.

---

### Post by Iowan on 2008-12-01
> **Bagboy23 said:**
> So would that be:

127.0.0.1
127.0.0.1 oracle.localdomain localhost
Leave 127.0.0.1 as localhost.
Make 127.0.1.1 oracle.localdomain oracle:
```

127.0.0.1 localhost
127.0.1.1 oracle.localdomain oracle
```
This may not solve the problem, but it's more the right direction...

---

