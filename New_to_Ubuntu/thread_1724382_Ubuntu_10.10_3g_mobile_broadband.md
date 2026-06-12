---
title: "Ubuntu 10.10 3g mobile broadband"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Imatech64 on 2011-04-08
Hello everyone,

Just finished installing 3g mobile broadband Huawei E1823 usb modem with Greek Cosmote provider on an old Sony Vaio lap with an Ubuntu 10.10.
The modem was recognized by the Network manager but the connection could not be established.
Being in Greece with Cosmote provider, and after several hours of search through threads and forums, the solution was finally quite simple.

Edit the connection (right click on NM icon, up right), and change the name of the APN from "3g-internet" to "internet". Restarst the system (with or without the usb modem) and that'it.
It worked for me and needed to share for others.

Have a nice day

---

