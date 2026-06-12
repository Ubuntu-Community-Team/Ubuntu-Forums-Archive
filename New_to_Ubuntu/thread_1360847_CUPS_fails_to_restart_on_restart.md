---
title: "CUPS fails to restart on restart?"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-21
Following this code:

sudo /etc/init.d/cupsys restart

my terminal said:

karmic:~/Downloads$ sudo /etc/init.d/cupsys restart

sudo: /etc/init.d/cupsys: **command not found**

I'm trying to restart CUPSYS and CUPS.

If you need background see:

[CUPS - Printer Server]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html")

and

[PC-FAX cupswrapper driver install]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_pcf1a.html")

---

### Post by philinux on 2009-12-21
```
sudo /etc/init.d/cups restart
```

If you look in /etc/init.d there is no cupsys.

---

