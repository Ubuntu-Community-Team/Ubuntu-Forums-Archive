---
title: "question about a ip?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by dahlberg84 on 2009-11-16
hello

im trying to set up ubuntu server edition on a virtualbox to play with.
ive only choosen to install the "LAMP-server" package and everything else is default.
just enabled the firewall and made sure no ports are open(sudo ufw status). 


this is a way of me  learning about linux and servers in general ;)
now here is my problem/question

when i run** ifconfig** i get ip 10.0.2.15 on eth0.
the only other device is the lo. 

the wird thing is installation went fine and i can still run apt-get to fetch updates and packages. but what is my virtual machines real ip? 

kind regards
dahlberg

---

### Post by blazemore on 2009-11-16
Your virtual machine doesn't have a real IP on your actual network (the hardware you can touch)
It uses Network Address Translation to use your host computer's network hardware.

---

