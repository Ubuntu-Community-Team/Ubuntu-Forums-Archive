---
title: "Cisco Packet Tracer closes himself"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by Cumatru on 2011-04-07
If i try to delete a network equipment or press the Undo button, the application shuts down whitout any warning.

I'm using Packet Tracer 5.3.

I've tried to start it as root from the console. here is the console output during the problem:

```
Debug: Number of items in m_selected before cancelItem:0
Debug: Number of items in m_selected after cancelItem:0
CPtmpConnection::socketError
callManager : onError
callManager : onDisconnect
Segmentation fault
```

Also, i can't even save the files that i'm working on.

---

### Post by Cumatru on 2011-04-07
Finally !
[This](http://ubuntuforums.org/showpost.php?p=10256185&postcount=10) script made it possible !
My Qt libraries where in /usr/lib/ not /usr/lib32 ; maybe others will face this "problem" too.

---

### Post by Cumatru on 2011-04-07
Damn.
Still not fixed entirely.
I can't open any Activities.

Suggestions ?

---

