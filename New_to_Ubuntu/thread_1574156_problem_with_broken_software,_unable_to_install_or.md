---
title: "problem with broken software, unable to install or remove any software"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by nadha on 2010-09-13
when i open synaptic package manager the following error occurs ,  

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

help me out i, unable to install or update any new software

---

### Post by rockerphil on 2010-09-13
pretty easy fix, all that happened is the last time you tried to install a program it didn't get to finish. simply open up a terminal and run this command.

```
sudo dpkg --configure -a
```

hope this helps,

Phil

---

### Post by nadha on 2010-09-13
phil 

i  tried that but its taking infinite time to complete  , i need help in removing this broken software

---

### Post by mowglinz on 2010-09-13
What software you were trying to install?

Try running 'tail -f /var/log/dpkg.log' in a second terminal while you run the first command.

---

### Post by nadha on 2010-09-13
there is some problem with some fonts provided by microsoft ,its unable to complete the download ,how do i stop it.I just want to run my synaptic manager properly  

( status half-configured ttf-mscorefonts-installer 3.2)

---

### Post by wilee-nilee on 2010-09-13
Besides the first command there is another you might try.
```

sudo apt-get install -f 
```

---

### Post by sandyd on 2010-09-13
> **nadha said:**
> there is some problem with some fonts provided by microsoft ,its unable to complete the download ,how do i stop it.I just want to run my synaptic manager properly  

( status half-configured ttf-mscorefonts-installer 3.2)
```

sudo dpkg --remove --force-remove-*reinstreq *ttf-mscorefonts-installer
```

---

### Post by nadha on 2010-09-13
thanks but it returned this:

dpkg: status database area is locked by another process

---

### Post by mowglinz on 2010-09-14
```
sudo killall dpkg synaptic aptitude
```

---

### Post by coffeecat on 2010-09-14
> **nadha said:**
> thanks but it returned this:

dpkg: status database area is locked by another process

People are giving you terminal commands without telling you why you are getting these errors. I'll explain this one. You were trying to run dpkg in the terminal with a graphical package manager open, either Synaptic, Update Manager or Software Centre. You can only have one graphical package manager open at once and you cannot run dpkg, apt-get or aptitude in the terminal if any of those are open. Close whichever package manager you have open and then try your dpkg command again.

---

### Post by nadha on 2010-09-14
thanks every one . Every thing is fine now  ):P

---

