---
title: "VMWare bridged networking"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by rodyhoe on 2007-06-17
Hi

I have a 7.04 (installed not upgraded) desktop, with VMServer installed from apt-get.

I have a Win2k Virtual machine set-up with a Bridged N/W.

From Win2k I can browse the Internet via a ADSL router, and browse to another physical computer on he N/W (and this computer can browse the Virtual Win2k server and access Apache web pages).
From the Ubuntu VMhost I can ping the W2k virtual machine, and from the W2k Virtual machine I can ping the Ubuntu Server.

But I can not get Network services to work between the VMServer and the VMhost - I am trying to get Samba & Apache to work in either direction - these do work between a third different physical computer and either the VMserver or the VMhost.

Any help/advice would be great.

Thanks

---

### Post by Gallows on 2007-07-04
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=482860") thread and then pop over to the VMWare site [here]("http://www.vmware.com/community/thread.jspa?threadID=78606&tstart=0")

Or just use the NAT interface (normally vmnet8)

---

