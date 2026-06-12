---
title: "Problems with pbis and Ubuntu 14.04 LTS"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by marciobacci on 2015-11-23
Hi,

I installed PBIS Open package in Ubuntu 4.14 and almost everything is working properly.

The only thing that does not work is the /opt/ppbis/bin /update-dns

When I run this command the output is as follows:

Failed to update DNS. Error code [42700]

I've read all the PBIS administration manual and also researched enough on the Internet, but so far have found nothing.

I performed virtually every PBIS tests and apparently everything is OK.

My /etc/resolv.conf is only with the nameserver that also is my DC . I'm using Samba 4.

Windows machines can insert your record in DNS normally, so I think it's a problem with the Linux stations.

I do not know if this problem is serious and can lead to a problem in authentication.

Has anyone a idea ?

Regards,

Márcio

---

