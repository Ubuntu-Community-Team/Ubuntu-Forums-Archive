---
title: "Update manager problem - Xulrunner gone AWOL?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by cogvos on 2010-09-21
Dear all,

Update manager keeps telling me that there is a security update for Xulrunner (whatever that is) but then fails to update with the following errors. Any ideas? I'm on Ubuntu 9.10


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9_1.9.2.9+build1+nobinonly-0ubuntu0.9.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9_1.9.2.9+build1+nobinonly-0ubuntu0.9.10.1_all.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1-gnome-support_1.9.1.12+build1+nobinonly-0ubuntu0.9.10.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1-gnome-support_1.9.1.12+build1+nobinonly-0ubuntu0.9.10.2_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.12+build1+nobinonly-0ubuntu0.9.10.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.12+build1+nobinonly-0ubuntu0.9.10.2_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.9+build1+nobinonly-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.9+build1+nobinonly-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]

---

### Post by Silent Warrior on 2010-09-21
Either your connection chose a fine time to glitch, or you should try updating the package list again. I can reach the directory just fine.

---

### Post by cogvos on 2010-09-21
> **Silent Warrior said:**
> Either your connection chose a fine time to glitch, or you should try updating the package list again. I can reach the directory just fine.

Many thanks for the quick reply - tried it again with the same result. How do I update the package list please?

---

### Post by Silent Warrior on 2010-09-21
Through terminal: sudo apt-get update (followed by sudo apt-get upgrade for the actual package-upgrade)
Through Synaptic: Refresh (left-most button on the icon-panel, might be called Reload), then select available updates, Apply.
Through Update Manager: Check for updates, select the available updates, Apply. (I think.)

---

