---
title: "X11 forwarding TO Ubuntu"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-10-22
I remotely log into my university's Debian server farm to do my programming work - they provided a guide on how to use Putty with Xming for X11 forwarding to use Gedit and everything as usual on Windows.

Well I don't know how to do the same with Ubuntu. I can SSH into the server fine, but I don't want to do my programming with nano, I want to do it with gedit.

How do I do this? What client do I use? Obviously Ubuntu has an X server.. so how do I get an SSH client to use it?

---

### Post by mikewhatever on 2010-10-22
Try using the -X flag, ssh -X ..., and if that doesn't work, ask the tech support.

---

### Post by Pas_sa on 2010-10-22
Ahh, just what I was after! And such a simple solution..

Thanks!

---

