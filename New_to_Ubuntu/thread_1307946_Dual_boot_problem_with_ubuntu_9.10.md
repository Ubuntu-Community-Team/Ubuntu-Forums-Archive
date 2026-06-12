---
title: "Dual boot problem with ubuntu 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by proaditya on 2009-10-31
Hi all
I am a newbie to linux
Before i had ubuntu 9.04. while installling i had grub install it not to the mbr but to the linux partition. Inside windows i used easybcd to add an entry to windows boot loader pointing to the appropriate partition. all this worked fine.
But the same dual boot method does not work for ubuntu 9.10. I have tried this 3 times. 
Any help on this would be really beneficial.
Aditya

---

### Post by proaditya on 2009-11-01
HI

I just solved the problem
I was not aware of the fact that Kaola uses grub 2 and not legacy.
The problem was solved by using the latest easy bcd (alpha)

aditya

---

