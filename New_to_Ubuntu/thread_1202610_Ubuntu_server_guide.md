---
title: "Ubuntu server guide"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by datarunner on 2009-07-02
Hi All

Is there a guide to setting up Ubuntu Server as a server for Windows clients?

Sorry if this has been asked before

Regards

---

### Post by Boondoklife on 2009-07-02
What type of services? File sharing, PDC, DNS?

You might want to look into SAMBA as it will do alot of windoes related services

---

### Post by datarunner on 2009-07-02
> **maletek said:**
> What type of services? File sharing, PDC, DNS?

You might want to look into SAMBA as it will do alot of windoes related services

Hi There

I'd like Ubuntu Server to replace Server 2003 / SBS Server with file, mail, DHCP, Print.

Basically just providing the Windows clients the same as an AD Domain

Regards

---

### Post by superprash2003 on 2009-07-02
check this out [http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

---

### Post by datarunner on 2009-07-02
Hi All

Can this be done within Ubuntu Server itself as the SAMBA / LDAP set up is way beyond my knowledge?

Regards

---

### Post by reeseslover531 on 2009-07-02
it is done with ubuntu server, but you have to run the SAMBA/LDAP services on top of it, so you have to configure SAMBA/LDAP.

---

### Post by datarunner on 2009-07-02
> **reeseslover531 said:**
> it is done with ubuntu server, but you have to run the SAMBA/LDAP services on top of it, so you have to configure SAMBA/LDAP.

Hi There

Is there a Dummies Guide?

Regards

---

### Post by lavinog on 2009-07-02
Have you tried the ubuntu server guide?
[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

---

### Post by Gone fishing on 2009-07-02
The samba can be set up independently of ldap and you can find guides on how to set it up - I've found swat and webmin helpful. If you go the ldap authentication method I found Opensuse way easier to set up than Ubuntu [http://digiplan.eu.org/ldap-samba-howto-v4.html](http://digiplan.eu.org/ldap-samba-howto-v4.html)

---

