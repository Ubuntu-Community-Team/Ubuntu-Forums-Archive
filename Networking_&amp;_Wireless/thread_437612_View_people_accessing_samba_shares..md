---
title: "View people accessing samba shares."
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by Matthaeus on 2007-05-09
Is there a way (like windows) to see the account/computer and or files which are being accessed via your samba shares?

Thanks, Matt.

---

### Post by gradedcheese on 2007-05-09
Not that I know of, though logs are always available if you are curious.  Try System->Administration->System Log, particularly the auth and daemon tabs.

---

### Post by Mike'sHardLinux on 2007-05-09
This may not be exactly what you're looking for, but I use this all the time:
```
smbstatus
```

---

