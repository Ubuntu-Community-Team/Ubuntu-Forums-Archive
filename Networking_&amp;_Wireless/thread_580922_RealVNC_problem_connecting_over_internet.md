---
title: "RealVNC problem connecting over internet"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by mollison on 2007-10-19
I have 2 Unubtu machines running next to each other in the same room. One is my laptop, and I'd like to be able to take it somewhere far, far away and still connect to my desktop.

I'm running the RealVNC server on the desktop (which comes with ubuntu) and I can connect just fine over the local network.

When I try to connect over the internet, I get:

VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)

When I'm connecting locally, I then get a Password: prompt. (Or, if I disable that, I just get the remote connection immediately.) But when I'm connecting over the internet, that's all I get... it just hangs.

I have port forwarding set up correctly... if I hadn't, I wouldn't get that last line, which shows that it's detecting the VNC server I'm trying to connect to.

So... why's it hanging, and how can I fix this? SSH is possibly something I'll set up in the future, but I'd really like to know what's going on.

---

### Post by mollison on 2007-10-19
*nudge*

---

### Post by mollison on 2007-10-20
bump

---

### Post by giruzz on 2007-12-30
> **mollison said:**
> bump

got the same issue. have you solved?

g.

---

### Post by mollison on 2007-12-30
Yeah - I solved it by trying a different router. The above problem was happening on a D-Link, but everything worked fine when I switched to Linksys.

I am SURE I had the D-Link configured correctly - it's just that D-Link routers are known to suck.

If you are having the exact same problem and are also using a D-Link router, let me know and we can compare model numbers, for curiosity's sake.

---

