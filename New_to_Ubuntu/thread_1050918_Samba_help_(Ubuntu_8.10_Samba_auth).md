---
title: "Samba help (Ubuntu 8.10 Samba auth)"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Boktegrob on 2009-01-26
So, hi all :)

I've a problem that you m8s can probably help me with. I need to join Ubuntu 8.10 (patched) to our Samba server here in the company. 

I need to authenticate with my domain username and need the four network drives auto mapped. 

So I dig the smb.conf part, but where I regularly mess up is the PAM auth part. So if anybody could be nice enough to post/point me to a step by step guide in doing this in 8.10.

thank you very much,

Mormz

---

### Post by blackgr on 2009-01-26
```
sudo apt-get install system-config-samba
```
Its Gui for samba to easily configure it without messing with smb.conf. As for the password issue.You ll propably need to set the security mode to "shared"

---

### Post by Boktegrob on 2009-01-26
:lol:

I don't need to setup a samba server. I need my client to authenticate against SAMBA (hosted on SUSE) and instead of using Unix auth, to use Samba auth.

---

### Post by Boktegrob on 2009-01-26
any1?

---

