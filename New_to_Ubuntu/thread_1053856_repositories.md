---
title: "repositories"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by crystalclaws on 2009-01-29
How can I add source repositories to sources.list?
all I have in sources.list is

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted multiverse $
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse universe #Added by s$

---

### Post by overdrank on 2009-01-29
> **crystalclaws said:**
> How can I add source repositories to sources.list?
all I have in sources.list is

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted multiverse $
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse universe #Added by s$

Hi and you will have to edit the list.
[This link]("https://help.ubuntu.com/community/Repositories/Ubuntu") Has some good info

---

### Post by crystalclaws on 2009-01-29
Problem is Im not able to download sources  of any package

aragon@g33kcafe:~/softwares$ sudo apt-get source vlc
[sudo] password for aragon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/10.65.0.42_ubuntu_dists_hardy_main_source_Sources - open (2 No such file or directory)

---

### Post by overdrank on 2009-01-29
> **crystalclaws said:**
> Problem is Im not able to download sources  of any package

aragon@g33kcafe:~/softwares$ sudo apt-get source vlc
[sudo] password for aragon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/10.65.0.42_ubuntu_dists_hardy_main_source_Sources - open (2 No such file or directory)

I have no issue but here is mine and it appears you are missing deb -src
```
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by zvacet on 2009-01-29
You can generate new source list [here.]("http://repogen.simplylinux.ch/") There is no need for proposed and backports.

---

