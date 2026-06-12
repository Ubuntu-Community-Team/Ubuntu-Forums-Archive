---
title: "socat"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by dante_armando on 2008-04-30
Hi,

I just wanted to report that the socat version that gets installed by Feisty doesn't work with my IP adresses:

dante@dante-laptop:~/$ socat pipe:con,ignoreeof tcp6:192.168.1.3:4001,ignoreeof &

That returned a "Address family for hostname not supported" message.

I had to download the socat source and compile it myself. Is there a way I could upload my compiled files to the repository? I don't know how they work.

Dante

---

