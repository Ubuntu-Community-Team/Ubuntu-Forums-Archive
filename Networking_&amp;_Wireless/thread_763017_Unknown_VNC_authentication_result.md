---
title: "Unknown VNC authentication result"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by deejross on 2008-04-22
I'm running the Remote Desktop in Hardy on two different machines and whenever I connect to them for the first two or three times, it works great, but after that, I start getting the error, "Unknown VNC authentication result!". Turning off Remote Desktop, then running the command "killall vino", then re-enabling the Remote Desktop fixes the problem, but obviously, I can't do that from a remote location, which completely defeats the purpose of Remote Desktop.

I am using the latest Hardy and the client is an XP machine using the UltraVNC client. I guess I should also mention that one of my machines has port 5900 forwarded through the router, so I can directly connect to it. In order to connect to the other machine, I log into via SSH and use the port forwarding feature of SSH to connect to Remote Desktop.

So summarize, the machine I directly connect to gives the error "Unknown authentication scheme!",  while the one connecting through SSH gives the error "Unknown VNC authentication result!".

Has anyone else had a problem with this is Hardy? Thanks.

---

### Post by Jive Turkey on 2008-05-31
As far as I can tell vnc is broken on Hardy, let me know if you can make it work at all.  I'm going to post to launchpad with this issue soon afer I gather some more info.

---

### Post by deejross on 2008-05-31
I upgraded from Gusty to Hardy during one of the Alpha releases. Ever since then, so many things were broken. I eventually had to reinstall when Hardy was actually released. After I did that, VNC started working. The only thing I can think of is that one of the Alpha's screwed something up which was later fixed, but an upgrade path was not created to fix the problem that was introduced.

---

