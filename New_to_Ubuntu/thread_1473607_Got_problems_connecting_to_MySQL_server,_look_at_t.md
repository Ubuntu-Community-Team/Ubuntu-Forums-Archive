---
title: "Got problems connecting to MySQL server, look at this"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Ubunser on 2010-05-05
I used [HTML]mysql -u username -p[/HTML] but it says Error 1045, access denied to user bla bla bla.
Then I figured there's command [HTML]mysql_setpermission --user=my_bla_bla_bla[/HTML] But that failed me too.
I am stuck on connecting stage. I read somewhere etc/mysql/my.conf may nasty at times. But watching it I didn't get what I am supposed to fix. But you can may a difference if you help me!

---

### Post by jvc26 on 2010-05-08
Did you add the user? Is this on your server or someone elses?

The simple response would be to make sure the user is actually present - add a user as the mysql root user, and then log in - by the sounds of it, either your user is failing auth (password wrong) or the user doesnt exist.

J

---

