---
title: "How do I determine what version of Ubuntu I have installed?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by deleyd on 2009-02-06
This is so basic I'm embarrassed to ask. How do I determine what version of Ubuntu I have installed?

Where can I get system info?

---

### Post by howefield on 2009-02-06
Open a terminal and type

```
cat /etc/lsb-release
```

---

### Post by LowSky on 2009-02-06
open Firefox click on help, then on about, at the bottom will tell you whaty version of ubuntu you are using

---

### Post by carml on 2009-02-06
More simple go to System-Administration->System monitor.You'll see there the main info for your system. :)

---

### Post by sambita on 2009-02-06
You can type this in a terminal: 
lsb_release -a

or you can go to System->Administration->System Monitor

and you'll find all the information under the "System" tab.

Hope it helped!

Edit: wow, 3 posts while i was writing this one haha

---

