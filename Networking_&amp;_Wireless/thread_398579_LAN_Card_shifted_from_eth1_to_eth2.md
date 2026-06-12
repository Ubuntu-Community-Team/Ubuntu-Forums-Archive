---
title: "LAN Card shifted from eth1 to eth2"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by rvbhute on 2007-04-01
I have an Asus M2N-MX mainboard with an Asus LAN card. Initially it was detected as **eth1**. The on-board LAN card takes **eth0**. However, this afternoon, after a (normal) reboot, I found it to be detected as **eth2** and the Network Manager applet spent a lot of time "acquiring IP address" when I selected it because obviously **eth2** was not configured and automatically set to roaming mode. Whatever happened to **eth1**?

---

### Post by netztier on 2007-04-01
> **rvbhute said:**
> I have an Asus M2N-MX mainboard with an Asus LAN card. Initially it was detected as **eth1**. The on-board LAN card takes **eth0**. However, this afternoon, after a (normal) reboot, I found it to be detected as **eth2** and the Network Manager applet spent a lot of time "acquiring IP address" when I selected it because obviously **eth2** was not configured and automatically set to roaming mode. Whatever happened to **eth1**?

Check **/etc/iftab**'s content how it tries to map MAC-Addresses to ethX names. Delete the entries or correct them, as you like it. It might even be that it maps eth1 to some MAC-address that was temporarily found on the system- did you happen to have an USB-(W)LAN module plugged in at some time?

Best regards

Marc

---

### Post by rvbhute on 2007-04-01
This are the contents of my **/etc/iftab** file. **eth1** isn't there at all!
```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:18:f3:6d:4b:17 arp 1

```

Should I add something like the following?
```

eth1 mac  00:17:31:2B:B0:85 arp1

```

Update : added it and am checking and thats the solution!
Thanks!

---

