---
title: "i can't save xorg conf not even with kdesudo"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by 4chan on 2010-06-27
hi i need help. i just install kubuntu lucid, after installing nvidia driver i restart and then create xconfig with sudo nvidia-xconfig and then kdesudo nvidia-settings but when i want to save to x configuration it says. failed to write. what did i miss?

edit: the error output is **Unable to open X config file '/etc/X11/xorg.conf' for writing.**

---

### Post by cariboo on 2010-06-27
What are the permission and ownership of /etc/X11/xorg.conf?

---

### Post by ankspo71 on 2010-06-29
hi,
Here is something I wrote on the Kubuntu forum that I think might help.
[http://kubuntuforums.net/forums/index.php?topic=3111614.msg228465#msg228465](http://kubuntuforums.net/forums/index.php?topic=3111614.msg228465#msg228465)
Hope that helps.

---

### Post by bodhi.zazen on 2010-06-29
There is an option to "merge" your settings with the previous xorg.conf, and this option fails.

Unselect the merge option or manually copy-paste as indicated by ankspo71 .

---

### Post by 4chan on 2010-06-29
thank you for all your responses.

it is working now. i will mark this thread as solved.

---

