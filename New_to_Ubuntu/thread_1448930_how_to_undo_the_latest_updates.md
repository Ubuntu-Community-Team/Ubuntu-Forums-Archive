---
title: "how to undo the latest updates?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-04-07
after i updated my system using update manager There have been some problems, and i want to restore the system before this update?
any help!

---

### Post by philinux on 2010-04-07
> **MBG1987 said:**
> after i updated my system using update manager There have been some problems, and i want to restore the system before this update?
any help!

Not possible unless you used something like remastersys. What are the problems?

---

### Post by ajgreeny on 2010-04-07
Depending on the problem application(s) it might just be possible that you still have a deb file of the older version in /var/cache/apt/archives.  If so it could be possible to install the older version, either by first uninstalling it and installing the older version, or using the force option which I think is```
sudo dpkg -i --force packagename
```

However, I agree with philinux, it would be far better not to even try this, but to sort out the problems that have happened which may be far better than retracing your steps back to an older package version.

---

