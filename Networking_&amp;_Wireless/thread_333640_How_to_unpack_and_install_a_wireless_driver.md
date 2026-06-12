---
title: "How to unpack and install a wireless driver"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by clemkonan on 2007-01-07
Ok so I think I have found the driver for my WUSB 54G adapter and I have downloaded Ndiswrapper 1.8. The driver is called rt2570-cvs-daily.tar.gz  and its located on my desktop.


I came across $ tar xfvz rt2500-X.X.X.XXtar.gz  and I am assuming  the xfvz must be a location which for me would be what desktop?

Can I get a bit of help here, please and thanks?

Using Ubuntu CE EDGY

---

### Post by Jussi Kukkonen on 2007-01-07
zxvf is the command (read *man tar* if you want the details). the correct command is something like:
```
tar zxvf  ~/Desktop/rt2500-X.X.X.XX.tar.gz
```

---

### Post by clemkonan on 2007-01-07
Thanks I will give it  try

---

