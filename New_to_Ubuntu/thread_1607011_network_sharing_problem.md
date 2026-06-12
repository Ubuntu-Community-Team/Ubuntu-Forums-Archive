---
title: "network sharing problem"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by knils00717 on 2010-10-27
i hv shared folder in ubuntu and connected it with win 7 when i m opening that folder  in win 7 it is asking for username and pass
after giving that it is not authenticating?

---

### Post by Verbeck on 2010-10-27
if you created the share by file properties>share tab then try checking the guest access box

[IMG]http://www.freeimagehosting.net/uploads/9a0de1b3fb.png[/IMG]

---

### Post by aeiah on 2010-10-27
if you want authentication, i think that the login needs to exist on both computers, if i remember correctly. this might be a lie though :p

---

### Post by linux-hack on 2010-10-27
do you have samba installed ? if yes you must create the user in samba or synchronize with the system users.

you type in a terminal :

```
smbpasswd USER_NAME
```

The user must exist on the system
[http://www.delafond.org/traducmanfr/man/man8/smbpasswd.8.html](http://www.delafond.org/traducmanfr/man/man8/smbpasswd.8.html)

---

### Post by knils00717 on 2010-10-27
>if you created the share by file properties>share tab then try  checking the guest access box
yes i hv done that....;)

---

### Post by Verbeck on 2010-10-27
> **knils00717 said:**
> >if you created the share by file properties>share tab then try  checking the guest access box
yes i hv done that....;)
Did it work?

---

### Post by knils00717 on 2010-10-27
no yar

---

### Post by knils00717 on 2010-10-27
no yar

i think in permission tab before share
others>folders access>none (not able to change it to Access folder)

---

### Post by Morbius1 on 2010-10-27
Please post the output of the following commands:

```
net usershare info -l
``````
testparm -s
```

---

