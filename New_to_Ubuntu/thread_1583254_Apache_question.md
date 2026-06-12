---
title: "Apache question"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Nxion on 2010-09-27
Dumb question.

I have a LAMP server all setup. Where is it that I put my websites at? Does they go in /var/www in there respective folder? Or is it somewhere else?

Thanks

---

### Post by bodhi.zazen on 2010-09-27
I personally put them in 

/var/www/site_1
/var/www/site_2

etc

You then point document root to the respective directories.

---

### Post by Nxion on 2010-09-27
Long time no see bodhi!

I figured that was the right way to do it. Keeps everything simple and together. Thanks!

---

### Post by bodhi.zazen on 2010-09-27
You are most welcome, nice site.

---

### Post by Bachstelze on 2010-09-27
Keep in mind, though, that you can put them pretty much anywhere else if needed.  For example if your root (or /var) partition is small and you need to host a heavy site, you can put in for example in /home/www if you have a big home partition.

Of course use common sense and don't put them in /root or /etc/ssl/private. ;)

---

