---
title: "SSH Remote Host Key change error on suspend and resume"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by warraagal on 2018-10-14
In my lab at my university I am trying to set up SSH Server in a Server machine with Supermicro X11DPG-QT board. It currently has Ubuntu 16.04.5 (server) installed. For some reason whenever I suspend and resume, on trying to connect to the SSH Server I get the "Remote Host Identification Changed Error". When I restart the computer everything works fine. I considered the possibility that some other computer in our university's LAN may have got the same IP and my connection attempts may be hitting this other computer instead of the server I am actually trying to access. But when I disconnect the LAN cable of the server I get a timeout instead of the previously mentioned error. This means that no other computer has that IP, I am indeed connecting to the server. What am I doing wrong ? Could this have something to do with settings in the low-level BIOS Settings interface ?

---

### Post by TheFu on 2018-10-14
check the logs.
use more verbosity with the clients.

---

