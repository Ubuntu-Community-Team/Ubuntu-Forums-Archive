---
title: "Accessed denied from a lock file as an administrator"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by wannabeterminalpro on 2010-11-04
I was trying to remove a piece of software that didn't work but this popped up.

z@z-pc:~$ apt-get remove rpm
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

There's only one user on this computer and I should be the administrator so how can something be denied from me?

ps. I got ubuntu 2 days ago

---

### Post by amauk on 2010-11-04
use
```
sudo apt-get remove rpm
```

You need sudo to elevate your privileges to root

---

### Post by cipherboy_loc on 2010-11-04
[now class="redundant"]
Use sudo:
sudo apt-get remove rpm
[/now]




While you are an "administrator", you are just another user, except you can use sudo. Sudo allows you to perform commands as "root", the real administrator. Hence you could be called a sudo user.




Cipherboy

---

### Post by Jetso on 2010-11-04
Yeah, if you want to do someting important, and it won't let you, throw "sudo" in front and it will work usually. But be careful, don't always use sudo, you can mess things up.

---

### Post by wannabeterminalpro on 2010-11-04
Thanks I got the problem solved but I had the same problem with a game I tried to install. Now it's a different problem. Can you help me with that?
[http://ubuntuforums.org/showthread.php?p=10073366#post10073366](http://ubuntuforums.org/showthread.php?p=10073366#post10073366)

---

### Post by miyu123 on 2011-01-24
Thank you so much for your explanation! I was stuck and received an error when running *apt-get update*. Using *sudo* solved my problem!



> **cipherboy_loc said:**
> [now class="redundant"]
Use sudo:
sudo apt-get remove rpm
[/now]




While you are an "administrator", you are just another user, except you can use sudo. Sudo allows you to perform commands as "root", the real administrator. Hence you could be called a sudo user.




Cipherboy

---

