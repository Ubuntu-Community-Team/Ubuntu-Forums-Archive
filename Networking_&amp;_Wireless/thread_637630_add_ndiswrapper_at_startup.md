---
title: "add ndiswrapper at startup"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by ThaDoctor99 on 2007-12-11
Hi.

Having some problems getting ndiswrapper to start at boot.
Either I have forgotten the command - or else it is not on my system
I thought it was rc-update but my system can't find this.
So what should I do.

---

### Post by kevdog on 2007-12-11
echo ndiswrapper | sudo tee -a /etc/modules

---

