---
title: "HOW TO connect to internet"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Xidiot on 2009-06-11
Hi, first sry for the bad english.
Here's my problem, I have new i-net provider and I can't connect to internet. My old provider give's me PPPoE connection, but the new one give's me normal cable net. On win I have no problem, my ip adress is 192.168.XXX.XX. Do I have to delete the pppoe config on ubuntu or what have to do?! Please help me. I tried with :
ifconf eth0 down
ifconf eth0 up

---

### Post by briguy47 on 2009-06-13
> **Xidiot said:**
> Hi, first sry for the bad english.
Here's my problem, I have new i-net provider and I can't connect to internet. My old provider give's me PPPoE connection, but the new one give's me normal cable net. On win I have no problem, my ip adress is 192.168.XXX.XX. Do I have to delete the pppoe config on ubuntu or what have to do?! Please help me. I tried with :
ifconf eth0 down
ifconf eth0 up


If you are switching from PPoE to Cable HSI, then you should probably delete or disable the PPoE config and start fresh.  Can you post the results of ifconfig please?

---

