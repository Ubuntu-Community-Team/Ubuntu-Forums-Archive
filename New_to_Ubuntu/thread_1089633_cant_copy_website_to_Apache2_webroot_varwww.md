---
title: "cant copy website to Apache2 webroot ///var/www"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by rd123 on 2009-03-07
Re: How I can install apache web server manually?
i am a complete newbie to LINUX and i am trying to setup a LINUX BOX it appears i have installed the apache2 server on ULTIMATE UBUNTU 1.8 and on 127.0.0.1 i get the default page index.html.

i now want to upload my website which as a windows user i would have thought was relatively easy but i cannot copy files to ///var/www/

access denied why is this and how do i get round this

or

how do i get my default web server to point to a folder on my system

i have no idea what i am doing admittadly but as a long term windows user i know

NO QUESTION IS A STUPID QUESTION please help

Anyone

Please

---

### Post by taurus on 2009-03-07
If you want to move files to /var/www, you can either change the ownership of that directory or permissions.  

Otherwise, use sudo (or gksudo).

Applications -> Accessories -> Terminal
```
sudo mv *filename* /var/www
```
or
```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rd123 on 2009-03-07
i think you may be right 

linux vs windows......

but any way tried gksudo nautilus and copied files to var/www

many thanks

looks like i will lean on a few minds before i complete my transition

still need DNS, DHCP, and FTP to run no way near as easy to configure finding this hard work been using Server2003 R2 for a good few years

---

