---
title: "PHP Scripts not working after transfer from Windows to Ubuntu"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by reaktiv8 on 2011-03-15
Hi again, complete unix newb here.
 
I have just set up a LAMP server. I created a file called test.php on my windows machine. It looks like this
 
[PHP]<?php
phpinfo();
?>[/PHP]
 
I copy it into /var/www and all i get is a blank page like this
 
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<HTML><HEAD>
<META content="text/html; charset=windows-1252" http-equiv=Content-Type></HEAD>
<BODY></BODY></HTML>
```
 
however, if i go sudo nano /var/www/test2.php, type in 
[PHP]<?php
phpinfo();
?>[/PHP] and then save, the script actually works. Why?

---

### Post by wojox on 2011-03-15
Maybe permissions. Try

```
sudo chmod +x /var/www/test.php
```

---

### Post by reaktiv8 on 2011-03-15
> **wojox said:**
> Maybe permissions. Try
 
```
sudo chmod +x /var/www/test.php
```
still no go :(

---

### Post by wojox on 2011-03-15
I know Windows uses carriage return and a line feed to end lines, while Linux just uses line feed.

---

### Post by reaktiv8 on 2011-03-15
> **wojox said:**
> I know Windows uses carriage return and a line feed to end lines, while Linux just uses line feed.
 That was my first thought also, so I created the same file with line feeds only (0A) but it still gave the same result.

---

### Post by wojox on 2011-03-15
Have you opened test.php in nano and did anything look peculiar?

---

### Post by reaktiv8 on 2011-03-15
> **wojox said:**
> Have you opened test.php in nano and did anything look peculiar?
 i opened it in nano, deleted a character and then retyped it, then saved. it still doesn't work. everything looked normal.

---

