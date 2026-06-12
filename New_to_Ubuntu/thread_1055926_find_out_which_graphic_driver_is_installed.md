---
title: "find out which graphic driver is installed"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by josiano on 2009-01-31
Hello.

I installed ubuntu (Hardy) on a Thinkpad T40 last year.
Now my mother has the same computer and I installed Hardy on that one too, but I couldn't get a decent screen resolution, although it's perfect on mine, but I forgot which graphic driver I installed.

How can I find out which graphic driver is installed on my computer, so I can install the same on my mum's one.

Thanks for your help.

_j

---

### Post by x33a on 2009-01-31
which graphic card is installed on those computers?

---

### Post by josiano on 2009-01-31
It's an ATI Mobility 7500.

ps: there is no "Device" section in my xorg.conf file

---

### Post by Nepherte on 2009-01-31
You can check in /var/log/Xorg.0.log to see what driver is loaded.

---

