---
title: "[SOLVED] Remote desktop broken"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by cmittle on 2008-10-27
I installed proftpd and gproftpd on my house server this afternoon and tried using the gui to setup an ftp.  gproftpd closed on me and when I tried to relaunch it I got a message (I don't recall the message verbatim right now:( ) so I restarted the server to do some more toying with it.  When it came back up I was no longer able to use my remote desktop viewer to view my server desktop.  When I launch remote desktop viewer I get a message that says "connection to host "server" was closed."

Please help me resolve this remote desktop problem as this is very helpful at certain times.

Thanks,
Cory

---

### Post by cmittle on 2008-10-29
Has anyone had rdesktop stop working on them before?

Please respond.

---

### Post by cmittle on 2008-10-31
I seemed to have solved this by uninstalling proftpd, apt-get autoremove, and reinstalling and reconfiguring.

---

