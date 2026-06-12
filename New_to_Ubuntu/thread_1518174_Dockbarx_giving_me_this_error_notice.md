---
title: "Dockbarx giving me this error notice"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-06-26
This is the pop up that I am getting, this is when I go to add it to the panel....

---

### Post by M7S on 2010-06-26
I would guess you're missing the dependency python-keyring. It's not set as a dependency in the ppa for some reason. This should fix it

```
sudo apt-get install python-keyring
```

Regards,
M7S
DockbarX developer

---

