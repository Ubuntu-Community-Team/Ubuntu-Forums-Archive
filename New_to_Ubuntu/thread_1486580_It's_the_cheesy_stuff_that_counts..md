---
title: "It's the cheesy stuff that counts."
date: 2010-05-18
forum: New to Ubuntu
---

### Post by uRock on 2010-05-18
I have found how to change the motto of the day banner in the ssh terminals, but I have not yet found how to do it for the regular terminal. Does anyone know how I can create an MOTD that comes up every time a terminal is opened?

Thanks,
uRock

---

### Post by rnerwein on 2010-05-18
hi
for random messages like: You may worry about your hair-do today, but tomorrow much peanut butter will
be sold.
or: If it is not broke, fix it till it is.
you can get the fortune by: [COLOR=Blue]sudo apt-get install fortune-mod[/COLOR]

and in your ~/.bashrc you have to insert: [COLOR=Blue]test -x /usr/games/fortune && /usr/games/fortune[/COLOR]
(same you can do for /etc/motd : test -f /etc/motd && cat /etc/motd )

this will cause that every time you open a terminal you will get a new slogan.
have fun
ciao

---

### Post by marshmallow1304 on 2010-05-18
Edit: Or that ^.  Probably that ^.  Definitely that ^.



You can probably put echo "message" in .bashrc

---

### Post by uRock on 2010-05-20
> **rnerwein said:**
> hi
for random messages like: You may worry about your hair-do today, but tomorrow much peanut butter will
be sold.
or: If it is not broke, fix it till it is.
you can get the fortune by: [COLOR=Blue]sudo apt-get install fortune-mod[/COLOR]

and in your ~/.bashrc you have to insert: [COLOR=Blue]test -x /usr/games/fortune && /usr/games/fortune[/COLOR]
(same you can do for /etc/motd : test -f /etc/motd && cat /etc/motd )

this will cause that every time you open a terminal you will get a new slogan.
have fun
ciao

Thanks, that worked. I didn't change the MOTD file. I already have that customized to curse at anyone who connects via ssh.

---

### Post by jvector on 2010-05-20
> **uRock said:**
> Thanks, that worked. I didn't change the MOTD file. I already have that customized to curse at anyone who connects via ssh.
...why?

---

### Post by uRock on 2010-05-20
> **jvector said:**
> ...why?

Why not?

---

### Post by jvector on 2010-05-21
but ssh is goo.o.o.d... (especially now we have byobu) - I think I spend half my life ssh'ed into somewhere or other. People should exchange ssh keys instead of wedding rings. People should exchange ssh keys instead of body fluids.

---

