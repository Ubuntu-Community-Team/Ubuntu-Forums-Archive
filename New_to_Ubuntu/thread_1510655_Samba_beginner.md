---
title: "Samba beginner"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by jrab227 on 2010-06-15
Can someone point me in the direction of good material on learning how to use Samba? I don't really have any idea on how to use it.

---

### Post by sandyd on 2010-06-15
> **jrab227 said:**
> Can someone point me in the direction of good material on learning how to use Samba? I don't really have any idea on how to use it.
```

sudo apt-get install system-config-samba
gksudo system-config-samba
```
Click on Preferences -> Server Settings.
Set your workgroup so that it is the same as the windows workgroup (in windows 7, you will have to right click on "my computer" and roam around the tabs to find where you set the workgroup).
Click on security, change authentication to "share"

click "ok"
-------------------------
Click the "+" sign on the top left of the window.

select the directory

type in the description.

put a check box next to visible, and one next to writable (if you need it)

click on "access" select allow access to everybody.

restart.

---

### Post by jrab227 on 2010-06-15
Now also how would I create users, manage what each individual user can view and write, and require login? All while my laptop is Ubuntu but others are Windows and another's a Jolicloud distro? :confused:

---

### Post by reccakeys on 2010-06-15
Hello!
   I am also a beginner of samba. I want to learn more about it. I am very thankful that there is someone starting this forum. Hope you could help me also filled the lack of knowledge about samba. I am willing to learn how to use it.

Thank you so much in advance. GUd Luck us all:confused:

---

### Post by jrab227 on 2010-06-15
Lol This is actually my second attempt. There's also some questions that I have regarding what the difference between "server" and "share" is. And I would like to be able to change settings remotely using a password.

---

### Post by beowulf1416 on 2010-06-15
[http://samba.org/](http://samba.org/)
[http://samba.org/samba/docs/](http://samba.org/samba/docs/)

---

### Post by jrab227 on 2010-06-17
> **beowulf1416 said:**
> [http://samba.org/](http://samba.org/)
[http://samba.org/samba/docs/](http://samba.org/samba/docs/)

High five bro!

---

