---
title: "Showing error message &quot;/etc/network/interfaces E514:write error (file sytem fulll))"
date: 2017-08-09
forum: Networking &amp; Wireless
---

### Post by thyagaabb on 2017-08-09
we trying to edit the network interface eth0 using vi /etc/network/interface showing an error message /etc/network/interfaces E514:write error (file sytem fulll)

---

### Post by ajgreeny on 2017-08-09
It appears from that error that you have no space in your filesystem.
Show us the output of ```
df -hT
df -i
```which may help figure out the problem.

---

