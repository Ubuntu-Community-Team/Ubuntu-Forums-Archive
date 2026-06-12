---
title: "ubuntu LAMP server 6.06.2 can't install ddclient"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Thocrun on 2010-02-07
for some reason everytime I try to install ddclient I get this:

matthew@UBUNTU:~$ sudo apt-get install ddclient
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ddclient
matthew@UBUNTU:~$

So, now I am wondering if something is wrong here ?

I seem to be able to get updates though.
and I am working over ssh between both pc's.??

---

### Post by halitech on 2010-02-07
it means the package doesn't exist in the repos you have added. have you enabled the Universe repo?

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by Thocrun on 2010-02-07
Thanks didn't even think of that, I'll try it.

---

### Post by Thocrun on 2010-02-07
I still can't seem to get it to work I uncommented all but the comments in the /etc/apt/sources.list.

edit: now I am trying sudo apt-get update to see if it works.

Worked: solved.

---

### Post by Thocrun on 2010-02-07
one more question: how do you change your posts to be a solved post?

---

