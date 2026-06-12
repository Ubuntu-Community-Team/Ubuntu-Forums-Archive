---
title: "Backing up OpenLdap"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by tcpip4lyfe on 2008-03-12
Anyone know how to backup a ldap database?  Can I just rsync /var/lib/ldap and /etc/ldap/?

---

### Post by tcpip4lyfe on 2008-03-12
sudo slapcat -v -n 1 -l  ~/ldap.ldif

That's how.

---

