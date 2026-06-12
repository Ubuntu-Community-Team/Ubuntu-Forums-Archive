---
title: "Ubuntu and AD authentication"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by lwoodtri on 2007-01-24
Hello All,

I have been trying to get AD authentication working for 2 days now to no avail.  I tried following the AD howto listed here, but either it is missing something or I am.  I can see the kerberos auth hitting the domain contoller, but I never get the server to pull the accounts/ information from the domain controller and let the user through.  

Is there anyone that has gotten this working properly with a Windows 2003 SR2 AD server and if so what are the steps verbatim that you took.  I do not want to use SAMBA, I just want a single sign on authentication against the accounts in the AD DB.  It appears that Kerberos is working fine so I am guessing something is misconfigure with the libnss-ldap or ldap.conf settings somewhere.  

If someone has gotten this operational please shed some light on it for me if you can!  Thank you much in Advance!

cb

---

### Post by spd106 on 2007-01-25
Sorry I can't help, but I would like to add a "me too!".

I got as far as joining the AD Domain, but when I try to log in it fails with an error about not having permission to create the user's directory.

I tried both the winbind way and without.

---

### Post by lwoodtri on 2007-02-01
All,

Well its now working . . .  and certainly not with any help from these forums . . .

---

### Post by spd106 on 2007-02-01
[QUOTE=lwoodtri]All,

Well its now working . . . and certainly not with any help from these forums . . .[/QUOTE]

So how did you get it working? It would be helpful if you could please say what you did.

---

