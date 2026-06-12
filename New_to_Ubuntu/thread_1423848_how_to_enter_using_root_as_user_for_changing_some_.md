---
title: "how to enter using root as user for changing some config files"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by cello_911 on 2010-03-07
please can someone tell me if there is a standard password to enter into ubuntu in root..??

---

### Post by CharlesA on 2010-03-07
Just use sudo/gksu and your user's password.

---

### Post by inobe on 2010-03-07
```
gksu nautilus
```

---

### Post by halitech on 2010-03-07
root logins are disabled by default. Does as Charles says, use gksudo gedit /path/to/file to open the file you want to edit. It will give you root permissions to edit files.

---

### Post by Robster2 on 2010-03-07
Applications>Accessories>Terminal

```
su
```

su = super user

You will be asked for your password and you will log in as root.

type exit to leave.

If you want to use the GUI window manager (nautilus) as root then.

```
sudo nautilus
```

If you are using Karmic you will find a lot of error messages do not worry it is not a problem

---

### Post by Silvertones on 2010-03-07
If you don't have the knowledge to get there you probably shouldn't go there!
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by madmaxou on 2010-03-07
> **Robster2 said:**
> Applications>Accessories>Terminal

```
su
```su = super user

You will be asked for your password and you will log in as root.

type exit to leave.

If you want to use the GUI window manager (nautilus) as root then.

```
sudo nautilus
```If you are using Karmic you will find a lot of error messages do not worry it is not a problem

su and then your password will not work.
just use sudo

---

### Post by Robster2 on 2010-03-07
> **madmaxou said:**
> su and then your password will not work.
just use sudo

What do you mean?

---

### Post by NightwishFan on 2010-03-07
Just using sudo is advised, but you **can** use su.
```
sudo su
```

---

