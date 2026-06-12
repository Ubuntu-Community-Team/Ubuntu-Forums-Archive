---
title: "Can't install graphics driver"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-10
When I go to hardware drivers and try to activate my NVDIA accelerated graphics driver, I get the message:  "SystemError: Failed to lock /var/cache/apt/archives/lock"


There are two identical drivers except that one says "(recommended)" and I get the same message for each.

Any thoughts?

---

### Post by unutbu on 2008-12-10
Go to System>Pref>Main Menu. Select System>Admin on the left panel, Hardware Drivers in the middle panel. Click the Properties button.

Change the command to:```

gksu /usr/bin/python /usr/bin/jockey-gtk
```

The "gksu", I believe, is missing in the default installation.

Close the window(s), and then try System>Admin>Hardware Drivers again.

---

