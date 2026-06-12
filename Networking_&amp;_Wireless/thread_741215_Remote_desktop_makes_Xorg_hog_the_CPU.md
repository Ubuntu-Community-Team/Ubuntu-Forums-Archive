---
title: "Remote desktop makes Xorg hog the CPU"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by girto on 2008-03-31
Ubuntu Gutsy
Celeron 2.5GHz
512 MB RAM
Intel 845GV chipset
i810 graphics driver
Remote desktop enabled (VNC)

Normally CPU usage is less than 10%. However, when a remote connection is established, Xorg by itself consumes 50-60% of CPU cycles considerably slowing the machine. Everything goes back to normal once the remote connection is ended.

How can we find out the cause?

---

### Post by Transient77 on 2008-04-04
I have this same problem. It seems to be a bug with vino-server, but I'm not really sure what. 

I've seen others post about this in various forums but nobody ever has an answer.

Maybe we can try to figure this out?

Do you by any chance have two network adapters in your PC? I have both wired and wireless, so I was thinking maybe it gets hung up on that somehow...

---

### Post by girto on 2008-04-23
I have only a wired connection.
It is most probably a vino-server bug, and I wish we could pin point what's causing it as not all systems are affected.

Can you post your system configuration?

---

