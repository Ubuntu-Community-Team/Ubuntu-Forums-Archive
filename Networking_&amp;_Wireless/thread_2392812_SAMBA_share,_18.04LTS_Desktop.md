---
title: "SAMBA share, 18.04LTS Desktop"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by polaris20 on 2018-05-25
Just to preface, I've used Ubuntu for ages, and never seemed to have any issues getting it to work from Windows and Mac (using Ubuntu as the file server). However, with 18.04LTS, I just want to set up a simple share on a barebones Ubuntu install for Plex. I'm using the GUI, because I don't have major requirements for it; simple read/write. 

However, when I attempt to access it, password denied. I'm using MACHINENAME\USERNAME and the password. When I set it to "guests allowed", it works fine. Something seems to have changed in how Samba users are authenticated, and I'm certainly doing something wrong, but I cannot seem to figure it out. 

I wanted to move my Plex server from 16.04 (where Samba works great) to 18.04, but perhaps that's not in the cards yet. Thoughts?

---

### Post by TheFu on 2018-05-25
Release notes have these bugs listed:
[https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1764778](https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1764778)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572132](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572132)
and say to try forcing vers=1.0 if connections aren't working.

---

