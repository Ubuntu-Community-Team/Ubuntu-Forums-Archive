---
title: "ssh help"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by mvalviar on 2009-12-28
How do I start a process on a remote machine that will continue running even if I disconnect from the remote machine?

---

### Post by Bachstelze on 2009-12-28
screen is what you need.

---

### Post by The Cog on 2009-12-28
For one-off launching a command that you intend to forget, starting it with **nohup** will do - e.g. 
nohup myprog
but for programs you want to reconnect to and see how they're doing, then **screen** is indeed the real answer. It's in the repositories. It operates one or more virtual terminals that you can switch between. You can logout/disconnect, then come back later and reconnect to screen and see all your virtual terminals still going. You need to read up on how to drive it, but it's worth the effort.

---

### Post by mvalviar on 2009-12-29
I just checked and I saw that screen is installed by default in ubuntu KK. My current trick is to run 'at' a couple of minutes ahead. That's really all I need.

---

