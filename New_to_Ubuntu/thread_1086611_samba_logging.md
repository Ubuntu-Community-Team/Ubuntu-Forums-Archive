---
title: "samba logging"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by hammad1337 on 2009-03-04
Is it possible to monitor which computer is accessing which smb share on my pc at any time?

Or configure logs to show which ip accessed what files?

Or at least, monitor what connections are being made to my pc, from which ip and to which server running on my pc?

---

### Post by hammad1337 on 2009-03-04
bump.
Sorry, but I need to know urgently.

---

### Post by hammad1337 on 2009-03-04
re-bump

---

### Post by albinootje on 2009-03-04
> **hammad1337 said:**
> Is it possible to monitor which computer is accessing which smb share on my pc at any time?


Check the /var/log/samba directory, with this command you can see which log file is the newest :
```

watch -n1 ls -latr /var/log/samba

```

---

