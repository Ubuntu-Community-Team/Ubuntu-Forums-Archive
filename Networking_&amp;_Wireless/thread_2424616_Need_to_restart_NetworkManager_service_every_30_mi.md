---
title: "Need to restart NetworkManager service every 30 min"
date: 2019-08-11
forum: Networking &amp; Wireless
---

### Post by mr-mister on 2019-08-11
My connection drops every 30 min. I fix it temporarly with systemctl restart NetworkManager

[https://paste.ubuntu.com/p/MFrsdDgxwF/](https://paste.ubuntu.com/p/MFrsdDgxwF/)

Given that this is a HP notebook i know there inevitable trouble with every driver

---

### Post by &amp;wP*!) on 2019-08-13
Your wlp2s0 (wireless interface) is up, so this might not be related to your home devices, but your internet provider. Initial guess, might be wrong.

Type 
```
systemctl status NetworkManager

```
... and paste the output here 1) once when the connection is live, 2) once when the connection drops (i.e. two different
Also, show the last lines in the file **/var/log/syslog** and the output of the command **journalctl -xe** when the connection drops.

This will give us more information so that we can help you faster.

---

