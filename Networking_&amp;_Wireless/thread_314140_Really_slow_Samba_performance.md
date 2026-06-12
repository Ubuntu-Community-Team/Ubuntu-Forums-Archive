---
title: "Really slow Samba performance"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by ToniVR on 2006-12-07
I recently got a new mainboard for a server (Asus P5L-VM 1394), reinstalled Ubuntu on it.

*CPU*
Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz
*Kernel*
Linux Palladio 2.6.17-10-server #2 SMP Fri Oct 13 15:35:28 UTC 2006 x86_64 GNU/Linux
*Network driver*
root@Palladio:~# modinfo atl1
filename:       /lib/modules/2.6.17-10-server/kernel/drivers/net/atl1/atl1.ko
author:         Attansic Corporation, <xiong_huang@attansic.com>
description:    Attansic 1000M Ethernet Network Driver
license:        GPL
version:        0.1.40.8
*Networking*
Joined to Windows domain, authentication through winbind.

When I transfer files through ftp or http, it goes like it should (approx 600kbps).
When I transfer files over Samba from any Windows based pc or server, I get about 6kbps.

Anybody a clue where to seek?

---

