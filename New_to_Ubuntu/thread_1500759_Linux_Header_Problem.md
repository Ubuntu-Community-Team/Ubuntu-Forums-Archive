---
title: "Linux Header Problem"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by alfa_80 on 2010-06-03
Hi,

After updating a new Linux header, i have received a message "There is a configuration server, (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)".

I need this repair urgent..please help me my friends

---

### Post by oldsoundguy on 2010-06-03
> **alfa_80 said:**
> Hi,

After updating a new Linux header, i have received a message "There is a configuration server, (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)".

I need this repair urgent..please help me my friends

Try the fix in this thread:
[http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306)
found by entering "status 256" into a Google search.

---

### Post by alfa_80 on 2010-06-03
Thanks a lot to oldsoundguy. It's solved finally with the help of your link :-) BTW, I wonder how great is your search methodology via google for I have spent a lot reading treads, but couldn't find..

This fixed me anyway: ```
chmod ugo=rwxt /tmp
```


Thanks again!

---

### Post by oldsoundguy on 2010-06-03
The search engine on this forum leaves a LOT to be desired .. so I utilize Google instead.

---

