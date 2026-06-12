---
title: "User names"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by danensis on 2010-02-03
OK, I'm brand new to Ubuntu, though have been using UNIX since the 1970s.

I have several *NIX systems running, which all share files using NFS and have common user names and passwords.

However I've just tried to install Ubuntu 9.04 server edition. When it came to adding user names, it would not accept an underscore in the user name, or special characters (!.) in the password. Is this a restiction of Ubuntu, or just the installation programme?

---

### Post by Grenage on 2010-02-03
It's a bug (I believe), see [here]("http://ubuntuforums.org/showthread.php?t=233716").

---

### Post by nothingspecial on 2010-02-03
Special characters mean something to the shell. All sorts of shenanigans can happen if the shell interprets special characters in a username incorrectly (correctly). You can get round it but I wouldn`t say it was worth it.

---

### Post by danensis on 2010-02-03
Thanks, that link to usermod was just what I needed.

Now I've found how to change the root password I might even find Ubuntu useable.

---

### Post by clive littlewood on 2010-02-03
```
Now I've found how to change the root password I might even find Ubuntu useable.
```


Why ?????    ;)

Clive

---

### Post by bodhi.zazen on 2010-02-03
> **danensis said:**
> Thanks, that link to usermod was just what I needed.

Now I've found how to change the root password I might even find Ubuntu useable.

Once you settle into Ubuntu you might want to take a look at sudo.

You get a root shell with sudo -i rather then su -

Sudo is highly configurable and allows sys admins to allow graded root access.

All too often, IMO, people disable sudo without considering the benefits.

Now if you are familiar with sudo, and choose not to use it, that is different.

---

### Post by danensis on 2010-02-04
OK, a few more questions on this.

First of all the manual is a bit misleading, as the -m option seems to have to go between the directory and the username, not with the other option flags at the beginning of the line.

Also its not clear if the new directory should be the absolute path or the path relative to /home.

Now when I log in with the amended user name it tells me I have no home directory.

---

