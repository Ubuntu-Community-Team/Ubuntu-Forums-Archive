---
title: "firestarter rule"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by ramboza on 2008-07-15
When firestarter is active, there's no windows workgroup in Network Servers->Windows Network. When i turn it off, the workgroup appears.
What rule should i add to make it work?
Thank you.

---

### Post by ramboza on 2008-07-15
The ubuntu PC is also not accessible from windows PC when the firestarter is active. Tried to add the policy "Allow connections from 192.168.0.0" - didn't work.

---

### Post by ramboza on 2008-07-15
solved. By default firestarter is blocking all broadcast traffic which is needed by netbios to resolve host names. Should turn it off in preferences...

---

