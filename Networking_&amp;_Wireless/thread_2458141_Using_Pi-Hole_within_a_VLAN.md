---
title: "Using Pi-Hole within a VLAN"
date: 2021-02-17
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2021-02-17
Folks,

Had Pi-Hole running on my network for some time with no issues.  I have started experimenting with VLAN which, I am assuming this is the norm, creates another subnet.

If I create the VLAN without enabling **isolate** then Pi-Hole is seen, if I choose to **isolate** then it is not seen on the VLAN but obviously is on the original subnet.

Being new to VLAN I am not sure why one would create a VLAN and then not **isolate** but I may be missing some pros and cons.

Now I've tried using **ip addr add** to give the adapter a second IP address but, although it works fine if second address within same subnet it does not appear to work if the extra IP is within the second VLAN subnet.

There do not appear any obvious router settings to achieve this, any suggestions appreciated.

Geoff Lane

---

