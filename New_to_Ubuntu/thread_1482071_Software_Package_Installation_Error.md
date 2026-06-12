---
title: "Software Package Installation Error"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by bluesoldier007 on 2010-05-13
Hello, I am a new ubuntu user, and I need some help with software package installation.
 
I was installing the flash player plugin for firefox from the software center when my neice unplugged my computer accidentally.  When I rebooted and tried to install the plugin again, I got an error message saying that the last software installation had failed and I needed to fix it before I could continue installing software.
 
Can anyone tell me how to fix this problem so I can continue installing software from the software center?  Any help would be very much appreciated.
 
Thanks!

---

### Post by sisco311 on 2010-05-13
Hi and welcome to the forums!

Go to System -> Administration -> Synaptic -> Edit menu -> Fix Broken Packages

or open a terminal and run:
```
sudo apt-get -f install
sudo apt-get update
```

---

### Post by bluesoldier007 on 2010-05-13
Thank you.  I will try that this evening when I get home.
 
I appreciate the help very much.

---

