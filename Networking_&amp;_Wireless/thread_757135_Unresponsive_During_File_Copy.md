---
title: "Unresponsive During File Copy"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by Kissell on 2008-04-16
Okay, I recently upgraded to latest Hardy release candidate on both a RAID-5 file server running Samba, and my laptop, and I've noticed that when I do a large file transfer between the two that is initiated on my workstation, the workstation becomes unresponsive during the duration of the transfer.

My workstation is a laptop with 2GB of RAM and a dual-core amd64 processor running Gnome and compiz.  The server is an intel P4 with 2GB of RAM running a RAID-5+1 array with Samba and nobody else was using it for anything during this instance.

By unresponsive, I mean that i can still navigate the OS, I can change workspaces I can even use nautilus to change directories, but I cannot open programs without significant delay (several seconds) or type anything in any screen, especially firefox without significant delay, sometimes over 10 seconds before the keys i type show up.

I opened the system monitor and nearly 50% of the CPU is taken up by two processes, 1=nautilus 2=gvfsd-smb.  

These symptoms did not exist before upgrading from Gutsy to Hardy, and I'm wondering if there is a fix...  or if I can at least expect it to "fix itself" with updates by the 24th when the final release comes out.

---

