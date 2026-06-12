---
title: "Logs?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Someone uk on 2010-08-04
hi, i get blank screens on ubuntu and i want to ask if there are any logs which could help figure out what is causing the blank screens?

---

### Post by Rubi1200 on 2010-08-04
You could try looking at the logs in dmesg.
 
Also, post the output of
```
 
lspci | grep VGA

```

---

### Post by t0p on 2010-08-04
Logs are to be found in the directory **/var/log/**.  There's also a "friendlier" GUI interface for reading logfiles at **System > Administration > Log File Viewer**.  There are a lot of log files to look at.  Happy hunting!

---

### Post by Someone uk on 2010-08-04
> **Rubi1200 said:**
> You could try looking at the logs in dmesg.
 
Also, post the output of
```
 
lspci | grep VGA

```
08:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)

can anyone explain what the numbers inside the square brackets  mean like "[    0.000000]"

---

