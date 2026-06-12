---
title: "Ubuntu 22.04.3 LTS server - Network issues with Broadcom NIC"
date: 2023-10-13
forum: Networking &amp; Wireless
---

### Post by oletkt on 2023-10-13
Hello,

On a Ubuntu 22.04.3 LTS (GNU/Linux 5.15.0-67-generic x86_64 Kernel) we are having issues with a Broadcom NIC.

We are hosted on a 10G line. The server was setup on March 2023 and during the past 2 months (since the last kernel update we made) we are experiencing slow speeds. Although we used to get 9-10Gbit/s, ever since we made the update we are getting a maximum of 4.35Gbits/sec. The tests have been made on different times and with different machines using iperf3. We are around 2-4Gbits/sec most of the time.

We contacted the Data Center and after some digging they found that another customer of theirs also had a similar issue. When they changed him to an Intel 10GE NIC, he reached back to 10Gbit/s speeds. The other customer also had Ubuntu 22.04 and their conclusion, based on their research, was that it must be a kernel driver/Linux firmware issue.

We are using Broadcom's "BCM57416 NetXtreme-E Dual-Media 10G RDMA Ethernet Controller". If you require also the firmware version, please let us know, so that i can send it in a private message.

We've been offered by the Data Center to get a free of charge installation of an Intel 10GE NIC, but we'd rather avoid the hustle of downtime and network changes.

What could we do to get rid of the issue?

---

### Post by TheFu on 2023-10-13
Open a bug in landscape with Canonical. Nobody here works for Canonical.  They will need the exact card, kernel, and driver in addition to all the normal bug reporting things.
The switch and firmware on it would also be useful, I'd bet.

In the meantime, look for differences in the driver between the 2 kernels. I don't know if broadcom makes their source available or not, but if they do, might be worth looking at any diffs in the driver code too.

---

### Post by oletkt on 2023-10-14
> **TheFu said:**
> Open a bug in landscape with Canonical. Nobody here works for Canonical.  They will need the exact card, kernel, and driver in addition to all the normal bug reporting things.
The switch and firmware on it would also be useful, I'd bet.

In the meantime, look for differences in the driver between the 2 kernels. I don't know if broadcom makes their source available or not, but if they do, might be worth looking at any diffs in the driver code too.

Thank you for your reply. Could you please verify that the following is the correct URL you mentioned: [https://bugs.launchpad.net/landscape](https://bugs.launchpad.net/landscape) ?

---

