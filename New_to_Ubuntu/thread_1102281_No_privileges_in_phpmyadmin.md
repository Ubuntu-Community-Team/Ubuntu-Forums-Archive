---
title: "No privileges in phpmyadmin"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by blackfox on 2009-03-21
Hey, I'm using ubuntu 8.10 and I've installed Xampp for linux. It's working perfectly fine but, It says I don't have privileges to create new databases from phpmyadmin? - why is it like that? and how can I fix it?

thanks

---

### Post by yeats on 2009-03-21
Are you logging into MySQL as root? or as yourself?  You have to explicitly grant privileges to your "regular" MySQL user account while logged in as MySQL root. (Not to be confused with your Linux user/root accounts).

---

