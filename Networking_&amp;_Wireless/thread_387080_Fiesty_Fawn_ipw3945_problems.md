---
title: "Fiesty Fawn ipw3945 problems"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by bpasdar on 2007-03-17
Hello,

I have an IBM Thinkpad T60p that has an IPW3945ABG card in it.  I installed Kubuntu Fiesty Fawn Herd 4 on it and all worked OK for weeks.  Then all-of-the-sudden one day after an apt-get update it stopped working and is not longer recognized by iwconfig.

I checked lsmod and ipw3945 is loaded as is ipw3945d.

When I try to look for an update via apt-cache search no ipw3945 modules exist.

Can anyone offer any ideas?

Thanks

Babak

---

### Post by gradedcheese on 2007-03-17
You're probably missing the regulatory daemon.  The update most likely updated your kernel and thus a new version of the daemon is needed.  You have several options.  You can reboot into the older kernel that worked (press ESC at bootup to get the grub menu and choose a different kernel), or you can build the driver from source.  The latter is actually not that hard, ipw3945 comes with thorough instructions for compiling and installing.  You could also wait until the Feisty maintainers update the appropriate ipw3945 restricted modules package.

---

### Post by YourDoom123 on 2007-03-29
wait, does your wireless card still show up in network manager?

---

