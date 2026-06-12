---
title: "Use Mac OS X to RDP into My Linux Box ?"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by rompstar420 on 2008-09-23
I have a Ubuntu 8.04 server box which sits and runs in the garage.  I do a lot of things in the shell, so SSH is good.

But I wanted to learn how to RDP into it, so that I can see the Desktop ?

Please let me know what I need to read, learn and do, thanks!

So I use Mac OS X 10.5.5 in my bedroom.

---

### Post by willca on 2008-09-24
I think your best bet is to use ssh.

Basically allow X11 forwarding.

so from your client machine

ssh -Y user@hostorIP
once you in the ssh session, then just run the app you normally work on via desktop locally.

If does not work, then you can try to check out FreeNX.

---

