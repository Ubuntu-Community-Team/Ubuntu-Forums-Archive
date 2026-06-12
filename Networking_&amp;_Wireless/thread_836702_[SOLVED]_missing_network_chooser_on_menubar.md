---
title: "[SOLVED] missing network chooser on menubar"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Domas on 2008-06-21
Hi all,

Could anyone tell me please how to get back Network chooser icon on menubar (top right corner)? It just dissapeared without reason, I can use terminal to connect to my wifi network, but it was easier just clicking on it and connect :) It should be easy, but I cant find a solution. Thanks in advance.

---

### Post by nixscripter on 2008-06-26
That's called the network manager applet. It should reappear if you do this: ```
nm-applet
``` in terminal.

---

### Post by Domas on 2008-06-27
Thanks, it worked ! But if i close terminal it dissapears again...any idea?

hit alt-F2 and type "nm-applet" - solved the problem.

---

### Post by nixscripter on 2008-06-27
Glad I could help. Please mark this thread as solved (under the Thread Tools menu).

---

