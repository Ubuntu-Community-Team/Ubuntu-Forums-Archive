---
title: "[SOLVED] What version is this???"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-24
Okay this might sound stupid.... how exactly do you tell which version of Ubuntu you're using? I am just starting to use my computer again. And I've downloaded all the updates. Shouldn't I have the latest version of Ubuntu?:confused:

---

### Post by Nepherte on 2008-12-24
You can type this in a terminal:
```
lsb_release
```

When a new distribution version is released (e.g. 8.10), you will not automatically update to it. You will only get the updates of the current release. However, I believe you should get a notification that there's a new release.

---

### Post by sanubie on 2008-12-24
> **Nepherte said:**
> You can type this in a terminal:
```
lsb_release
```

it says 

```
No LSB modules are available.

```

---

### Post by RomeReactor on 2008-12-24
> **Nepherte said:**
> You can type this in a terminal:
```
lsb_release
```

Shouldn't that be:
```
cat /etc/lsb-release
```

---

### Post by Joeb454 on 2008-12-24
I believe ```
lsb_release -a
``` would also work :)

---

### Post by Nepherte on 2008-12-24
Perhaps
```
lsb_release -a
```
gives you more information.

RomeReactor's suggestion might work to. It should basically do the same as the command.

---

### Post by sanubie on 2008-12-24
> **Nepherte said:**
> 

When a new distribution version is released (e.g. 8.10), you will not automatically update to it. You will only get the updates of the current release. However, I believe you should get a notification that there's a new release.

Hmmm, I'm not sure. When I first came back there was a bunch of updates, and it took forever. Maybe it updated to the new version and I just didn't realize it. But I still can't tell. Some things are working better now...

---

### Post by sanubie on 2008-12-24
Okay!! 

It says I'm still using 8.04.... 


```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

```

How do I update to the latest version?

---

### Post by Nepherte on 2008-12-24
[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended))

---

