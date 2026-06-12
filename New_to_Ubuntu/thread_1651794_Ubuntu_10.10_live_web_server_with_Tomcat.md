---
title: "Ubuntu 10.10 live web server with Tomcat"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by yekoko on 2010-12-23
Hello everyone,

I installed ubuntu 10.10 and also Tomcat6 correctly. I copied my war file under webapps, and I can see my jsps in localhost.

Everything so great so far...

But now I want to see my jsps when I enter [www.myaddress.com](www.myaddress.com) in the browser.

I read things like mod_jk but couldn't come up with a good solution.

What must I do?

Please help me, I have to finish a school project.

Thanks...

---

### Post by jvc26 on 2010-12-30
Well, I assume that you have installed the tomcat6 locally and are using localhost on your computer to see the webapps.

If you want to use [www.yourdomain.com](www.yourdomain.com) then you need to update the DNS to point at the machine which has the tomcat6 installation on it, and then it will work.

J

---

