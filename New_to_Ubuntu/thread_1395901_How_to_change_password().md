---
title: "How to change password(?)"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Bill Sheppard on 2010-02-01
Dumb question, but what is the procedure for changing the password? 
thanks
Bill

---

### Post by sandyd on 2010-02-01
```

sudo passwd *username*
```

---

### Post by JoeWheeler on 2010-02-01
System>Administration>Users and groups

Then you click edit on the password box of your account. You might also want to change root.

---

### Post by drs305 on 2010-02-01
From a terminal, you can run this:
```

sudo passwd [username]

```
username is current user unless entered.

You will be asked to enter your old password, then your new password and verify it.

You can do it via menus: System, Administration, Users & Groups. Highlight your name and select: Edit Password.

---

### Post by theozzlives on 2010-02-01
GUI, go to System > Administration > Users and Groups
Terminal:
```
sudo passwd <username>
```
Where username is your username without the <>

---

### Post by Monotoko on 2010-02-01
> **JoeWheeler said:**
> System>Administration>Users and groups

Then you click edit on the password box of your account. You might also want to change root.

No, dont change root unless you need it, otherwise use sudo which does everything root can. Once the root password is set it opens you to unnecessary security issues.

---

### Post by jd65pl on 2010-02-01
> **carlee said:**
> ```

sudo passwd *username*
```

If you want to change your own password there is no need for you to be running passwd as super user, so if you want to change the current users password just do:

```
passwd
```

If it is another user use the 'sudo' method

---

