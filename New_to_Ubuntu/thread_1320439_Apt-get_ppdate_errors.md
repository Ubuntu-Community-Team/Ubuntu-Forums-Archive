---
title: "Apt-get ppdate errors"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-11-09
I get the following error while trying to update my software in karmic:

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  adduser system-tools-backends
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 233kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://ubuntu.oss.eznetsols.org karmic-proposed/main adduser 3.110ubuntu7
  404  Not Found
Err http://ubuntu.oss.eznetsols.org karmic-proposed/main system-tools-backends 2.8.2-1ubuntu1
  404  Not Found
Failed to fetch http://ubuntu.oss.eznetsols.org/ubuntu/pool/main/a/adduser/adduser_3.110ubuntu7_all.deb  404  Not Found
Failed to fetch http://ubuntu.oss.eznetsols.org/ubuntu/pool/main/s/system-tools-backends/system-tools-backends_2.8.2-1ubuntu1_i386.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

NB: I'm using software sources that are local (i.e. configured from "Software Sources").

Any thoughts?

---

### Post by MelDJ on 2009-11-09
the server is down?

---

### Post by abhiroopb on 2009-11-09
I suppose that could be it. Just that in 4 years of using ubuntu thats never happened. And I did try a couple of different servers. I guess worth waiting till tomorrow at least.

---

