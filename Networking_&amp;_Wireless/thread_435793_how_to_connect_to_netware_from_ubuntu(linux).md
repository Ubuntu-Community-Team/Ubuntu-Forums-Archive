---
title: "how to connect to netware from ubuntu(linux)"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by ferhatgurgen on 2007-05-07
I install ubuntu 7.04.

there is a linux server and netware server.
windows users are connecting to linux server and netware server because they installed netware client(IPX). no problem.

ubuntu users connecting to linux server, but they aren't connecting to netware server.
how to connect to netware server ubuntu users?

I from turkey.

thanks

---

### Post by dcd7 on 2007-06-12
Depends on the netware version; servers version 5.X or 6.X allow to connect via smb://[serverurl]/[volume] in Konqueror - if this service is enabled on the netware server. I'm running netware servers (version 6.5 SP6) with afp, cifs (smb) and nfs enabled; checked smb and it works, did not check nfs.

---

