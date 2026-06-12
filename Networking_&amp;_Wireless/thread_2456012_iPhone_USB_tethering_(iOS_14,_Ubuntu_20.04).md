---
title: "iPhone USB tethering (iOS 14, Ubuntu 20.04)"
date: 2021-01-02
forum: Networking &amp; Wireless
---

### Post by percy-pugwash on 2021-01-02
I'm unable to get iPhone tethering to work over USB. I've already installed the packages mentioned in [this answer]("https://askubuntu.com/questions/126340/how-do-i-set-up-the-iphone-usb-ethernet-driver"). From a bit of searching I can see this was an issue that came in with iOS 14.

Comments in [this issue]("https://github.com/libimobiledevice/libimobiledevice/issues/1038") indicate that a fix has already been made "in Linux" I presume at the kernel level. However despite installing all updates available for my system, tethering still doesn't work. Since the fix was only implemented a couple of weeks ago, I'm wondering whether I need to upgrade to a beta version of the kernel or something to get it now?

Grateful for any thoughts on this.

---

### Post by brewstah on 2021-02-23
Someone called potato1992 posted a fix for kernels < 5.10.4 in that github thread you linked.  You can find it [here]("https://github.com/potato1992/Iphone_usb_tethering_fix").

I tried it using the automatic install script.  And, it worked for me (Ubuntu 20.10 with kernel 5.8.0-44).

---

