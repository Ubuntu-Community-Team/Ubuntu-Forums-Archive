---
title: "Apache Error 403 Forbidden"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by bloodymind on 2008-12-13
I cannot access any files on my server
I've installed LAMP but I get this message when I try to access any on http://

Forbidden

You don't have permission to access / on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at localhost Port 80

can anyone help ?

I'm using Intrepid

---

### Post by spiderbatdad on 2008-12-13
I believe you are using the default sites-available file in /etc/apache2/sites-available/default.
Please post the contents of that file, and the output of the command ```
ls -l /var
```This is a permissions problem. Not sure why you are getting the error. I suspect an extra space in the document directory, or bad permissions. Also see: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Personally I think a lamp stack is not a good way to start. I would recommend starting with apache2, then adding modules as you find a use for them. Why have mysql if you aren't using it?

---

