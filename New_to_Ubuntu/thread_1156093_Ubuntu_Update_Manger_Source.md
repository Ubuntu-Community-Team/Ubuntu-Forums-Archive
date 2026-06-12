---
title: "Ubuntu Update Manger Source"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by JonDobbs on 2009-05-11
I recently loaded Ubuntu 8.x , this is my first look ever at a Linux distribution and had what may seem like a silly question.  Where does the updates that Update Manger offers come from?

---

### Post by ptn107 on 2009-05-11
Packages and package updates are from:
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

Security updates are from:
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

---

### Post by Didius Falco on 2009-05-11
> **JonDobbs said:**
> I recently loaded Ubuntu 8.x , this is my first look ever at a Linux distribution and had what may seem like a silly question.  Where does the updates that Update Manager offers come from?

All the files that you download using **Add/Remove**, **Synaptic Package Manager**, **Update Manager**, **Hardware Drivers** and the command line **apt-get** and **synaptic** come from repositories. Repositories, or repos, as they are commonly called, are simply servers that have an entry in your **/etc/apt/sources.list **

You may have already added a third party source to your list - Medibuntu is often the first one people add because it allows you to get multimedia codecs that Ubuntu doesn't package because of varying legal requirements in different countries.

I hope this explanation helped...

Regards,

Didius

---

### Post by drs305 on 2009-05-11
And here is the ubuntu documentation explaining the repositories:
[_https://help.ubuntu.com/community/Repositories/Ubuntu_]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

