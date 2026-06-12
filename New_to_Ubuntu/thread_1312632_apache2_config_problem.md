---
title: "apache2 config problem"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by neonas on 2009-11-03
I have this problem with apache2 configuration. I have installed mambo and I don't know how to configurate redirect. To access mambo I use my ip\mambo insted I wont to access it like this: my ip\blabla(anything) and whe I type my ip\a it shoul redirect me to my ip\mambo\administrator\ so how to do that?
any ideas?
pls help :(

---

### Post by liquidbee on 2009-11-03
/var/www/.htaccess
```
Redirect 301 /mambo /mambo/administrator
```

This is just a temporary solution. Mambo should have it's own configuration file for Apache ( like phpMyAdmin, etc. ).

---

### Post by neonas on 2009-11-04
thanks! I'll try :)

---

