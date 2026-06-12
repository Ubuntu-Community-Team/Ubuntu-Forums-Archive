---
title: "Cannot log in to newly created username"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by promitt on 2010-01-25
[FONT=Arial]Hi.
In Ubuntu terminal I typed the following:
[/FONT][FONT=Arial][FONT=Courier New]usermod -p passwdw simon[/FONT]
(let simon be the new user's name and passwdw his new password). The new password appears in [FONT=Courier New]/etc/shadow[/FONT] but is unavailable - I cannot log on to it neither with [FONT=Courier New]su simon[/FONT] command, nor by switching user in graphic mode... The new password is just not recognized. What's wrong?[/FONT]

---

### Post by bodhi.zazen on 2010-01-25
How did you make this user and what is the default log in shell ?

---

### Post by promitt on 2010-01-25
I made the user simply by using useradd command... My default shell seems to be /bin/sh.

---

### Post by sisco311 on 2010-01-25
> **promitt said:**
> [FONT=Arial]Hi.
In Ubuntu terminal I typed the following:
[/FONT][FONT=Arial][FONT=Courier New]usermod -p passwdw simon[/FONT]
(let simon be the new user's name and passwdw his new password). The new password appears in [FONT=Courier New]/etc/shadow[/FONT] but is unavailable - I cannot log on to it neither with [FONT=Courier New]su simon[/FONT] command, nor by switching user in graphic mode... The new password is just not recognized. What's wrong?[/FONT]

passwdw should be the encrypted password.
You can use mkpasswd to encrypt a password:

```
mkpasswd -m sha-512 plaintextpassword salt
```

Or simply run:
```
sudo passwd username
```to change the user's password.

---

### Post by promitt on 2010-01-25
Thanks, the sudo command worked.
I'm just at the beginning... :) Thanks for your attention.

---

### Post by promitt on 2010-01-25
apropo, sisco, n-am observat la timp ca esti din Romania :) Salutari

---

### Post by sisco311 on 2010-01-25
> **promitt said:**
> Thanks, the sudo command worked.
I'm just at the beginning... :) Thanks for your attention.

Cu pl&#259;cere! (You're welcome!)

BTW, to add a new user you could use the adduser command which is a front end to the low level tools like useradd and usermod.
For details read the man page:
```
man adduser
```


> **promitt said:**
> apropo, sisco, n-am observat la timp ca esti din Romania :) Salutari

):P

---

