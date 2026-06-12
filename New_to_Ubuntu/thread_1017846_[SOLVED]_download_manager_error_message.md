---
title: "[SOLVED] download manager error message"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by tobeach on 2008-12-21
How do I fix this error when attempting to use download manager

Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-lpia/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-lpia/Packages.gz)  404 Not Found [IP: 204.9.165.83 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Cheers

---

### Post by adobrakic on 2008-12-21
What download manager are you using?

---

### Post by drs305 on 2008-12-21
I just added the repository as written in the ubuntu skype wiki and it did not work. Most likely the skype server is down but it could be the repository address has changed.

Added: Try again later.

---

### Post by tobeach on 2008-12-21
heres the full error messgae when attempting update manager

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

---

### Post by tobeach on 2008-12-21
how do i delete this so that update manager can continue. this error is preventing updates.

thanks

---

### Post by drs305 on 2008-12-21
> **tobeach said:**
> how do i delete this so that update manager can continue. this error is preventing updates.

thanks

synaptic or (System > Admin > Software Sources), Settings > Repositories > Third Party and untick Skype. Reload.

---

