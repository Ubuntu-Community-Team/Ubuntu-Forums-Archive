---
title: "How to query DHCP options"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by Mike_Soultanian on 2014-09-09
Hi,
I have about 300 Ubuntu (14.04) workstations set to DHCP and running a custom application that processes data retrieved from a camera and sends it to a server.  I don't want to hard-code the server address on all of those workstations, so I was hoping I could set that address using a DHCP option and then have the application retrieve that option so that it knows the server address.  I don't mind parsing through config files for the information (if available), I just was looking for some guidance on how to accomplish this, if it's even possible.

Thanks!
Mike

---

### Post by TheFu on 2014-09-10
DHCP Reservations.  The MAC address for every "server" will need to be set inside the DHCP server so they always get the same IP.  

With 300 systems, it is time to use DevOps methods - take a look at **Ansible**. Managing static IPs for 300 systems is trivial with that tool.  I only have 20 systems, but 2, 20, 200, 2000 - doesn't matter with Ansible. Only 1 workstation needs that software - there aren't any client agents required, just ssh.

---

