---
title: "Can rsync read from FTP?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by occams_beard on 2009-07-24
Say I want to mirror an FTP site, could rsync read the files over FTP? If not is there an equivalent to rsync for syncing/mirroring over FTP?

---

### Post by frunns on 2009-07-24
Well... Couldn't you mount the FTP site locally and rsync from there? Not the best solution I guess though.

---

### Post by XCan on 2009-07-24
No, rsync doesn't suppot FTP. I think frunns' suggestion is quite good.

---

### Post by The Cog on 2009-07-24
No. rsync uses its own protocol. It does have the ability to tunnel itself through SSH though, so if one end is running an SSH server then it would make sense to make use of that.

e.g.
rsync -av -rsh=ssh /localdir 1.2.3.4:/remotedir

---

