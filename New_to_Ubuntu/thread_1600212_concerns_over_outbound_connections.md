---
title: "concerns over outbound connections"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by djyoung4 on 2010-10-18
So in my conky that I have it monitors the outbound connections and every once and a while I will notice connections to a couple sites when I have no browser open.  One of them is [www.moneybookers.com](www.moneybookers.com) and the other is engage2enable.com.  I have quite a few scripts going in my conky so i'm not quite sure if they have something to do with the scripts but I can't really tell what the sites are for.  any suggestions.

---

### Post by robsoles on 2010-10-18
Maybe firestarter (look in repository) can help - it is for controlling the Linux firewall but I see it lists connections and tries to display the name of the program on your system the connection is using/for.

If firestarter will tell you what program(s) is(/are) making or using those connections then that will provide a clue to pursue.

---

### Post by djyoung4 on 2010-10-18
> **robsoles said:**
> Maybe firestarter (look in repository) can help - it is for controlling the Linux firewall but I see it lists connections and tries to display the name of the program on your system the connection is using/for.

If firestarter will tell you what program(s) is(/are) making or using those connections then that will provide a clue to pursue.

ok i tried that and it gives me no program for moneybookers.  should i be concerned

---

### Post by robsoles on 2010-10-18
If you haven't 'joined' moneybookers.com then you should definitely worry and find the source of the connection from your machine.

Add ```
127.0.0.1   moneybookers.com
127.0.0.1   www.moneybookers.com
``` to your /etc/hosts file for now to block the connection from leaving your computer (it makes your OS treat moneybookers.com as if it is itself.)
```
sudo nano /etc/hosts
```...

---

