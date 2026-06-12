---
title: "How do I turn off network by default?"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by oldcpu on 2007-07-03
I want my system to be disconnected when I boot up.  And manually require me to connect with 'ifup'.  How do I do it?

---

### Post by GeeZor on 2007-07-03
If i am not mistaken, there is a folder called /etc/init.d/rc.2
in that folder there are file that start with K and files that start with S.
These files control which services are started in that runlevel..

S will start the service, K will kill it.   And also there are some numbers so you can control the starting order. 
Now rc.2 stands for runlevel 2, which on most systems is the default runlevel to boot into.

So, knowing in what runlevel you boot, (probably 2) you enter that rc.x folder and search for a file called network which will probably have an S in front of its name. rename that file to K and your done..

---

