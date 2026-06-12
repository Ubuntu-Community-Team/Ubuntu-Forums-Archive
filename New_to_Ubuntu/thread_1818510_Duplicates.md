---
title: "Duplicates"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-04
>  W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) natty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_natty_partner_binary-amd64_Packages) W: You may want to run apt-get update to correct these problems    How could I fix this problem? I tried apt-get update but it still doesn't work.

---

### Post by jtarin on 2011-08-04
> **WubiAR said:**
> How could I fix this problem? I tried apt-get update but it still doesn't work.
In a terminal issue the command ```
gksudo gedit /etc/apt/sources.list
``` and look for and remove the duplicate line.

---

