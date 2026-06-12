---
title: "Root login vs User login??"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by UmbrInKID on 2009-11-28
I am fairly new to linux (few months of so). I am trying to discover all the wonderous things linux has to offer. One thing in particular though that I am tying to figure out is why the difference between root and user login??

I am the only person that uses my computer so it didnt make sense for me to always login in as a user? As well it annoys me when I want to do various thing to have to type a "sudo" password all the time. But when I look to see how root login works I see all these cations about using root login.. why??? Whats the difference if I am the only user of my computer??

Thanks in advance for all the help!

---

### Post by Some Penguin on 2009-11-28
Every file, every directory, etc. is associated with a user and a group.  There are three sets of permissions:  permissions for that user (it is possible for an owner to remove his permissions to write or remove his own file -- but being owner, normally he'll be able to set them back again); those for other users in the designated group; and everybody else.

In Linux, 'root' is an essentially unrestricted user.  Root may create files anywhere, alter any file's permissions, edit or delete them... (well, except on read-only filesystems, of course).   Careless typing, or worse, the execution of malicious commands, can cause fairly significant problems (wiping out configuration files, overwriting the wrong disk sectors with a typo in a 'dd' command, et cetera).

Hence, it's often advised to not use root unless you need to, because even if you're not running untested programs you may find yourself regretting an error more if made as root.

---

### Post by UmbrInKID on 2009-11-28
> **Some Penguin said:**
> Every file, every directory, etc. is associated with a user and a group.  There are three sets of permissions:  permissions for that user (it is possible for an owner to remove his permissions to write or remove his own file -- but being owner, normally he'll be able to set them back again); those for other users in the designated group; and everybody else.

In Linux, 'root' is an essentially unrestricted user.  Root may create files anywhere, alter any file's permissions, edit or delete them... (well, except on read-only filesystems, of course).   Careless typing, or worse, the execution of malicious commands, can cause fairly significant problems (wiping out configuration files, overwriting the wrong disk sectors with a typo in a 'dd' command, et cetera).

Hence, it's often advised to not use root unless you need to, because even if you're not running untested programs you may find yourself regretting an error more if made as root.

So is there an easy solution for my "user" to have all access that is not fragile system changes?? If that is the right way to ask that. My frustration is having to type a password it seems 30 times every session... I do not have to worry about other users accessing my stuff as I am the only user... (not on a network with other computers) on connection to the outside world is obviously the internet..

..I also seem to have the problem even using some of the aplications on my computer because they are "root" owned??

---

### Post by jrrader on 2009-11-28
You can edit your sudoers file so it does not require you to use a password to do certain things.  If you mess up while editing the sudoers file, you will understand why Linux has these precautions in place.

---

### Post by Elfy on 2009-11-28
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by aysiu on 2009-11-28
> **forestpiskie said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
These two links explain everything.

---

