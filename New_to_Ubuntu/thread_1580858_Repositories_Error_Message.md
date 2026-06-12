---
title: "Repositories Error Message"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by jinouye on 2010-09-24
Hi,

I'm brand new to Ubuntu and am having the hardest time with it.  I'm trying to install updates and extra repositories, but keep getting this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Help!  What do I do to fix this?

Thank you very much for your assistance :)

---

### Post by Gone fishing on 2010-09-24
I Googled this one as it looked interesting and seems to be caused by an interrupted broken update.

I'd try opening a terminal

```
and sudo dpkg -- configure -a
```

followed by

```
sudo apt-get -f install
```

if that doesn't work

```
cd /var/lib/dpkg/updates
```

then 

```
rm *
```

---

### Post by NightwishFan on 2010-09-24
Open the applications -> accessories -> terminal, type the following, and push enter.
```
sudo dpkg --configure -a
```

It will as for your password but wont show up, this is normal. Let it run, and push y if prompted.

Welcome to Ubuntu! I hope you have fun with it! Please note that errors like this do not happen in usual operation. However being like the old Unix you have the power and are encouraged to have control over your system. This includes having the power to cause problems. Be especially careful when a program asks to prompt for your password. :)

I hope it works out well for you.

---

