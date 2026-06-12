---
title: "unable to run  webapplications in tomcat"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by sree_charan on 2010-03-03
the following is the error i get every time i try to run my web application in tomcat 6. im using ubuntu 9.04. i have placed my application in webapps folder correctly but still im unable to run it from the tomcat manager.. any one please help im stuck up i am my college project.

HTTP Status 404 - /SearchDoctors/

type Status report

message /SearchDoctors/

description The requested resource (/SearchDoctors/) is not available.
Apache Tomcat/5.5.28

i have placed my application in /usr/local/tomcat/webapps/SearchDoctors/WEB-INF folder correctly 


ill also post the contents of /usr/local/tomcat/webapps/SearchDoctors/WEB-INF/web.xml of my application as i have searched they say problem is with this can anyone please help.the college project still needs a long way to go :( 
```
   
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE web-app
      PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
      "http://java.sun.com/dtd/web-app_2_3.dtd">

<web-app>
  <display-name>Forms</display-name>
  <servlet>
    <servlet-name>Validation</servlet-name>
    <servlet-class>org.apache.tapestry.ApplicationServlet</servlet-class>
    <load-on-startup>0</load-on-startup>
  </servlet>
  <servlet-mapping>
    <servlet-name>Validation</servlet-name>
    <url-pattern>/app</url-pattern>
  </servlet-mapping>
  <servlet>
  <servlet-name>dwr-invoker</servlet-name>
  <display-name>DWR Servlet</display-name>
  <servlet-class>org.directwebremoting.servlet.DwrServlet</servlet-class>
  <init-param>
     <param-name>debug</param-name>
     <param-value>true</param-value>
  </init-param>
</servlet>

<servlet-mapping>
  <servlet-name>dwr-invoker</servlet-name>
  <url-pattern>/dwr/*</url-pattern>
</servlet-mapping>
  
</web-app>
 
```

---

### Post by Sef on 2010-03-04
Moved to ABT.

---

### Post by sree_charan on 2010-03-04
> **Sef said:**
> Moved to ABT.


what was that reply didnt undesrtand

---

