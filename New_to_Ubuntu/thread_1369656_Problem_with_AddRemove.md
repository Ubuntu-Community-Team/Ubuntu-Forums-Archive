---
title: "Problem with Add/Remove"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by mmsb85 on 2010-01-01
Hello, 

I have been trying to install some software such as firefox (latest  version) and clam, but i am always getting the following message.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I ran 'sudo dpkg --configure -a' in a terminal but nothing happened.

Also, I tried to install the software from terminal but I got the same message given above. 

Please be as detailed as possible as I am very new to Linux.

Any help is highly appreciated. 

Thanks

---

### Post by spiderbatdad on 2010-01-01
how about try:
```
sudo apt-get install -f
sudo apt-get autoremove
```

---

### Post by mmsb85 on 2010-01-01
Thank you spiderbatdad, it is working now

---

