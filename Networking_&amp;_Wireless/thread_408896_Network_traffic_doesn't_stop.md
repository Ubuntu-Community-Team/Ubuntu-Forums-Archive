---
title: "Network traffic doesn't stop"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by amklinux on 2007-04-13
Hi.

I'm using Edgy and, since yesterday, I'm observing a strange behavior of my Internet connection. The System Monitor says there is a download/upload that never stops, but I'm not downloading anything. I'm using cable modem connection, and don't know what is going on. I would like to know which programs are doing these downloads, but I don't know which software to use.

Thanks.

Adrovane.

---

### Post by souki on 2007-04-14
probably the update tool ?
try this in a terminal :
```
 sudo lsof -i
```

---

### Post by amklinux on 2007-04-14
I tried that, and killed every process listed, but the problem continues. 

Thanks.

Adrovane.

---

