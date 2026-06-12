---
title: "display kernel error messages"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by herbert tamayo on 2010-11-03
Hi, i need to display the latest warning/errors from the kernel, this question is because in the ubuntu loading process i saw some warnings but I could not read it, so my question is:

what file should I browse to display the latest warnings/errors?

regards

---

### Post by janpol on 2010-11-03
I think you should take a look at **/var/log/kern.log**

Also, you can query for kernel bootup messages via the dmesg utility:

```
dmesg | less
```

Maybe the message your are looking for is in another log file, take a look at this link:

[Linux Log Files]("https://help.ubuntu.com/community/LinuxLogFiles")

---

