---
title: "Problems with WiFi - greyed out?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by listerdl on 2010-05-05
Hi I just installed 10.4 on a friends laptop but the wifi is just greyed out and says that it has been disconnected.

It doesnt pick up any signals by scanning....

Any ideas what I need to do to fix this?

Thanks!

---

### Post by Peter09 on 2010-05-05
Can you provide the output of the commands
 
```
lshw -C network
```
 
and
 
```
ifconfig
```
 
Also check for a hardware switch for the wireless device

---

### Post by philinux on 2010-05-05
> **listerdl said:**
> Hi I just installed 10.4 on a friends laptop but the wifi is just greyed out and says that it has been disconnected.

It doesnt pick up any signals by scanning....

Any ideas what I need to do to fix this?

Thanks!

One thing to try is to connect wired. Then use update manager to update the system. Then check system>admin>hardware drivers. Then try wireless.

---

