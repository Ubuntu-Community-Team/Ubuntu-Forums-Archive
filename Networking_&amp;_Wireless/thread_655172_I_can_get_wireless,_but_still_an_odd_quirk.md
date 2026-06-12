---
title: "I can get wireless, but still an odd quirk"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by weatherguy48 on 2008-01-01
I hope this hasn't been covered, but I consider it a unique quirk.

I was able to get my Belkin N USB wireless adapter working through NDISWrapper, via XP64 drivers (I obviously use Gutsy 64 bit), but sometimes, and out of nowhere, it'll quit working.  A re-connect to the network (a very strong 75%-91% network) doesn't yield anything...it simply can't find it.

However, the oddest quirk, a reboot solves the problem.  I'm thinking I need a way to emulate whatever happens during reboot to solve it (something with the usb controller maybe?, possibly with a shell script?) to be able to fix this in one click without rebooting, but I have no clue where to start.  A re-modprobe of NDISwrapper doesn't work, and reconnecting in Gnome's Network Manager doesn't work, it's just....odd that a reboot solves the issue.

If you need anymore details just ask, I'm obviously a linux n00b haha.

PS this is my first post, I'm glad to be part of the community.

---

### Post by Predator[23rd] on 2008-01-01
> **weatherguy48 said:**
> However, the oddest quirk, a reboot solves the problem.  I'm thinking I need a way to emulate whatever happens during reboot to solve it (something with the usb controller maybe?, possibly with a shell script?) to be able to fix this in one click without rebooting, but I have no clue where to start.

welcome!

you usually do not reboot UNIX/LINUX systems to solve problems. :D you restart services, disable and enable devices instead. hehehehe

next time try to restart your network with **/etc/init.d/networking restart**.

---

