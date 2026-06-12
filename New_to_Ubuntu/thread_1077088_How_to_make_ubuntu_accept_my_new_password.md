---
title: "How to make ubuntu accept my new password?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by kapmsd on 2009-02-22
Hi guys!!

I would like to know is there anyway through which i can make ubuntu accept my new password(it mostly returns bad:new password is too simple).i.e.I want it to accept even my "**_*simple*_**" password.

Thanks a lot in advance :p
Pls help me.

---

### Post by Temposs on 2009-02-22
Open a terminal and type

```
passwd
```

---

### Post by evilGUI on 2009-02-22
> **Temposs said:**
> Open a terminal and type

```
passwd
```

Even though you can do this I would recommend not to, if you ever install SSH "make sure" to create a stronger password first, week passwords are a security problem in any operating system.

---

### Post by anthony riggins on 2009-02-22
I just registered, can anyone tell me how I post my question?

---

### Post by kapmsd on 2009-02-23
Using "passwd" i can change the password but the matter is that i want it to accept my simplest of passwords.

I dont want ubuntu to instruct me.

---

### Post by vdobriakov on 2009-11-05
You can bypass the (cracklib ?) checks with

```
sudo passwd your_user_name
```

That means the super user is allowed to set weak passwords.

--
Vladimir Dobriakov
[http://blog.geekq.net](http://blog.geekq.net)

---

### Post by Tony Flury on 2009-11-05
> **anthony riggins said:**
> I just registered, can anyone tell me how I post my question?

You click the New Thread button in the forum you want to ask the question in .......

---

