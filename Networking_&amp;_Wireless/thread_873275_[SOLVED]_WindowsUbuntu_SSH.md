---
title: "[SOLVED] Windows/Ubuntu SSH"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Yuki_Nagato on 2008-07-28
I have a server that I SSH into using a pair of RSA keys.  The client was an Ubuntu box tunneling into the Mint Apache2 server.  I disabled password authentication, making that computer the only one able to SSH into it.  It has been working nicely.

Now I need to get a Windows Vista machine able to SSH into the Mint box.  I have direct access to the server, so I can re-enable password authentication if I need to.

Should I clone my Ubuntu private key and move it to the Vista machine?  Where would I put it so that the Mint box will find it?  Or should I create a new key with puTTygen?  I still do not know where to drop the key file.

---

### Post by dmizer on 2008-07-28
> **Yuki_Nagato said:**
> Should I clone my Ubuntu private key and move it to the Vista machine?
Absolutely not.

> **Yuki_Nagato said:**
> [snip]Or should I create a new key with puTTygen?  I still do not know where to drop the key file.

You should create a new key with the puttygen: [http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

---

### Post by Yuki_Nagato on 2008-07-28
Alright.

I got both machines working correctly now.  That article was a huge help.

---

