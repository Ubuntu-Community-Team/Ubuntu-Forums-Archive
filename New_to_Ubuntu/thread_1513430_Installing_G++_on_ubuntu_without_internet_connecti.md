---
title: "Installing G++ on ubuntu without internet connection"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by bakul2331 on 2010-06-19
Hi ,

I have installed ubuntu v10.04 in my machine. I want to compile my C++ application. But there is no g++ compiler by default. I know that we can install g++ using following command

sudo apt-get install g++

But  above command needs Internet connection to complete installation process. And I do not have Internet connection in my machine. Is there any other way to install g++? 

Can anybody give me link of the package which I can download from somewhere else and install it on my machine?


Regards,
Bakul

---

### Post by cariboo on 2010-06-19
You can install build-essential from the Live CD. Make sure the CD is enabled in Software Sources, then use the usual methods to install the meta package.

---

### Post by bakul2331 on 2010-06-20
Thanks a lot. It worked. 


Regards,
Bakul

---

