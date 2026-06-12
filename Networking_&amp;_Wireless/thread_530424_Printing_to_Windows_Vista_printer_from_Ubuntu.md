---
title: "Printing to Windows Vista printer from Ubuntu"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by mikko.ohtamaa on 2007-08-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/107087](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/107087) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ubuntu Feisty (Samba 3.0.24) and Windows Vista don't mix together, because Vista uses newer SMB2 sharing protocol and due to a bug in Samba, Samba clients don't fall back to SMB protocol version 1. 

One cannot access printers and folders SMB shared on Windows Vista from Linux. 

However, after [installing LPD printing support on Vista]("http://ubuntuforums.org/showpost.php?p=110503&postcount=4"), one can print from Linux client to Windows Vista server.

More details can be found [here]("http://blog.redinnovation.com/2007/08/20/printing-to-windows-vista-printer-from-linux/").

---

