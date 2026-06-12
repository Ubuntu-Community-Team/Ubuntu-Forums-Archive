---
title: "Ubuntu file sharing with windows 7"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by Krishnan on 2011-06-21
Hi, I have installed Ubuntu 11.04 in VMBOX, When i try to access the shared folder, it says you dont have sufficient permission to access?

I have attached an image. Kindly, provide a solution.....

---

### Post by sanderd17 on 2011-06-21
try running 
```

gksudo nautilus

```

and access it now. Does it work?

---

### Post by Krishnan on 2011-06-22
> **sanderd17 said:**
> try running 
```

gksudo nautilus

```

and access it now. Does it work?

Done that, now can access the folder, but nothing inside is being displayed?

---

### Post by crispy_420 on 2011-06-22
Are both systems Ubuntu/Linux? Or is the "server" Windows?

It sounds like a permission issue on the "server" system. On the server system try temporarily opening up the permissions on the shared folder to allow everyone read/execute for now to see if that resolves the issue.

---

### Post by Krishnan on 2011-06-22
Tried the command again, Now its working. Thanks a lot for your replies :)

---

