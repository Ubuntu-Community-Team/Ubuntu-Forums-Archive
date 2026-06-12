---
title: "Wireshark : no interface found"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-04
Wireshark says there is no interface. I have a thinkpad built in wifi card which works fine.

---

### Post by vivek.pandey on 2011-06-04
run it as a root
 
```

sudo wireshark


```

---

### Post by danbishop on 2011-06-04
Better to use:

```
gksudo wireshark
``` :)

---

### Post by kalimojo on 2011-06-04
Thanks. Sorted.

---

### Post by Rubi1200 on 2011-06-04
It is a bad idea and very insecure to run Wireshark as root; please don't do it!!!
[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

---

### Post by rhigmus on 2011-12-06
> **Rubi1200 said:**
> It is a bad idea and very insecure to run Wireshark as root; please don't do it!!!
[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

thank you! that was very helpful.

---

