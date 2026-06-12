---
title: "can't resume freenx session -- depth issues?"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by felixnine on 2007-09-28
i start the freenx server, then connect to it from a windows client. if i suspend the session and try to resume it from a linux client, i get the error: 

"failed to restore all the required pixmap formats. can't resume the nx session on this display."

this also happens if i do it in the opposite order; connect from linux, then windows. i suspect it has something to do with the fact that the color depth in windows is 32-bit and in x11 it is 24-bit. i don't know why the freenx server wouldn't control this, but it seems set by the first connecting client. is there anything i can do server-side to fix this aside from (presumably) setting matching color depths?

unfortunately, there are no errors in /var/log/messages.

thanks.

---

