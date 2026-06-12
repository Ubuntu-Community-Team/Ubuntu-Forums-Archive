---
title: "setuid root"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by 007casper on 2008-12-29
I type in terminal 

sudo su

then I get
sudo: must be setuid root 

what is that mean?

thank you

---

### Post by jpkotta on 2008-12-29
"setuid" is a property of files in a Unix system.  It sets the user id to the owner of the file instead of the user that executed the file when the file is executed.  Executables are usually run as whichever user ran them.  

Does sudo work?  If so, you can make sudo setuid with 
```
sudo chmod 4755 $(which sudo)
```
If not, you will have to boot in recovery mode and run the above command.

Also, you can use ```
sudo -i
``` or ```
sudo -s
``` to do what you want.

---

### Post by 007casper on 2008-12-29
Thank you.  I think I did something wrong in the terminal the other day.  A lot of the files, applications are acting up.  I think I am going to reinstall ubuntu. :-/

---

