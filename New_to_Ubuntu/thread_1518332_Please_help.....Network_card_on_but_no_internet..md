---
title: "Please help.....Network card on but no internet."
date: 2010-06-26
forum: New to Ubuntu
---

### Post by hendrix1564 on 2010-06-26
So, i am a complete newbie to Ubuntu. I used Wubi to install ubuntu. It installed ubuntu 10.04 (The newest version)  I've been trying to set up the connection for hours..  I use 64 bit wep. (Yes i know, i shouldn't but, no one lives by me. lol)  I put in the codes and nothing happens. It just says disconnected.  I have it duel booted with vista. I'm guessing i need some sort of driver right? Please help. :)

---

### Post by mapes12 on 2010-06-26
What wifi adapter do you have? Applications>Accessories>Terminal ```
sudo lshw -C network
```

---

### Post by hendrix1564 on 2010-06-26
Ive done that code before and it asks me for my password but it will not allow me to put my password it.  But i know its a Dell wireless 1390 WLAN Mini-Card

---

### Post by flyfishingphil on 2010-06-26
> **hendrix1564 said:**
> Ive done that code before and it asks me for my password but it will not allow me to put my password it.  But i know its a Dell wireless 1390 WLAN Mini-Card
Just in case you're not aware. When you type in the password it won't show. It's in there but you can't see it. Try entering the password and hit Enter.

---

### Post by mapes12 on 2010-06-26
> **hendrix1564 said:**
> Ive done that code before and it asks me for my password but it will not allow me to put my password it.In that case something is wrong with how Ubu has installed. Dual booting is an alternative to Wubi and may solve your problem. Here's a HowTo:-

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by t1nm@n on 2010-06-26
hey you must be new to to linux...you see you cannot see the password as you type it in.
not even like the dots you see when you type the password in windows... it's supposed to be comman for all *nix .just type the password as usual...it'll be alright heres an example

> 
tinman@pc:~$ sudo su
[sudo] password for tinman: 
root@pc:/home/tinman# 


---

