---
title: "Running the Shell with su"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by SteelCore on 2010-07-17
I'm trying to change to root using su as follows
```
me@my-laptop:~$ su -
Password: 
su: Authentication failure
me@my-laptop:~$
```
but I'm getting the Authentication failure even if I enter the correct password.

---

### Post by Hanzerik on 2010-07-17
> **SteelCore said:**
> I'm trying to change to root using su as follows
```
me@my-laptop:~$ su -
Password: 
su: Authentication failure
me@my-laptop:~$
```
but I'm getting the Authentication failure even if I enter the correct password.

```

sudo su -

```

---

### Post by techunit on 2010-07-17
generally i use

```
sudo su
``` this nearly always works...

I used to use ```
sudo -i
```

---

### Post by new__buntu on 2010-07-17
> **SteelCore said:**
> I'm trying to change to root using su as follows
```
me@my-laptop:~$ su -
Password: 
su: Authentication failure
me@my-laptop:~$
```but I'm getting the Authentication failure even if I enter the correct password.


I'm going to guess that the reason you got an authentication failure was that you were inputting your password, not the root password. To set the root password simply use 

$sudo passwd root

It's not recommended however that you enable the root account, which is by default disabled on ubuntu machines, for security reasons. Using the command 

$sudo su

,which was mentioned above, will get you into root whether or not you have disabled the password. Lastly, if you have set a root password and want to disable it, the command 

$sudo usermod -p '!' root 

will do that for you. I probably just told you a bunch of stuff you already knew, sorry if that's the case.

---

### Post by bodhi.zazen on 2010-07-17
The preferred method (in Ubuntu) of obtaining a root shell is ```
sudo -i
```

This is due to environmental variables , see :

[Difference between sudo su and sudo -s]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") 

For graphical applications use gksu

See also :

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by SteelCore on 2010-07-18
> **new__buntu said:**
> I probably just told you a bunch of stuff you already knew, sorry if that's the case.

Not at all. Your reply was very instructive. I thank you and the other forum members for your time.

---

### Post by new__buntu on 2010-07-18
> **SteelCore said:**
> Not at all. Your reply was very instructive. I thank you and the other forum members for your time.

In that case, glad to be of assistance :)

---

