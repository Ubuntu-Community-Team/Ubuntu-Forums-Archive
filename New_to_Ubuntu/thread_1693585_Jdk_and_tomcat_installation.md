---
title: "Jdk and tomcat installation"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by drathi on 2011-02-23
Hi,

*[I]sudo apt-get install [[COLOR=#0072bc]sun[/COLOR]]("http://www.ghacks.net/2010/05/21/install-java-on-ubuntu-10-04/#")-java6-jre sun-java6-plugin sun-java6-fonts : command not *[/I]working and it is giving this below problems:
deepak@kalpna-desktop:/$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I am new to Ubuntu.Please guide for complete jdk and tomcat installation on Ubuntu and also give methods to set environment path.



Regards

---

### Post by Perfect Storm on 2011-02-23
This error occur often when you have one/more package software running simultaneous. Close them and try again.

---

