---
title: "Work offline problem"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-03-01
I am using dial-up 3G EV-DO Internet. So, whenever i would boot my system, i have to fire "wvdial" command. But after connecting, as i open FF, often i found it set to "work offline". Now, how to eradicate this problem? help!!!

---

### Post by supersonicdarky on 2009-03-02
Type **about:config** in ff address bar, [enter]

Find toolkit.networkmanager.disable, and set to **True** (double click)

It should disable checking whether net is connected or not.

---

