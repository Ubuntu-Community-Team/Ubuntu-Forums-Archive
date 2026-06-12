---
title: "cannot wubi install xubuntu"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by noorez on 2010-09-02
I am trying to install xubuntu on my parents laptop via wubi. I had the xubuntu iso already downloaded so I placed it in the same directory as wubi.exe however, wubi insisted on downloading a new one. After a few attempts I just let it download the iso however, first it tells me that it's downloading xubuntu-***-.iso.torrent (which takes about 20min) and it tells me it is downloading xubuntu-***-.iso! Can someone tell me what is happening here?

---

### Post by bcbc on 2010-09-02
> **noorez said:**
> I am trying to install xubuntu on my parents laptop via wubi. I had the xubuntu iso already downloaded so I placed it in the same directory as wubi.exe however, wubi insisted on downloading a new one. After a few attempts I just let it download the iso however, first it tells me that it's downloading xubuntu-***-.iso.torrent (which takes about 20min) and it tells me it is downloading xubuntu-***-.iso! Can someone tell me what is happening here?

I think... that the problem is this. Wubi.exe has been bumped to release 10.04.1. However, not every flavour of Ubuntu has a 10.04.1 release yet. Wubi.exe cannot use a .iso with a different release, so it is trying to download the xubuntu .iso again, then it probably checks it and finds it's wrong, so tries again.

So you need the 10.04 version of wubi.exe (or just burn the .iso to CD and run it from there). PS wubi announces it's version so you should be able to see whether it's 10.04.1 or 10.04

---

### Post by noorez on 2010-09-03
The Wubi I downloaded did say 10.04 and not 10.04.1, however, upon starting the program it showed that it was version 10.04.1. I am unable to find an older 10.04 version of wubi. Is there a location to download it yet?

---

### Post by bcbc on 2010-09-03
> **noorez said:**
> The Wubi I downloaded did say 10.04 and not 10.04.1, however, upon starting the program it showed that it was version 10.04.1. I am unable to find an older 10.04 version of wubi. Is there a location to download it yet?

[http://people.canonical.com/~evand/wubi/lucid/wubi-r189.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r189.exe)

I think that is the one you want.

---

### Post by campb.andrew on 2010-12-09
Can you let me know if this solution worked please? I've been trying to install xubuntu myself, it downloads the iso, finishes and restarts. But fails when im booting into it. I'm puzzled.

---

### Post by bcbc on 2010-12-09
> **campb.andrew said:**
> Can you let me know if this solution worked please? I've been trying to install xubuntu myself, it downloads the iso, finishes and restarts. But fails when im booting into it. I'm puzzled.

what version do you want. If it's 10.04, use the above link. If it's 10.10 use this one: [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) (download the wubi.exe you find there).

Note: if you download 10.04 it will offer you an upgrade (packages grub-pc and grub-common) that is likely to break the wubi install. It's best to avoid all grub-* package updates altogether - they are not security updates and even when they work are unnecessary on wubi installs.

---

