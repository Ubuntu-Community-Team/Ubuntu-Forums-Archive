---
title: "samba and ldap"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by call_krushna on 2010-06-19
Hi,
  
    We have LDAP server for authentication and separate samba server used as a file server.All client machine runs windows. How to integrate file server (samba server) with LDAP server so that there will single point of authentication.

regards
Krushna

---

### Post by luvshines on 2011-01-23
Maybe my reply is toooo..... late :D

I think you will need to migrate Samba user accounts to LDAP server and change Samba configuration to fetch authentication/authorization data from LDAP server

---

