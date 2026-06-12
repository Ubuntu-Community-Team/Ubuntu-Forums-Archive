---
title: "Tomcat 6 security problem"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by abacabus on 2009-05-20
I have recently updated to Ubuntu 9.04. At the same time I guess my Tomcat 6 installation was updated as well, resulting in that I can no longer use the webapplication that was run by Tomcat. Apparently the security was switched on, which cause the webapplication to malfunction since it wants to connect using a socket. So, my question is, does anyone know how I can turn off the security for Tomcat6?
It is installed using the package manager.

Thanks in advance

---

### Post by realflash on 2009-12-02
Open up */etc/init.d/tomcat6* and find the line TOMCAT6_SECURITY=yes. Change it to TOMCAT6_SECURITY=no. Restart tomcat.

---

