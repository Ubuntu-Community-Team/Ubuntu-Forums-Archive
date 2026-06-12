---
title: "sysvbanner  - HELP!"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by B34ST1Y on 2009-01-28
I cant seem to find a proper usage for this anywhere...I want to display ASCII text horizontally in a terminal....the command "Banner" seems to only scroll it vertically.....so I did ```
sudo apt-get install sysvbanner
``` ...which installed successfully...but I have no idea how to use it....and there's no manual for it

---

### Post by jimmy the saint on 2009-01-28
nothing comes up when you type in 
```
man sysvbanner
```

---

### Post by B34ST1Y on 2009-01-28
it says there is no manual for it

---

### Post by jimmy the saint on 2009-01-28
I hate it when people do this.
The program name is banner, even though the isnallation package is titles sysvbanner.  Oh well.
```
man banner
``` will get you what you need.  It is pretty easy though.  the shortest manual Ive ever seen.  All it says for usage is ```
banner TEXT
```
Apparently it will print the first 10 characters.

---

### Post by B34ST1Y on 2009-01-28
sysvbanner is apparently able to print horizontally...however, it still prints vertically - which is my problem =S

---

