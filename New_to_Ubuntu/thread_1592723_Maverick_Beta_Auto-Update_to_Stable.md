---
title: "Maverick Beta Auto-Update to Stable?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by aust77 on 2010-10-10
Hello,

Last week I installed the Lubuntu Maverick Beta 2 while waiting for the final release. It's been working fine, but I am wondering if Beta 2 auto-updates to the final release or not. Do I need to burn another CD (I have no problems with doing so) in order to have the final Maverick release or is did my beta upgrade on its own?

Cheers,



aust77

---

### Post by ptn107 on 2010-10-10
Updates automatically?  No.  You can, however, upgrade yourself.  Open a terminal and type:
```
sudo apt-get update && sudo apt-get upgrade
```
to update your system to the final release.

---

### Post by aust77 on 2010-10-10
Thanks for the help ptn107! I will do so right now. I appreciate the assistance.

Thanks,


aust77

---

### Post by psusi on 2010-10-10
> **ptn107 said:**
> Updates automatically?  No.  You can, however, upgrade yourself.  Open a terminal and type:
```
sudo apt-get update && sudo apt-get upgrade
```
to update your system to the final release.

Umm... yes, it does... that big update manager window that pops up automatically would be it.

---

### Post by aust77 on 2010-10-10
> **ptn107 said:**
> Updates automatically?  No.  You can, however, upgrade yourself.  Open a terminal and type:
```
sudo apt-get update && sudo apt-get upgrade
```
to update your system to the final release.

It just basically showed all the repositories and ended, as usual when there are no available updates. The graphical update manager had a kernel update available and thats about it. I am trying to check what my computer says is installed -- 10.10 Beta or 10.10 . How would I do so?

---

### Post by alphacrucis2 on 2010-10-10
> **aust77 said:**
> It just basically showed all the repositories and ended, as usual when there are no available updates. The graphical update manager had a kernel update available and thats about it. I am trying to check what my computer says is installed -- 10.10 Beta or 10.10 . How would I do so?


If you have all updates installed, you effectively have the final release version.

---

