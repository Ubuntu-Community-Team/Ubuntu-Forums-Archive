---
title: "How to Share local Internet Using a Proxy client?"
date: 2024-05-30
forum: Networking &amp; Wireless
---

### Post by usoviet on 2024-05-30
I want to download/setup a proxy on a VM to send the network traffic from the host machine to the local Internet but not the remote server who has a different IP.

---

### Post by currentshaft on 2024-05-30
d1188:188

---

### Post by usoviet on 2024-05-30
SSH login from host to guest machine (ssh -D   root@192.168.56.6) is what I need, it can make a proxy servicing for programs in hostOS, and do some iptables settings in guestOS beforehand.

---

