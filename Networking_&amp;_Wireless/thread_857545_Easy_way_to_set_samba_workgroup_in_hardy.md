---
title: "Easy way to set samba workgroup in hardy"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by mariano.pelizzari on 2008-07-12
In previous versions I think it was a sharing options menu under system/administration to do this. Is there a similar way to do it in hardy? or I just have to edit smb.conf.

Thks

---

### Post by BrowneR on 2008-07-12
I too am missing the option in system/administration and the following is the closes thing i've found so far:

```
sudo apt-get install system-config-samba
```

---

### Post by hyper_ch on 2008-07-12
I'd edit smb.conf. A simple one looks sort of like this:
```

[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

[appz]
comment = Appz
path = /home/hyper/Appz

```

---

