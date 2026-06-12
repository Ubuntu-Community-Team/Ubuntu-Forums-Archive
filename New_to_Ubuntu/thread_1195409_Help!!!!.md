---
title: "Help!!!!"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by rkae1020 on 2009-06-23
hi im new to ubuntu, im from windows and practicing it..im having problem with permission..it goes like this..i want to save a file called myphp.php in the folder named www which can be found in my system file /var/www/ but the system won't let me save any kind of file on that folder its because i don't have permission to do so..WHAT THE HECK!!! im the administrator yet i don't have PERMISSION???!!!!!! what should i do?? how many admin do ubuntu has aside from me?? its really confusing..and im still a newbie here..as in 0% knowledge on this..Please help me everyone..

---

### Post by Zzl1xndd on 2009-06-23
The trick here is that you are not the Root user. Ubuntu doesn't have a Root user by defualt. There are several ways you could gain access to this folder and Im sure some will suggest different ways. 

I use 

```
gksudo nautilus
```

This opens a Nautilus window with access to everything.

---

### Post by Sub101 on 2009-06-23
Ubuntu has the normal users, like the user account you will use to sign into your computer, and super user accounts, namely the root account. This is to ensure users, and more importantly intruders, can not do too much damage to the pc.

/var/www is, I believe, owned by root so no users other than root can edit the folder.

---

### Post by jbruced on 2009-06-23
Couple ways to do it.

If you are using nautilus(Ubuntu file manager) then you will need to start nautilus with root permissions from the terminal like this:

sudo nautilus

This is dangerous if you make any mistakes, so using the terminal to do your work is the recommended means using sudo before any file copy/move/create commands. This is a temporary means to gain root (as in master admin) access.


Ubuntu is not like Windows, nor will it every be. Ubuntu is inherently secure, and moving files into areas other than the home directories is usually done by admins and higher end users, so dangerous file system areas are always protected.

Hope this helps.

---

### Post by MC JJ Lazer Fists on 2009-06-23
[]("http://ubuntuforums.org/showthread.php?t=560592")[http://ubuntuforums.org/showthread.php?t=560592](http://ubuntuforums.org/showthread.php?t=560592)

Basically you need to set the ownership to your account instead of root.
Change group ownership to www-data 
Set the permissions of /var/www to 0751
Set the permissions of /var/www/* to 0771


chmod permission masks:
---------------------------------
Owner   Group   Public
4-2-1     4-2-1     4-2-1
r-w-x     r-w-x    r-w-x
--------------------------------

sudo chown YourLogin -R /var/www
sudo chgrp www-data -R /var/www
sudo chmod 0751 -R /var/www

sudo chmod 0771 /var/www/*

---

### Post by rkae1020 on 2009-06-23
so what should i actually do? will some one give some step by step easy to understand procedures on this?

ohh well i got it..hehehe THANK YOU SO MUCH GUYS... ^_^

---

### Post by Zzl1xndd on 2009-06-23
For my method open a terminal window from: Applications > accessories. Then type in 


```
gksudo nautilus
``` 

it will ask for your password.

it will open a Nautilus Windows with Root permisions, simply navigate to the folder you want and drop the file in.

---

