---
title: "paste problem in filesystem"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by aurjun on 2010-08-15
i can't paste any file in the file system. here paste option is omit. if i drag a file a news shows that "permission denied." i need to setup joomla. so its need to paste joomla installation file paste in /var/www inside but i cant do it . what can i do

---

### Post by sandyd on 2010-08-15
> **aurjun said:**
> i can't paste any file in the file system. here paste option is omit. if i drag a file a news shows that "permission denied." i need to setup joomla. so its need to paste joomla installation file paste in /var/www inside but i cant do it . what can i do
```
gksudo nautilus
```navigate over to /var/www with the nautilus window that opens, and drag and drop.
then, run
```

sudo chown -R www-data:www-data /var/www
```

---

### Post by aurjun on 2010-08-15
> **carlee said:**
> ```
gksudo naitulus
```navigate over to /var/www with the nautilus window that opens, and drag and drop.
then, run
```

sudo chown -R www-data:www-data /var/www
```

it doesn't work. nothing is come when i put this code in terminal

---

### Post by sandyd on 2010-08-15
> **aurjun said:**
> it doesn't work. nothing is come when i put this code in terminal
im sorry, im a typo prone person...
try again.

---

