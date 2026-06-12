---
title: "wpa_supplicant seg faulting?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by skip27 on 2007-04-21
Strange thing... if I run wpa_supplicant in the background and re-run it without killing it first, it tells me that I've already got a pid (process id) for the one already running in the background, but it seg faults before terminating. Though this isn't a problem on face, I'm concerned that it might indicate something that something else is wrong. I didn't have this problem in Edgy, but now have it in Feisty. Solution? I recompiled wpa_supplicant and now it doesn't ever seg fault. Is the version from the repo broken? Anyone else having issues?

---

