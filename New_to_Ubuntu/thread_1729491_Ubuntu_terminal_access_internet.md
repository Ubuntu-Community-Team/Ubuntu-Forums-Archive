---
title: "Ubuntu terminal access internet"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Olim on 2011-04-15
Hi, fiends!
Please help me, I've newbie in Ubuntu
I want to install C++ compiler on my Ubuntu, I've internet access with login and password. If I open browser, it requires login and password, there is not problem, all works.
If I write to terminal apt-get install build-essential terminal tries to download needed files. But terminal not requiring login and password, I think that is a problem and that's why I terminal can not download files for installing compiler (g++, g++ 4.3 ...)
How do I install g++?
Thanks for all and sorry for my bad English...

---

### Post by topgun446 on 2011-04-15
> **Olim said:**
> Hi, fiends!
If I open browser, it requires login and password, there is not problem, all works.
If I write to terminal apt-get install build-essential terminal tries to download needed files. But terminal not requiring login and password, I think that is a problem 

Open your browser and enter login n password, once it is connected, then open a terminal and run apt-get... hope this helps :)

---

### Post by Olim on 2011-04-15
> **topgun446 said:**
> Open your browser and enter login n password, once it is connected, then open a terminal and run apt-get... hope this helps :)

I already did it, no luck. Can not access to archive.ubuntu.com
No problem with browser, it opens archive.ubuntu.com, but terminal can not...
Is there any solution?

---

### Post by yetiman64 on 2011-04-15
> **Olim said:**
> Hi, fiends!
Please help me, I've newbie in Ubuntu
I want to install C++ compiler on my Ubuntu, I've internet access with login and password. If I open browser, it requires login and password, there is not problem, all works.
If I write to terminal **apt-get install build-essential** terminal tries to download needed files. But terminal not requiring login and password, I think that is a problem and that's why I terminal can not download files for installing compiler (g++, g++ 4.3 ...)
How do I install g++?
Thanks for all and sorry for my bad English...

The bolded command would actually require the use of sudo to elevate its privileges to that of root, requiring the password. 

If you _did_ use sudo before that command and it _didn't_ ask for a password then you must have previously entered the sudo password in terminal within the timeout period for sudo (usually 5 minutes). This is the only circumstance I can think of to explain an apt-get command not asking for a password (or giving the error below when used without sudo)

> $ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?Try the command in terminal
```
sudo apt-get install build-essential
```and let us know if it still fails to download (Edit: please also post here any errors outputted from the terminal if it fails).

---

