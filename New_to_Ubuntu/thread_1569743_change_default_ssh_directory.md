---
title: "change default ssh directory"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by abraxas334 on 2010-09-07
When I remotely log into a machine in order to get to go to my directory I want to do all my work in I have to type a very long cd command every time. Is there a config file where I can specify my directory path for an ssh login, do I have to do that on the remote host, i.e. where I'd normally type the cd command or on my local computer?

---

### Post by spjackson on 2010-09-07
> **abraxas334 said:**
> When I remotely log into a machine in order to get to go to my directory I want to do all my work in I have to type a very long cd command every time. Is there a config file where I can specify my directory path for an ssh login, do I have to do that on the remote host, i.e. where I'd normally type the cd command or on my local computer?
Can't you simply add the cd command to the end of ~/.profile on the remote computer?

---

### Post by abraxas334 on 2010-09-07
It worked like magic! Thanks alot :)

---

