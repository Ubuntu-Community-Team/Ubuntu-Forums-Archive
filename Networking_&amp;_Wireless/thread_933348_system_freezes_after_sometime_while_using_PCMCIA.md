---
title: "system freezes after sometime while using PCMCIA"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by coolyap on 2008-09-29
I face a very frustrating problem. I have installed Ubuntu Hardy on my laptop, a HCL make. I use a Huawei EC 321 PCMCIA as my wireless data card. Also I use the 'Gnore PPP' to establish the connection.

The problem I face is that after a few minutes of being online the system freezes. I am not sure how to work around this problem. Initially I was under the impression that this is a one-off case but the problem persisted over a last few attempts. In fact, today this is my 4th reboot of the system. The only solution is to (hard) reboot my laptop and that is frustrating. I want to migrate entirely away from Windows and into Ubuntu but this hang/freeze is the only blocker.

Please suggest what should I do?

I am not sure if I am capturing the proper logs but I have captured the following. Hope this is of some use to solve the problem :

========================================>/var/log/kern.log<=======================================================

Sep 29 21:22:38 rp-laptop kernel: [   47.233635] EXT3 FS on sda9, internal journal
Sep 29 21:22:38 rp-laptop kernel: [   47.233639] EXT3-fs: mounted filesystem with ordered data mode.
Sep 29 21:22:38 rp-laptop kernel: [   50.200777] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 29 21:22:38 rp-laptop kernel: [   50.589239] No dock devices found.
Sep 29 21:22:38 rp-laptop kernel: [   50.927445] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFC) is beyond end of object [20070126]
Sep 29 21:22:38 rp-laptop kernel: [   50.927469] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PSS] (Node f7824ca8), AE_AML_PACKAGE_LIMIT
Sep 29 21:22:38 rp-laptop kernel: [   50.927520] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Sep 29 21:22:38 rp-laptop kernel: [   50.927755] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFC) is beyond end of object [20070126]
Sep 29 21:22:38 rp-laptop kernel: [   50.927775] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PSS] (Node f7824eb8), AE_AML_PACKAGE_LIMIT
Sep 29 21:22:38 rp-laptop kernel: [   50.927823] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Sep 29 21:22:38 rp-laptop kernel: [   51.769986] apm: BIOS not found.
Sep 29 21:22:38 rp-laptop kernel: [   51.904173] ppdev: user-space parallel port driver
Sep 29 21:22:39 rp-laptop kernel: [   52.030272] audit(1222703559.007:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5254 profile="/usr/sbin/cupsd" namespace="default"
Sep 29 21:22:41 rp-laptop kernel: [   54.138414] eth0: link down
Sep 29 21:22:41 rp-laptop kernel: [   54.185274] Bluetooth: L2CAP ver 2.9
Sep 29 21:22:41 rp-laptop kernel: [   54.185280] Bluetooth: L2CAP socket layer initialized
Sep 29 21:22:41 rp-laptop kernel: [   54.256698] Bluetooth: RFCOMM socket layer initialized
Sep 29 21:22:41 rp-laptop kernel: [   54.256729] Bluetooth: RFCOMM TTY layer initialized
Sep 29 21:22:41 rp-laptop kernel: [   54.256731] Bluetooth: RFCOMM ver 1.8
Sep 29 21:22:51 rp-laptop kernel: [   64.812289] hda-intel: Invalid position buffer, using LPIB read method instead.
Sep 29 21:23:00 rp-laptop kernel: [   73.054645] NET: Registered protocol family 10
Sep 29 21:23:00 rp-laptop kernel: [   73.055012] lo: Disabled Privacy Extensions
Sep 29 21:23:00 rp-laptop kernel: [   73.055486] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 29 21:23:05 rp-laptop kernel: [   78.580385] CPU0 attaching NULL sched-domain.
Sep 29 21:23:07 rp-laptop kernel: [   78.580394] CPU1 attaching NULL sched-domain.
Sep 29 21:23:07 rp-laptop kernel: [   78.610566] CPU0 attaching sched-domain:
Sep 29 21:23:07 rp-laptop kernel: [   78.610575]  domain 0: span 03
Sep 29 21:23:07 rp-laptop kernel: [   78.610577]   groups: 01 02
Sep 29 21:23:07 rp-laptop kernel: [   78.610581] CPU1 attaching sched-domain:
Sep 29 21:23:07 rp-laptop kernel: [   78.610585]  domain 0: span 03
Sep 29 21:23:07 rp-laptop kernel: [   78.610587]   groups: 02 01
Sep 29 21:23:58 rp-laptop kernel: [  131.654823] PPP generic driver version 2.4.2
Sep 29 21:24:01 rp-laptop kernel: [  134.847105] PPP BSD Compression module registered
Sep 29 21:24:01 rp-laptop kernel: [  134.947367] PPP Deflate Compression module registered

=========================================>/var/log/messages<====================================================
Sep 29 21:23:00 rp-laptop kernel: [   73.054645] NET: Registered protocol family 10
Sep 29 21:23:00 rp-laptop kernel: [   73.055012] lo: Disabled Privacy Extensions
Sep 29 21:23:00 rp-laptop kernel: [   73.055486] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 29 21:23:58 rp-laptop kernel: [  131.654823] PPP generic driver version 2.4.2
Sep 29 21:23:58 rp-laptop pppd[6328]: pppd 2.4.4 started by rp, uid 1000
Sep 29 21:23:58 rp-laptop pppd[6328]: Using interface ppp0
Sep 29 21:23:58 rp-laptop pppd[6328]: Connect: ppp0 <--> /dev/ttyUSB0
Sep 29 21:24:01 rp-laptop pppd[6328]: PAP authentication succeeded
Sep 29 21:24:01 rp-laptop kernel: [  134.847105] PPP BSD Compression module registered
Sep 29 21:24:01 rp-laptop kernel: [  134.947367] PPP Deflate Compression module registered
Sep 29 21:24:02 rp-laptop pppd[6328]: local  IP address 220.226.84.47
Sep 29 21:24:02 rp-laptop pppd[6328]: remote IP address 220.224.135.78
Sep 29 21:24:02 rp-laptop pppd[6328]: primary   DNS address 202.138.103.100
Sep 29 21:24:02 rp-laptop pppd[6328]: secondary DNS address 202.138.96.2

---

### Post by coolyap on 2008-09-30
folks
This is quite important for me and quite frustrating too.
I need to get this done asap.
Can somebody please help me! What should I do and how do i solve this?

~ rp

---

