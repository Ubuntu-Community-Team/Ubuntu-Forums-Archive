---
title: "IDLE crash using Python"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by spiepie on 2010-07-26
Hi
I am learning Python and using IDLE, however the IDLE keeps crashing. When it does I have to use system monitor to get rid of the IDLE program and reboot the whole PC. If I don't reboot the IDLE has blank pages?

---

### Post by Paqman on 2010-07-26
You might be able to find out why it crashed by launching it from the command line. Open a terminal and enter:
```
idle
```
if you're running Python 2.6, or:
```
idle3
```
if you're running Python 3.1

When it crashes it will generate some output about what's gone wrong. You might be able to sort it from that. If not, then you can file a bug a by hitting Alt-F2 and typing:
```
ubuntu-bug idle
```
(or idle3, depending). You'll need to register on Launchpad to file a bug, if you aren't already.

---

### Post by spiepie on 2010-07-26
no luck with that as yet . i have reported the bug as you suggested 

thanks

si

---

### Post by Paqman on 2010-07-26
Can you post up the output that it generates in the terminal when it crashes?

---

