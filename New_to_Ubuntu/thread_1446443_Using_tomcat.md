---
title: "Using tomcat"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by anirup on 2010-04-04
I INSTALLED TOMCAT-5.5 USING SYNAPTIC MANAGER.WHEN I TYPE LOCALHOST:8180 THE DEFAULT PAGE IS DISPLAYED AND ALL THE OTHER EXAMPLES ARE DISPLAYED.The problem is suppose **i have a file say index1.jsp** and i want to display it through a browser as **_[http://localhost:8180/index1.jsp](http://localhost:8180/index1.jsp)_** then where should i keep the file??

my version of ubuntu is ubuntu 8.04.

---

### Post by @rizz on 2010-04-04
Hello,

  May be you can keep the file in /var/www

 I use apache and thats where i keep my files

---

### Post by anirup on 2010-04-04
I tried it out.no use.

---

### Post by @rizz on 2010-04-04
And what about this?


Go to /etc/tomcat5.5/Catalina/localhost directory, add an XML file (for example: ROOT.xml) which contains:
<Context path="/" docBase="/home/USERNAME/Programs/JavaEE" reloadable="true" />


Put a JSP file (test.jsp) in /home/Username/Programs/JavaEE/, which contains:
<% out.println("It works"); %>
Restart tomcat and visit [http://localhost:8080/test.jsp](http://localhost:8080/test.jsp) to test it.

[http://deepbluespaces.blogspot.com/2008/07/installing-tomcat-on-ubuntu-linux.html](http://deepbluespaces.blogspot.com/2008/07/installing-tomcat-on-ubuntu-linux.html)

---

### Post by anirup on 2010-04-04
It worked.thanks for the help.

---

### Post by @rizz on 2010-04-04
Cheers dude! even i learned the trick!:lolflag:

---

