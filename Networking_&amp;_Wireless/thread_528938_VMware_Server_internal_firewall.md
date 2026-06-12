---
title: "VMware Server internal firewall?"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by rsv869 on 2007-08-18
Greetings all -

On my VMWare Server (the free version) I have no success using FTP or SCP to tansfer files between guest servers and the host, or vise-versa. I can easily do the above from other VMWare guests running on other machines, but not from guest to host on this machine. Anyone seen this before?

I'm running the VMWare server 1.0.3 build-44356 on my Ubuntu 7.04 machine and the Server implementation was retrieved from the Ubuntu repositories.

I have looked at output from Wireshark packet captures and see nothing of interest though there is consistent episode of checksum errors which may or may not be a red herring. Also I have seen tcpdumps which show evidence that the packets are hitting something called stgxfws at port 1226. Not sure why.

Any thoughts would be appreciated.

Reid

---

