---
title: "Need the Network Manager back!"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Julita on 2010-02-13
Hi! I have removed network manager to try wicd, and it turned out that the latter would not connect to my wireless network. I wanted to install the .deb packages, but the error occurs about the package "upstart job" that is not installed (I have, however, upstart package.) I don't have CD/DVD-Rom or wired network, so that's not an option. I can, however, burn DVD iso on my flash, but it would take some time. Currently I am writing from my Windows system that I haven't deleted, and I already miss Ubuntu :) Please help. What is this upstart job? Maybe I haven't looked for it as thoroughly as I should have. Please help!

---

### Post by coolbrook on 2010-02-13
You can search for package *network-manager-gnome* and its dependencies here

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Julita on 2010-02-13
I have found those packages, but the problem is that there is no "upstart job" package anywhere. Whenever I try to install NM, there are always broken dependencies exactly with this package.

---

### Post by k3lt01 on 2010-02-13
This happens often and it doesn't matter what people try to do they always end up doing a complete re-install of Ubuntu. So my advice is to do a backup of everything you must keep and re-install Ubuntu. It will save you alot of time and aggravation in the long run.

---

### Post by Julita on 2010-02-14
In the end, I have re-installed system, only this time I have installed Xubuntu 9.10 (the kernel would load only with  ro quiet splash nomodeset parameters, though) and for the first time I have chosen reiserfs, and I love it! noatime and notail are great options. Outstanding performance, really.

---

