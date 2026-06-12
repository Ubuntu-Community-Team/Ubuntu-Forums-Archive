---
title: "Hamachi stops working after reboot"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by vto80 on 2007-02-06
I installed hamachi following the instructions in the readme file, and it worked fine, until i restarted the machine. Now if i try hamachi start i get the error "tap: connect() failed 2 (No such file or directory)".
I tried reinstalling it, and then it works, but only until i restart the computer again.
Am i missing something? :confused: 

vto.

---

### Post by etaham on 2007-02-21
you need to restart hamachi and tuncfg on each reboot.
Try:
```
sudo tuncfg
hamachi start
```

---

### Post by escapist on 2007-05-14
I was having the same problem and that solved it completely, thanks very much.

If this is a required part of running Hamachi, why the heck doesn't it tell you that?

---

