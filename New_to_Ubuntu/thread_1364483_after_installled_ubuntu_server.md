---
title: "after installled ubuntu server?"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by ttdanh on 2009-12-25
how can i upload my files to the root of web?

and what is free web server control panel you guys recommend today?

i am new to ubuntu ? (lenovo j115 amd64)

thank all ! happy holiday?

---

### Post by ikt on 2009-12-26
> **ttdanh said:**
> how can i upload my files to the root of web?

If you're trying to upload files to your web host, usually the best way is via ftp, there are multiple ftp clients that you can download.

---

### Post by Rhubarb on 2009-12-26
> **ttdanh said:**
> how can i upload my files to the root of web?
You'll need to put your files (eg index.html) into /var/www/ directory, and if you like, change the files' ownership to www-data.

Example:
```
sudo cp index.html /var/www/
sudo chown www-data:www-data /var/www/index.html
```


> **ttdanh said:**
> and what is free web server control panel you guys recommend today?
I don't use one myself, I just ssh into my server, there I have full access to the bash prompt (serveral bash prompts if I use *screen*
Others use *phpmyadmin*

---

