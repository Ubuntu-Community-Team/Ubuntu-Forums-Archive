---
title: "Password problem"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Yammy45 on 2009-02-03
Help! new to all this, I installed version 8.10, it repartioned the hard drive and done everything fine, when rebooted it asked for my password but, says its wrong. I know my password was correct and in lower case. So how do i get into it to either change it or get it back off my system to even attempt to re-install it

---

### Post by theDaveTheRave on 2009-02-03
Yammy45

Ahh the pleasures of linux!

I had a similar issue with an old desktop, the solution is amazingly simple really.

When you are booting up you will get a screen where you have a choice of different kernel's (and if you dual boot, into Windows too).

One of the options should be <recovery>

start up this system and then change the password for your sign on with the following from the command line

```

passwd yammy45

```

(I am assuming that yammy45 is your selected username on the system, if not change it as required)

The system will then banner back at you to enter a new password (it will do this twice!). now you should be good to reboot back into your "normal" system.

Hope it all works out for you.

David

ps. sorry for the slow response.

---

