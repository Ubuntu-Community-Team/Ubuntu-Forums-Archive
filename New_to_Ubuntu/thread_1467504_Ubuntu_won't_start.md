---
title: "Ubuntu won't start"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by bobheaps on 2010-04-30
I have been using, sucessfully, 9.10 for a few weeks now. however when i tried to boot my laptop a few minutes ago I got the message
There is a problem with the configuration server (/usr/lib/libgconf2-4/conf-sanity-check-2 exited with status 256.
it then asked for my password which i entered and it returned the message
Install problem The configuration defaults for GNOME Power Manager have not been set Contact the system administrator.
What Can I Do to Get Over This Problem?

---

### Post by johngreth on 2010-04-30
Can you log into a terminal?

---

### Post by bobheaps on 2010-05-01
> **johngreth said:**
> Can you log into a terminal?

yes

---

### Post by ugm6hr on 2010-05-01
Have you recently run an update / upgrade or powered off without a proper shutdown?

---

### Post by bobheaps on 2010-05-01
> **ugm6hr said:**
> Have you recently run an update / upgrade or powered off without a proper shutdown?

yes to both. I installed updates 2 days prior, then later I exited without going thro the proper procedure

---

### Post by johngreth on 2010-05-01
Have you tried running updates and shutting down from the prompt that you can now get into.

---

### Post by ugm6hr on 2010-05-02
> **bobheaps said:**
> yes to both. I installed updates 2 days prior, then later I exited without going thro the proper procedure

It is likely you have some partially installed updates.

Log into Terminal / recovery mode:
```
sudo apt-get update
sudo apt-get install -f
sudo poweroff
```

If you don't use wired internet - then this could prove a bit trickier.  But it is likely that the 2nd 2 commands will still fix things, provided the update completed downloading the necessary files.

---

