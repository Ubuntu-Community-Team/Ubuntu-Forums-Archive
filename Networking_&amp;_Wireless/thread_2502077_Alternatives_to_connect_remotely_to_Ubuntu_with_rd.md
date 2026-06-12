---
title: "Alternatives to connect remotely to Ubuntu with rdp"
date: 2024-11-01
forum: Networking &amp; Wireless
---

### Post by Shishimaru on 2024-11-01
Hi all.


I have a mini PC with Ubuntu 24.04.1 freshly installed.


I am having trouble using the remote sharing feature. It often uses port 3390, but I need 3389. I managed to workaround it by doing this:
- I enabled sharing
- enabled remote access (which uses 3389)
- disabled sharing
- " " remote access
- re-enabled sharing. Magically it has 3389.


After a system reboot, everything went back to how it was before, but with the addition of not being able to enable remote access anymore, thus leaving remote sharing with port 3390.


Do we have any alternatives in Ubuntu or Windows to connect remotely? Unfortunately Chrome is not an option as it requires sending a code and does not remember GNU/Linux devices.


I don't know if there is a different client on Windows that uses a different port or if it is possible to completely remove the solution that Ubuntu uses, in order to use another one.


Thank you.

---

### Post by The Cog on 2024-11-01
I'm pretty sure that xrdp listens on port 3389. It's an RDP server in case you hadn't guessed. I use the remmina client to connect to xrdp on my mini-pc. 
**[FONT=Courier New]sudo apt install xrdp[/FONT]**

---

