---
title: "Network Manager inactive"
date: 2019-05-04
forum: Networking &amp; Wireless
---

### Post by kaet on 2019-05-04
Hello,
So my network manager stopped running, and I can't reinstall since I can't connect with the internet now. I'm not quite sure why it stopped running and I can't get it to start running again.
Does anyone now how I can fix this?

---

### Post by wildmanne39 on 2019-05-04
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by kryten35 on 2019-05-05
One thing to try is as admin with your preferred text editor
     ```
/etc/NetworkManager/NetworkManager.conf
```
and check if managed=false or true  if false change to true then restart network manager
```
service network-manager restart

```

Sometimes it glitches and reverts back to false.

---

