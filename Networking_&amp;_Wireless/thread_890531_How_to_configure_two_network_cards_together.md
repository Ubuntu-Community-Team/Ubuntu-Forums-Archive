---
title: "How to configure two network cards together?"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Guruprasad on 2008-08-15
I have two network cards on my ubuntu...

Only one works at a time...

How to configure both together?
One is for Broadband internet and other for office intranet.

---

### Post by Iowan on 2008-08-15
Easiest way is to edit **/etc/network/interfaces** file and add an "auto" line for whichever interface currently does not start. ```
sudo nano /etc/network/interfaces
``` CTRL-O to write changes, CTRL-X to quit.

---

