---
title: "who is admin ???"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by sam_ad on 2010-11-04
While installing ubuntu I don't remember being asked about setting admin password.
Now I want to change source.list file and it is asking me for admin password which i obviously don't know ..
what to do ??? please help .

---

### Post by wojox on 2010-11-04
Your the admin. Enter your normal password.

---

### Post by marin123 on 2010-11-04
i guess you will need to make a fresh install and remember admin password...
if it was that easy to break admin password, there would be no point in creating one.
admin (root user) it user that has rights to make changes to your system... basically, its a security thing, which makes you type in your password before modifying your system...

---

### Post by julio_cortez on 2010-11-04
> **marin123 said:**
> i guess you will need to make a fresh install and remember admin password...
Before doing so, try the password of your account.

Ubuntu needs root privileges to perform some tasks (like modifying files like fstab). But the root account is disabled by default in Ubuntu so you'll have to provide **your account's password** when asked for an admin password (*provided that you're using the account that you setup during installation, or another account that has proper **sudo** rights*).

---

### Post by uRock on 2010-11-04
> **marin123 said:**
> i guess you will need to make a fresh install and remember admin password...
if it was that easy to break admin password, there would be no point in creating one.
admin (root user) it user that has rights to make changes to your system... basically, its a security thing, which makes you type in your password before modifying your system...
The password can be retrieved without reinstalling. 

OP, if you can't remember your password, then let us know.

---

### Post by sam_ad on 2010-11-04
I tried did that but it doesn't work. It is now allowing me to change permissions for source.list.
After that I tried $su  which didn't work

---

### Post by uRock on 2010-11-04
You have to use the sudo command. su has to be configured.

---

### Post by sam_ad on 2010-11-04
So I should be able to change permissions for sources.list with sudo ?

---

### Post by Hippytaff on 2010-11-04
> **sam_ad said:**
> So I should be able to change permissions for sources.list with sudo ?
 
did you give a password when you installed ubuntu
 
you should be able to
```

sudo gedit /path/to/source.list

```
(not at my ubuntu box and cant remember the path to source.list) :-s
Then it'll ask for your password (the one you gave on installation)

---

### Post by oldos2er on 2010-11-04
Since gedit is a graphical gtk program, use gksu to call it: ```
gksu gedit /etc/apt/sources.list
```

---

### Post by Hippytaff on 2010-11-04
> **oldos2er said:**
> Since gedit is a graphical gtk program, use gksu to call it: ```
gksu gedit /etc/apt/sources.list
```
 
:-s good point

---

### Post by sam_ad on 2010-11-04
yup ! it worked .. thank u all for the help :)

---

