---
title: "Kernel Update Can't be Authenticated?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by ecmatter on 2009-10-03
From Update Manager

> 
**NOT AUTHENTICATED**

linux-image-2.6.28-15-generic
python-problem-report
python-apport
apport
apport-gtk
linux-headers-2.6.28-15
linux-headers-2.6.28-15-generic
linux-libc-dev


Is anyone else having an issue with this?

---

### Post by kansas_plainsman on 2009-10-03
I did.

---

### Post by bwang on 2009-10-03
It should still be safe to install the updates, unless someone's been messing around with the software sources.

---

### Post by jchaumont on 2009-10-03
I am getting the same warnings when trying to update.  I'm sure it's safe but I'm not installing these updates until they can be authenticated.  The authentication serves no purpose if I am just going to ignore when it fails.

---

### Post by 3rdalbum on 2009-10-03
I had this problem last night with some Samba updates; I just clicked the Reload button in Synaptic (sudo apt-get update) and everything went back to normal. Maybe the Security repository changed GPG key or something.

---

### Post by ecmatter on 2009-10-03
Thanks everyone.

I think I'll wait to download the updates.

---

### Post by ecmatter on 2009-10-03
```

sudo rm /var/cache/apt/archives/partial/*

```

Deleted a partially downloaded kernel update.  Once I did that, Update authenticated everything.

---

