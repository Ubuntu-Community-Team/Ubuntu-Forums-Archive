---
title: "DHCP stopped working"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by jimjim197 on 2008-05-18
Hi,

I was trying to fix a problem with my audio, and after removing some alsa audio software with the package manager I rebooted and now the DHCP does not work. Now the audio and DHCP is down plus the cdrom will not mount because iso9660 is not recognized. 

When I run ifup eth0 I get the following:

socket: Address family not supported by protocol - make sure
CONFIG_PACKET (Packet socket) and CONFIG_FILTER
(Socket Filtering) are enabled in your kernel
configuration!
Failed to bring up eth0.

I did not touch any networking or file devices. Can someone help me with this?


Thanks,
Jim

---

### Post by p_quarles on 2008-05-18
Moved to Networking & Wireless.

---

