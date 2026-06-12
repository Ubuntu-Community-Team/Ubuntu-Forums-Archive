---
title: "Xampp"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Mpa4Hu on 2010-03-29
Hey all. I'm using Windows 7 and Ubuntu Koala.
so on windows I use denwer. but I need apache on both systems.
so as I know XAMPP supports both.
can I install XAMPP so, that i can use one SQL and PHP on both systems?
I mean to access same sites that i have on XAMPP

---

### Post by s_ø on 2010-03-29
Hi.
You are dual booting, right?
You cant share the programs between win/ubuntu.
You should setup the server on both systems, and share the document root - the files you need to serve.
Im unsure if you can share the mysql db in your setup.

You should istall LAMP on your ubuntu. Use tasksel.
In terminal
```
sudo tasksel
```

And select LAMP server (space to select)

---

