---
title: "Getting WiFi to work through the shell"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by NCLI on 2008-11-14
I managed to install Intrepid using the alternate install cd, but my monitor gives me an "out of range" message when I try to start Ubuntu, which means that I have to rely on the terminal. This would be no problem if it wasn't for the fact that I have no idea how to get my Linksys WMP54G card working through the shell, and do not have access to a wired network from this desktop.

Help?

---

### Post by kevdog on 2008-11-14
Do you know the chipset of your card -- since this will tell us what driver is needed (technically driver in linux = kernel module).

Use lshw -C network to discover this.

Also once the appropriate driver is loaded,  I have a thread about configuring the parameters manually in my signature.

---

