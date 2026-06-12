---
title: "Extending Ubuntu in a created dual boot"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Merisi on 2011-09-03
I've been using Ubuntu properly for just under a week and I've realised I enjoy it much more than the Windows side of my PC but I've only given Ubuntu about 120 gb of which 90 gb is free while windows has about 750 gb.  Is there a way I can extend my Ubuntu partition without messing things up?

---

### Post by Leshrac on 2011-09-03
You could use a partitioning tool, such as gparted to resize the Windows partition and then either make another partition for ubuntu or resize the current partition to make it cover the left over empty space.

While in theory it should be possible to do this operation without any data loss, it is still dangerous so the prudent thing to do is to backup everything you don't want to lose before you start.

---

### Post by Frogs Hair on 2011-09-03
You can shrink the Windows partition from Windows disk management and increase the ubuntu partition . You should be able to do this without any boot loader problem.

---

### Post by Merisi on 2011-09-03
> **Frogs Hair said:**
> You can shrink the Windows partition from Windows disk management and increase the ubuntu partition . You should be able to do this without any boot loader problem.

I wasn't sure whether it would work but I'll definitely give that solution a go.  Thank you.

---

