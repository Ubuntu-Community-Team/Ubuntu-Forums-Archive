---
title: "aMule doesn't work with Unity"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by itayshom on 2011-04-30
Hi,

I upgraded from 10.10 to 11.04 last night. Among the many bug introduced by the new Unity interface, I cannot run aMule 2.2.6 properly.

When I run aMule, the process is running (shows on System Monitor) but there is no indicator on the top right corner, nor is there any icon in the launcher bar. In fact I have to access to the application.

Is there any way to fix this?

---

### Post by 3rdalbum on 2011-04-30
aMule has not been updated to work with the Indicators system in Ubuntu, plus it looks like it makes the cardinal error of not actually spawning a window when you open it (from your description).

You can add aMule to Unity's indicators whitelist, to show the old-style notification area icon for aMule only.

You need to download and run this script in order to do it: [http://www.fewt.com/2011/03/whitelist-utility-script-to-allow-apps.html](http://www.fewt.com/2011/03/whitelist-utility-script-to-allow-apps.html)

---

