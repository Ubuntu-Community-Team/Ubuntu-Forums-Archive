---
title: "Autofs + LDAP + rfc2307bis.schema"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by caspcasp on 2007-08-08
Hi all

I have read [https://help.ubuntu.com/community/AutofsLDAP?highlight=%28autofs%29](https://help.ubuntu.com/community/AutofsLDAP?highlight=%28autofs%29)

they use autofs.schema but I use rfc2307bis.schema on OpenSuSE LDAP server.

I wrote in /etc/auto.master the following line on suse ldap client and it works:
ldap ldap-server:ou=AUTOFS,dc=domain,dc=com

When I do the same steps on Ubuntu 7.04 than it does not work.

What i need to do to use autofs + ldap?

---

