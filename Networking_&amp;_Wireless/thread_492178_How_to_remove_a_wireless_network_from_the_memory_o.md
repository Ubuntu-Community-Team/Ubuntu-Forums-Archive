---
title: "How to remove a wireless network from the memory of the nm-applet's roaming mode?"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by KyleBrandt on 2007-07-04
I want to make it so when I am in roaming mode, the nm-applet wireless applet will _not_ try to connect to certain wireless networks that I specify.  Anyone know how to do this?

---

### Post by sj3fk3 on 2007-07-05
> **Miles800 said:**
> I want to make it so when I am in roaming mode, the nm-applet wireless applet will _not_ try to connect to certain wireless networks that I specify.  Anyone know how to do this?

The only way I found to remove a network is by using gconf-editor, the networks are stored in /system/networking/wireless/networks

---

### Post by KyleBrandt on 2007-07-05
Thanks sj3fk3, I think that did it.  I appreciate the help.

---

