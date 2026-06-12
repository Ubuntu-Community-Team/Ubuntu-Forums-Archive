---
title: "Cant remove wine..."
date: 2011-02-03
forum: New to Ubuntu
---

### Post by tropicz on 2011-02-03
Hey guys, I am having a little trouble removing wine, Here is the output in terminal:


```
jacques@jacques-M50Vm:~$ sudo apt-get remove wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages will be REMOVED:
  wine1.2
0 upgraded, 0 newly installed, 1 to remove and 259 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
```

Thanks

---

### Post by quesadilla on 2011-02-03
how did you solve it? I am having problems removing wine too.

---

### Post by TechWiz2100 on 2011-02-03
Reboot usually helps lock issues

That either happens when update manager is checking updates and/or package manager is doing something else to make sure that you cant have 2 instances installing/updating at the same time.

Also sometimes the managers fail to remove locks so reboots unlock and reset as per usual.

---

