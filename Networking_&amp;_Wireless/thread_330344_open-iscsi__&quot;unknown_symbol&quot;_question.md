---
title: "open-iscsi  &quot;unknown symbol&quot; question"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by tom_adams on 2007-01-03
I downloaded and installed open-iscsi-2.0.730 on ubuntu amd64 edgy.

Among other things the  "make install "  command   replaced the **isci_tcp.ko** and **scsi_transport_iscsi.ko** located at /lib/modules/2.6.17-10-generic/kernel/drivers/scsi.

When I start  the iscsid daemon I get  77 "Unknown symbol"  errors in dmesg coming from iscsi_tcp.  They look  something like this [COLOR="Red"]**"iscsi_tcp: Unknown symbol iscsi_conn_start".**
[/COLOR]   These symbols are all defined in the downloaded source package in a file called Modules.symvers.

Am i running into a conflict between the open-iscsi code and the iscsi stuff that was built into the 2.6.17-10 kernel?    
Do I need a different kernel that does not include the iscsi modules?  *(I hope not because I would not have a clue as to how to do that!)*

---

