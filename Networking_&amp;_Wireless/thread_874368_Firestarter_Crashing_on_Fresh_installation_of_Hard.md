---
title: "Firestarter Crashing on Fresh installation of Hardy"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-07-29
I just did a fresh install of Hardy, and installed firestarter

during the boot process the progress gauge halts,

drops to the black screen and sticks at  

*** Stopping Firestarter Firewall

Is anyone else experiencing this behaviour whereby a fresh installation of Hardy crashes on boot when you install firestarter?

If I remove it everything boots fine.

If it is installed and my USB adapter is not plugged in it also boots fine.

---

### Post by Vivaldi Gloria on 2008-07-29
> **sefs said:**
> Hardy crashes on boot when you install firestarter?

I don't know about this problem but let me point out that ubuntu already comes with ufw. See

```
man ufw
```

Look especially at the EXAMPLES of the man page to see how easy it's to use.

---

### Post by sefs on 2008-07-30
Is it a gui or command line thing? :)

---

### Post by sefs on 2008-07-30
Part of the problem is when Mr. Shuttleworth decided to bind the firestarter to the network interface.  Why?

This would work if were not bound.

Ubuntu is becoming like windows.

---

### Post by sefs on 2008-07-30
A gui for ufw called gufw :D.

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Shweet!

---

