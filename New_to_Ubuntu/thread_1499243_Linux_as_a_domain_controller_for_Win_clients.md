---
title: "Linux as a domain controller for Win clients"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by henriquelm on 2010-06-01
I want to learn how to set up Linux as a Domain Controller for windows clients. I found four different topics on the Ubuntu documentation about this subject, but I don't know which ones are good for me.

Someone told me that I only need Samba in order to have a linux domain controller for windows clients, but that openldap would be good in case I also need authentication to other softwares.

That being said, I think it would be better to also have OpenLDAP because I'm also planning on running squid, etc.

So, I'm guessing the first two links are for those who want to use OpenLDAP with Samba and the third and fourth links are for those who want to use Samba by itself, is that it?


[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

[https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)

[https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html)

---

### Post by linux-hack on 2010-06-01
actually it would be good to use samba and Open LDAP if you want a domain controller.but the problem is that open ldap is not so easy to use like windows active directory. its more powerful but more hard to put in place too.

you can easy your work a litle bit with webmin

---

