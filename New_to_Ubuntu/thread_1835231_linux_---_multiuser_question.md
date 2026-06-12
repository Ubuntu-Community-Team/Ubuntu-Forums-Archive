---
title: "linux --- multiuser question"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by katochd46 on 2011-08-29
Hi when i press keys: 
ALt+ctrl+F1 
ALt+ctrl+F2 
ALt+ctrl+F3 
 
We can login as multiuser on single machine, but at same time on PC only one user can work with keyboard & monitor. 
 
Is it possible that we have single CPU & multiple user can work on that cpu 
with there Keyboard & monitor ? 
 
Then only we can call it an multi-user O.S working at an same time on single machine.

---

### Post by mcduck on 2011-08-29
Yea, it is possible, although not that easy to set up. But I've seen it done.

Anyway, you don't need that for the system to count as simultaneous multi-user system. Much more common scenario would be multiple users connecting to the machine through network, using SSH to connect to their account or some remote desktop protocol to access their desktop.

Besides, even withonly local access, sharing the mouse, keyboard and display, users are able to have their programs running at the same time. And that's all that really matters to make it a multi-user system, it's not about how many people are interacting with the system at the same time, but about how many can be running programs and using the system's resources at the same time.

---

