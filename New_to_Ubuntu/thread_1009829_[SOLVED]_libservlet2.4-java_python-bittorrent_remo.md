---
title: "[SOLVED] libservlet2.4-java python-bittorrent removed"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-13
i was trying to install a program on the terminal, and it processed to ask me to remove > libservlet2.4-java python-bittorrent

it says it is unused and i need to remove it in order to install mobloquer.

anyways it was removed. and i coudlnt get mobloquer to install. some 404 error. which was weird.

I use transmission bittorrent to download movies. 

what is 
> libservlet2.4-java python-bittorrent
is it an important file that i need? is it a security vulnerability that i need for transmission bittorrent?

---

### Post by nakama85 on 2008-12-13
> **shiningkenmonster said:**
> i was trying to install a program on the terminal, and it processed to ask me to remove 

it says it is unused and i need to remove it in order to install mobloquer.

anyways it was removed. and i coudlnt get mobloquer to install. some 404 error. which was weird.

I use transmission bittorrent to download movies. 

what is 

is it an important file that i need? is it a security vulnerability that i need for transmission bittorrent?

you can be pretty confident that if it says it is not used than it is not needed.

 apps have dependencies if you ever do need this dependency again it will let you know and prompt you to install it.

Or if your still concerned you can reinstall it via synaptic.

as for what it does I am not exactly sure

---

### Post by nakama85 on 2008-12-13
or if you want to reinstall it simply go to 
Applications--->Accessories---->Terminal 

and paste this code
```
sudo apt-get install libservlet2.4-java python-bittorrent
```

It will prompt you for your password and then automatically install it agian

---

### Post by shiningkenmonster on 2008-12-13
thanks bro. you get a thanks medal

---

