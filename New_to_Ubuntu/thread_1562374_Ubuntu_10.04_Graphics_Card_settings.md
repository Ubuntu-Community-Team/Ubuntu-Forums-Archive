---
title: "Ubuntu 10.04 Graphics Card settings"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by DaGeek247 on 2010-08-27
I am wondering, how do I change the Ubuntu graphics cards settings? (e.g. memory allotment, using acceleration...) And, since i think this applies, where is gconf.conf file located?

---

### Post by DaGeek247 on 2010-09-11
bump.

why didn't anyone reply?

---

### Post by Jazzy_Jeff on 2010-09-11
What video card are you using?

---

### Post by DaGeek247 on 2010-09-11
I have two, one that is not compatible tih Ubuntu 10.04 and is rather old. The other one i am borrowing from my brother, until i get a different one that is compatible. unfortunantly, i have no idea what it is. where would i find the name of it?

---

### Post by DaGeek247 on 2010-09-21
bump. again. :~P

---

### Post by bradleypariah on 2010-09-21
```
sudo apt-get install hwinfo
```

```
hwinfo | more
```

Thumb through the lists.  It should likely tell you what your card is.

---

### Post by bradleypariah on 2010-09-21
Other than that, typically you should be able to just go to
System > Administration > Additional Drivers
If Ubuntu has a GUI for your graphics driver, it will be there.  (ie. - if it's an ATI card, it should want to automatically download Catalyst Control Center).
If not, I personally don't know how to to control an unknown graphics card through the CLI, sorry.

---

### Post by DaGeek247 on 2010-10-17
It was that i had not installed "proprietery" software, and NVIDIA failed to work normaly. thanks for helping, and sorr y for the late replies....

---

