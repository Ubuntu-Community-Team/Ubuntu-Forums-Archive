---
title: "Winbind AD group GID mapping inconsistent, screws up ownership/permissions"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by inselaffe on 2007-11-07
I am logging onto Ubuntu workstations with Actie Directory authentication.

I have a Ubuntu server which is exporting an NFS share. The group the exported folder belongs to is an AD group. However, the GID assigned to that AD group varies by computer, so although GroupA is the owner on the server, the owner is GroupB on one workstation and GroupC on another. This means that the permissions obviously don't work as intended.

I need to ensure the GID assigned to each group is consistent. How can I achieve this?

---

