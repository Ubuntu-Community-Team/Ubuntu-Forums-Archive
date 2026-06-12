---
title: "pureftp virtual users wont authenticate"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by kmortensen on 2011-03-24
All-
I am desperately attempting to install an ftp server on my ubuntu 10.04 box.  I am really new to linux, so i am not looking to mess with command line too much...but dont worry, i'll get my hands dirty if i need to.  Long story short, I have installed pureftpd and pureadmin. i have created virtual users, and mapped them to a specific folder in my home directory.  When I go to log on as that virtual user, authentication fails.  however if i log on as a system user, it works.  I really need to use virtual users though because of the ability to lock the user into a specific directory.  Any help would be greatly appreciated!

---

### Post by ingramproductions on 2011-07-18
[http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-incl-quota-and-bandwidth-management-on-ubuntu-10.10-maverick-meerkat]("http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-incl-quota-and-bandwidth-management-on-ubuntu-10.10-maverick-meerkat")

I followed these steps and got virtual users working. But virtual users are typically only for when you have a really large number of users. You can lock system users into a specific directory just as easily.

---

