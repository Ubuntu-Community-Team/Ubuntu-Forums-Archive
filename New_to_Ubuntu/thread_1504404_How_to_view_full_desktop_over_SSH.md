---
title: "How to view full desktop over SSH?"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by IAmAnarch on 2010-06-08
OK, so I forwarded X11 over SSH. I know how to launch a few applications (Firefox and a couple others), but I'd like to access the entire GNOME desktop. What command do I type?

---

### Post by Gone fishing on 2010-06-08
Tried it on mine started with ssh -X -C user@192.168.1.1 and then ran gnome-session.

Worked fine.

---

