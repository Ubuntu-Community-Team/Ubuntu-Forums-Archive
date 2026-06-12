---
title: "Just installed 9.10, but have a problem installing libdvdread4 package."
date: 2010-01-16
forum: New to Ubuntu
---

### Post by todayisgood on 2010-01-16
I put the terminal input for it, but the output didn't install the package:

> mike@mike-desktop:~$ sudo apt-get install libdvdread4
[sudo] password for mike:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread

---

### Post by marshmallow1304 on 2010-01-16
Go to System->Administration->Software Sources and make sure universe is checked.  Close the window then
```
sudo apt-get update && sudo apt-get install libdvdread4
```

---

### Post by todayisgood on 2010-01-16
> **marshmallow1304 said:**
> Go to System->Administration->Software Sources and make sure universe is checked.  Close the window then
```
sudo apt-get update && sudo apt-get install libdvdread4
```

How do I check Universe? There are different tabs in Software Sources.

---

### Post by marshmallow1304 on 2010-01-16
Go to the Ubuntu Software tab.  Universe is "Community-maintained Open-Source software (universe)".

---

### Post by howefield on 2010-01-16
[http://packages.ubuntu.com/karmic/libdvdread4](http://packages.ubuntu.com/karmic/libdvdread4)

---

