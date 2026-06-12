---
title: "VNC over SSH Very Slow"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by deejross on 2008-06-11
My router at home only forwards the SSH port on my Hardy machine. I also have VNC (Remote Desktop) running on it. Since VNC is insecure, I use Putty at work to connect to my home machine's SSH, and forward port 5900. This is SO SLOW.

Just for laughs, I forwarded port 5900 directly and tried connecting that way and it's pretty fast. I know SSH encrypts the VNC traffic, but I wouldn't think it would slow it down that much.

Unencrypted, it takes about 3 seconds to do a full screen refresh. Using VNC over SSH takes about 30 seconds. The machine I'm connecting to is a quad-core 2.4 Ghz, with 4GB ram, so I doubt the encryption process is slowing is the cause.

---

### Post by deejross on 2008-06-13
*shameless bump*

---

