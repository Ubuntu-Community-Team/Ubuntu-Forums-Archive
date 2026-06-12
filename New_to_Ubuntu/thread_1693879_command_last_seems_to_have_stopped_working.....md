---
title: "command last seems to have stopped working....?"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by werty2010 on 2011-02-23
from time to time i type the command "last" to see the logins
that seemed to work until today:doesn't show the latest logins(the list stops yesterday)
can someone tell me how to fix it and why this is happening?

---

### Post by werty2010 on 2011-02-23
bump

---

### Post by kellemes on 2011-02-24
Don't know..
[Manpage]("http://linux.die.net/man/1/last") says it reads from "var/log/wtmp", maybe it's corrupted or something?

---

### Post by werty2010 on 2011-02-24
> **kellemes said:**
> Don't know..
[Manpage]("http://linux.die.net/man/1/last") says it reads from "var/log/wtmp", maybe it's corrupted or something?

since im not very experienced could you tell me how to check it and fix it?

---

### Post by kellemes on 2011-02-24
> **werty2010 said:**
> since im not very experienced could you tell me how to check it and fix it?

Well, I've never encountered this as well.

I see besides wtmp there is also wtmp.1 (in my case at least).
It seems to be login-data up to about a month ago (better then nothing I guess). If this is not acceptable then you better wait for someone who can help you get back the original data, if possible at all. I don't know how to do that.


From a terminal window..
Backup original (just in case) and copy wtmp.1 to wtmp

```
cd /var/log
sudo mv wtmp wtmp.mybak
sudo cp wtmp.1 wtmp
```

Now, try again..

Now, I really don't know what wtmp is meant for except this, so I can't guaranty your computer won't explode ;-)

---

