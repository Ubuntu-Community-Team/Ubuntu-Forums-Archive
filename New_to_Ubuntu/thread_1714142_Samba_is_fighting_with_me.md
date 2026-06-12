---
title: "Samba is fighting with me"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by K.R.O.N.I.K on 2011-03-25
Ok So I have been using Webmin to set up samba on my Centos 5.5 machine (Domain name in Samba is KISKA).

I set up a test directory /smbtest on the machine and made a share on webmin. 

My problem is that when I try to connect to the share on my windows machine (im running windows 7) it gives me a message saying this:

```
Windows Cannot Access \\Kiska\smbtest
```I have made sure to make the permissions on /smbtest 777 and I have tried alot of other stuff as well.

Here is my Smb.conf

```
[global]
    load printers = yes
    cups options = raw
    netbios name = KISKA
    winbind enum users = no
    default = global
    workgroup = NUS
    os level = 20
    winbind enum groups = no
    null passwords = yes
    winbind enable local accounts = no
    winbind trusted domains only = yes
    security = share
    preferred master = no
    passdb backend = tdbsam

[SMBTEST]
    writeable = yes
    delete readonly = yes
    path = /smbtest
    force directory mode = 777
    force create mode = 777
    public = yes
    create mode = 777
    directory mode = 777

```Thanks for any help you can give!!!

---

### Post by mastablasta on 2011-03-25
> **K.R.O.N.I.K said:**
> Ok So I have been using Webmin to set up samba on my**[SIZE=2] Centos 5.5[/SIZE]** machine (Domain name in Samba is KISKA).
 

 
 
Well, use Ubuntu instead. Maybe it will support samba better.
 
Edit: before i get another yellow, you are probably missing a package.

---

