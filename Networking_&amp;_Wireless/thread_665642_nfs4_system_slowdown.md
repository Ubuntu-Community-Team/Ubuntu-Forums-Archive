---
title: "nfs4 system slowdown"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by dblevitan on 2008-01-12
I'm running Kubuntu gutsy on my laptop. I have an NSLU2 running Debian that I am trying to read/write to/from from my laptop over a wired network. I am primarily trying to use NFS4 (no GSSAPI) but am running into weird issues. Whenever I try to copy data, the laptop will randomly hang for 30 seconds, then keep running as if everything was fine. Files transfer without any issues except for the hangs. If I use FTP instead, there are no issues, leading me to believe that this is an NFS issue. There are no processes running at high CPU utilization and I'm pretty much stumped as to what's going on. My only thoughts are that the laptop (core 2 duo)  is capable of transmitting at a much higher rate than the NSLU2 is capable of receiving, and that's causing the slowdowns. Anyone have any ideas?

Thanks,
David

---

