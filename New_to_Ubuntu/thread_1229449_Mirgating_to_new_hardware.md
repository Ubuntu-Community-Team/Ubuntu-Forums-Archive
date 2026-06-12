---
title: "Mirgating to new hardware"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by jlerossignol on 2009-08-02
I have Ubuntu 9.04 setup of two different computers.  The old one has all the users and data, and I want to move it to the new machine, which is a fresh install of Ubuntu 9.04.  What I've looked at so far doesn't make much sense.

What directories do I need to copy and how would I do it?

---

### Post by braete on 2009-08-02
usually just copy your /home folder onto the new pc
if you get some error regarding permissions run ```
chmod -R 775 ~
```
edit: if you like more security read [http://www.linuxcommand.org/lts0070.php]("http://www.linuxcommand.org/lts0070.php")

you could also use synaptic's ability to generate a file with all the packages you have installed and load that onto the new install to get all ur programs.
if you dont want to dl them ( if you have a slow connection)  you can copy ur /var/cache/apt/archives onto then new pc

---

