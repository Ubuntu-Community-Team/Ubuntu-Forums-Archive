---
title: "ssh desktop mounts"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by bclark on 2007-06-28
If I mount a folder on the desktop using Places->Connect to Server and then mount and ssh connection is it possible to navigate to to that directory via the shell? I checked /mnt and there is nothing in there. Thanks!

---

### Post by crashovaride on 2007-06-28
I don't think i understand your question. Are you looking to mount a device drive? Like lets say, USB, or something like SAMBA? Technically speaking, you should be able to view it if you are as root. Or, set a low level account for SSH and then su to root. Let me know if this helps. If not, i will help you further.

---

### Post by bclark on 2007-06-28
you can "mount" a folder on your desktop using connect to server and it offers various ways of connecting to servers. so for instance i have a server with ssh access, and i create a folder to it on my desktop, is it then possible to navigate to it in the file system, or is it merely a normal ssh session?

---

### Post by crashovaride on 2007-06-28
If i understand this correctly, think you want to do this in X. In any case when you mount something in linux and you ssh into it. You should be able to get those resources.

---

