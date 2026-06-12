---
title: "ntpdate..installed but wont run"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by phoenix24x on 2007-10-18
i am trying to get my ubuntu server to join an active directory domain. in order to do this time must be synchronized between my machine and the network time. i have been using this [tutorial]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"): 
i fail at the second part, **Time Settings**. i swiped the quote below (thanks monah!) from another thread but the exact same thing happens to me. 

i  enter in my domain controller to the *ntpdate* file, then i attempt to start the service:
```
sudo /etc/init.d/ntpdate start
```
**bash: /etc/init.d/ntpdate: No such file or directory** is the error i get too. So, i try copying the *ntpdate* file to the /init.d directory...no dice.

please help   :) 

> **Monah said:**
> hello, i'm from Ukraine!
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
It has passed normally!
I carry out

server to me writes!
**bash: /etc/init.d/ntpdate: No such file or directory**

All has put and &#1079; specified!

---

### Post by tkharris on 2007-10-18
Have you installed ntpdate itself?  Like apt-get install ntpdate?

---

