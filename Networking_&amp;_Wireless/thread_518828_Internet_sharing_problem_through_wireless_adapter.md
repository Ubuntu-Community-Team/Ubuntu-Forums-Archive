---
title: "Internet sharing problem through wireless adapter"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by dying4004 on 2007-08-06
guyz

i am new to ubuntu. using kubuntu 7 for last 3 days.  i need some help regarding internet sharing through wireless adapter.


heres my setup:


PC with kubuntu 7.0   with the internet connection and laptop with windows xp.

PC is connected through lan card and PPPoE. PC got an wireless adapter.

Laptop got builtin wireless adapter.

so now i need to setup the internet sharing on kubuntu so that my laptop can access internet through kubuntu.

so guyz please help me to configure this. cheerz

---

### Post by zero-9376 on 2007-08-06
have you established a connection between the laptop and PC, if you dont have a wireless AP you will have to set up an adhoc network (unless you are lucky and your PCs wireless can be put into master mode so it acts as an AP). Im sure there are howtos on here about adhoc wireless, you then need to look at the connection sharing, which I am looking into myself at the moment. For me the best solution would be bridging the connections but apparently this rarely works with wireless cards so the other option is to use a program called firestarter which will allow you to configure your firewall/routing and make your pc a gateway.

---

### Post by dying4004 on 2007-08-06
zero-9376:  bro actually i have been trying for last 2 days to set this up and i tried so many things.

i am using tp link wireless adapter and i used windows driver in kubuntu to install my adapter.

wireless adapter is found and works fine in kubuntu but unfortunately i couldnt connect my laptop with kubuntu. 

i tried firestarter  but doesnt work.

if you find anything helpful regarding this issue plz let me know in this thread.  cheerz

---

### Post by zero-9376 on 2007-08-07
have you looked into ad-hoc mode, it is to join two computers without a router and may be your solution. 
if you do this you may need to set your wireless card up with a static ip, this is also required for firestarter to work
you will need to make sure that the addresses of the eth0 and wireless are not in the same range, i used 192.168.0.X for internet side and 192.168.1.X for internal. Because your connection is via DHCP you just need to make sure they are not the same.

you have to establish a connection between the laptop and comptuer via ad-hoc network before you can do any of this, have a look at the man page for iwconfig to get started.

---

