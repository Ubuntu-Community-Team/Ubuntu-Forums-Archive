---
title: "Scanner driver help!!!"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Xrahdio on 2011-01-23
Can anyone tell me how to obtain a driver for my Canon Lide 60 scanner?  I'm getting an error message "Fail to scan" when I try Simple Scan.  I think I need a driver for Office.  I've searched the internet but have had no luck in obtaining a driver for this scanner.  Thanks to anyone who can help.:-|

---

### Post by I8NY on 2011-01-24
Try xsane, it takes awhile to start up but has some built in canon drivers.  One problems is that if there are two scanners on the network it doesn't like to use the other one.

---

### Post by honeybear on 2011-01-25
> **Xrahdio said:**
> Can anyone tell me how to obtain a driver for my Canon Lide 60 scanner?  I'm getting an error message "Fail to scan" when I try Simple Scan.  I think I need a driver for Office.  I've searched the internet but have had no luck in obtaining a driver for this scanner.  Thanks to anyone who can help.:-|


```
xterm
dmesg
```
what tell dmesg when you plug and replug your scanner? 


and this ?
```
xterm
scanimage -L 
```

---

