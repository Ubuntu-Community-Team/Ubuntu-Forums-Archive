---
title: "Add Active Directory user to /etc/passwd"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by rdionicio on 2008-09-11
I am trying to set up virtual box on my ubuntu, which is connected to my active directory domain but in order to run virtual box properly I need to add my active directory user account to the vboxusers group.

I cant do that because my active directory account that I sign into ubuntu with is not in the /etc/passwd file. Does anyone know how to do this?

---

### Post by forger on 2008-09-11
what's Active Directory? if it's a username you can add users using:
```
sudo adduser yournewusername
```

---

### Post by rdionicio on 2008-09-11
Windows Server 2003 Active Directory. I don't think that command will fully work since the account I want to add is aassociated with the Windows domain.

---

### Post by rdionicio on 2008-09-11
bump

---

### Post by forger on 2008-09-13
Active directory is a shared directory?

If it's in a local network, I think you could make a samba share and mount it on /media/windows - then you would be able to connect to the mounted directory.
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Edit: read "Samba and Active Directory" at that link

---

### Post by rdionicio on 2008-09-15
> **forger said:**
> Active directory is a shared directory?

If it's in a local network, I think you could make a samba share and mount it on /media/windows - then you would be able to connect to the mounted directory.
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Edit: read "Samba and Active Directory" at that link

Not quite what I was looking for. I solved my own problem by mapping my active directory user account to a local account on my ubuntu box. Thanks.

---

