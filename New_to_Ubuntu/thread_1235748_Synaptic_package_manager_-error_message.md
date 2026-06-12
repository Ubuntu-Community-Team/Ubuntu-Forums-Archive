---
title: "Synaptic package manager -error message"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by singhs on 2009-08-09
Less than a month using Jaunty. Managed to make Netgear Wn111v2 up and running using advices from this forums. Trying to get plugins installed. Received this message when I opened Synaptic while trying to install Java6.


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Please help
Thanks

---

### Post by halitech on 2009-08-09
open a terminal and run
```
sudo dpkg --configure -a
```

---

### Post by hansdown on 2009-08-09
Hi singhs.

Click applications> accessories> terminal.

Copy and paste 

```
sudo dpkg --configure -a
```

Into the terminal.

Hit enter. Enter your password, (you won't see it as you type).Just type it in and hit enter.

---

### Post by singhs on 2009-08-09
Done. Thanks to both.:P

---

