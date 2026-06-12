---
title: "'ssh -X' not X-ing!"
date: 2024-11-22
forum: Networking &amp; Wireless
---

### Post by john163 on 2024-11-22
Every now and then, I'll try to 'ssh -x" from my Ubuntu 22.04 to 24.04.  A couple of times, it's worked, and I can get a remote browser.  Most of the time, though, the browser opens on the desktop of the machine I'm SSHing to.

I know Wayland is very different from X.  I do not want to have to take a huge step back in time to be able to have this work!  How can I reliably display remote apps?

---

### Post by TheFu on 2024-11-23
Capital -X, not lowercase?
Try Capital -Y too. Slightly different levels of security.

Lowercase -x disables X11 forwarding, according to the ssh manpage.

---

