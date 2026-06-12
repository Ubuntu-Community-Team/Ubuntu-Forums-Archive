---
title: "LDAP Samba file server"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by netwerkdude on 2008-01-31
Hello, 

I have a working LDAP/Samba/BIND/DHCP "Domain Controller" working on Server 7.10 .

I would like to make anotehr server, a samba file server that authenticates to that domain controller. 

How would I make this file server authenticate to the ldap server?

---

### Post by rickyjones on 2008-01-31
Check out your smb.conf file on the primary server. There should be some items in it regarding LDAP. Find those sections and replicate them on the second server, obviously replacing "localhost" or "127.0.0.1" with the actual IP of the primary server.

That should get you started if I'm right!

-Richard

---

