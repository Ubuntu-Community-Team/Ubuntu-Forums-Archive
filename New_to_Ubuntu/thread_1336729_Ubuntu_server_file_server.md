---
title: "Ubuntu server file server"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by abraves247 on 2009-11-24
I installed Ubuntu server and I was trying to make it a file server I installed samba but I don't know how to configure it so I can have it be a file server with windows 7 machines.

---

### Post by 3rdalbum on 2009-11-24
If you've got a GUI, I recommend installing the "system-config-samba" program. This program makes it easy to set up a basic Samba configuration.

If you don't have a GUI, then this should help: [https://help.ubuntu.com/community/SettingUpSamba#Samba Server Manual Configuration]("https://help.ubuntu.com/community/SettingUpSamba#Samba Server Manual Configuration")

---

### Post by abraves247 on 2009-11-24
I do not have a GUI so thank you for the link

---

### Post by Spiritof76 on 2009-11-24
On a headless server, can one use a gui on the desktop to configure the headless server?

---

### Post by 3rdalbum on 2009-11-24
> **Spiritof76 said:**
> On a headless server, can one use a gui on the desktop to configure the headless server?

That is true. If you have system-config-samba and openssh-server installed on the server, you can run system-config-samba from another computer across the ssh connection:

```
chris@chris-desktop:~$ ssh -XC 192.168.0.12
chris@192.168.0.12 password:
chris@chris-server:~$ system-config-samba
```

---

### Post by SIGTERMer on 2009-11-24
> **3rdalbum said:**
> That is true. If you have system-config-samba and openssh-server installed on the server, you can run system-config-samba from another computer across the ssh connection:

```
chris@chris-desktop:~$ ssh -XC 192.168.0.12
chris@192.168.0.12 password:
chris@chris-server:~$ system-config-samba
```

you'll need Xorg installed on the server for that to work ;)

---

### Post by abraves247 on 2009-12-09
thanks that worked great

---

