---
title: "Can't install any software"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Jolicoeur on 2010-09-21
I was installing software this morning when one of them messed up and stopped intalling (crashed).  got out of it all and then opened up the software center and tried to install different software it would not install, tried more same thing. I think something from the crashed install is hanging it up. Can anybody help?  Thank you.

---

### Post by hipp-e on 2010-09-21
try installing something from a console, through a 
sudo apt-get install *programm name* (mc for example)
enter root password and read the error message - most likely you'll find a command to repair it in the error message

---

### Post by oldos2er on 2010-09-21
Open a terminal (Applications, Accessories, Terminal), and run ```
sudo apt-get update && sudo apt-get safe-upgrade
```
If there are errors, please post the full terminal output here.

---

### Post by madmax75 on 2010-09-22
You probably have some broken packages as a result of the crash.

Try these commands in the Terminal:

sudo apt-get update
sudo apt-get -f install

"sudo" will give you root privileges and it will prompt you for your password. The first one updates your software package list, the second one will try to fix any broken packages.

You could also try:

sudo dpkg --configure --pending

This will reconfigure all unpacked but unconfigured packages (according to dpkg man page).

---

