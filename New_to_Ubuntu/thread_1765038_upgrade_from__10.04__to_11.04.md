---
title: "upgrade from  10.04  to 11.04"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by quarkhirad on 2011-05-22
I have  ubuntu  10.04 lucid lynx. I wanted to directly upgrade from  10.04 to 11.04 hence  i downloaded the alternate version of 11.04. But now when i try and start the upgrade  it  says this  application cannot  upgrade lucid  to natty.  

Please help me to upgrade from 10.04 to 11.04 directly.  

:(:(

---

### Post by corncob on 2011-05-22
Hopefully somebody will jump in and tell us what the alternate version is.  Although I've seen it on the list I have no idea what its for.
Anyway, my understanding is that you can only do that upgrade one step at a time -- first to 10.10, then to 11.04.  The command is
```
sudo apt-get dist-upgrade
```
If you want to use the graphical interface go to System > Administration > Update Manager > Settings and change Release Upgrade to 'Normal Releases'.  It should then give you the option to upgrade in Upgrade Manager.

---

### Post by quarkhirad on 2011-05-22
Thanks

---

### Post by muteXe on 2011-05-22
I'd be tempted with a fresh install tbh. Back your stuff up somewhere else and copy it back.
Upgrades have never worked for me.

---

### Post by Megaptera on 2011-05-22
> **corncob said:**
> Hopefully somebody will jump in and tell us what the alternate version is.  Although I've seen it on the list I have no idea what its for.

It's a more minimal text based installer I think, rather than GUI installer

---

### Post by quarkhirad on 2011-05-22
> **muteXe said:**
> I'd be tempted with a fresh install tbh. Back your stuff up somewhere else and copy it back.
Upgrades have never worked for me.

I wonder why?? as i  have upgraded to 8.10 then to 9.04 then to 9.10  then to 10.04 very easily. 

anyway  thanks

---

### Post by muteXe on 2011-05-22
> 
I wanted to directly upgrade from 10.04 to 11.04 hence I downloaded the alternate version of 11.04.


Hold on... Why do you say "hence"?? You don't need to pick the alternative version if you want to upgrade.

---

