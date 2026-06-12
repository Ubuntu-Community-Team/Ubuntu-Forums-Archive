---
title: "[SOLVED] DNS question about ubunto server"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-12
The server box is connected to a linksys router. I have configured a static ip for the server. I have two dns adresses provided by my cable isp. As I understand those adresses should be entered in the /etc/resolv.config. My question is should I have only the adresses in /etc/resolv.config? Or do I still have to use "search blabla.com"  at the top?

nameserver 2.2.2.2
nameserver 3.3.3.3

or

search blabla.com
nameserver 2.2.2.2
nameserver 3.3.3.3

which is correct? Thanks:confused:

---

### Post by bluefrog on 2008-12-12
both are correct.

if search is included (search example.com) then ping www will search example.com fisrt to find a machine called www. that's all

---

