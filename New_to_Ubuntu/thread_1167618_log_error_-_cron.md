---
title: "log error - cron"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-23
Anybody got any idea what is happening here...my log is full of this...


23 16:35:43 pj-indulgence kernel: [92431.018974] [drm:i915_getparam] *ERROR* Unknown parameter 6
May 23 16:40:01 pj-indulgence /USR/SBIN/CRON[16425]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 23 16:50:01 pj-indulgence /USR/SBIN/CRON[17044]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 23 17:00:01 pj-indulgence /USR/SBIN/CRON[17668]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 23 17:00:01 pj-indulgence /USR/SBIN/CRON[17667]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)

---

### Post by kidders on 2009-05-24
Hi there,

> **dunbrokin said:**
> Unknown parameter 6That's a warning message related to your Intel chipset. The message suggests an incompatibility between your kernel's DRM implementation and the version of libdrm you're using. Bugs have been filed about similar issues on a variety of Linux distros, but the general consensus *seems* to be that this particular message is harmless.

The other messages log periodic updates to your motd file, triggered by cron.

I hope that helps.

---

### Post by dunbrokin on 2009-05-24
Hmmmm!...thanks for that.

Not sure why I have "message of the day" (motd) as I am not operating as a server.

---

