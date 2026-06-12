---
title: "phpmyadmin won't run on IE or chrome"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by anujs on 2009-04-15
I am logging to phpmyadmin on ubuntu server through winxp client and IE or chrome browser. Th error come as :
"Access denied for user 'login-name'@'localhost' (using password: YES)".

But I am able to login with firefox browser. Why??? what changes are required in conf file? Also, I am able to login through linux machine as client.

Thanks in advance.

---

### Post by freak42 on 2009-04-15
you are able to login from firefox _from the same xp machine_ that runs IE and opera, or are you able to login from firefox _on the same machine_ that runs phpmyadmin?

---

### Post by anujs on 2009-04-16
well....server (ubuntu) with phpmyadmin is one machine and client machine with winxp is different. from client machine...I can login to phpmyadmin with firefos as browser, but unable with other web browsers. why?

---

### Post by nandemonai on 2009-04-16
Works here in both. Are you certain you're entering your details properly?

Only other thing I can think of is an old saved password or perhaps clearing cookies/cache etc

---

### Post by anujs on 2009-04-17
yes...it worked at last... i re-checked username/password of phpmyadmin...and it work fine now in all browsers. 
thanks for all your help.

---

