---
title: "openvpn Diffie Hellman parameters"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by Doug S on 2014-09-11
Hi all,

Is there an openvpn expert that could help confirm or deny a recent Ubuntu serverguide[ bug report]("https://bugs.launchpad.net/serverguide/+bug/1367083").
The claim is that the "parameters in easyrsa have changed from 1024 bits to 2048 bits at some point in time" and a doc update is needed.

If confirmed, I'll do the fix in the master bzr branch, which would literally take about 5 minutes.

---

### Post by Doug S on 2014-09-13
O.K. I used a VM and installed and configured openvpn far enough to confirm the bug report myself.

---

