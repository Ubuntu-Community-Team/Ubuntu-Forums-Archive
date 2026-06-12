---
title: "NFS over wireless broken with rsize=8192 - ideas?"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by AndyC_772 on 2007-01-29
I've spent the last couple of days trying to get my NAS working as well as it should. It's mounted over NFS, and with mount options rsize=8192,wsize=8192 I get around 70Mbit/s on a 100M Ethernet link, which I figure is pretty good.

On wireless, though, it's a different story. To get it to work reliably without freezing up (see [here](http://ftp.utcluj.ro/pub/docs/diverse/freeBSD/FreeBSD-handbook/handbook178.html), I have to set rsize and wsize to 1024 or 4096 - it doesn't seem to matter which.

With that setting, as of yesterday evening I was getting 4 Mbit/s.
With a change of wireless driver (bcmwl5 / ndiswrapper) I was up to 6.4 Mbit/s
This morning, with updated firmware in my wireless access point, I have 12 Mbit/s

So, it's now much better, but still poor.

On the wired network, with rsize=wsize=1024, I get 30 Mbit/s, or less than half what I get with a block size of 8192. So, there's a massive improvement still to be had if only I could get the larger block size to work over wireless.

Question is: why doesn't rsize=wsize=8192 over wireless work, and can it be fixed?

---

### Post by AndyC_772 on 2007-02-01
Much as it pains me to do this... bttt :(

I've tried the latest ndiswrapper (1.35, from SourceForge) and increased the number of NFS buffers. No difference.

I'm all out of ideas without spending money now. Maybe a change of access point and/or wireless card is called for.

Has anyone had any success with any 802.11n kit yet?

---

### Post by AndyC_772 on 2007-02-03
I take it that's a 'no' then? :(

---

