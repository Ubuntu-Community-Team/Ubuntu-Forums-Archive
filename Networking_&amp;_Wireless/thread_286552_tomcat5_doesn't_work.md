---
title: "tomcat5 doesn't work"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by mohtasham1983 on 2006-10-27
Hi,
I have installed tomcat5 using synaptic and installed SDK and JRE. 
I can run tomcat by /etc/init/tomcat5 start

but when I check [http://localhost](http://localhost) it says that page cannot be displayed.
[http://localsot:8080/](http://localsot:8080/) also doesn't show antrhing. I even change the port to 80 in server.xml file. 

Does anyone know how it is possible to see the page confirming successful installation of tomcat?

I have to mention that apache is working on my machine and whenever I run tomcat I stop apache. I want to know how I can disable apache running when I boot my computer and enable tomcat instead of it.

---

### Post by Jof84 on 2006-10-29
the tomcat version that comes with ubuntu is using port 8180.
Try [http://localhost:8180](http://localhost:8180) this shuld work

---

