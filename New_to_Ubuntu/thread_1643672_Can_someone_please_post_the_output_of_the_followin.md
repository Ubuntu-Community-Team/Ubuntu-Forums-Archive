---
title: "Can someone please post the output of the following ..."
date: 2010-12-12
forum: New to Ubuntu
---

### Post by tesex167 on 2010-12-12
cat /etc/apt/apt.conf.d/99synaptic 
 
 
under the condition that they are using Ubuntu 10.04 LTS and that they are experiencing no problems with regards to the functioning of their software centre application or indeed installing programs. 
 
 
Thanks

---

### Post by warfacegod on 2010-12-12
This thread may be useful to you. [http://ubuntuforums.org/showthread.php?t=1500473](http://ubuntuforums.org/showthread.php?t=1500473)

---

### Post by cotcot on 2010-12-12
~$ cat /etc/apt/apt.conf.d/99synaptic 
APT::Install-Recommends "true";

---

