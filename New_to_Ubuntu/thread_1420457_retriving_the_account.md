---
title: "retriving the account"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-03-03
by mistake i deleted all the user in kubuntu and when i restarted the computer and tried to log in it show that log in failed and there any other way to access the kubuntu ?

---

### Post by delectate on 2010-03-03
root ,login

---

### Post by 1991sudarshan on 2010-03-03
password for that??

---

### Post by Genius2999 on 2010-03-03
The root account on Kubuntu is disabled by default, so that's a no go.  Your best bet is to enter recovery mode and create another user account  through the console. I would have a read of this [link :)]("http://www.psychocats.net/ubuntu/resetpassword")

[B]Edit
[/B]Or use the instructions my learned friend below has posted :)

---

### Post by sisco311 on 2010-03-03
Reboot the computer and select Recovery Mode from the grub menu.

You may have to press the Escape key or hold down the Shift key (9.10) during bootup in order to see the menu.

Wait for all the boot-up processes to finish.

Select *Drop to root shell prompt* option from the Recovery Mode menu.

Type:
```
adduser **username**
```
to create a new user.

Add it to the admin group:
```
gpasswd -a **username** admin
```

Type **exit** or press Ctrl+d and choose to *resume a normal boot*.

---

### Post by anaconda on 2010-03-03
another way to add user to a (admin) group:
```
adduser username admin
```
(when the user "username" already exists..

When you deleted your old users their home-directories were propably NOT deleted! So you propably didn't lose any data.  :)

---

