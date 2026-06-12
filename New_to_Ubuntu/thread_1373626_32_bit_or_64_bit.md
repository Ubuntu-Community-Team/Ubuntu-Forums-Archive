---
title: "32 bit or 64 bit?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by TracyO on 2010-01-05
I totally get that if I have to ask this question, maybe I shouldn't be using Linux.  I'm going to ask anyway.

How do I know if I have a 32 bit system or a 64 bit system?  I cannot remember for the life of me, and I've searched all over and can't figure out where this information is.  

Having Flash troubles at the moment.

---

### Post by cjazz on 2010-01-05
Enter in a terminal:

```
uname -a
```

---

### Post by njdove on 2010-01-05
Open a terminal and run "uname -m". If it says "x86_64" then it's 64-bit. If it says something else (e.g. "i686") then it's not.

---

### Post by TracyO on 2010-01-06
Thank you both!  Looks like I'm 32-bit.

---

### Post by njdove on 2010-01-06
Others have had success in fixing random Flash problems with the following advice. Close any open browser, then open a Terminal (Accessories...Terminal) and run the following commands to first remove common Flash packages then cleanly the first party Adobe plugin:
[LIST=1]
[*]sudo dpkg --purge swfdec-mozilla adobe-flashplugin flashplugin-nonfree mozilla-plugin-gnash
[*]sudo apt-get install adobe-flashplugin
[/LIST]

---

