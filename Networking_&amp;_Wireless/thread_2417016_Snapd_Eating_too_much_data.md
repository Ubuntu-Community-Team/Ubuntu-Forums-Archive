---
title: "Snapd Eating too much data"
date: 2019-04-19
forum: Networking &amp; Wireless
---

### Post by akash1998 on 2019-04-19
I currently have ubuntu 18.04.02 . The problem is snapd is continuously running in background and eating my internet. I have a metered connection so it becomes problem.

---

### Post by TheFu on 2019-04-20
Snaps like to update themselves.
[https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707/14](https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707/14) is a discussion about this issue. There was clear disagreement.
Perhaps they've solved it with some settings?  A way to disable all automatic with the expectation that you would run snap update every few weeks or months.

---

### Post by akash1998 on 2019-04-24
thanks for your help but it is running continuously from 3-4 days should i disable them??

---

### Post by TheFu on 2019-04-24
> **akash1998 said:**
> thanks for your help but it is running continuously from 3-4 days should i disable them??

I would have long ago.  You do know that nobody here works for Canonical and that your ability to work around any issues caused by removing any snaps should be key in your decisions.  Things that I'm willing to do aren't necessarily the same as what you are willing to do.

I have daily backups which I 100% know can be restored.
I'm not worried if a system fails to boot. That is a minor inconvenience to me, fixed within either a few minutes or 30min by restoring backups.
I don't use 18.xx. Removal of snaps in 16.04 hasn't caused major issues to me. In 18.04 and later, I understand Canonical has chosen to force some core programs as snaps.  If you reboot and there isn't a GUI at all, would that be bad?

Have you disabled automatic snap updates already? Did that not work?

---

### Post by cruzer001 on 2019-04-24
You could disable snap and see if that gives you the desired results.
```
sudo systemctl stop snapd && sudo systemctl disable snapd
```
and to restore to default
```
sudo systemctl enable snapd && sudo systemctl start snapd
```

---

