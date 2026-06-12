---
title: "Wireless card trouble"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by sideverteuil on 2009-08-11
Hello, I have recently installed Ubuntu 8.10 on my desktop and i am having some trouble getting my wireless card to work. I have a RaLink RT2800 n card.

So far I have tried using the Windows Wireless Drivers program, where you have to find the .inf file, but that does not seem to change anything. As far as compiling the drivers from RaLink's website, well, lets just say I cannot fully understand what they are telling me to do. I can understand it to an extent but whenever I do "make" in teminal, I always end up with some kind of error.

Can anyone help guide me through this process? 

Here is a link to RaLink's website support page: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

And here is a link to the driver I need: [http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz](http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz)

---

### Post by 3rdalbum on 2009-08-11
1. Have you got the build-essential package installed?

2. Have you got the "linux-headers-generic" package installed?

3. Have you navigated your terminal to the directory that contains the source code?

4. What error message are you getting?

---

