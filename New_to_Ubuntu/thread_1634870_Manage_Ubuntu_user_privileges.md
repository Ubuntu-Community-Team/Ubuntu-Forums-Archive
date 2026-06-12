---
title: "Manage Ubuntu user privileges"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by tdapower on 2010-12-01
[SIZE=4][COLOR=Blue]In my company there are client computers for employees which has Ubuntu. Those users doesn't have super user privileges. But they can change there own user passwords without the authority of me. I need to disable that feature. Because we have some policies in company to keep passwords of employees with us. So if they change there passwords. There will be a problem for us.
Please tell me how to disable password change facility of non-super users.[/COLOR][/SIZE]:D

---

### Post by Wtower on 2010-12-01
I didn't understand very well but the following link may be of help

[https://help.ubuntu.com/10.10/serverguide/C/user-management.html](https://help.ubuntu.com/10.10/serverguide/C/user-management.html)

Regards

---

### Post by surfer on 2010-12-01
as root you can always login to other users's accounts without knowing their password (as long as you do not encrypt their home directory with ecryptfs or something similar).

what is your benefit of really knowing their passwords?

sorry, that may be no help for your problem at hand...

---

### Post by tdapower on 2010-12-02
We need to know their passwords, because if they leave the company we cannot log into their pcs. But as you said root can log to any user account. we don't have any problem. but I need to disable the ability to change the user passwords.

---

### Post by srikanth.gundaz on 2010-12-02
> **tdapower said:**
> We need to know their passwords, because if they leave the company we cannot log into their pcs. But as you said root can log to any user account. we don't have any problem. but I need to disable the ability to change the user passwords.

Make several groups under one user(Say, ur company name) and change the permission to read-only for the fields which you want :)

---

### Post by sisco311 on 2010-12-02
> **tdapower said:**
> We need to know their passwords, because if they leave the company we cannot log into their pcs. But as you said root can log to any user account. we don't have any problem. but I need to disable the ability to change the user passwords.

Set the minimum number of days between password changes to something high like 32000 days (~= 90 years).

```
sudo passwd -n 32000 username
```

See:
```
man 5 shadow
man passwd
```

---

### Post by SecretCode on 2010-12-03
> **tdapower said:**
> We need to know their passwords, because if they leave the company we cannot log into their pcs.

If you have a separate admin account on each user PC with sudo privileges, you can log on with that and change the main user's password. (I don't know if there's a way to have a central admin account via LDAP...?)

For mgt to know all users' passwords is bad practice: it could open you up to accusations of deniability - "I didn't do that, mgt must have used my PC". And it makes users less concerned about not sharing their password with others. And you lose the benefits (whatever they are) of regular changes to user passwords.

---

### Post by endotherm on 2010-12-03
> **sisco311 said:**
> set the minimum number of days between password changes to something high like 32000 days (~= 90 years).

```
sudo passwd -n 32000 username
```see:
```
man 5 shadow
man passwd
```
+1

---

### Post by tdapower on 2010-12-06
Thanks

---

