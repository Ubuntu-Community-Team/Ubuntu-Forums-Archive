---
title: "NetworkManager takes a while to load"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by Angafirith on 2007-11-13
I recently got a new laptop with an AMD Athlon 64 X2 processor. Ubuntu loads incredibly quickly on it, but certain things take a while to  "catch up", so to speak. Both gnome-power-manager and NetworkManager take at least 30 seconds to a minute longer to come up than Gnome. While I enjoy how quickly my desktop comes up, it's rather annoying to have to wait to get on the wireless. I'm reasonably sure that this has something to do with the dual core processor: perhaps the tasks involved with starting NM and GPM are running in parallel with those used to start the desktop.

Basically, I want to know if there's any way to have NM (and thus, my network connection) running at the time that my desktop starts, without causing my desktop to take longer to start. Any ideas?

---

### Post by Angafirith on 2007-11-14
I've looked into the issue a bit more, and I think it's actually an issue with nm-applet and my gnome-session. I'm going to make a post over in the Desktop Environment forums detailing the issue I'm having.

---

