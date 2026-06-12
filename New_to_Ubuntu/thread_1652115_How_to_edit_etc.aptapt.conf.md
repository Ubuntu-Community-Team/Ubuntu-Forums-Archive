---
title: "How to edit /etc.apt/apt.conf"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Gav1991 on 2010-12-24
How can I edit "/etc.apt/apt.conf" ?

---

### Post by jroa on 2010-12-24
What are you trying to do, if you do not mind me asking?

---

### Post by Gav1991 on 2010-12-24
I want to use internet behind a proxy with password.

---

### Post by sffvba[e0rt on 2010-12-24
In terminal:

```
sudo nano /etc.apt/apt.conf
```

... or am I missing something?


404

---

### Post by jroa on 2010-12-24
> **Gav1991 said:**
> How can I edit "/etc.apt/apt.conf" ?

I think you mean /etc/apt/apt.conf .

If so, then just type 

```
sudo gedit /etc/apt/apt.conf
```

---

### Post by sffvba[e0rt on 2010-12-24
> **jroa said:**
> I think you mean /etc/apt/apt.conf .

If so, then just type 

```
sudo gedit /etc/apt/apt.conf
```

Yup, that looks a bit more likely to be correct :p


404

---

### Post by skd2011 on 2011-04-12
I edited with nano /etc/apt/apt.conf  to enter proxserver settings

I entered but when i close the file and try to apt-get update its giving extra junk at end of file error in apt/apt.conf

please help asap

Thanks in advance !!

---

### Post by Spyderkid on 2011-04-12
sudo gedit /etc.apt/apt.conf

---

### Post by skd2011 on 2011-04-12
got the solution

in the last in hurry  i forget to add ";

it should be Acquire::http:: proxy:17.0.0.6:8080:;

cheers to ubuntu users !!

---

