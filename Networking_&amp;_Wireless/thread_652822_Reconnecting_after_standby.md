---
title: "Reconnecting after standby"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by Twizzle on 2007-12-29
I have an XP machine, a Ubuntu Machine and a second XP machine (as a media player) on my home network. I control all of them from the main XP machine using TightVC.

I have been trying to set up my Ubuntu machine as a sever (but using the desktop release not the server release) to store my backups and media files. I am playing around trying to get my media machine to wake up the server from standby when I turn it on and have managed using a magic packet, but when it resumes, I have been having problems accessing it again from TightVNC. I have finally realised that the IP address changes each time it wakes up. Initially it was 192.xxx.xxx.65 but after waking it was 192.xxx.xxx.72 and it still thought that the original connection was there (the ...165 one).

Is there any way to automatically disconnect TightVNC when the machine goes into standby and/or make sure it always keeps the same IP address? Or is this something to do with my router?

---

