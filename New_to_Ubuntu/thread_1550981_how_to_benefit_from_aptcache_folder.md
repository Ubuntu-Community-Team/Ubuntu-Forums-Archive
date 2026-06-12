---
title: "how to benefit from apt/cache folder"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by magedsoft on 2010-08-11
[SIZE=4]Hay Every Body : [/SIZE]

[SIZE=2]at the first i want to ask all of you to excuze me , i'm not good in english 
 
i have qestion i get and install ubuntu 10.4 like [/SIZE]
**snowpine**

advise me and i want to thank him too much 

my qestion ??
how can i benefit from deb package in apt/cache folder ???? i make update and install deb package  how make it useful 

put in mine i can't paste in thing in cache folder 

i wait the respond

---

### Post by mike555 on 2010-08-11
Is this the info you want?

 to avoid downloading all updates after a reinstall:
ubuntu stores downloaded packages in /var/cache/apt/archives

save these files and after a new installation copy them to the same location.
after that do a apt-get update and apt-get upgrade

---

### Post by theboxseat on 2010-08-11
> **mike555 said:**
> Is this the info you want?

 to avoid downloading all updates after a reinstall:
ubuntu stores downloaded packages in /var/cache/apt/archives

save these files and after a new installation copy them to the same location.
after that do a apt-get update and apt-get upgrade

Would it not be optimal to actually have /apt on its own separate partition then?

---

### Post by holastickboy on 2010-08-11
I also find it very useful for when you are downloading an update (which contains a lot of packages usually) and your internet drops out, you can pick up from where you left off (eg you dont have to download the packages that are already in the cache, just the ones that you didnt download).  In other words, its useful for unreliable connections (or even slow ones)

---

### Post by magedsoft on 2010-08-12
thank u for your answer 
but i can't paste any thing in cache folder

---

### Post by mike555 on 2010-08-12
type in terminal    "  gksu nautilus  " without the quotes    ... that will give you root rights in nautilus ,so be careful...

---

