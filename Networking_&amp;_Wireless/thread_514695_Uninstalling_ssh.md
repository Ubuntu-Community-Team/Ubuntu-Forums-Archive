---
title: "Uninstalling ssh"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by psbp on 2007-08-01
I'm a newbie and am in need of some help in uninstalling ssh. It was installed on my computer unbeknown to me and i need a walkthrough of uninstalling it so I can go straight in and do it as fast as possible, before the person controlling my computer shuts me down. Can someone walk me through how to uninstall ssh please?

---

### Post by aysiu on 2007-08-01
```
sudo apt-get remove openssh-server
``` But if someone with malicious intent installed something on your computer, she may very well have set up road blocks to you removing access.

If you're really that worried, unplug your computer from the internet, reinstall Ubuntu, and then plug it in again.

---

