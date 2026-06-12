---
title: "Mu computer says I have filesystem errors and it's given me a maintenance shell."
date: 2010-02-21
forum: New to Ubuntu
---

### Post by dggreen on 2010-02-21
I have Ubuntu 9.10.  It is forcing file system checks and says file system mount has failed.  /dev/sda2 has a file system with errors and Inode 124417 (/etc/ppp/pap-secrets) has invalid mode (00).  It also says unexpected inconsistency, run f sck manually.  I am new to all of this and any help would be greatly appreciated.  Thank you!

---

### Post by bodhi.zazen on 2010-02-21
You can try running this:

```
fsck -y /dev/sda2
```

If you get a message about the file system being mounted, run that command from a live CD.

---

