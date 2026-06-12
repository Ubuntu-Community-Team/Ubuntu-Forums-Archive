---
title: "Adding vt320 support to 6.10?"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by Spankypoo on 2007-05-12
I'm using MidpSSH to connect to an ubuntu machine (running , and any time I try to run anything (even just top, for example), I get this:

'vt320': unknown terminal type

Any idea how to add support? Unfortunately I don't have the option of using another SSH client that supports more terminal types.

---

### Post by jjstautt on 2007-06-22
sudo apt-get install ncurses-term

---

### Post by Spankypoo on 2007-06-28
> **jjstautt said:**
> sudo apt-get install ncurses-termYou rock. Thanks.

---

