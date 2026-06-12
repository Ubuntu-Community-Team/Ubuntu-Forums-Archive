---
title: "SAMBA with 2008 server"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by exz on 2008-04-07
Hi!

I am trying to run SAMBA as an member server with Microsoft 2008 Server. I've set up a couple of SAMBA servers with 2003 Server which have worked fine, this time i get this error when running net ads join:

```
[2008/04/07 17:49:10, 0] utils/net_ads.c:ads_startup(289)
  ads_connect: Connection refused

```

I've tried the web but noone seems to have the same problem as me, anyone have any experience with SAMBA and 2008 Server?

---

### Post by exz on 2008-04-09
OK! I've gotten a little bit closer. After upgrading samba to the latest version, I am now joined to the domain:

```
root@justitia:~# net ads info
LDAP server: 1.2.3.4
LDAP server name: ad.mydomain
Realm: mydomain
Bind Path: dc=mydomain
LDAP port: 389
Server time: Wed, 09 Apr 2008 23:23:49 CEST
KDC server: 1.2.3.4
Server time offset: 1 
```

Logns work fine:

```
root@justitia:~# ntlm_auth --username=userabc
password:
NT_STATUS_OK: Success (0x0)
```

But logging in from windows doesn't work, it just says "Be sure that your username and password is correct".

Any ideas? I could post smb.conf if anyone is interested in helping out.

---

### Post by exz on 2008-04-09
After several hours of trying I've decided to file this as a bug. [https://bugzilla.samba.org/show_bug.cgi?id=5382](https://bugzilla.samba.org/show_bug.cgi?id=5382) if anyone would encounter the same problem.

---

