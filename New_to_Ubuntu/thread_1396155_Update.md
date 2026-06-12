---
title: "Update"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by OwNeD on 2010-02-01
is there a program or a way that i can update all programs  that i have installed on my machine in one single time?


Thanks.

---

### Post by samantha_ on 2010-02-01
> **OwNeD said:**
> is there a program or a way that i can update all programs  that i have installed on my machine in one single time?


Thanks.

if your using gnome, theirs the update-manager thats in your menus somewhere.
if you cant find it, use
```

update-manager -d

```
You can also use
```

sudo apt-get upgrade
```

---

### Post by howefield on 2010-02-01
> **OwNeD said:**
> is there a program or a way that i can update all programs  that i have installed on my machine in one single time?

Depends on what you mean by update all programs, as already advised you can use update manager which is predominantly going to serve you security updates, but not program version updates (there are a few exceptions to this, like Firefox).

The version number of most programs tends to be static within each release and won't be updated till the next Ubuntu release is done.

---

