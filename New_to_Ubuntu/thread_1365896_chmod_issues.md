---
title: "chmod issues"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Pevichaey5 on 2009-12-27
hey
i'm trying to run the ddclient for use with my domain, however i am having permissions issues

if i do this
sudo chmod 777 ddclient.conf
it says that the file must be accessible only by its owner.

if i set the permissions to 770
the file executes, but i get loads of permission denied errors and it doesn't update with a final warning that it is unable to determine IP address

anyone got any suggestions

cheers

---

### Post by Barriehie on 2009-12-27
> **thexero said:**
> hey
i'm trying to run the ddclient for use with my domain, however i am having permissions issues

if i do this
sudo chmod 777 ddclient.conf
it says that the file must be accessible only by its owner.

if i set the permissions to 770
the file executes, but i get loads of permission denied errors and it doesn't update with a final warning that it is unable to determine IP address

anyone got any suggestions

cheers

I think that file has to be owned by root user:group.```
Sudo chown root:root /etc/ddclient/ddclient.conf
```

Barrie

Edit: Permissions 600

---

