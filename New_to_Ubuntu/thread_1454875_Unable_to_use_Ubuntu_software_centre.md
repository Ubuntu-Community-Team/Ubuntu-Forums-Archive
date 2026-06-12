---
title: "Unable to use Ubuntu software centre"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-15
Hii! I am facing an issue off late:-1.whenever I try to install any package through the Ubuntu software center .. I get a message"The action would require the installation of packages from not authenticated sources." and I am unable to install anything..
help!!!

---

### Post by stoneage on 2010-04-15
What applications are you trying to install, and what Software Sources are you using ?

---

### Post by vivek40 on 2010-04-15
Hii ...name any application.. nothing is installing and as far as software sources are concerned.. please find the snapshot attached

---

### Post by philinux on 2010-04-15
> **vivek40 said:**
> Hii! I am facing an issue off late:-1.whenever I try to install any package through the Ubuntu software center .. I get a message"The action would require the installation of packages from not authenticated sources." and I am unable to install anything..
help!!!

Open a terminal, Apps>access>terminal and do this.

```
sudo apt-get update
```

Post back what it says. Remember to put code tags around it.

---

### Post by vivek40 on 2010-04-15
Hii ! please find the result of the command below: seems like nothing is working:-
```
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
vivek@host:~$ 

```

---

### Post by philinux on 2010-04-15
Go into system>admin>software sources and change the server to say Main.

---

### Post by vivek40 on 2010-04-15
Hii thanks a lot Philinux...that seems to have solved the issue...!! was it a server issue?

---

### Post by philinux on 2010-04-15
> **vivek40 said:**
> Hii thanks a lot Philinux...that seems to have solved the issue...!! was it a server issue?

When that happens almost certainly yes.

---

