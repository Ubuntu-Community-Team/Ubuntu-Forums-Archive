---
title: "Access Ubuntu disks via network on Win &amp; Mac"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by mscoxoh on 2008-04-28
I'm sure this has been answered, but I searched like crazy and everything I found was about accessing Windows drives from Ubuntu. I want the opposite. How can I mount my Ubuntu partitions as a network drives in Windows (and for that matter, Mac OS X, too?)

I'm trying to use an Ubuntu server as a big network disk for multiple PC/Mac backup purposes, and would rather not use FTP and such like. Not it's main goal in life, but it would be so perfect! Can it happen?

.m.

---

### Post by cnschulz on 2008-04-28
Yes.

Just install Samba (smb). Youll find its probably already installed. Then once you configure some shares you mount your Ubuntu drives just like any other windows share (\\SERVER\Share)

There is heaps of info on this forum and google to get you started. Samba is the key. :)

c.

---

