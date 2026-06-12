---
title: "Shorewall setup help..."
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Hobbes20xx on 2009-12-13
Hey, so i just installed shorewall (on ubuntu server v8.10 32-bit) using this command: ```
sudo aptitude install shorewall
```Now, i want to block everything other than port 80 (HTTP) and port 22 (SSH). i read that ima supposed to copy the configuration files using this command---
```
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/
```[FONT=Verdana]
(is this even  a necessary step?) but, when i do, i get an error saying that it doesn't exist...[/FONT]

[FONT=Verdana]anyway, even if i try to open the rules file to edit them using [/FONT]this code:
```
sudo nano /etc/shorewall/rules
```[FONT=Verdana] 
it opens the file with nothing in it...[/FONT]
[FONT=Verdana]
thanks ahead of time :)[/FONT]

---

### Post by talsemgeest on 2009-12-13
> **Hobbes20xx said:**
> Hey, so i just installed shorewall (on ubuntu server v8.10 32-bit) using this command: ```
sudo aptitude install shorewall
```Now, i want to block everything other than port 80 (HTTP) and port 22 (SSH). i read that ima supposed to copy the configuration files using this command---
```
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/
```[FONT=Verdana]
(is this even  a necessary step?) but, when i do, i get an error saying that it doesn't exist...[/FONT]

[FONT=Verdana]anyway, even if i try to open the rules file to edit them using [/FONT]this code:
```
sudo nano /etc/shorewall/rules
```[FONT=Verdana] 
it opens the file with nothing in it...[/FONT]
[FONT=Verdana]
thanks ahead of time :)[/FONT]
Try running ```
ls /etc/shorewall/
``` and see if the file is actually there. If it isn't, try running ```
ls /usr/share/doc/shorewall-common/examples/one-interface/
``` to see which files should have been copied.

---

### Post by Hobbes20xx on 2009-12-14
Alright, so i ran the 
```
ls /etc/shorewall/
```and came up with "no such file or directory"
so, moving on to  
```
ls /usr/share/doc/shorewall-common/examples/one-interface/
```same deal, "no such file or directory"

---

### Post by talsemgeest on 2009-12-14
> **Hobbes20xx said:**
> Alright, so i ran the 
```
ls /etc/shorewall/
```and came up with "no such file or directory"
so, moving on to  
```
ls /usr/share/doc/shorewall-common/examples/one-interface/
```same deal, "no such file or directory"
Hmm, in that case either the application is not installed, or you have installed a version that is different from the version the instructions were written for.

---

### Post by Andreauk on 2010-07-22
> **Hobbes20xx said:**
> Alright, so i ran the 
```
ls /etc/shorewall/
```and came up with "no such file or directory"
so, moving on to  
```
ls /usr/share/doc/shorewall-common/examples/one-interface/
```same deal, "no such file or directory"

Try:

```
sudo cp /usr/share/doc/shorewall/default-config/* /etc/shorewall/
```

---

### Post by descon on 2012-05-06
same problem as OP - Andreauk's solution worked! thanks!

---

