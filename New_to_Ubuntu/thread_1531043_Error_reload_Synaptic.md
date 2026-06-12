---
title: "Error reload Synaptic"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by Whatrymes on 2010-07-14
I'm trying to reload the Synaptic Pkg Manager and I keep getting this error:

---

### Post by fooman on 2010-07-14
open a terminal and run the following command (type or copy/paste):

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0c5a2783
```

that should fix it.

hope it helps.

---

### Post by Excedio on 2010-07-14
This thread may be of assistance.
 
[http://ubuntuforums.org/showthread.php?t=1491927](http://ubuntuforums.org/showthread.php?t=1491927)

---

### Post by Whatrymes on 2010-07-14
> **fooman said:**
> open a terminal and run the following command (type or copy/paste):

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0c5a2783
```

that should fix it.

hope it helps.

Yes it did, Thank you.

---

