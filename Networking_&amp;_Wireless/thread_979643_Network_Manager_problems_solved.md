---
title: "Network Manager problems solved"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by b3n87 on 2008-11-12
Hello everyone,

Just like a lot of people on the forums, I updated my Hardy Dell Inspiron 1525 to Ibex just after the release. The network manager broke, there were problems with the applet not showing in the notification bar too.

To solve my problem I did this:

```
sudo gedit /etc/network/interfaces
```

copy and pasted the contents to a file on my desktop for back up purposes then just deleted the contents of the interfaces file.
I then rebooted and my network manager seems to be working fine.

Hope this helps other people.

Oh and my wireless is now working, because that broke too after the upgrade.

---

### Post by majedaly on 2010-10-12
> **b3n87 said:**
> 
Hope this helps other people.

.
Thanks, I have been banging my head in the wall for the same...!

---

