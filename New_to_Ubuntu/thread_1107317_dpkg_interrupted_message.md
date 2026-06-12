---
title: "dpkg interrupted message"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by dbuss63 on 2009-03-26
I was attempting to download several applications recommended by Sayek Banerjee. I attempted to follow his directions based on his web page "Software you may need".

Apparently the downloads were interrupted and I get this message on my terminal:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dennis@dennis-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Warning:  I am an absolute beginner and I realize that I am way over my head.  All I want to do is correct this problem and return to my simple use of Ubuntu 8.10.  Can anyone help?  Thanks,
Dennis Buss

---

### Post by Bachstelze on 2009-03-26
Runing a command "with superuser privileges" means running it using [font="monospace"]sudo[/font]:

```
sudo dpkg --configure -a
```

---

### Post by ulfj on 2009-03-26
I had the same problem a few times but take HymntoLife's advice and run that in the terminal and all will be well.Don't get frustrated and give up it get's much ezier as time goes on!

---

### Post by dbuss63 on 2009-03-26
Thanks HymnToLife -- that did the trick!

---

