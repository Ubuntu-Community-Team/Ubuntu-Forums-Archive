---
title: "su authentication problem - 64 bit ubuntu"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by destrich on 2011-05-03
I have an application that I am trying to install on my ubuntu 64 bit machine, and it requires super user priveledges.  I've run the 'su' command according to the documentation that came with the application, but I am getting an error "Authentication error" after entering my password.  Now you might think that a rank beginner mistyped the password, but I've tried it several times with the same result.  The password required is the same one, I presume, that I use when logging on to the system, and it works fine in that case, so why isn't it working here?

---

### Post by blind2314 on 2011-05-03
It's the same password that you login with only when you use ```
sudo
```. Root's account comes locked by default in Ubuntu, which is why ```
su
``` is not working. As per the guidelines on the forum, I'm not going to mention how to unlock it..but sudo should work for what you need, just preface the commands that the documentation tells you to run with 'sudo', and use your normal password.

---

### Post by destrich on 2011-05-03
thx much - that worked..

---

