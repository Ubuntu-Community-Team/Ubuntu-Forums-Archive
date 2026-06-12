---
title: "installing tomcat?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by ja660k on 2009-02-15
I think i have it, i have something in
/etc/init.d/tomcat5.5

and when i type tomcat into sympatic i get results that i allready have installed.

but when i try to run my .jsp pages in /var/www/ it doesnt process, it just displays the source, which means that tomcat isnt configured? or theres something im missing

can anyone help?

---

### Post by Nepherte on 2009-02-15
Tomcat listens on port 8000 or 8080 if I recall correctly. So you will have to change your url to something like [http://localhost:8080/](http://localhost:8080/). I'm also not sure about .jsp pages in particular, but tomcat web applications shouldn't be placed in /var/www but in /usr/share/tomcat/webapps instead.

---

