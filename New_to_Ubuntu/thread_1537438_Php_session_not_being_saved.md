---
title: "Php session not being saved"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by mvalviar on 2010-07-23
According to my phpinfo my session save dir is /var/lib/php5. I visited some of my localhost sites and sessions are not being saved across pages. I monitored that dir for changes and I don't see any session files being generated.```
root@mumee:/var/lib/php5# ls -l
total 0
root@mumee:/var/lib/php5# ls -la
total 8
drwx-wx-wt  2 root root 4096 2010-07-24 02:36 .
drwxr-xr-x 71 root root 4096 2010-07-02 10:57 ..

```

Could you please explain the terminal output for me? Why does it say 8? when there is nothing there?

---

### Post by mvalviar on 2010-07-24
up

---

### Post by bigboy_pdb on 2010-07-24
It might currently be being saved in the /tmp directory somewhere. You might want to create a [session variable]("http://www.tizag.com/phpT/phpsessions.php") and see if it is being saved. It could be something simple such as a value which is being incremented.

---

