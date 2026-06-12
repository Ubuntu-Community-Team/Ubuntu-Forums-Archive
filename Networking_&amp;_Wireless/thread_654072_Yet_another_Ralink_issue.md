---
title: "Yet another Ralink issue"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by veribaka on 2007-12-30
Hello friends! I've been working around gutsy for a few months now, however I came across a rather annoying problem. I am able to connect to the internet using my  RaLink RT2561/RT61 rev B 802.11g, however whenever I reboot the computer I have to re-enter the WEP code which is extremely annoying.

When I boot my laptop I get this message...:

> kinit: No resume image, doing normal boot.

I am very sure this has something to do with my problem. I have tried to follow wieman's guide AND the wiki on RT61 chip wireless cards, however there's always something foiling my intentions.

On the part in the wiki where it said to enter "make all" I got the following:
> 
root@carmo-laptop:/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module# make all
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function &#8216;RT61_probe&#8217;:
/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function &#8216;RT61_open&#8217;:
/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[2]: ** [/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Erro 1
make[1]: ** [_module_/home/carmo/RT61_Linux_STA_Drv1.1.0.0/Module] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.22-14-generic'
make: ** [all] Erro 2

Whenever I follow wiemans guide, I get to the part where I got to extract the driver from the windows installation file and I get some error about the file not being compressed.

Any help out there? Feels like I've tried everything.

PS. If there's a part you don't understand in the log, ask, it's probably because it's in portuguese ;).

Edgar

---

### Post by veribaka on 2007-12-31
/bump !

Any tips would really come in handy.

---

### Post by veribaka on 2008-01-02
Small update. Whenever I try to install other drivers I purely lose every internet connection I got, cabled or wireless.

---

### Post by wieman01 on 2008-01-10
Still struggling with the driver?

---

### Post by veribaka on 2008-01-10
Well I'm not so sure it's because of drivers, does it have to do with having to input my WEP everytime I boot?

---

### Post by wieman01 on 2008-01-10
You could try to follow my Ralink tutorial (see signature for more)... Or is your card now working?

---

### Post by veribaka on 2008-01-10
I have tried to, but last time I did I wasn't able to unpack the windows drivers. I access the internet, it's just a pain to have to enter the code every single time I boot the computer.


I might try this:

[http://www.cnet.com/8301-13880_1-9839735-68.html](http://www.cnet.com/8301-13880_1-9839735-68.html)

The comments there suggest the people got it to work.Using the solution they posted.

---

### Post by veribaka on 2008-01-12
Solved it with wicd wireless manager!

---

