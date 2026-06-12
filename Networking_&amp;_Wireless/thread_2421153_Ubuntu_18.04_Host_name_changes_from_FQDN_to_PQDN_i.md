---
title: "Ubuntu 18.04: Host name changes from FQDN to PQDN in DNS"
date: 2019-06-17
forum: Networking &amp; Wireless
---

### Post by david.aldrich.ntml on 2019-06-17
We are running Ubuntu 18.04 LTS with networking configured by NetPlan. The network has a Windows DHCP server and a Windows DNS server.

The Ubuntu 18.04 machine uses this NetPlan cfg file to obtain a dynamic IP address:

$ cat /etc/cloud/cloud.cfg.d/50-curtin-networking.cfg
network:
  ethernets:
    ens4:
      addresses: []
      dhcp4: true
  version: 2

The partially qualified host name is ubuntusim01.  After reboot the FQDN in DNS is:

ubuntusim01.uktm.<snip>.com

which is correct. But the host name stored in DNS sometimes spontaneously changes to the PQDN:

ubuntusim01.

(interrogated by nslookup) and then other systems lose connectivity to the Ubuntu machine.

It is possible that this change happens when the DHCP lease expires, but we are not sure of that.

This problem does not occur with our Ubuntu 16.04 LTS servers (which use NetworkManager).

Is this a known bug, or is our configuration wrong in some way?

---

### Post by SeijiSensei on 2019-06-17
If this is a serverb it should have a static address and configuration and not use DHCP.

---

### Post by david.aldrich.ntml on 2019-06-17
It is a server in the sense that it is not a desktop. It is one of a group of machines used for simulation work and is accessible by multiple users to run their simulation jobs. So DHCP is a valid choice.

---

