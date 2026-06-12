---
title: "CPU Stuck at 100%"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by taddy_porter on 2009-08-21
After an upgrade (to 8.04) I think, I've been having issues with ubuntu behaving. I'm on Jaunty now, but updates don't seem to help. My CPU usage is just stuck at 100%. According to TOP, Kio_http and Opera are using 20% of CPU and memory. Xorg is using another 20% of CPU. DBUS is taking a third of my memory. Shutting Opera down just pushes the CPU off to other processes. What's going on here? Computer's an old Athlon XP 1900, but it ran just fine a few months ago. Any ideas on where to start fixing it up? Could there be a problem with the Nvidia drivers? I had issues with the kernel updates in the past, but those appear fixed now.

---

### Post by philinux on 2009-08-21
Reboot, login but dont start any apps. Then run top. It should idle less than 10% cpu.

---

### Post by Sir Jasper on 2009-08-21
Hi,

This has happened to me twice in the last three weeks since I upgraded to 9.04 (with Xubuntu desktop installed). Everything locked up but after a hard reset all went back to normal use.

My regards

PS I have the CPU Graph on a panel and clicking on it brings up ¨top¨

---

### Post by taddy_porter on 2009-08-21
I found the culprit--kio_http

For some reason it sucks up all the available CPU and memory. It survives reboots as well. Any idea why?

---

### Post by philinux on 2009-08-21
Take your pick.

[http://www.google.co.uk/search?q=kio_http&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=kio_http&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by taddy_porter on 2009-08-22
I spoke too soon. It dropped for a short while after I killed kio_http, then Opera filled it up. Kill Opera, something else fills it up. Dbus has jumped up to 80% of my memory. I'm wondering if that's not the problem.

---

