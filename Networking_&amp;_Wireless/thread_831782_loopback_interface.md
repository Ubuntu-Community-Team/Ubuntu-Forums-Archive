---
title: "loopback interface"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by talihsizim on 2008-06-17
how can I add lo (loopback interface) to my interfaces. whenever I boot my computer I have to start lo manually. in other words localhost and  www root. How can I fix this problem. I think I must add lo to  /etc/network/interfaces.

My second problem: when I wanna change my privilages  with the command sudo -i on the console it waits for a while and gives an error message sudo:unable to resolve host A--. Is this problem related with the problem mentioned above.

thanks in advance.

---

### Post by chili555 on 2008-06-17
*sudo gedit /etc/network/interfaces* and add:```
auto lo
iface lo inet loopback
```Proofread, save and close. If you do not have gedit, you can use kwrite, nano, kate, or vim, but not emacs.> Is this problem related with the problem mentioned above.Probably. You will know in a few moments. If this doesn't fix it, please post back.

To the searchers: don't let this happen to you, when you see lo or the loopback interface, **hands off!**

---

