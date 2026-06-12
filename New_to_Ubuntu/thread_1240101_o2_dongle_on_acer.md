---
title: "o2 dongle on acer"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by rabbi burns on 2009-08-14
Two issues  1)had a great deal of trouble finding help with installing "o2 dongle" (Ubuntu)search coming up with many different types of wifi bt etc. But not o2.

I am relatively new so I assume I am incorrectly using search. Still here's how I managed it.

1.take out your sim  and put it in an unlocked phone then connect to o2 you will receive 3 emails from o2 
1, were sending WAP settings

2,configuration settings slect save, from options 'Access Points' o2 postpay wap  Web settings.....WAP

3,your phone should now be set up any probs free-phone etc.

connect to o2web to establish a connection. But do not browse you will be charged.

remove sim from phone and place back in dongle. Connect to Ubuntu 

You may find a wizard pops up OR  

in the top right panel right click network Edit connections select mobile broadband

a)Select country(wizard only)  
b)select 02 contract or prepay etc
c)connect auto blank
d)number  *99# or (*99***1#)
e)username  o2web
f)password  password
g)APN   mobile.o2.co.uk


PPP settings    configure methods allow tick all  EAP PAP CHAP MSCHAP MSCHAP v2

ipv4 settings.  DNS servers should be filled in automatically if not phone o2
 
click Apply  then SHUT DOWN remove dongle

restart
open Ubuntu
plug dongle in

the o2 icon should be on your desktop if its not wait restart until it is. you wont be able to connect if it isnt there

right click on the o2 icon

select EJECT

Your top right network connections  should start to work if not click on them select o2 connect button and you should start to connect. 

This is the point  I would like someones advice on o2 then asks for access to your keyrings i denied this at first and was cut off i reapplied several times after which o2 message said  o2 requires access to o2s secret password which I allowed and haven't had any further trouble.

 Not knowing a lot about keyrings should I be worried about this request? Anyway I hope this is of help  to some.

---

### Post by ibizatunes on 2009-08-14
what version of ubuntu are you using? 3G support for 02 is very good is 9.04

---

### Post by rabbi burns on 2009-08-14
> **ibizatunes said:**
> what version of ubuntu are you using? 3G support for 02 is very good is 9.04
   
Im'e Using (9.04) it has taken two weeks plus two days of serious trial and error + searching no one seems to have had the same problem getting the o2 dongle to work so there is no help. type in o2 dongle in search and nothing specific comes up.

---

### Post by ibizatunes on 2009-08-14
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/316347](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/316347)
i think you have this bug, i must be luckly i have 02 dongle in 9.04 and it works

Why dont you try 8.10 via a live cd and see if you can connect then, you may need to go back a version till this bug is fixed

---

### Post by rabbi burns on 2009-08-14
> **ibizatunes said:**
> [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/316347](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/316347)
i think you have this bug, i must be luckly i have 02 dongle in 9.04 and it works

Why dont you try 8.10 via a live cd and see if you can connect then, you may need to go back a version till this bug is fixed

I am posting on Ubuntu 9.04 If you read my first post it is a HOW TO I have solved the problem.

I am just trying to help people who come after me as at present searching o2 dongle points nowhere.

---

### Post by ibizatunes on 2009-08-14
O sorry, long day at the office, and its a friday, Sorry

---

### Post by rabbi burns on 2009-08-14
> **ibizatunes said:**
> O sorry, long day at the office, and its a friday, Sorry
  
No worries, is it Friday already?

---

