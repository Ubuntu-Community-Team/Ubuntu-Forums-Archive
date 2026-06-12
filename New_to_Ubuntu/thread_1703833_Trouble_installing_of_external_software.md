---
title: "Trouble installing of external software"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by spirited on 2011-03-09
Hi all, 
 
I have just installed ubuntu , and i am trying to install another software on it , however i hit an error indicating that the environment variable for the software has not been set. However the software installation is complete and in a directory but i just can't execute it.
 
The error is 
 
ERROR 9146:
The environment variable FEKO_HOME must be set.
Please execute the shell script "initfeko".
 
would it be there some libraries are missing for the environment variable to be set??
 
Thanks;)

---

### Post by Locke_99GS on 2011-03-09
Have you tried running the shell script "initfeko" yet?

---

### Post by spirited on 2011-03-09
> **Locke_99GS said:**
> Have you tried running the shell script "initfeko" yet?
 
 
Yup i tried but there is no response as well and there is no shortcut on the menu

---

### Post by Locke_99GS on 2011-03-09
If you installed feko to default location, it looks to install to /opt/feko. Try running */opt/feko/bin/initfeko*

---

### Post by spirited on 2011-03-09
> **Locke_99GS said:**
> If you installed feko to default location, it looks to install to /opt/feko. Try running */opt/feko/bin/initfeko*
 
Thanks for the reply 
 
I tried to run the path given but still there is no response from the system.

---

### Post by userdce on 2011-03-13
open initfeko file and edit it

it works by editing there

---

