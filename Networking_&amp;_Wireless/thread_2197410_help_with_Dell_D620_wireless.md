---
title: "help with Dell D620 wireless"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by Dave.B on 2014-01-03
I am trying to install Ubuntu on a Dell D620 and am having trouble getting the wireless working
I am not sure where to start 
any help would be appreciated
thanks

---

### Post by varunendra on 2014-01-04
Please post the output of -
```
lspci -nnk | grep -iA2 net
``` to show us which wireless chip you have.

Also, which version of Ubuntu are you trying to install? For details, please also post -
```
lsb_release -d
uname -mr
```

---

### Post by Bucky Ball on 2014-01-04
*Thread moved to **Networking & Wireless**.*

When you say you are trying install Ubuntu, do you have it installed and you are having trouble getting wireless to work, or are you running 'Try Ubuntu' from the install media and can't get wireless to work.

Sometimes extremely problematic getting wireless to work when not a hard drive install of Ubuntu. Please clarify. ;)

---

