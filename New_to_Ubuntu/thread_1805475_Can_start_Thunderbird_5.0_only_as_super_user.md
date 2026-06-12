---
title: "Can start Thunderbird 5.0 only as super user"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by trustno1. on 2011-07-16
So I added ppa for mozillas stable thunderbird 5.0 and upgraded. Now I can't start thunderbird as normal user. Starting it from terminal with sudo works though, however, I'd rather not resolve to that. **.thuderbird** folder contains useless crash reports with names like **InstallTime20110516220806** and content of the said folder **1310803255**. Anyone else experiencing these problems?

---

### Post by mikejonesey on 2011-07-16
> **trustno1. said:**
> So I added ppa for mozillas stable thunderbird 5.0 and upgraded. Now I can't start thunderbird as normal user. Starting it from terminal with sudo works though, however, I'd rather not resolve to that. **.thuderbird** folder contains useless crash reports with names like **InstallTime20110516220806** and content of the said folder **1310803255**. Anyone else experiencing these problems?

what is the output from command line as a normal user?

---

### Post by pqwoerituytrueiwoq on 2011-07-16
my guess is you messed up the permission with sudo thunderbird when open a graphical program you should use gksudo not sudo
if so this should fix it
```
sudo chown -R ~/.thunderbird
```

---

