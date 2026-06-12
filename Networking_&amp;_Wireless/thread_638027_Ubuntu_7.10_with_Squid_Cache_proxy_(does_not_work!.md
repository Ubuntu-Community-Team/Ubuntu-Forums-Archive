---
title: "Ubuntu 7.10 with Squid Cache proxy (does not work!)"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Tiderfish on 2007-12-11
I am trying to setup a web cache proxy with Squid on a freshly formatted Ubuntu 7.10 Gutsy Gibbon computer. I have read a few how to's and one mentioned the transparent proxy does not work on Feisty. Is this true for Gusty as well? If it does work, then I am at a loss. I can't figure out what the problem is. I have configured http_access deny all, just to test the proxy. With that enabled I can still get everywhere. I have squid version 2.6. As I mentioned, all I want it for is to cache the pages I visit. Also if anyone knows a GUI squid tool that will let me set it up, please let me know! Thanks!

Matt|ttaM

---

### Post by Tiderfish on 2007-12-12
I sat down and read through the squid.conf and made changes to the items I understood, and needed or wanted. Then restarted squid, and after some tweaking, it worked! I am no chillin' on a nice cacheing proxyed connection! w00t for Linux!

Matt|ttaM

---

