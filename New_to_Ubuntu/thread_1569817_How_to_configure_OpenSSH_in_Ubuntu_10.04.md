---
title: "How to configure OpenSSH in Ubuntu 10.04 ?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Jian0203 on 2010-09-07
Can anyone provide me the tutorial on how to configure for OpenSSH after installed ?

I'm still new to Ubuntu so can you give me a detail solution for that please ?

Thanks a lot for helping ^^ 
Appreciate that ~

---

### Post by pricetech on 2010-09-07
Is openssh-server installed ??  If so, is should just plain work.

What do you need to know ??

---

### Post by endotherm on 2010-09-07
unless you want it facing the public internet, there isn't really any config. 
usually I go into the sshd_conf (in /etc/ssh/ I think) and set "PermitRootLogin" to no, but that is about it. 

if you are wanting one that it public facing, I suggest you use keys rather than passwords, and look into fail2ban and denyhosts.

---

### Post by bodhi.zazen on 2010-09-07
> **Jian0203 said:**
> Can anyone provide me the tutorial on how to configure for OpenSSH after installed ?

I'm still new to Ubuntu so can you give me a detail solution for that please ?

Thanks a lot for helping ^^ 
Appreciate that ~

There are many tutorials and many features to ssh.

What do you want to do exactly ?

As a general answer to a general question see :

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by mapes12 on 2010-09-07
> There are many tutorials and many features to ssh.

What do you want to do exactly ?Precisely! If you could tell us what your are trying to connect to then we may be able to help you further.

For example:-

[LIST]Are you looking to connect 2 Ubu boxes?[/LIST]
[LIST]Are any windoze boxes involved?[/LIST]
[LIST]How is you local LAN connected together?[/LIST]

Mark

---

### Post by tahitiwibble on 2010-09-07
This got me up and running in no time :) [http://ubuntuforums.org/showpost.php?p=4956300&postcount=2](http://ubuntuforums.org/showpost.php?p=4956300&postcount=2)

---

### Post by v1ad on 2010-09-07
```

sudo apt-get install ssh sshfs

```

---

### Post by manoja422002 on 2010-09-24
OpenSsh server is not getting installed even after executing 'sudo apt-get install openssh-server' command.
It throws following message:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Package openssh-server is not available, but is referred to by another package.**
**This may mean that the package is missing, has been obsoleted, or**
is only available from another source
E: Package openssh-server has no installation candidate

Is package name changed? Can anybody help me to figure out the root cause?

--
Thanks,
Manoj Kumar

---

### Post by mapes12 on 2010-09-24
```
sudo apt-get install ssh
```should install everything you need.

---

