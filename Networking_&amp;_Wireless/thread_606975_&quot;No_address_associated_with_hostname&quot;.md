---
title: "&quot;No address associated with hostname&quot;"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by hastings- on 2007-11-08
Hey all,

I recently tried to install and play "Frets on Fire", which is basically an open source keyboard based Guitar Hero for Linux. The game installs and loads fine, except when I try to play it either in single player or tutorial mode, it gives me the error;

"No address associated with hostname".

Then...that's it, I can't continue. I have spent quite a bit of time searching Google for an answer to how this can be resolved, or maybe even why it is happening in the first place.

Do any of you have any ideas? I'm running Ubuntu Gutsy 7.10 and I'm connected to the Internet using a wireless D-link adapter (DWLG122) using Linuxant to emulate the Windows drivers.

Any suggestions would be appreciated!

:guitar:

---

### Post by HermanAB on 2007-11-08
Add your hostname to /etc/hosts:
127.0.0.1 localhost.localdomain localhost yourhostname

That will likely fix it immediately.

Cheers,

Herman

---

