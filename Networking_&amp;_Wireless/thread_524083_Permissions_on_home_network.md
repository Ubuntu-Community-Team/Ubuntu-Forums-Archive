---
title: "Permissions on home network"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by BruceCorkern on 2007-08-12
We have always had a shared folder on our Windows network at home where anyone could create folders and/or files.  All such folders and files were open to any of us with access to the folder.

Now I'm using a linux server (ubuntu 6.06).  All of us are in the group Corkerns.  I can set permissions on the files and folders that currently exist so that anyone can read, write, erase, etc.  However, new folders or files don't inherit those permissions.  Does anyone know of a way to do that?

*e.g., my wife creates a new picture folder, say Vacation2007.  I edit an individual picture and try to save it back again...no go...owned by the missus and I can't overwrite.*

Thanks for your help!

---

### Post by PilotJLR on 2007-08-12
You need to set the group ID bit in the directory, so that new files belong to the right group, rather than a private group. Like so:
```

sudo chmod g+s <the shared directory>

```

---

### Post by PilotJLR on 2007-08-12
And of course also want to make sure the directory itself is owned by the right group. For example:
```

sudo chown bruce:corken <the shared directory>

```

---

