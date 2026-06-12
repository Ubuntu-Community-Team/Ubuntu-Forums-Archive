---
title: "ps command question"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-06-07
who can i get ps to show a user say user with status pid ppid and only for user and not jonsmith or root

---

### Post by Toz on 2011-06-07
Is this what you're looking for:```
ps -u <user> -U <user> -ostat,pid,ppid,cmd
```

---

