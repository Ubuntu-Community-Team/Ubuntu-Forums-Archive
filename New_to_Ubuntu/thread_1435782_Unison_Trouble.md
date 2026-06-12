---
title: "Unison Trouble"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-03-21
I'm trying to get Unison to synchronize the home directories of my desktop and laptop, but it's acting strange. Take a look at my profile:

```

root = /home/john/
root = ssh://192.168.1.6//home/john
include default

```

But when I run $ unison home, it starts saying "scanning .gvfs/sftp on 192.168.1.6/bin/grep

Why is it looking in the /bin directory when it should only be looking in my home directory?

---

### Post by EnigmaticCoder on 2010-03-21
Bump

---

### Post by EnigmaticCoder on 2010-03-21
Alright, I think I fixed it. I had to close my sftp:// folder and unmount it as well.

---

