---
title: "why cant i copy into /opt/lampp/htdocs ?"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-10
why cant i copy into /opt/lampp/htdocs ?
how do i copy as root ?

---

### Post by Telengard C64 on 2011-04-10
> **neil_1 said:**
> why cant i copy into /opt/lampp/htdocs ?

I don't know. How are you trying to copy it? What happens then?

> how do i copy as root ?

```
sudo cp /PATH/TO/SOURCE /PATH/TO/TARGET
```

---

### Post by neil_1 on 2011-04-10
> 
neil@lappy:~$ sudo cp /home/neil/Downloads/Panel /opt/lampp/htdocs
[sudo] password for neil: 
cp: omitting directory `/home/neil/Downloads/Panel'
i did this before ,
if i try to copy by right clicking , when i paste into /opt ,it says im not privileged :/

---

### Post by Old *ix Geek on 2011-04-10
> [QUOTE]neil@lappy:~$ sudo cp /home/neil/Downloads/Panel /opt/lampp/htdocs
[sudo] password for neil:
cp: omitting directory `/home/neil/Downloads/Panel' 

i did this before[/quote]

You need to use the recursive option:
```
sudo cp -r /home/neil/Downloads/Panel /opt/lampp/htdocs
```

---

### Post by dcsoldschool53 on 2011-04-10
> 
**why cant i copy into /opt/lampp/htdocs ?**
[B]         why cant i copy into /opt/lampp/htdocs ?
how do i copy as root ?[/B][B]

You can copy and paste anything when you are doing it in the /home/user name folder. If you want to copy and paste something into the root folder, you must do it as the root user. From the terminal, type:

sudo cp /home/user-name/file to be copied[/B] [B]/opt/lampp/htdocs
[/B][B]

or,

```
gksu nautilus
```Then just copy what you need and paste it to that folder.
Be careful when opening nautilus from the command line as root, you can do some harm to your system, if not done in the right way.
[/B]

---

### Post by neil_1 on 2011-04-10
> **dcsoldschool53 said:**
> [B]

You can copy and paste anything when you are doing it in the /home/user name folder. If you want to copy and paste something into the root folder, you must do it as the root user. From the terminal, type:

sudo cp /home/user-name/file to be copied[/B] [B]/opt/lampp/htdocs
[/B][B]

or,

```
gksu nautilus
```Then just copy what you need and paste it to that folder.
Be careful when opening nautilus from the command line as root, you can do some harm to your system, if not done in the right way.
[/B]
how do i disable gksudo privilege after im done ?

---

### Post by dcsoldschool53 on 2011-04-10
[quote=nell_1]how do i disable gksudo privilege after im done ?[/quote]

You don't need to disable gksu privileges, just close nautilus.

---

### Post by neil_1 on 2011-04-10
alright thanks guys :)

---

