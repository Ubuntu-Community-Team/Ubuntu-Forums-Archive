---
title: "How to access server behind router"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Duffy386 on 2008-12-03
Hi All,

Im new to using ubuntu as a "server" (still need gui so I am using desktop edition). I am more or less doing it to teach myself how to use it.  I want to set up remote desktop and remote ssh to it from work.  I am not too sure how to use it.

I have blanks in my knowledge of what to do. The server is behind a router and I have a dynamic IP.  How do i overcome this? What do I need to set up? 

Thanks

---

### Post by jbrown96 on 2008-12-04
I use dyndns.com, and its really nice. You can get a free account and get up to five addresses for free. Mine is XXXXX.homedns.org (name removed to keep the spam bots away). After registering the domain name, you need to install a small client program. They have a Linux version that runs in the background; every few mintues (I think 30 by default) it sends tells dyndns.com your computer's ip address. This is constantly updated, so any time you type in your website address it will be able to contact your server. I used this with no problems for quite a while (I still have it on my dad's laptop, so I can SSH in if he is having problems). However, now I run it on my router. I know most Linksys routers can do it (I'm using Tomato firmware on mine). This is far easier for me because I'm constantly reinstalling distros, so it's just one less thing to configure.

---

