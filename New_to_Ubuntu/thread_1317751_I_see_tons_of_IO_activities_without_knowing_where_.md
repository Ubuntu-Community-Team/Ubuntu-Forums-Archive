---
title: "I see tons of IO activities without knowing where it come from"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by legolas_w on 2009-11-07
Hi
When I start my computer (Karmic which is upgraded from Jaunty) I see a lots of IO activities without issuing any particular command. I is making me worried why it is happening and I have no means to see which process is eating all this IO resource and what it is doing.

Sometimes it took 5 minutes for the mysterious IO process to let my hard disk go.

Thanks

---

### Post by squaregoldfish on 2009-11-07
In some cases this is normal - things like the updatedb process run occasionally to reindex the filesystem for the locate command.

If you want  to see exactly what's going on, you can use iotop (in the repositories) - it's like top, but for I/O.

Steve.

---

