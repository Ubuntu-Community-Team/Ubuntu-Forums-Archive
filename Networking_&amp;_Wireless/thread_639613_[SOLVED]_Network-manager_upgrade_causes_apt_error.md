---
title: "[SOLVED] Network-manager upgrade causes apt error"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by rosslaird on 2007-12-13
A couple of days ago, the most recent gutsy upgrades caused my system to go into some weird circularity with regard to network-manager. The newest version tries to restart itself after the upgrade, but then hangs the entire system. After the required hard reboot, and my attempt to remove network-manager, I get this:

```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

And when I run this, apt tries to complete the previous upgrade, which causes the attempt to restart network-manager, which causes the system to crash...

Hm.

Ross

Edit:

Well, I seem to have fixed the issue (after one last hard reboot). I fiddled around with dpkg and apt options, and that seemed to get me most of the way there (stuff like  sudo dpkg --remove network-manager, which seems to me should be exactly the same as what I was doing before -- but it did work, more or less).

R.

---

