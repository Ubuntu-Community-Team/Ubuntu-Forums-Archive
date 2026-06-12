---
title: "emerald autostart"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-04-28
how do i make emerald to start when i boot up to ubuntu?

thanks!

---

### Post by doas777 on 2009-04-28
go to System -> Administration ->Startup Programs
and add an entry with 

```
emerald --replace
```

---

### Post by MontelEdwards on 2009-04-28
> **doas777 said:**
> go to System -> Administration ->Startup Programs
and add an entry with 

```
emerald --replace
```
or he can add that into his .profile

---

### Post by lovinglinux on 2009-04-28
Since I installed 9.04, emerald is loading automatically without adding *emerald --replace* to the "Startup Applications" (aka Session). Anyone can confirm this or my system has gone crazy?

I really don't care if it's a bug, because I like it  :lol:

BTW  doas777, since you are using Hardy Heron, you should look for "Session", not "Startup Applications"

---

### Post by doas777 on 2009-04-28
lol. I guess I need to update my profile. I must say, I find the new name an improvement.
I use a seperate home dir, so upon upgrade to januty, the "Session" setting remained, and i did not have to readd it this time, so i don't really know if it is still needed.

cheers

---

### Post by tjwoosta on 2009-04-28
if you have compiz fusion icon installed you can select emerald as the window decorator and it will start emerald for you, but i think you may need to add fusion-icon to the startup programs for this to work

---

