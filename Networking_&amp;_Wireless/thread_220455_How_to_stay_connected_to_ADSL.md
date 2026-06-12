---
title: "How to stay connected to ADSL"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by rudra on 2006-07-21
I have installed Dapper and used 'pppoeconf' to configure my ADSL connection. I can now connect to the internet using 'pon dsl-provider' and the connection speed is good. But the problem is, data transfer stops after about 10/15 minutes while surfing. I then log off from internet using 'poff' command and re-log in to surf the net, but again it is for a short while. Please advise me how to stay connected permanently.

---

### Post by narasim_7 on 2006-07-22
I installed ubuntu 2 hrs back and i am facing the same problem.Who is ur service provider (guess:bsnl).I fiddled with some pppoe.conf and installed pppoe from synaptic.Now waiting for some good news!!
If i succeed i will let u know..

---

### Post by rudra on 2006-07-22
Yes,I use Data One connection from BSNL (India).

---

### Post by narasim_7 on 2006-07-22
Theres is a line in pppoe.conf that asks for the  rp-pppoe.so in /etc/ppp/pluigns which is not there.If it was there i would atleast use pppoe-start to connect.

---

### Post by utnubu001 on 2006-07-22
didnt work mabey its my service provider-u see i live in the middle of no where in south africa
and when i get the guys out here they are like-'wheres the start menu'
wtf?

---

### Post by narasim_7 on 2006-07-22
> **utnubu001 said:**
> didnt work mabey its my service provider-u see i live in the middle of no where in south africa
and when i get the guys out here they are like-'wheres the start menu'
wtf?

I dont get u .. What is it exactly that you are trying to say ? My Dsl modem along with ethernet works fine in Windows XP, Fedora Core 5 and hence i find it fitting to report the problem.

---

### Post by ShirishAg75 on 2006-07-22
narasim_7 there are 3 things which u didn't say 
1. which modem/router you use?
2. which ISP do you connect to?
3. Last but not the least are u having issues or not, the statement doesn't make things clear?

 Have a good siggy which explains what u have as I've done, this way time is saved both ways.

---

### Post by mips on 2006-07-22
If you have a router why even bother using pppoe on ubuntu ???

---

