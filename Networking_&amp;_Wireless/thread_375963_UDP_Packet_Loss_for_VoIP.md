---
title: "UDP Packet Loss for VoIP"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by aie93 on 2007-03-04
A long time ago my VoIP PBX Asterisk stopped working with my SIP supplier properly, I thought this was an issue with them, or the software, not the OS as it was working perfectly with my internal SIP ATAs and had been working perfectly before.

I installed a second broadband line and thought that may have been the issue, but that didn't fix it at all.  Then I ran Trixbox (a pre-made Asterisk distro running on a doctored CentOS base) using VMWare on top of my Ubuntu distribution.  This worked perfectly, other than a few issues arising from the fact it was in VMWare.

This therefore proves the issue is not with the hardware, internet connection, PBX software or the supplier, but MUST be with Ubuntu.  I did a netstat -su and when calling through the VoIP supplier I'm getting 30% UDP packets being dropped by the kernel.

Trying to stop this I upgraded the PBX to version 1.2.15 and also dist-upgraded to Edgy from Dapper and also increased the UDP buffer to 8MB.  None of these have helped me.  I'm currently running the lastest version of Edgy.

Any ideas anyone?? I don't realy like running CentOS or VMWare, I want to get back to the way it was with Ubuntu running my network on one not-virtual box.

---

