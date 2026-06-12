---
title: "Pidgin Problem"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by IOWAHC on 2008-11-12
Hy there!

Don't know if this is the correct Forum.

My system freezes when I add / log into a bonjour account in pidgin.
No error message. 
No log entries,
No kernel panic,...

Don't know what to do..

Anyone got the same problem ? Any suggestions?

cu

---

### Post by superprash2003 on 2008-11-12
is there any specific pidgin plugin you installed recently?

---

### Post by Coreigh on 2008-11-12
if you open a terminal window and run pidgin with the debug switch it may reveal where it is crashing. But that may not lead to a solution.

Exit Pidgin, open a terminal window and type ```
pidgin --debug
```

Pidgin will run but the terminal window will stay open and show the debug information as you try to open an account.

---

### Post by jflaker on 2008-11-12
There are several reports at launchpad....

---

### Post by IOWAHC on 2008-11-12
Nope, I have no specific Plugin installed. running it OOTB

I try the debug switch and report here.

---

### Post by IOWAHC on 2008-11-12
Ok, I reactivated Bonjour and it doesn't freeze anymore, ..

I try again and hopefully it doesn't come again.

thx

---

