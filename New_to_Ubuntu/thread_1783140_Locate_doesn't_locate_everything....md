---
title: "Locate doesn't locate everything..."
date: 2011-06-15
forum: New to Ubuntu
---

### Post by vv1984 on 2011-06-15
Hi,
i've got little troubles with **locate** command.

I'm trying (as root) to locate some "sensible" files like
httpd.conf or mysql.sock among my filesystem. 
But it doesnt return a thing. 

Is there any problem with **locate** in ubuntu 10.10?
Or maybe the problem is **su**?

After logging as root i get errors when i try to edit some apache config files. The problem slips away if i use **sudo**. Quite weird, isn't it?

---

### Post by ajgreeny on 2011-06-15
Have you updated the files database with ```
sudo updatedb
```as a terminal command?

You have obviously activated the root user for some reason, and I suppose that may make a difference, but I am not sure why it should.

---

