---
title: "Domain"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by Ryan_Gormley on 2013-09-21
Hi all,
I am quite a newbie to Linux and I was wondering if its possible to setup a complete Domain using only Linux.  Something like windows server 2008 active directory.  Is there anything out there that can be installed on the server that will allow me to create users, groups, ou's and assign permissions to the groups and users.

Thanks :) ,
Ryan

---

### Post by Ryan_Gormley on 2013-09-23
Any ideas?

---

### Post by houstonbofh on 2013-09-23
Yes there is.

[https://help.ubuntu.com/lts/serverguide/openldap-server.html](https://help.ubuntu.com/lts/serverguide/openldap-server.html)

YOu have to set this up, and then set up each system to use LDAP for authentication.  Also look at the Linux Terminal Server Project (LTSP) as it does all this, including PXE booting.

---

### Post by SeijiSensei on 2013-09-24
I'd start by looking into [Samba 4]("http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO").

---

### Post by Ryan_Gormley on 2013-09-24
Thanks lads :)

---

