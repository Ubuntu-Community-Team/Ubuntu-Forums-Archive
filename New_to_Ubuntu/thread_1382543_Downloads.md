---
title: "Downloads"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by SekoR on 2010-01-16
Hi

I am planning to install ubuntu on more than 10 standalone PCs ... I have a pc on the other office attached to the dial up modem.  I have connected to the internet with it and have installed Wine using "apt-get install wine" command.  Now I would like to know if I can copy the installation files somewhere on an external drive and use the same files to install on the other 10 standalone PCs without them connecting to the internet?

please help.

---

### Post by Paqman on 2010-01-16
You can use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a custom .ISO that will include all the packages on the original system.

If bandwidth is an issue you also might want to look into using something like apt-cacher so that you've only got one machine on your network that is downloading the regular updates.

---

### Post by alwayshere on 2010-01-16
clonezilla will sort it heres a link  [http://clonezilla.org/]("http://clonezilla.org/")

---

### Post by Mornedhel on 2010-01-16
The simplest solution would be to get the .deb files from /var/cache/apt/archives on the computer that downloaded the updates.

---

