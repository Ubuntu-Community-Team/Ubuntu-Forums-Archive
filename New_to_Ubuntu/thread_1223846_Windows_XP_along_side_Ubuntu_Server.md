---
title: "Windows XP along side Ubuntu Server"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Grifulkin on 2009-07-26
Install 9.04 sever next to XP, so my set up is as follows I have a 320 gb hard drive, 200 is XP and 100 is Windows 7 RC.  What I would like to do is delete Windows 7 and then Install 9.04 Sever in its place.  I already know how to get rid of Windows 7 and fix the windows boot manager to get it boot back into XP.  Now my question are there any tips on how to install server to that 100 gb partition, or is is pretty straight forward.  I am not at home and won't be home until tomorrow I was just hoping someone would be able to tell me if it is easy or not.  Thank you, any insight would be appreciated.

And on another note, after I install server how can I just install the basic GNome GUI?  Without the rest of the software so I can really build up the programs I want and nothing that I don't need.

---

### Post by bodhi.zazen on 2009-07-27
Most linux servers run without X. If you want to run gnome I would simply do a desktop installation and add what servers you wish.

You can do a server install and add gnome if you wish.

Either way, server or desktop install, the installation is fairly straight forward. You need two partitions, root and swap. Swap = RAM X 2. max 1 Gb.

[https://help.ubuntu.com/9.04/serverguide/C/installation.html](https://help.ubuntu.com/9.04/serverguide/C/installation.html)

---

### Post by ainsworth_t on 2009-07-27
> after I install server how can I just install the basic GNome GUI? Without the rest of the software so I can really build up the programs I want and nothing that I don't need.

```
sudo apt-get install gnome-desktop-environment
```

---

